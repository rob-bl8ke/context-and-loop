Build this as a **learning system first, knowledge base second, automation platform third**. The trap would be designing a sophisticated ICM/agentic system before you understand either approach deeply enough to know what the architecture should be.

The roadmap should therefore deliberately make the repository **earn its complexity**.

# Roadmap: ICM × Agentic Engineering Knowledge System

The overall progression I’d use is:

```text
Learn
  ↓
Capture
  ↓
Structure
  ↓
Connect
  ↓
Experiment
  ↓
Synthesize
  ↓
Automate
  ↓
Evaluate
  ↓
Refactor
  ↓
Repeat
```

And importantly:

> **The knowledge base should evolve because your understanding changes—not because you predicted the perfect structure upfront.**

## Phase 0 — Establish the experiment

Start with an extremely small Git repository.

```text
ai-engineering-kb/
│
├── README.md
├── AGENTS.md
│
├── inbox/
├── sources/
├── concepts/
├── synthesis/
├── experiments/
└── system/
```

Do **not** create dozens of folders yet.

Your `README.md` should establish the purpose:

```markdown
# AI-Assisted Engineering Knowledge Base

This repository is a living knowledge system for studying,
experimenting with, and synthesising ideas about:

- Interpreted Context Methodology (ICM)
- autonomous / verification-driven agentic engineering
- the relationship between context architecture and agent loops

The repository is both:

1. a knowledge base about these approaches; and
2. an experimental implementation of the approaches themselves.

Structure should evolve as understanding improves.
```

Your first `AGENTS.md` can be almost comically small:

```markdown
# Repository Instructions

This repository is an evolving research and learning system.

When working here:

1. Preserve source provenance.
2. Distinguish source material from interpretation.
3. Prefer improving existing concepts over duplicating them.
4. Do not restructure the repository without explaining why.
5. Record uncertainty rather than presenting speculation as fact.
6. Cross-link related concepts where useful.
```

That's enough.

---

# Phase 1 — Learn before architecting

The first real learning cycle should be deliberately manual.

Study the two approaches independently.

Don't immediately ask:

> How do I combine them?

First ask:

```text
What is ICM actually trying to solve?

What are its fundamental primitives?

What problems arise without it?

What assumptions does it make?


What is Karpathy-style agentic iteration trying to solve?

What are its fundamental primitives?

What makes an autonomous loop safe or useful?

What assumptions does it make?
```

For each meaningful source, create something like:

```text
sources/
    clief/
        foundations-notes.md
        icm-architect.md

    karpathy/
        autoresearch.md
        agentic-engineering-notes.md
```

At this stage, **capture rather than synthesize**.

A source note should contain roughly:

```markdown
# Source

## Citation

...

## What the author is arguing

...

## Important concepts

...

## Examples

...

## Questions I have

...

## My initial interpretation

...

## Related material

...
```

This distinction is critical:

```text
SOURCE NOTE ≠ KNOWLEDGE
```

A source note records what you encountered.

Your actual knowledge base develops later.

---

# Phase 2 — Introduce an AI learning companion

Now start using AI as a **Socratic tutor**, not as an author.

A useful prompt would be:

```text
You are helping me study Interpreted Context Methodology.

Do not simply summarise the material.

First examine the source notes I provide.

Then:

- identify the central claims;
- identify terminology I need to understand;
- identify assumptions behind those claims;
- distinguish principles from implementation details;
- identify anything I appear to have misunderstood;
- ask me questions that test whether I understand the ideas.

Do not modify my knowledge base yet.

The goal of this session is understanding, not documentation.
```

And similarly for Karpathy-style loops:

```text
Help me understand verification-driven autonomous agent loops.

Focus particularly on:

- objective functions;
- feedback;
- iteration;
- bounded action spaces;
- stopping conditions;
- experimentation;
- evaluation;
- failure modes.

Contrast deterministic evaluation with LLM judgement.

Ask questions that expose weaknesses in my understanding.

Do not create permanent knowledge-base material until
we have clarified the concepts.
```

That last instruction matters enormously.

Otherwise your AI will happily populate your repository with plausible-sounding sludge.

---

# Phase 3 — Start extracting concepts

After several source notes, patterns will emerge.

Only then start `concepts/`.

For example:

```text
concepts/
    context-engineering.md
    progressive-disclosure.md
    context-routing.md
    agent-loop.md
    verification.md
    stopping-condition.md
    evaluator.md
```

These should be **source-independent**.

`agent-loop.md` should not be:

> Karpathy says...

Instead:

```markdown
# Agent Loop

An agent loop is...

## Purpose

...

## Typical structure

...

## Properties

...

## Failure modes

...

## Related approaches

- Karpathy AutoResearch
- Ralph
- Claude /goal

## Related concepts

- [[Verification]]
- [[Evaluator]]
- [[Stopping Condition]]
```

