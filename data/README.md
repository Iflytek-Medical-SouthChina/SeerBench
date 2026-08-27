# Data Card

All files in this directory are released under [CC BY-NC 4.0](../DATA_LICENSE),
subject to the SEER data-use terms and the NCCN Guidelines® terms of use
described there.

## `seer_bench/` — the evaluation benchmark

`seer_bench.jsonl` (JSON Lines, one case per line) and `seer_bench.xlsx`
(same content, for browsing). 1,992 cases across 16 cancer-type groups.

| Field | Type | Description |
| :--- | :--- | :--- |
| `ID` | int | Case identifier, 1–1992 |
| `query` | str | Clinical vignette with exactly one masked staging target (T, N, M, or overall stage) |
| `answer` | str | Gold label for the masked target, taken from the coded SEER staging field |
| `rationale` | str | Reference reasoning chain for the gold label |

**Provenance.** Cases are drawn from coded fields in a versioned SEER Research
Data release. Vignettes are natural-language narratives synthesized from those
coded fields; gold labels come from the coded staging variables, not from a
model. Every candidate underwent 100% double-blind physician review (96.9%
raw agreement, Cohen's κ = 0.87); only passing cases are included here.

**Metrics.** *Answer accuracy* requires an exact match to `answer` after
case-insensitive normalization and common variants (e.g. "Stage IA" / "Stage
1A"). *Rationale accuracy* additionally requires the explanation to reproduce
the key clinical reasoning in `rationale`. See `../prompts/` for the grading
prompt.

## `train/` — format-rendered update supervision

Four corpora of 2,530 items each, rendered from the same pool of 2,530 unique
clinical vignettes so that the only variable is supervision structure:

| File | Format |
| :--- | :--- |
| `saq.jsonl` | SAQ — short answer |
| `fitb.jsonl` | FITB — fill in the blank |
| `msq.jsonl` | MSQ — multiple select, item-local options |
| `emq.jsonl` | EMQ — extended matching, shared option pool across vignettes |

Each line is a chat record: `{"messages": [{"role": "user", ...},
{"role": "assistant", ...}]}`.

**Provenance.** Items are rendered from clinical update events identified in
the NCCN Guidelines® and related expert consensus documents. They are
paraphrased questions and rationales and do not reproduce guideline text
verbatim. Average prompt length is comparable across the four formats
(254.3–261.5 tokens), which is what makes the budget-matched comparison in the
paper meaningful.

## Not for clinical use

These artifacts support research on medical knowledge updating and
benchmarking. They must not be used as a basis for diagnosis, staging,
treatment, or medication decisions without qualified clinical oversight.
