# Research: Canonical Karpathy and Agent-Loop Sources

> Resolves issue #4 — "Find canonical Karpathy and agent-loop sources"
> Researched 2026-08-26 against primary sources (authors' own pages, arxiv, GitHub).

---

## What "Karpathy-style" Agentic Engineering Means

Based on direct reading of his primary sources, Karpathy-style agentic engineering rests on four interlocking ideas:

1. **Objective-function primacy** — Do not hand-code solutions. If you can *evaluate* whether something is correct (test passes, game won, task done), you can automate search over program space. The bottleneck shifts from writing code to *defining good evaluators*. (Source: Software 2.0, 2017)

2. **LLM as operating-system kernel** — LLMs are not classifiers; they are general-purpose reasoning engines that can call tools, spawn sub-agents, browse the web, write and execute code, and maintain memory. The LLM is the CPU; everything else is a peripheral. (Source: Intro to Large Language Models, 2023)

3. **Iteration over perfection** — Build a tight observe→think→act loop, evaluate output against a concrete criterion, feed the signal back, repeat. This is Software 2.0 applied to software engineering itself.

4. **Vibe coding as a mode of development** — The programmer delegates implementation to an LLM while steering intent at a high level. The programmer's job is specifying objectives and grading outputs, not writing lines. The evaluator *is* the program. (Source: YC AI Startup School 2025 talk + public statements Feb 2025)

---

## Part 1 — Top Karpathy Sources on Agentic Thinking

### 1. "Software 2.0" (2017)

- **URL:** https://karpathy.medium.com/software-2-0-a64152b37c35
- **Format:** Blog post (Medium)
- **Confidence:** ★★★★★ High — authored directly by Karpathy; 61k claps; frequently cited as the ur-text of his agentic worldview.
- **Summary:** Karpathy argues that neural networks represent a fundamental paradigm shift: instead of writing explicit code, we specify a desired behaviour, provide training data, and let optimisation search program space. The key predicate for this transition is repeated, cheap evaluation. Any domain where you can define a loss function and measure success becomes a candidate for Software 2.0. This essay is the philosophical root of every claim he makes about autonomous agents — the idea that the *evaluator* is the real bottleneck, and that data labelling (i.e. specifying correct outputs) is the new programming. He explicitly predicts Software 2.0 IDEs that help humans curate training data and labels rather than write code — a direct precursor to agentic coding tools.

---

### 2. "Intro to Large Language Models" (2023)

- **URL:** https://www.youtube.com/watch?v=zjkBMFhNj_g
- **Format:** YouTube video (~1 hour, general-audience track)
- **Confidence:** ★★★★★ High — filmed and uploaded by Karpathy; his most-referenced treatment of LLMs as autonomous systems.
- **Summary:** This talk introduces the "LLM OS" framing: LLMs are the new operating-system kernel, with tools, memory, and sub-agents as peripherals. Karpathy walks through the LLM as a general-purpose CPU for reasoning — it can call a calculator, search the web, write and run Python, spawn sub-agents, and maintain context across steps. He discusses the current capability ceiling (unreliable multi-step reasoning, hallucination), the value of scaffolding, and the near-future trajectory toward increasingly autonomous loops. This is the primary source for the "LLM OS" concept that underlies most contemporary agentic engineering discourse.

---

### 3. "State of GPT" — Microsoft Build 2023

- **URL (video):** https://www.youtube.com/watch?v=bZQun8Y4L2A
- **URL (slides):** https://karpathy.ai/stateofgpt.pdf
- **Format:** Conference talk + slide deck
- **Confidence:** ★★★★★ High — delivered by Karpathy at Microsoft Build; slides are on his personal site.
- **Summary:** A systematic breakdown of how GPT models are trained (pre-training, supervised fine-tuning, reward modelling, RLHF) and, crucially, *how to use them effectively*. The agentic section covers: prompting strategies that improve multi-step reasoning (chain-of-thought, self-consistency), how to decompose long-horizon tasks, how to use tools, and how to structure multi-agent pipelines. The talk frames the practitioner's job as understanding the model's training distribution and aligning prompts to it — a concrete methodology for building reliable loops.

---

### 4. "YC AI Startup School" Talk — 2025

- **URL:** https://www.youtube.com/watch?v=LCEmiRjPEtQ
- **Format:** Conference talk (~1 hour, general-audience)
- **Confidence:** ★★★★☆ High — delivered by Karpathy at Y Combinator's AI Startup School; referenced on his personal site (karpathy.ai).
- **Summary:** Karpathy's most recent public talk on the state of AI and its implications for software products and startups. Covers his current thinking on agentic AI, "vibe coding" (programming by describing intent to an LLM and grading outputs rather than writing lines), evaluation-driven development, and the shift from Software 1.0 to a world where the model does most implementation. Explicitly argues that defining and running good evals is the highest-leverage engineering activity in an AI-native product.

---

## Part 2 — Top Non-Karpathy Sources on Verification-Driven Agent Loops

### 1. "ReAct: Synergizing Reasoning and Acting in Language Models" (2022)

- **URL:** https://arxiv.org/abs/2210.03629
- **Format:** Academic paper (ICLR 2023)
- **Authors:** Shunyu Yao, Jeffrey Zhao, Dian Yu, Nan Du, Izhak Shafran, Karthik Narasimhan, Yuan Cao (Princeton / Google)
- **Confidence:** ★★★★★ High — ICLR 2023; 13 blog links on arxiv; the most-cited formal specification of the think-act-observe agent loop pattern.
- **Summary:** ReAct formalises the canonical agent loop: interleave *reasoning traces* (Thought) with *environment actions* (Act) and *environment observations* (Observe). This is the core architecture of most production agentic systems. The paper shows that interspersing reasoning with action overcomes hallucination and error-propagation seen in pure chain-of-thought, while retaining interpretability. Evaluated on QA (HotpotQA, FEVER) and interactive decision-making (ALFWorld, WebShop), ReAct outperforms imitation and RL baselines. Almost every subsequent coding agent (SWE-agent, Claude Code, etc.) implements a variant of this loop with domain-specific tool schemas.

---

### 2. "SWE-bench: Can Language Models Resolve Real-World GitHub Issues?" (2023)

- **URL:** https://arxiv.org/abs/2310.06770
- **Format:** Academic paper (ICLR 2024)
- **Authors:** Jimenez, Yang, Wettig, Yao, Pei, Press, Narasimhan (Princeton)
- **Repo / Leaderboard:** https://www.swebench.com/
- **Confidence:** ★★★★★ High — ICLR 2024; the dominant evaluation framework for autonomous software-engineering agents.
- **Summary:** SWE-bench operationalises the agent-loop evaluation problem for software engineering: given a real GitHub repository and a real issue description, can an LLM produce a patch that passes the project's test suite? The benchmark contains 2,294 issues from 12 popular Python projects. Crucially, it enforces *objective verification*: the stopping condition is test-suite passage, not human judgement. At launch, the best model (Claude 2) solved only 1.96% of tasks — demonstrating a concrete, measurable gap between capability and autonomous execution. SWE-bench is now the standard leaderboard for coding agents and the best public example of the evaluation-gated loop Karpathy describes.

---

### 3. "Reflexion: Language Agents with Verbal Reinforcement Learning" (2023)

- **URL:** https://arxiv.org/abs/2303.11366
- **Format:** Academic paper (NeurIPS 2023)
- **Authors:** Shinn, Cassano, Berman, Gopinath, Narasimhan, Yao (Northeastern / MIT / Princeton)
- **Confidence:** ★★★★★ High — NeurIPS 2023; the canonical treatment of failure-mode analysis and verbal self-correction in agent loops.
- **Summary:** Reflexion directly addresses the core problem of agent loops: how does an agent learn from failure without retraining weights? The answer is verbal reflection: after a failed attempt, the agent generates a natural-language critique of what went wrong and stores it in an episodic memory buffer. On the next attempt, this reflection is prepended to the prompt. This implements a lightweight feedback and stopping-condition mechanism: the agent keeps iterating until it passes the evaluation criterion (or exhausts a budget). Reflexion achieves 91% pass@1 on HumanEval coding (vs. GPT-4 at 80%) by exploiting this loop. It directly models the iteration, feedback, and failure-mode components of Karpathy-style agentic engineering.

---

### 4. "SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering" (NeurIPS 2024)

- **URL (paper):** https://arxiv.org/abs/2405.15793
- **URL (repo):** https://github.com/SWE-agent/SWE-agent
- **URL (minimal version):** https://github.com/SWE-agent/mini-SWE-agent
- **Format:** Academic paper + open-source repo
- **Authors:** Yang, Jimenez, Wettig, Lieret, Yao, Narasimhan, Press (Princeton / Stanford)
- **Confidence:** ★★★★★ High — NeurIPS 2024; open-source; the most complete practical demonstration of a verification-driven autonomous coding agent.
- **Summary:** SWE-agent demonstrates that the *interface between agent and environment* is as important as the model itself. It wraps a shell environment and repository in a custom Agent-Computer Interface (ACI) — purpose-built for an LLM's needs (compact file views, persistent search, linting feedback, explicit submission command). The agent runs a ReAct-style loop: it reads the issue, plans, edits code, runs tests, observes failure messages, and iterates until the test suite passes or the budget is exhausted. The minimal version (`mini-swe-agent`) distils this to ~100 lines of Python and achieves >74% on SWE-bench verified — making it the closest practical embodiment of the "define-evaluate-iterate" pattern Karpathy describes. The mini version in particular is a reference implementation worth studying.

---

## Part 3 — Supporting Sources

### OpenAI Evals (2023–ongoing)

- **URL:** https://github.com/openai/evals
- **Format:** Open-source framework + benchmark registry
- **Confidence:** ★★★★☆ High — maintained by OpenAI; the most widely used open framework for building agent evaluators.
- **Summary:** OpenAI Evals provides the tooling to build the verification layer of an agent loop — the component that decides whether an agent's output is correct. It includes templates for model-graded evals, string-match evals, and custom code evals, plus a growing registry of public benchmarks. As Greg Brockman noted: "If you are building with LLMs, creating high-quality evals is one of the most impactful things you can do." This repo operationalises that claim. Relevant for anyone building the feedback signal in an autonomous agent loop.

---

## Synthesis — Reading Order

For someone building an autonomous agent loop:

1. **Read Software 2.0** — understand *why* evaluation-driven development is the paradigm shift.
2. **Watch Intro to Large Language Models** — understand the LLM OS architecture and what peripherals (tools, memory, agents) look like.
3. **Read ReAct** — understand the formal structure of the think-act-observe loop.
4. **Read Reflexion** — understand how to handle failure modes and implement self-correction.
5. **Study mini-SWE-agent source** (100 lines) — see the minimal viable implementation of all of the above on a real software-engineering task.
6. **Read SWE-bench paper** — understand how to define and run a verification-gated evaluation that serves as the stopping condition.
