

## Introduction
At the core of LLMs lies an autoregressive Transformer model. This model generates tokens, one at a time, based on the input and the previous sequence of the output's tokens it has generated so far. This repeats until the model outputs a termination token. Tis generation process makes the workload **memory-bound**, underutilizing the computation power of GPUs and limiting the serving throughput.

Since the model weights are constant and the activations only occupy a small fraction of the GPU memory, the way the KV cache is managed is critical in determining the maximum batch size.

In the vLLM paper, they observe that existing LLM serving systems fall short of managing the KV cache memory efficiently. This is because they store the KV cache of a request in contiguous memory space , due to most ML frameworks requiring tensors to be stored in contiguous memory. **However**, the KV cache has unique characteristics: 
1) It Dynamically grows and shrinks over time as the model generates new tokens.
2) Its lifetime and length are not known from what is known earlier.

Inefficiencies in prior systems:
1) Suffer from internal and external memory fragmentation largely because pre-allocation is done prior to the arrival to the KV-Cache.
2) Cannot Exploit the opportunities for memory sharing due to the KV cache of the sequences being stored in sperate contiguous spaces.

vLLM proposes **Paged Attention** which divides the request's KV cache into blocks, each of which can contain the attention **keys and values** of a fixed number of tokens. 
- Blocks are pages
- Tokens are bytes
- Requests are processes
This design alleviates internal fragmentation by using relatively small blocks and allocating them **on demand**.

## Transformer-Based LLM
The task of an LLM is to model the probability of a list of tokens, it is common to factorize the [^1]joint probability over the whole sequence as the product of conditional probabilities.
- This is also known as **Autoregressive decomposition**, where we break down a join probability distribution of a sequence into a product of conditional probabilities, where each element depends on the all prior elements in the sequence.

The most important component of a Transformer-based language model is the self-attention layer which first applies linear transformations on each position to get the **query, key, & value** vectors.

Then the self attention layer computes the attention score by multiplying the query vector at one position with all the key vectors before it.

Other components in a transformer model:
- Embedding layer
- Feed-Forward Layer
- Layer Normalization
- Residual Connection
- Output Logit Computation
- Query, Key, and Value Transformation

Due to the decomposition in the Autoregressive decomposition step, LLM can only sample and generate new tokens one by one and the new generation depends on all the previously generated tokens. Specially, the generation depends on the Key and Value tokens of previously generated tokens and they are typically cached resulting in the **KV cache.** 

The generation computation in the LLM service can be decomposed into two phases:
1) Prompt Phase
	- Takes the users prompt and computes the probability of the first new tokens. Since the computation of the prompt phase can be parallelized using matmul this phase can efficiently use the parallelism inherent in GPU's
2) Autoregressive Generation Phase
	- Model takes one token as input and compute the probability with the key and value vectors. Only the new KV vector are computed at this iteration. The computation at different iterations cannot be parallelized due to the data dependency and often uses matrix-vector multiplication.

Batching the requests to an LLM service is non-trivial for two reasons:
1) Requests may arrive at different times.
2) Requests may have vastly different input and output lengths.
Batching mechanisms such as cellular batch and iteration-level scheduling have been proposed.

## Memory Challenges in LLM Serving

The KV Cache size grows quickly with the number of requests, for a 13B OPT model a single token:
$$ 2 (\text{KV vectors}) \times5120(\text{hidden state size})\times40 (\text{number of layers}) \times2 (\text{bytes per FP16})$$
A KV cache of a single request on this model can be as much as up to 1.6 GB of space.

Complex Decoding Algorithms account for 12% of the total KV cache memory. During the prompt part this can be shared to minimize memory usage however during autoregressive generation phase should remain unshared due to the different sample results and their dependence on context and position.

The system needs to make scheduling decisions, such as deleting or swapping out the KV cache of some requests from GPU memory.

It is outlined that actual effective memory in previous systems can be as low as 20.4%

## Method
vLLM adopts a centralized scheduler to coordinate the execution of distributed GPU workers. The **KV cache manager** effectively manages the KV cache in a paged fashion enabled by the newly proposed algorithm **Paged Attention.** Specifically the KV cache manager manages the physical KV cache memory on the GPU workers through the instructions sent be the centralized scheduler.
![[Pasted image 20260825234054.png]]

### Paged Attention
Paged Attention partitions the KV cache of each sequence into **KV blocks**. Each block contains the key and value vectors for a fixed number of tokens.



[^1]: A joint probability distribution gives the probability that two or more random variables occur together.
	$$P(X=x, Y=y)$$
