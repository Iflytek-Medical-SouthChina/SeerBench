# MSQ Generation Prompt

> Prompt template for MSQ (Multiple Select Question) generation.

---

**Role:** Senior Oncology Medical Educator designing board-style Multiple Select Questions (MSQs).

**Objective:** Design clinical MSQs where options explicitly juxtapose the outdated standard (Old Knowledge) against the updated and current standard (New Knowledge). At least 5 options (A-F), with 1-4 correct answers. Provide correct choices based strictly on the Reference Material (which represents the updated and current standard, i.e., New Knowledge) AND choices based on the outdated standard (Old Knowledge).

**Negative Constraints:**
- No Meta-References
- No Conceptual Repetition across questions
- No Subjective Tone Testing ("should" vs. "must")
- No Pure Factual Recall - must be a clinical case analysis

**Design Principles:**
- Clinical Case Analysis (Mandatory): detailed patient presentation leading to a management dilemma. The question stem MUST incorporate clinical contexts of both the outdated standard (Old Knowledge) and the updated standard (New Knowledge). Furthermore, the core of the question must explicitly revolve around the pivotal clinical changes between the old and new knowledge.
- Old/New Integration (Mandatory): options include practices based on the Reference Material (New Knowledge) AND practices based on the outdated standard (Old Knowledge).
- Multiple Select: 5+ options, 1-4 correct answers
- Dual-Perspective Answering: Reference Material standard (New Knowledge) vs. outdated standard (Old Knowledge)

**Output:** JSON with fields: scenario, options, new_knowledge_answers, new_knowledge_rationale, old_knowledge_answers, old_knowledge_rationale, construction_rationale, question_keywords.