This is where your knowledge starts becoming yours.

A useful extraction prompt:

```text
Examine these source notes.

Identify concepts that appear to be generalisable beyond
the individual authors or implementations.

For each proposed concept:

- give it a neutral name;
- explain why it deserves to exist independently;
- identify which sources support it;
- identify overlapping existing concepts;
- identify disagreements between sources;
- recommend whether to:
  - create a new concept;
  - update an existing concept;
  - leave it only as a source note.

Prefer fewer strong concepts over many tiny notes.
```

That prompt will be useful throughout the project's life.

---

# Phase 4 — Build your first synthesis

Only after understanding both independently should you create:

```text
synthesis/
    icm-and-agent-loops.md
```

This is where you begin asking:

```text
ICM:
How does an agent know what it needs to know?

Karpathy:
How does an agent know whether what it did worked?
```

You may eventually develop something like:

```text
            AGENTIC SYSTEM

              Objective
                 │
                 ▼
        ┌── Context Routing ──┐
        │        ICM          │
        └─────────┬───────────┘
                  ▼
                Agent
                  │
                  ▼
                Action
                  │
                  ▼
             Evaluation
                  │
                  ▼
           Goal satisfied?
             /        \
            no        yes
            │          │
            └──────────┘
```

But treat that as a **hypothesis**, not doctrine.

Put statements such as:

```markdown
## Current hypothesis

ICM and verification-driven agent loops appear complementary:

- ICM optimises context selection.
- Agent loops optimise iterative execution.
- Evaluation connects behaviour to outcomes.

Confidence: Medium
```

Now your knowledge base can change without pretending earlier ideas never existed.

---

# Phase 5 — Introduce explicit principles

Eventually you'll encounter recurring conclusions.

Create:

```text
principles/
```

Examples might eventually include:

```text
progressive-context-over-global-context.md
verification-before-autonomy.md
evidence-before-abstraction.md
human-review-at-ambiguous-boundaries.md
skills-should-not-own-domain-knowledge.md
```

But principles have a higher evidentiary threshold.

I'd use this prompt before allowing one:

```text
I am considering promoting this idea into a principle:

<idea>

Act as a skeptical reviewer.

Examine:

- supporting evidence;
- counterexamples;
- assumptions;
- situations where the principle would fail;
- whether it is actually a principle or merely a technique;
- whether an existing principle already covers it.

Recommend one of:

ACCEPT
ACCEPT WITH QUALIFICATION
KEEP AS HYPOTHESIS
REJECT

Explain your reasoning.
```

This stops your repository becoming a graveyard of prematurely declared "best practices."

---

# Phase 6 — Start experimenting

This is where Karpathy's influence should become much stronger.

Create:

```text
experiments/
```

Your first experiments should be extremely small.

For example:

```text
experiments/
    001-flat-context-vs-routed-context/
    002-large-prompt-vs-progressive-disclosure/
    003-agent-loop-with-tests/
    004-llm-evaluator-vs-deterministic-tests/
```

Each experiment should contain:

```text
hypothesis.md
setup.md
runs/
results.md
conclusion.md
```

For example:

```markdown
# Hypothesis

An unfamiliar coding agent using routed context will consume
less context while producing results comparable to an agent
given the repository documentation upfront.
```

Now you're no longer merely studying ICM.

You're **testing it**.

And you're no longer merely reading about agent loops.

You're **using one**.

---

# Phase 7 — Build your first knowledge-maintenance skill

Only now would I introduce a reusable skill.

Something like:

```text
system/
    skills/
        integrate-learning/
            SKILL.md
```

Its responsibility:

```text
new source
   ↓
inspect existing KB
   ↓
identify novelty
   ↓
compare concepts
   ↓
propose updates
   ↓
identify contradictions
   ↓
update provenance
   ↓
suggest experiments
```

The corresponding prompt could be:

```text
Integrate this new learning into the knowledge base.

Do not simply create another note.

First inspect the relevant existing knowledge.

Determine whether the new information:

- reinforces an existing concept;
- contradicts an existing concept;
- refines an existing concept;
- introduces a genuinely new concept;
- affects one of my current principles;
- suggests an experiment;
- changes nothing important.

Preserve the original source separately.

Clearly distinguish:

SOURCE
INTERPRETATION
INFERENCE
EXPERIMENTAL EVIDENCE
CURRENT CONCLUSION

Prefer updating existing knowledge over duplication.

Report proposed structural changes before making major
reorganisation decisions.
```

This might become one of the most important prompts in the repository.

---

# Phase 8 — Introduce ICM routing to the knowledge base itself

By now your KB will be large enough to make context selection meaningful.

That's when you start applying ICM **to itself**.

