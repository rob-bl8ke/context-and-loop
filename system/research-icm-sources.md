# Research: ICM and Van Clief Sources

**Issue:** #3 — Find canonical ICM and Van Clief sources  
**Researched:** 2026-08-26

---

## Summary

**Who is Van Clief?**  
Jake Van Clief is a Marine veteran and University of Edinburgh researcher, and CEO/founder of Eduba (theceo@eduba.io). His GitHub handle is `RinDig` (display: JVRinDig). He created ICM as a general-purpose version of a content-production routing system he built for Eduba.

**What is ICM?**  
The correct name is **Interpretable Context Methodology** — not "Interpreted" (the issue has a minor typo). It was previously called **Model Workspace Protocol (MWP)**; that earlier label appears in the arXiv paper title.

The core claim: *folder structure is agent architecture*. Numbered folders represent pipeline stages; plain markdown files carry the prompts and context that tell a single AI agent what role to play at each step. One agent, reading the right files at the right moment, does the work that would otherwise require a multi-agent framework. The five-layer context hierarchy (Layers 0–4) answers: "Where am I?", "Where do I go?", "What do I do?", "What rules apply?", and "What am I working with?" — loading 2,000–8,000 focused tokens per stage instead of a 30,000–50,000 token monolith.

ICM draws on Unix pipeline design, Parnas's information-hiding criterion, multi-pass compilation, and literate programming. Its explicit contrasts are multi-agent frameworks (CrewAI, LangChain, AutoGen) for sequential human-in-the-loop workflows where those frameworks add unnecessary complexity.

---

## Sources

---

### 1. arXiv Preprint — Primary Paper

**Title:** Interpretable Context Methodology: Folder Structure as Agentic Architecture  
**URL:** https://arxiv.org/abs/2603.16021  
**PDF:** https://arxiv.org/pdf/2603.16021  
**Format:** Academic paper (arXiv cs.AI + cs.HC)  
**Authors:** Jake Van Clief, David McDermott (University of Edinburgh / Eduba)  
**Submitted:** 17 March 2026 (v2: 18 March 2026); 28 pages, 5 figures, 2 tables, 54 references

**Summary:** The canonical academic statement of ICM. Presents what was then called "Model Workspace Protocol (MWP)" — the name ICM superseded for public use. Argues that for sequential human-in-the-loop workflows, framework-level orchestration (multi-agent code) introduces unnecessary complexity: the same outcome can be achieved with a single agent reading the right filesystem at the right moment. Defines the five-layer context hierarchy, stage contracts (Inputs / Process / Outputs), and the principles of layered context loading, plain-text interfaces, and separation of factory configuration from per-run artifacts. Grounded in Unix pipeline design, modular decomposition, and literate programming.

**Confidence:** **High** — authored by Van Clief, published to arXiv, linked directly from his canonical GitHub repos. This is the most citable primary source.

---

### 2. Canonical GitHub Repository — RinDig/Interpretable-Context-Methodology

**Title:** Interpretable Context Methodology (ICM)  
**URL:** https://github.com/RinDig/Interpretable-Context-Methodology  
**Format:** GitHub repository (1.1k stars, 194 forks)  
**Author:** Jake Van Clief (GitHub: RinDig)

**Summary:** The canonical open-source implementation and reference workspace for ICM. Contains the full README explaining the methodology's rationale, the five design principles, the five-layer context hierarchy, stage contracts, observability properties, and portability claims. Includes three example workspaces (`script-to-animation`, `course-deck-production`, `workspace-builder`), a `_core/CONVENTIONS.md` file defining the 15 canonical patterns, and template files. The repo originated as `Model-Workspace-Protocol-MWP-` (the earlier name) before being renamed to `Interpretable-Context-Methodology`. The README also links to the arXiv paper and to the origin repo (`Content-Agent-Routing-Promptbase`).

**Confidence:** **High** — this is Van Clief's own repo, actively maintained, and cross-referenced by all downstream implementations. Best entry point for studying the method hands-on.

---

### 3. ICM Architect — Canonical Implementation Skill

**Title:** icm-architect  
**URL:** https://github.com/RinDig/icm-architect  
**Format:** GitHub repository / Claude Code + Codex skill (1.3k stars, 175 forks)  
**Author:** Jake Van Clief (GitHub: RinDig)

**Summary:** The canonical Claude/Codex skill for designing and restructuring ICM workspaces. Van Clief's most-starred repo. Operates in two modes — Build (extracts the structure already present in how you describe your work and scaffolds the smallest valid workspace) and Restructure (audits an existing folder, classifies every file, proposes a migration map, migrates, and validates). Encodes six ICM workspace forms: Pipeline, Umbrella, Record library, Knowledge bundle, Context map, and System map. Every output is validated with the "walk test": an agent with no memory must orient, act, and report status from the files alone. Contains `references/core.md` (five principles, five-layer hierarchy, naming, token discipline) and `references/forms.md` (six forms in depth) — these two files are the closest thing to a canonical terminology document / glossary for ICM.

**Confidence:** **High** — primary source authored and maintained by Van Clief; effectively the canonical reference implementation and the closest thing to a formal glossary.

---

### 4. Origin Repository — Content Agent Routing Promptbase

**Title:** Content Agent Routing Promptbase (Why I Built a Routing Architecture for AI Agents)  
**URL:** https://github.com/RinDig/Content-Agent-Routing-Promptbase  
**Format:** GitHub repository / long-form README post (135 stars, 23 forks)  
**Author:** Jake Van Clief (GitHub: RinDig)

