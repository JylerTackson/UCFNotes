##### Agents defined by OpenAI:
**Agents** are systems that *independently* accomplish tasks on your behalf.

A **workflow** is a sequence of steps that must be executed to meet the user's goal. Applications integrating **LLM's** into their workflow but do **NOT** give them control are not considered agents. 

**Agents** posses the following characteristics that allow it to act reliably and consistently on behalf of a user:
1) It leverages an LLM to manager **workflow execution** and make decisions. Recognizes when the workflow is complete and can **proactively** correct its actions if needed. In case of failure, if can **halt execution** and **transfer control** if needed.
2) It has access to **tools** to interact with **external system** to **retrieve context** and **take actions** dynamically selecting the appropriate tool depending on the workflow's current state, always operating within the guardrails.

---
# When should you build an agent?
There is a very nuanced differenced between the and analysis of building a natural automation algorithm vs an agent. An LLM agent functions by evaluating context, considering subtle patterns, and other suspicious or little details. In the mean time a traditional rules engine works like a checklist, flagging transactions based on preset criteria. 
1) **Complex decision-making:**
	- Nuanced judgement, exceptions, or context-sensitive decisions are great for agents.
2) **Difficult-to-maintain rules:**
	- Rules that become old and outdated.
3) **Heavy reliance on unstructured data:**
	- Natural Language (Documents), or conversations.

---
# Agent Design Foundations
An agent consists of three core components:
1) **Model:**
	- The LLM powering the agent's reasoning and decision making.
2) **Tools:**
	- External functions of APIs the agent has access too.
3) **Instructions:**
	- Explicit Guidelines and guardrails defining how the agent behaves.

Using the OpenAI [[Agents SDK]]. You can implement an agent using the following:
```Python
weather_agent = Agent(
	name = "Weather agent",
	instructions = "You are a helpful agent who can talk to users about the weather.",
	tools=[get_weather],	
)
```

---
## Selecting your models
It is beneficial to allow you model to be dynamic because not every task requires the smartest model. A simple retrieval task can be handled by smaller faster models.

Baseline approach is to build your agent prototype with the most capable model for every task to establish a performance baseline. Form there, try swapping in smaller model sand see if they still achieve acceptable results. If you do it this way you are only limiting the tools/tasks that are being throttled by the smaller models.

The principals for choosing the right model:
1) Set up evals to establish a performance baseline
2) Focus on meeting your accuracy target with the best models available
3) Optimize for cost and latency by replacing large models with smaller ones where possible.

---
## Defining tools
Tools extend agent's capabilities by using APIs from underlying applications or systems. For legacy without APIs, agents can rely on computer-use to interact through the UI just as a human would.

| Type          | Description                                                                                         |
| ------------- | --------------------------------------------------------------------------------------------------- |
| Data          | Enable agents to retrieve context and information necessary for exection                            |
| Action        | Enable agents to interact with systems to take *actions*.                                           |
| Orchestration | Agents themselves can serve as tools for other agents. Manager Pattern in the Orchestration section |

---
## Configuring instructions

The following are considered best practices for agent instructions:
- **Use existing documents:**
	- When Creating routines, use existing operating procedures, support scripts, or policy document to create LLM-friendly routines.
- **Prompt agents to break down tasks:**
	- Providing smaller, clearer steps from dense resources helps minimize ambiguity and helps the model better follow instructions.
- **Define clear actions:**
	- Make sure every step in your routine corresponds to a specific action or output.
- **Capture edge cases:**
	- Real-world interactions often create decision points such as how to proceed when a user provides incomplete information or asks an unexpected questions.

Sample prompt inllustrating this approach with the `o1` or `o3-mini` models:
```python
“You are an expert in writing instructions for an LLM agent. Convert the following help center document into a clear set of instructions, written in a numbered list. The document will be a policy followed by an LLM. Ensure that there is no ambiguity, and that the instructions are written as directions for an agent. The help center document to convert is the following {{help_center_doc}}”
```

---
## Orchestration
Orchestration patters fall into two categories and it typically helps to start small and build up:
### Single-agent systems
Single models are equipped with appropriate tools and instructions t o execute workflows in a loop. A single agent can handle many tasks by incrementally adding tools, keeping complexity manageable and simplifying evaluation and maintenance without forcing you to orchestrate multiple agents.

Every orchestration approach needs a **'run'**:
- a loop that lets agents operate until an exit condition is reached. [[Agents SDK]] creates agents that are started using `Runner.run()` method which loops over the LLM until either:
	1) Final output tool is invoked.
	2) Model returns a response without any tool calls.
```Python
Agent.run(agent, [UserMessage("What's the captial of the USA?")])
```

An effective strategy for managing complexity without switching to a multi agent framework is to use prompt templates. Rather than maintaining numerous individual prompts for distinct use cases, use a single flexible base prompt that accepts policy variables:
```Python
""" You are a call center agent. You are interacting with {{user_first_name}} who has been a member for {{user_tenure}}. The user's most common complains are about {{user_complaint_categories}}. Greet the user, thank them for being a loyal customer, and answer any questions the user may have!
```
Basically you just need to be embedding variables that can change and allow the propmt to be dynamic.

#### When to consider multiple agents:
- **Complex logic:**
	- When prompts contain many conditional statements, and prompt templates get difficult to scale, consider dividing each logical segment across separate agents.
- **Tool Overload:**
	- This issue refers to the number of tools, their similarity, or their overlap. Some implementations successfully manage **15** tools while others often struggling at **10**.
	- Sometimes you may improve performance by providing descriptive names, clear parameters, and detailed descriptions.

### Multi-agent systems
Multiple agents are used when workflow execution is distributed across multiple coordinated agents. There are two broadly applicable categories:

- **Manager:**
	- A central manager agent coordinates multiple specialized agents.
- **Decentralized:**
	- Multiple agents operating as peers handing items to each other.


# Guardrails

## Types of Rails
- **Relevance Classifier:**
	- Ensures agent responses stay within the intended scope by flagging off topic queries
- **Safety Classifier:**
	- Detects unsafe inputs (jailbroken or inject prompts) that attempt to exploit system vulnerabilities.
- **PII Filter:**
	- Prevents unnecessary exposure of **Personally Identifiable Information (PII)** by vetting model output for any potential PII.
- **Moderation:**
	- Flags harmful or inappropriate inputs.
- **Tool Safeguards:**
	- Assess the risk of each tool available to your agent by assigning a rating based on factors to trigger automated actions.
- **Rules-based protections:**
	- Simple deterministic measures to prevent known threats like prohibited terms or SQL injections.
- **Output validation:**
	- Ensures responses align with brand values via prompt engineering and content checks.

## Building Rails
The following heuristic can be effective when developing your guardrails:
1) Focus on data privacy and content safety
2) Add new guard rails based on real-world edge cases and failures you encounter
3) Optimize for both security and UX

# Conclusion
