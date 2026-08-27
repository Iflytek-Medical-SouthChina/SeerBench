# Knowledge Triplet Extraction Prompt

> Prompt template for knowledge triplet extraction (Stage 1). Given authoritative guideline text, Gemini 3.1 Pro identifies outdated or erroneous claims and outputs structured triplets used to construct clinically grounded distractors and updated answers.

---

**Role:** A senior oncologist and leading expert in multi-site cancer diagnosis, staging, and evidence-based treatment strategies. 

**Objective:** Analyze the provided Reference Material to identify oncology-related medical inaccuracies or suspicious claims. Generate question-building knowledge where the distractor is based on the incorrect text, but the correct answer reflects the current authoritative clinical standard.

**Reference Material:** `{guide}`

**Negative Constraints:**
- No Meta-References: never use phrases such as "According to the text", "The provided material states", or "Based on the reference".
- No Rote Memorization of Statistics: do not ask for specific percentages, p-values, hazard ratios, or study-specific response rates.
- No Study-Specific Hooks: do not use a clinical-trial name as the primary premise; convert trial findings into generalized clinical decision-making or standard of care.
- No Non-Medical Content: ignore formatting, dates, and page numbers; focus on diagnostic criteria, staging, and therapeutic interventions.

**Knowledge Extraction Principles:**
- Clinical Standalone: the extracted medical knowledge must be understandable by a specialist without seeing the reference material.
- Knowledge Triplet Mechanism: identify the current guideline-supported recommendation and the base model's non-current alternative, then output a triplet. `new_knowledge` must state the current recommendation supported by the reference; `old_knowledge` must faithfully represent the base-model alternative rather than a claim from the reference material; `difference` must explain the clinically meaningful contrast between them.
- Extraction Focus (Concept over Tone): extract only concrete factual shifts, such as drug indications, staging criteria, biomarker testing, or specific management steps. Do not extract differences based only on subjective degree, wording preferences, or modal verbs such as "should" versus "must".

**Output:** Return only a strictly valid JSON array. Each object contains `id` and `knowledge_triplet`, where `knowledge_triplet` contains `new_knowledge`, `old_knowledge`, and `difference`.
