# EMQ Generation Prompt

> Prompt template for EMQ (Extended Matching Question) generation.

---

**Role:** Senior Oncology Medical Educator designing board-style Extended Matching Questions (EMQs).

**Objective:** Design clinical EMQs where the shared options list contains elements from BOTH the outdated standard (Old Knowledge) and the updated standard (New Knowledge). Provide the correct answer based strictly on the Reference Material (which represents the updated and current standard, i.e., New Knowledge) AND the answer based on the outdated standard (Old Knowledge), for each vignette.

**Negative Constraints:**
- No Meta-References
- No Text-Matching (no wordplay or terminology formatting tests)
- No Conceptual Repetition across vignettes
- No Pure Factual Recall - must be clinical case analyses

**Design Principles:**
- EMQ Structure: single Theme, shared Options (A-H), >=2 distinct Clinical Vignettes
- Clinical Case Analysis (Mandatory): each vignette is a patient case requiring a clinical decision. Each vignette MUST incorporate clinical contexts of both the outdated standard (Old Knowledge) and the updated standard (New Knowledge). Furthermore, the core of the vignettes must explicitly revolve around the pivotal clinical changes between the old and new knowledge.
- Old/New Integration (Mandatory): options include practices based on the Reference Material (New Knowledge) AND practices based on the outdated standard (Old Knowledge).
- Dual-Perspective Answering per vignette: Reference Material standard (New Knowledge) vs. outdated standard (Old Knowledge)

**Output:** JSON with fields: theme, options, vignettes (each with scenario, new_knowledge_answer, new_knowledge_rationale, old_knowledge_answer, old_knowledge_rationale, construction_rationale, question_keywords).
