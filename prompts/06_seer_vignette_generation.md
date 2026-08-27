# SEER-Bench Vignette Generation Prompt

> Prompt template for SEER-Bench vignette generation and item construction. The model receives coded SEER patient records, synthesizes clinical narratives, and constructs masked staging inference items.

---

**Role:** Oncology Board Exam Developer and Clinical Educator. Synthesize high-quality clinical vignettes based on the SEER database to train medical students and residents on TNM staging and cancer prognosis.

**Input Data Format:** Patient records with: Gender, Age, Cancer Location, Pathological Diagnosis, Tumor Size (mm), Cancer Extension, Lymph Node Examined/Positive Status, Bone/Brain/Liver/Lung Metastatic Status, T/N/M/overall Stage.

**Input Data Coding:**
- **Cancer Size**: coded 0 (no mass), 001-988 (exact mm), 989 (>=989\,mm), 990 (microscopic focus), 991-995 (range descriptions), 999 (unknown).
- **Regional nodes examined**: coded as the exact number of nodes examined; exceptions include aspiration (coded 95), combinations of positive aspirated/biopsied/sampled/dissected nodes (coded 98), and unknown/not applicable (coded 99).
- **Regional nodes positive**: coded as the exact number of positive nodes; exceptions include positive aspiration (coded 95), combinations (coded 97), and cases where no nodes were examined (coded 98).  

**Task Instructions:**
- **Scenario Generation**: Convert the provided data into a professional clinical vignette. Do not just list the facts; describe the patient's presentation.
- **The "Omission" Logic**: For every record, randomly select ONE of the following variables to omit from the vignette and turn into the "Question": the T-category, the N-category, the M-category, or the Overall Stage. Ask a clear lead-in question about the omitted variable.
- **Answer & Rationale**: Provide the correct answer and a brief explanation using the latest NCCN guidelines.

**Output:** JSON with fields: `Question`, `Response`, `Rationale`.
