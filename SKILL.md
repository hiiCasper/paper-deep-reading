---
name: paper-deep-reading
description: Deep-read academic papers and generate structured Chinese research notes with critical analysis. Use when the user provides an academic paper title, DOI, arXiv/publisher/GitHub/PDF link, local PDF, asks to deep-read/read/organize/summarize an academic paper, or to maintain a paper-reading repository.
---

# Paper Deep Reading

## Overview

Use this skill to turn an academic paper into a long-lived Chinese research note, not a loose summary. Prioritize factual grounding, explicit uncertainty, and alignment with the user's existing paper-reading repository.

When creating or revising a note file, read `references/output-schema.md` for the full note structure.

## Workflow

### 1. Identify the Paper Source

If the user provides a local PDF, read it directly.
If the user provides a URL, open or download the paper from that URL.
If the user only provides a title, search official sources first: arXiv, the publisher page, author homepage, DOI page, conference page, or project page.
If metadata is uncertain, mark it as `Unknown` or `TBD`; do not invent the venue, year, code, dataset, or paper claims.

### 2. Read in Three Passes

First pass: read the abstract, introduction, and conclusion. Identify the problem, core motivation, basic idea, claimed contributions, and main results. Do not stop at surface-level motivation; distinguish the real pain point, missing capability, broken assumption, or research gap.

Second pass: read the method, model, assumptions, algorithms, system design, and definitions. Extract the paper's actual mechanism instead of only giving a high-level paraphrase. Reconstruct how the basic idea follows from the motivation and develops into the concrete method.

Third pass: read the evaluation, tables, figures, ablations, case studies, limitations, and related work. Check whether the experiments support the paper's claims.

### 3. Extract Evidence

Identify the paper's core figures, tables, formulas, algorithms, and definitions.
Include evidence that carries the paper's main claims; if the user asks for exhaustive notes, include every figure, every table, and all important formulas.
For formulas and algorithms, preserve the paper's notation and check variable meanings, value ranges, missing operators, and consistency with the surrounding text.
For tables and figures, explain what conclusion each one supports instead of only describing its appearance.

### 4. Position the Paper Against Prior Work

Identify the closest prior work and the increment claimed by the paper.
Distinguish novelty in method, setting, data, and findings.
If the claimed increment depends on recent work or post-publication impact, search current sources and cite them.

### 5. Perform Critical Synthesis

Judge whether the work is convincing, useful, reproducible, and clearly scoped.
Check the core questions: what problem it solves, what existing practice cannot handle, what is new, who benefits, what can go wrong, how costly it is to reproduce or deploy, and whether the experiments truly test the claims.
Check whether the method genuinely follows from the stated motivation or whether the motivation is mostly post-hoc framing.

Use this step as internal analysis. Do not create a standalone section for it in the final note.
Convert the judgment into the final note's `Strengths`, `Limitations`, and `My Takeaways` sections.
Keep attribution clear when needed: distinguish what the paper demonstrates from what the reader infers.
Make criticism specific.
If evaluating post-publication impact, adoption, or follow-up work, search the web in the same turn and cite the sources used. Do not cite impact from memory.

### 6. Write the Note in Chinese

Use the structure in `references/output-schema.md`.
Keep paper terminology precise; when translation may lose meaning, keep the key English term in parentheses.
Distinguish the authors' claims from your analysis.
Pay special attention to `Motivation and Basic Idea`: explain the most fundamental reason the paper exists and the simplest idea the method builds on.
Keep `Background` concise: record only the chain from background to problem to gap. Do not write a long textbook-style background section.
`Threat Model / Assumptions` is optional. Include it when assumptions materially affect correctness, security, economics, or applicability; otherwise write N/A or omit details.
In `Method`, analyze how the basic idea becomes the concrete method. Base this on the paper text, related work, assumptions, ablations, or system constraints; if the logic is inferred, say that it is an inference.
After `TL;DR`, add a short `毒舌评论`: use one sharp paragraph or 2-3 bullets to give a fact-grounded strong judgment about the paper's real value, biggest weakness, likely exaggeration, or most fragile assumption. It must not be a summary. Be harsh, but do not invent flaws or state uncertain criticism as fact.
`Evaluation` should focus on the experimental design, metrics, and results. Include dataset scale, baselines, or key figures only when they are necessary for understanding the result.
End by connecting the paper to prerequisite/follow-up papers and questions worth revisiting.

### 7. Generate the Note
Use `/Users/felix/WorkSpace/WHU/research/paper/paper-repo` as the paper-reading repository unless the user specifies another repo.
Before editing the repository, inspect the current state with `git status --short` and do not overwrite unrelated user changes.
Create one new folder named with the paper's Chinese title. If a folder with that name already exists, inspect it first and choose a non-destructive path instead of overwriting files.
Copy the paper PDF into that folder and rename it with the paper's Chinese title.
Save the Chinese note as a `.md` file in the same folder.

### 8. Sync the Finished Note to GitHub When Requested
Run `git status --short` again and review the exact files to be committed.
Commit only the new paper folder unless the user explicitly asks for broader changes.
Use a concise commit message that names the paper.
Push to the repository's configured remote and current branch only after the commit succeeds.