Instead of:

```text
AI reads everything
```

you move toward:

```text
root
 ↓
determine intent
 ↓
select domain
 ↓
read local context
 ↓
follow references
 ↓
perform task
```

For example:

```text
AGENTS.md
    │
    ├── concepts/
    │      └── AGENTS.md
    │
    ├── experiments/
    │      └── AGENTS.md
    │
    ├── sources/
    │      └── AGENTS.md
    │
    └── synthesis/
           └── AGENTS.md
```

But only create these files where agents genuinely need different instructions.

This is where you start experiencing ICM rather than merely reading about it.

---

# Phase 9 — Create a repository cartographer

At this point your earlier Graphify ideas become relevant.

You could have a skill whose job is:

```text
inspect repository
     ↓
build knowledge map
     ↓
identify:
    orphan notes
    duplicate concepts
    weak links
    overloaded folders
    missing indexes
    routing problems
```

Graph tooling could optionally improve this, but the system should still work using plain filesystem search/grep when Graphify isn't installed. That aligns nicely with the optional-Graphify approach you've already been considering.

A useful prompt:

```text
Audit the knowledge architecture.

Do not judge the factual content yet.

Evaluate the repository as a context-navigation system.

Look for:

- duplicate concepts;
- orphaned documents;
- ambiguous document placement;
- overly broad context files;
- unnecessary nesting;
- weak routing;
- excessive context requirements;
- missing cross-links;
- concepts hidden under source-specific folders.

Ask:

"Could an unfamiliar agent find the minimum sufficient
context for a question without reading most of the repository?"

Suggest improvements but avoid unnecessary restructuring.
```

That question could almost become your ICM quality metric.

---

# Phase 10 — Introduce Karpathy-style maintenance loops

Now you're ready for genuine autonomous maintenance.

For example:

```text
Goal:

Improve the discoverability of the knowledge base.

Loop:

inspect
 ↓
choose one measurable improvement
 ↓
modify
 ↓
run validators
 ↓
measure
 ↓
keep / revert
 ↓
repeat
```

You'll need evaluators.

Some can be deterministic:

```text
broken links
duplicate IDs
missing metadata
orphan pages
invalid references
unreachable concepts
```

Others require judgement:

```text
Is this concept redundant?

Is this routing understandable?

Does this principle have sufficient evidence?

Is this synthesis accurate?
```

This distinction itself becomes something worth documenting:

```text
deterministic evaluation
        vs
semantic evaluation
```

---

# Phase 11 — Add a challenger agent

One danger of a personal knowledge system is confirmation bias.

Create an intentionally adversarial workflow.

Prompt:

```text
Act as a skeptical research reviewer.

Select one current principle or synthesis claim.

Attempt to falsify it.

Look for:

- counterexamples;
- contradictory evidence;
- hidden assumptions;
- terminology being used inconsistently;
- conclusions stronger than the evidence;
- alternative explanations.

Do not rewrite the principle.

Produce a challenge report containing:

CLAIM
SUPPORTING EVIDENCE
COUNTER-EVIDENCE
UNRESOLVED QUESTIONS
RECOMMENDED EXPERIMENT
CURRENT CONFIDENCE
```

Now your KB doesn't just accumulate beliefs.

It **challenges them**.

That's a very Karpathy-like idea applied to knowledge.

---

# Phase 12 — Introduce lifecycle states

Eventually documents should move through stages.

Something like:

```text
captured
   ↓
understood
   ↓
connected
   ↓
tested
   ↓
accepted
   ↓
challenged
   ↓
revised
```

I wouldn't encode that into elaborate tooling initially.

Simple metadata is enough:

```yaml
status: hypothesis
confidence: medium
last-reviewed: 2026-08-18
```

Possible statuses:

```text
source
hypothesis
concept
experimental
accepted
contested
deprecated
```

This creates a huge distinction between:

> "This is in my repository."

and:

> "I believe this is true."

---

# Phase 13 — Begin studying the intersection explicitly

At this stage, your learning questions become much more sophisticated.

Instead of:

> What is ICM?

you start asking:

> Can context architecture itself be optimized through feedback loops?

Or:

> Can context routing effectiveness be measured?

Or:

> Should autonomous agents modify their own routing architecture?

Or:

> Does progressive disclosure outperform retrieval in this situation?

Or:

> Which information belongs in knowledge, skills, agent definitions, or execution state?

Now you're no longer studying two approaches separately.

You're studying the **design space between them**.

That is where I'd expect your most valuable original insights to emerge.

---

# Phase 14 — Allow controlled self-evolution

Eventually you can let the system propose structural changes.

But I would put a human approval boundary here.

