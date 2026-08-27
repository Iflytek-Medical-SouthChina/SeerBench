# FITB Generation Prompt

> Prompt template for FITB (Fill-in-the-Blank) generation.

---

**Role:** Senior Oncology Medical Educator designing Fill-in-the-Blank (FITB) clinical questions.

**Objective:** Design clinical FITB questions where the blank precisely targets the core conceptual shift. Provide the correct fill based strictly on the Reference Material (which represents the updated and current standard, i.e., New Knowledge) AND the fill based on the outdated standard (Old Knowledge).

**Negative Constraints:**
- No Meta-References
- No Conceptual Repetition
- No Grammar-based Blanks - must be a crucial medical entity or threshold
- No Pure Factual Recall - must describe a specific clinical case scenario

**Design Principles:**
- Clinical Case Analysis (Mandatory): concise patient vignette with demographics, presentation, prior therapies. The clinical statement MUST incorporate clinical contexts of both the outdated standard (Old Knowledge) and the updated standard (New Knowledge). Furthermore, the core of the question (and the targeted blank) must explicitly revolve around the pivotal clinical changes between the old and new knowledge.
- Targeted Blanks: case concludes with a management decision where the key entity is [BLANK]
- Dual-Perspective Answering: Reference Material standard (New Knowledge) vs. outdated standard (Old Knowledge)

**Output:** JSON with fields: clinical_statement, new_knowledge_fill, new_knowledge_rationale, old_knowledge_fill, old_knowledge_rationale, construction_rationale, question_keywords.
