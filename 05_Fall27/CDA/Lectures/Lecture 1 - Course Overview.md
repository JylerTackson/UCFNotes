**AI Computing Infrastructure: LLM Serving and Post-Training Systems** Dr. Qian Lou | Week 1, Monday Aug 24, 2026

---

## 1. Framing: Why this course exists

Dr. Lou opened by being upfront that this isn't the "classic" CDA 5106 (Advanced Computer Architecture) syllabus you might expect. His pitch, distilled:

- **Classical architecture concepts haven't disappeared — they've moved up the stack.** Cache, virtual memory, speculation, and scheduling are all still here, just reincarnated as KV cache, Paged Attention, speculative decoding, and continuous batching. The course teaches these AI-infra mechanisms _as instances of_ the classical principle, not as a divorced new topic.
- **The job-market argument:** models and applications churn fast, but infrastructure is closer to civil infrastructure — expensive to build, slow to replace, and the leverage point where a single improvement compounds across every model that runs on it. Whether you end up an AI researcher or a "traditional" architecture person, infra fluency is the asymmetric skill.
- **This is not an AI/ML course.** No model design, no training-an-LLM-from-scratch, no prompting theory. The target is _the system that makes the model usable in production_ — treating a modern LLM as a workload to profile, bottleneck-hunt, and optimize, the same way you'd approach any other systems-architecture problem.

Practical implication for you: don't walk in expecting ML theory. Walk in expecting workload characterization, bottleneck analysis, and systems design — with LLM inference/post-training as the running example.

---

## 2. Instructor background (context for later readings)

Dr. Lou's research is in AI systems — efficiency, reliability, production security, across models/software/hardware. He mentioned recent publications in top ML/systems venues that will inform some lab material (not required reading, just influence). Relevant since several assigned papers this term (SGLang, PagedAttention/vLLM, FlashAttention — all three of which you already have in the project files) sit squarely in this research area.

---

## 3. The core mental model taught this lecture: black box → white box

This is the actual methodological backbone of the course, and it's worth internalizing now because every lab and both projects will follow it:

1. **Treat a component as a black box first.** Don't ask "how does attention work internally" — ask "given this input, what's the output, what's the latency, what's the cost?"
2. **Profile at the black-box level** across the whole pipeline to find where the workload is actually constrained — compute-bound, memory-bound, communication-bound, or scheduling-bound.
3. **Only once you've identified the bottleneck component do you open it up into a white box** — now you study _why_ it behaves that way and what the design space looks like.
4. **Metrics matter and aren't always aligned** — latency, throughput (tokens/requests per second), cost ($), and memory footprint. Optimizing one can move another; sometimes for the better, sometimes not. Pick the metric that matches what you're actually optimizing for before you start.

This is a completely standard systems-engineering discipline (you'd recognize it from any perf-eng workflow), just applied with LLM serving/post-training as the workload. Nothing exotic — good.

---

## 4. The four-layer AI computing stack

Dr. Lou sketched a rough stack to locate where this course sits:

|Layer|Example concerns|
|---|---|
|Application|Chatbot, agent, routing which model/hardware to use|
|**AI Serving / Model Execution** ← course focus|Batching, KV cache, scheduling, decode loop|
|Hardware substrate|GPU kernels, memory hierarchy|
|(Security/safety)|Explicitly **out of scope** for this course|

The course's center of gravity is the **serving/model-execution layer**, treated from a _service provider's_ perspective — not "I send one prompt, get one answer," but "I have limited hardware, many concurrent users, many models, and I need to hit latency/cost/throughput SLAs across all of them." That reframing (single-user mental model → multi-tenant service mental model) is the perspective shift he wants you to make early.

---

## 5. The classical-architecture → AI-infra mapping table

This was the centerpiece analogy of the lecture — four classical concepts, each re-expressed as a modern serving mechanism (and each maps directly onto one of your three project-file papers):

|Classical concept|AI-infra reincarnation|Where you'll read about it|
|---|---|---|
|**Cache** (locality, hot data near the CPU)|**KV cache reuse** — don't recompute attention keys/values for tokens you've already processed|PagedAttention/vLLM, SGLang (RadixAttention)|
|**Virtual memory** (logical→physical page tables, fragmentation control)|**PagedAttention** — logical KV blocks mapped to non-contiguous physical GPU blocks|PagedAttention/vLLM paper|
|**Speculative execution**|**Speculative decoding** — small draft model proposes tokens, target model verifies/corrects|Mentioned Week 7 on schedule|
|**Scheduling** (task batching/interleaving)|**Continuous batching**, chunked prefill, cache-aware / prefix-sharing schedulers|vLLM scheduler, SGLang cache-aware scheduling|

Dr. Lou's framing device for cache specifically: _cache is your desk, disk is the basement archive, memory is the shelf in between — you keep your most-used books on the desk._ KV cache does the same thing for attention: **don't recompute what you've already computed and can cheaply keep around.**

He was explicit that the course won't spend a month on cache theory or VM theory in the classical sense — one lecture's worth of grounding, then straight into the AI-specific mechanism, because the _design principle_ transfers and that's the transferable skill being taught.

---

## 6. Logistics recap (syllabus is authoritative — this is just what he flagged live)

- **No required textbook.** Readings will be papers + framework docs posted to Webcourses, released roughly a week ahead of when they're needed.
- **Grading structure**, confirmed live: 3 labs + 2 projects + 5% participation, no written midterm/final — Project 1 is the midterm-equivalent, Project 2 is the final-equivalent (report only, no exam).
- **No GPU required.** Every lab has a CPU/trace/simulator/analytical-model path. Lab 1 is measurement-focused; Labs 2–3 are simulator-design labs, so hardware access isn't a blocker for anyone.
- **Office hours:** ~8 hrs/week combined across the two TAs (Sevitha, Jihwan), in-person + Zoom. His advice: attempt the lab yourself first, bring good/specific questions to office hours.
- **Lab 1 timeline:** he plans to release it in about **three weeks** — matches the syllabus's Week 2 "Lab 1 assigned" slot. He'll also share a "map instruction" document specifically for bottleneck identification/measurement, which is the practical tool for Lab 1.
- **Participation (5%)** is meant as an attendance incentive, run informally — occasional cold-call/discussion moments in class rather than a separate assignment.

One live-audience Q&A worth flagging for you specifically, since you're coming in without formal ML background: a student asked essentially "5 years industry experience, no AI background, can I succeed?" — Dr. Lou's answer was **yes**, as long as you're solid on basic math (linear algebra) and comfortable picking up GPU/hardware fundamentals as you go; he said the course will cover the necessary basics rather than assuming prior ML coursework.

---

## 7. How this sets up the rest of the semester

Given the syllabus schedule you already have, this lecture is essentially the **thesis statement** for weeks 2–15: everything from PagedAttention (Week 4) through RadixAttention/SGLang (Week 6) through speculative decoding (Week 7) through distributed serving and post-training infra (Weeks 8–13) is going to keep re-running this same loop:

> **AI workload → bottleneck → architectural principle → system design → implementation/simulation → evaluation**

That loop _is_ the course. Lecture 1 was mostly about convincing you the loop is worth learning and giving you the cache/VM/speculation/scheduling analogy as the on-ramp. Next lecture (Aug 26, per syllabus) goes straight into transformer execution and inference/serving/post-training workload characterization — i.e., you start actually running the loop.

**My read, for what it's worth:** the black-box-then-white-box discipline he's pushing is the right way to approach any unfamiliar system, AI or not — worth internalizing now rather than treating it as course-specific flavor text, since it'll transfer directly to how you should be approaching Lab 1's bottleneck-identification work in three weeks.