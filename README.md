# Fahes (فاحص)
### The Intelligent AI Assistant for Statistical Survey Validation (v1.0)

Fahes (فاحص) is an advanced, multilingual AI-driven system designed to detect logical and semantic discrepancies in statistical surveys in real-time. Operating dynamically during data entry, the platform processes dual Arabic and English inputs concurrently while providing intuitive, human-readable explanations and analysis entirely in Arabic. 

The project aims to proactively elevate national statistical data quality, eliminating the manual overhead and resource drain typically associated with post-collection data cleaning.

---

## Tech Stack & Toolbelt
* **Frontend UI:** HTML5, CSS3, JavaScript (For building dynamic forms, interactive real-time validation, and field highlighting)
* **Core Language & Backend:** Python (FastAPI / Web Server Framework)
* **Data Processing:** Pandas, NumPy
* **Semantic Analysis Model:** HuggingFace Transformers (paraphrase-multilingual-MiniLM-L12-v2)
* **Explanation Generation:** Allam LLM (علاّم) by SDAIA / Tailored Prompt Templates
* **Development Environment:** VS Code & Git Workflow

---

## Core Features & Outputs
For every survey validated, Fahes dynamically outputs four distinct, actionable metrics:
1. **Field Highlighting:** Immediate red-highlighting of erroneous fields within the HTML UI during data entry or batch parsing.
2. **Confidence Score:** A weighted mathematical metric between 0 and 1 representing the overall reliability and truthfulness of the entered row data.
3. **Error Classification:** Categorizing the bug type (e.g., Pure Logical Contradiction vs. Deep Semantic Inconsistency).
4. **Human-Readable Explanation:** Plain, contextual Arabic text generated to explain why the data fields contradict each other, enabling instant user correction.

---

## System Architecture & Workflow
The core backend relies on a modular architecture merging deterministic validation with predictive deep learning:
* **Rule Engine:** A highly performant framework checking explicit mathematical or physical constraints (e.g., Age: 22 vs. Years of Experience: 15).
* **Semantic Similarity Model:** Utilizing multilingual sentence embeddings to detect implicit semantic mismatches (e.g., Degree: Islamic Law vs. Job Title: Senior Software Engineer).
* **Weighted Aggregation Formula:** Melds the Rule Engine and Semantic vectors into a singular unified Confidence Score.

---

## Engineering Team & Responsibilities
The project was successfully built and integrated through the collaboration of the following engineering team, structured by technical specialization and project roles:

* **Eng. Rahaf Al-Shammari**
  * *Role:* Software Engineer
  * *Responsibility:* Architected the full-stack system integration, developed the responsive web interface using HTML, and orchestrated the end-to-end component data flow between the frontend and the backend.

* **Leen Al-Masri**
  * *Role:* Data Architect (Computer Science)
  * *Responsibility:* Designed the unified survey JSON/CSV Schemas and engineered the synthetic benchmarking datasets.
  
* **Renad Al-Aufi**
  * *Role:* Backend Systems Developer (Computer Science)
  * *Responsibility:* Constructed the deterministic logic and structured the hard-coded Rule Engine core.

* **Ghaid Al-Oqaili**
  * *Role:* NLP Specialist (Artificial Intelligence)
  * *Responsibility:* Deployed the Semantic Similarity transformers and developed the error categorization taxonomy.

* **Shahad Al-Obeid**
  * *Role:* Core AI Developer (Artificial Intelligence)
  * *Responsibility:* Formulated the weighted mathematical Confidence Score algorithm and integrated the Allam LLM prompt generation engine.

---

## Getting Started

### 1. Clone the repository
```bash
git clone [https://github.com/Leen-Almasri/LexiAI-System-ICAIRE-AI-Glossary-Challenge-Project-.git](https://github.com/Leen-Almasri/LexiAI-System-ICAIRE-AI-Glossary-Challenge-Project-.git)
cd LexiAI-System-ICAIRE-AI-Glossary-Challenge-Project-
