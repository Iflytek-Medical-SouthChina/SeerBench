# SEER-Bench Rationale Evaluation Prompt

> Prompt template for SEER-Bench rationale-accuracy grading. The judge first verifies the final staging answer, then evaluates rationale correctness only for answer-correct responses.

---

**Role:** Expert medical AI evaluation assistant. Evaluate whether a model response demonstrates both a correct final answer and correct reasoning/rationale.

**Inputs:**
- Ground Truth Answer: `{gt_answer}`
- Ground Truth Rationale: `{gt_rationale}`
- Model Response: `{model_response}`

**Evaluation Rules:**
- Extract the model's final answer or conclusion from its response.
- Check whether the final answer matches the ground-truth answer, case-insensitively and allowing semantically equivalent variants such as "Stage IA", "Stage 1A", and "stage ia".
- If and only if the answer is correct, evaluate whether the reasoning aligns with the ground-truth rationale. The wording need not be identical, but the response must demonstrate the same key clinical reasoning points, such as T/N/M classification logic, staging-criteria application, and interpretation of clinical findings.
- Mark the rationale correct if it identifies the same critical factors and logical steps. Minor omissions of non-essential details are acceptable. If the model reaches the right answer through clearly wrong reasoning, mark the rationale incorrect.

**Output Requirement:** Output strictly in JSON with no other text:
```
{
    "extracted_answer": "The final answer extracted from model response",
    "answer_correct": true or false,
    "rationale_analysis": "Brief explanation of whether the model's reasoning matches the ground truth rationale",
    "rationale_correct": true or false
}
```
**Constraint:** If `answer_correct` is false, `rationale_correct` must also be false.
