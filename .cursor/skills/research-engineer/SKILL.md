---
name: research-engineer
description: Reads research papers and turns them into faithful implementations with structured article summaries, implementation plans, and modern tooling checks. Use when the user asks to implement a paper, reproduce results, or translate a method into production-ready code.
---

# Research Engineer

## Purpose

Use this skill to implement a research paper faithfully while keeping the work reproducible, technically current, and explicitly tied to the paper's claims.

## Trigger

Apply this skill when the user asks to:
- implement a research paper
- replicate or reproduce a method
- convert a paper method into working code

## Required Workflow

Copy this checklist and keep it updated:

```markdown
Research Engineer Progress
- [ ] Parse paper and extract core claims
- [ ] Write structured article summary
- [ ] Draft implementation plan and design decisions
- [ ] Verify current libraries and APIs (quick web check)
- [ ] Implement baseline faithfully
- [ ] Validate behavior against paper expectations
- [ ] Propose follow-up research questions
```

### 1) Parse paper and extract claims

Before coding, identify:
- research question and why it matters
- hypotheses or explicit paper claims
- method details needed for implementation (architecture, objective, data pipeline, optimization, metrics)
- reported results and evaluation protocol
- assumptions, constraints, and missing details

If the paper is ambiguous, state assumptions clearly and keep them minimal.

### 2) Write a structured article summary

Follow the structure from:
- https://writingcenter.uconn.edu/wp-content/uploads/sites/593/2014/06/How_to_Summarize_a_Research_Article1.pdf

Use this output format:

```markdown
## Paper Summary

### Research question and motivation
[1 concise paragraph]

### Hypotheses or primary claims
- Claim 1
- Claim 2

### Methods
- Design:
- Data:
- Model/system:
- Training/inference procedure:
- Variables/metrics:
- Analysis approach:

### Results
- Key quantitative findings
- Whether findings support claims/hypotheses

### Interpretation and limitations
- Authors' interpretation
- What remains unanswered
- Risks to validity / reproducibility
```

Guidelines:
- paraphrase in your own words
- stay precise and avoid overclaiming
- connect results directly to claims

### 3) Draft implementation plan and design decisions

Produce a concrete plan before writing code:

```markdown
## Implementation Plan

### Scope of faithful baseline
- What will be implemented exactly as written
- What is intentionally out-of-scope for first pass

### Design decisions
- Decision:
  - Paper requirement:
  - Chosen implementation:
  - Alternatives considered:
  - Rationale:

### Work breakdown
1. Data and preprocessing
2. Model/components
3. Loss/objective and optimization
4. Training loop and evaluation
5. Reproducibility tooling (seeds, configs, logging)

### Validation plan
- Unit or shape checks
- Metric parity checks
- Ablation/sanity checks
- Failure criteria
```

Decision rules:
- prefer paper-faithful defaults for baseline
- isolate deviations behind explicit config flags
- prioritize reproducibility over micro-optimizations

### 4) Verify up-to-date tooling (quick check)

Run a quick web check before finalizing dependencies:
- confirm current stable versions of key libraries used by the implementation
- confirm the APIs used are not deprecated
- avoid legacy modules if a maintained standard replacement exists

Document findings in:

```markdown
## Tooling Freshness Check
- Library:
  - Version chosen:
  - Why:
  - Source:
```

Keep this quick and focused on directly used libraries only.

### 5) Implement faithful baseline

Implementation principles:
- map each major code module to a paper component
- keep experiment settings in config files
- separate baseline replication code from exploratory improvements
- ensure deterministic behavior where practical (seed control and explicit randomness handling)
- add concise comments only where paper-to-code mapping is non-obvious

### 6) Validate against paper expectations

After initial implementation:
- run minimal reproducibility checks
- compare trend-level behavior and key metrics with paper values
- report mismatches and likely causes (data, hardware, undocumented tricks, evaluation differences)

Use this format:

```markdown
## Replication Notes
- Matched:
- Partially matched:
- Not matched:
- Most likely causes:
- Next verification step:
```

### 7) Propose follow-up research questions

After baseline completion, generate targeted follow-up questions:
- performance improvements
- stability and robustness
- computational efficiency (time/memory)
- data efficiency and generalization
- system-level optimizations (throughput, scaling, deployment constraints)

Use this format:

```markdown
## Follow-up Research Questions
1. Question:
   - Motivation:
   - Minimal experiment:
   - Success signal:
```

Questions should be testable and tied to specific experiments.

## Quality Bar

A response using this skill is complete only if it includes:
- structured summary aligned with the article-summarization guide
- explicit implementation plan with design decisions
- quick web-based tooling freshness check
- baseline implementation status and replication notes
- concrete follow-up research questions with experiment ideas
