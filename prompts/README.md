# Prompts

Every prompt used to build and evaluate the released artifacts. These are the
same templates reproduced in the paper's appendix; placeholders are written as
`{name}`.

## Update supervision (two-stage construction)

| File | Stage | Purpose |
| :--- | :--- | :--- |
| [`01_knowledge_triplet_extraction.md`](01_knowledge_triplet_extraction.md) | 1 | From guideline text plus the base model's judgment, extract the triplet (current recommendation, base-model non-current alternative, clinical contrast) |
| [`02_render_saq.md`](02_render_saq.md) | 2 | Render a triplet as a short-answer item |
| [`03_render_msq.md`](03_render_msq.md) | 2 | Render as multiple-select with item-local options |
| [`04_render_fitb.md`](04_render_fitb.md) | 2 | Render as fill-in-the-blank |
| [`05_render_emq.md`](05_render_emq.md) | 2 | Render as extended matching: one theme, a shared option pool, several vignettes |

All four Stage-2 prompts require clinical case analysis rather than factual
recall, and require dual-perspective answers so that both the current standard
and the non-current alternative are recorded for each item.

## SEER-Bench

| File | Purpose |
| :--- | :--- |
| [`06_seer_vignette_generation.md`](06_seer_vignette_generation.md) | Convert coded SEER records into a clinical vignette, mask one staging target, and supply the gold answer and rationale |
| [`07_rationale_grading.md`](07_rationale_grading.md) | Judge prompt for rationale accuracy: verify the final answer first, then evaluate reasoning only for answer-correct responses |

## Baseline

| File | Purpose |
| :--- | :--- |
| [`08_rag_inference.md`](08_rag_inference.md) | Inference prompt for the Base RAG baseline |