**Summary:** The proto-ICM system from which the general methodology was extracted. Van Clief's original content-production routing system for Eduba (scripting, animation specs, Remotion video builds, brand management). The README is a detailed practitioner's explanation of why context should be separated by concern — comparing the context window to working memory, and the information architecture to microservices with clear contracts. Introduces the core patterns (canonical sources, one-way dependencies, selective section loading) with concrete token-count comparisons showing focused stages using 1,500–5,000 tokens vs. a monolith at 15,000+. This is the source Van Clief describes as where ICM "grew out of" — useful for understanding the engineering motivation and the practitioner's perspective before the methodology was formalised.

**Confidence:** **High** — primary source authored by Van Clief; the narrative README is the clearest statement of the motivation and the "why" behind ICM.

---

### 5. Clief Notes — Community and Course

**Title:** Clief Notes  
**URL:** https://www.skool.com/cliefnotes  
**Format:** Online community / course (Skool platform)  
**Author:** Jake Van Clief

**Summary:** Van Clief's primary teaching platform, with 46,600 members and 40+ structured lessons at time of research. Contains "The Foundation" course (concepts, folder architecture, prompting framework), bi-weekly competitions, premium templates and artifacts (The Vault), and VIP resources (The Drawing Room). The community is active with members sharing ICM implementations across domains. This is where the bulk of Van Clief's instructional video content lives; community members have uploaded his videos to NotebookLM for AI-assisted study. Useful for applied examples, community Q&A, and Van Clief's direct explanations of edge cases (CoWork compatibility, multi-model portability, etc.).

**Confidence:** **High** (as a primary source channel) — Van Clief runs and participates actively. **Note:** much of the lesson content requires membership; the community feed is viewable but the classroom is gated.

---

## Secondary Sources

---

### 6. ktnCodes/icm-template — ICM + Karpathy Extension

**Title:** ICM — Interpretable Context Methodology (Template)  
**URL:** https://github.com/ktnCodes/icm-template  
**Format:** GitHub repository (39 stars)  
**Author:** ktnCodes (community member)

**Summary:** A model-agnostic template that implements ICM and extends it with Karpathy's LLM knowledge base architecture (raw → compile → wiki → Q&A). Contains a `docs/methodology.md` that is a faithful and well-written secondary explanation of the five-layer hierarchy, the five design principles, stage contracts, and the compilation metaphor. Also includes a PDF of the original paper (`docs/Interpretable_Context_Methdology_.pdf`) and links to the MWP repo. The "compilation metaphor" extension — treating the LLM as a compiler with defined inputs and structured outputs rather than a chatbot — is a useful synthesis of ICM with Karpathy's thinking. Useful for studying the methodology applied to knowledge-compilation pipelines.

**Confidence:** **Medium** — faithfully explains ICM and cites Van Clief & McDermott correctly; the Karpathy extension is the author's own synthesis, not Van Clief's. Good secondary source.

---

### 7. jonathanmalkin/icm-field-guide — Community Field Guide

**Title:** ICM Field Guide  
**URL:** https://github.com/jonathanmalkin/icm-field-guide  
**Format:** GitHub repository / Claude/Codex skill (5 stars)  
**Author:** Jonathan Malkin (community member)

**Summary:** An unofficial, read-only community companion to ICM focused on fit assessment, pattern selection, and decision aids — explicitly not a replacement for the canonical ICM Architect. Covers which ICM pattern fits a given workflow, how to compare workspace forms (e.g. company brain vs. research hub), and operational cautions. References are pinned to a specific commit of RinDig/icm-architect for stability. Designed to be used before building: "use the Field Guide to decide whether ICM is the smallest sufficient mechanism." Useful as a contrasting perspective on when to use or not use ICM.

**Confidence:** **Medium-Low** — useful for applied pattern selection; secondary community source, not authored by Van Clief. Best used as a complement to the primary sources.

---

## Terminology Note

| Term used in issue | Correct term |
|---|---|
| "Interpreted Context Methodology" | **Interpretable** Context Methodology (ICM) |
| "Van Clief" | Correct — full name is **Jake Van Clief** |
| ICM | Correct; earlier name was **Model Workspace Protocol (MWP)** |

The issue's terminology ("Interpreted" vs. "Interpretable") is a one-word difference. The arXiv paper title contains "Interpretable" and that is what all primary sources use. The methodology is sometimes described as making context *interpretable* to a single agent — the name signals that design intent.

---

## What Contrasts with ICM

The following are useful contrast sources when extracting ICM concepts:

- **Multi-agent frameworks** (CrewAI, LangChain, AutoGen) — ICM's explicit foils. Van Clief acknowledges they work but argues they add engineering overhead for sequential human-in-the-loop workflows.
- **Anthropic's Model Context Protocol (MCP)** — ICM itself distinguishes the two: MCP standardises *how* models access external tools (the integration layer); ICM addresses *how to structure context delivery* across workflow stages. They are complementary, not competing.
- **Karpathy's agentic engineering approach** — frequently integrated with ICM (the compilation metaphor) rather than contrasted with it; the two approaches occupy different layers of the same problem.

---

## Recommended Reading Order

1. **arXiv paper** (https://arxiv.org/abs/2603.16021) — canonical definition, academic treatment
2. **RinDig/Interpretable-Context-Methodology README** — hands-on rationale, design principles, example workspaces
3. **Content-Agent-Routing-Promptbase README** — practitioner origin story, "why" motivation
4. **icm-architect `references/core.md` and `references/forms.md`** — closest thing to a terminology glossary
5. **Clief Notes** — applied instruction, video content, community examples
