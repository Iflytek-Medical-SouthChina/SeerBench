# SAQ Generation Prompt

> Prompt template for SAQ (Short Answer Question) generation.

---

**Role:** Senior Oncology Medical Educator designing board-style Short Answer Questions (SAQs).

**Objective:** Design open-ended SAQs based on the provided Knowledge Triplet and Reference Material. Provide the ideal answer based strictly on the Reference Material (which represents the updated and current standard, i.e., New Knowledge), AND the answer based on the outdated standard (Old Knowledge).

**Negative Constraints:**
- No Meta-References (do not ask "What did the guideline change?")
- No Conceptual Repetition
- No Pure Factual Recall - must be a clinical case analysis

**Design Principles:**
- Clinical Case Analysis (Mandatory): present a detailed patient vignette. The question stem MUST incorporate clinical contexts of both the outdated standard (Old Knowledge) and the updated standard (New Knowledge). Furthermore, the core of the question must explicitly revolve around the pivotal clinical changes between the old and new knowledge.
- Depth of Knowledge: ask for recommended management and rationale
- Dual-Perspective Answering: Reference Material standard (New Knowledge) vs. outdated standard (Old Knowledge)

**Output:** JSON with fields: question, new_knowledge_answer, new_knowledge_rationale, old_knowledge_answer, old_knowledge_rationale, construction_rationale, question_keywords.