```text
Agent discovers architectural problem
          │
          ▼
    proposes restructuring
          │
          ▼
       explains:
       - why
       - evidence
       - migration
       - expected benefit
          │
          ▼
        YOU approve
          │
          ▼
       agent executes
```

I would **not** initially allow:

```text
AI decides architecture
     ↓
AI rewrites architecture
```

because you lose one of the biggest learning opportunities: understanding *why* the architecture evolved.

---

# Phase 15 — Create a recurring learning cycle

At maturity, your normal workflow might simply become:

```text
           FIND SOMETHING INTERESTING
                       │
                       ▼
                    CAPTURE
                       │
                       ▼
                    STUDY
                       │
                       ▼
             DISCUSS WITH AI TUTOR
                       │
                       ▼
                 SOURCE NOTE
                       │
                       ▼
            KNOWLEDGE INTEGRATION
                       │
             ┌─────────┴──────────┐
             │                    │
          reinforces           contradicts
             │                    │
             ▼                    ▼
       update concept       challenge belief
             │                    │
             └──────────┬─────────┘
                        ▼
                 EXPERIMENT?
                    /     \
                  yes     no
                   │       │
                   ▼       │
                execute    │
                   │       │
                   ▼       │
                evaluate   │
                   └───┬───┘
                       ▼
                   SYNTHESIZE
                       │
                       ▼
                  KB EVOLVES
```

That's the system I'd ultimately aim for.

## A small prompt library I'd create early

I'd keep reusable prompts for these jobs:

**Learn**

```text
Teach me this material Socratically.

Test understanding rather than summarising.
Distinguish terminology, principles, assumptions,
implementations and unresolved questions.
```

**Integrate**

```text
Compare this new learning against the existing knowledge base.

Prefer updating existing knowledge over creating duplicates.

Identify reinforcement, contradiction, refinement,
novel concepts and experiment opportunities.
```

**Challenge**

```text
Try to falsify this conclusion.

Search for assumptions, counterexamples,
contradictory evidence and alternative explanations.
```

**Synthesize**

```text
Compare these approaches at the conceptual level.

Do not merely describe them side-by-side.

Identify:
- common principles;
- genuine disagreements;
- complementary responsibilities;
- incompatible assumptions;
- opportunities for synthesis.
```

**Experiment**

```text
Turn this claim into a falsifiable experiment.

Define:

hypothesis
independent variable
observable outcome
control/comparison
evaluation method
success criteria
failure criteria
confounding factors
```

**Reflect**

```text
Review what I have learned recently.

Identify:

- ideas whose confidence increased;
- ideas whose confidence decreased;
- concepts I still misunderstand;
- contradictions I have not resolved;
- experiments that would most improve understanding;
- parts of the knowledge architecture that no longer
  reflect my mental model.
```

**Refactor**

```text
Evaluate the knowledge base as a context system.

Recommend the smallest structural changes that improve
discoverability, progressive disclosure and conceptual clarity.

Do not reorganise merely for aesthetic consistency.
```

Those seven prompts alone could take you surprisingly far.

---

# What I would *not* build initially

Avoid starting with:

```text
20 agents
30 skills
knowledge graphs
vector databases
RAG
automatic ingestion
automatic web scraping
complex metadata schemas
automatic ontology generation
Graphify dependency
MCP infrastructure
agent swarms
```

All of those may eventually have a role.

But they would obscure the thing you're trying to learn.

Your initial system should be:

```text
Git
Markdown
folders
links
one AI agent
a handful of prompts
your judgement
```

Then complexity is introduced only when you experience a problem that warrants it.

That is itself consistent with both philosophies.

## The first four weeks

If I were actually starting this project, I'd make the initial progression:

**Week 1 — Observe**

Study ICM. Capture source notes. Don't automate anything.

**Week 2 — Contrast**

Study Karpathy/agent-loop thinking. Start neutral concept notes and explicitly compare the approaches.

**Week 3 — Experiment**

Perform two or three tiny experiments around context routing, verification, and autonomous iteration.

**Week 4 — Dogfood**

Create the first `integrate-learning` skill and use the repository itself as the test environment.

After that, don't follow a rigid curriculum.

Allow:

```text
learning → friction → hypothesis → improvement
```

to determine what you build next.

The repository's Git history will then become interesting in its own right, because you'll be able to see the evolution from:

```text
notes repository
       ↓
structured knowledge
       ↓
ICM knowledge system
       ↓
experimental laboratory
       ↓
agent-maintained knowledge system
       ↓
personal AI-engineering methodology
```

And I think **that final transformation should be the real objective**.

You aren't trying merely to become knowledgeable about Van Clief and Karpathy. You're using their ideas as starting points to develop a **tested personal methodology for AI-assisted software engineering**, while preserving enough provenance that you can always distinguish their teachings from your own conclusions. You might lean on other ideas and approaches to improve your system later.
