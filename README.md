<div align="center">

# 🧠 Fahes — فاحص

### Intelligent AI Assistant for Statistical Survey Validation

![Version](https://img.shields.io/badge/Version-1.0-blueviolet?style=for-the-badge)
![AI Powered](https://img.shields.io/badge/AI-Powered-ff69b4?style=for-the-badge&logo=openai&logoColor=white)
![Bilingual](https://img.shields.io/badge/Bilingual-AR%20%2B%20EN-0088cc?style=for-the-badge)
![Real-Time](https://img.shields.io/badge/Validation-Real--Time-00c851?style=for-the-badge)
![License](https://img.shields.io/badge/License-Academic-orange?style=for-the-badge)

> ✅ **جميع ملفات أكواد المشروع تم رفعها في هذا الريبو** — كما أن **واجهة النظام مفعّلة ويمكن تجربة النظام مباشرةً** 🚀

</div>

---

## 📌 Overview

**Fahes (فاحص)** is an advanced AI-powered system designed to proactively detect logical and semantic inconsistencies in statistical survey data in real-time.

The system operates dynamically during data entry, supporting both **Arabic and English** inputs simultaneously, while generating clear, human-readable explanations in Arabic.

> 🎯 **The goal** is to enhance national data quality, reduce human error, and eliminate the heavy cost of post-collection data cleaning.

---

## 🚨 Problem Statement

Traditional validation systems fail to detect complex inconsistencies in survey data, especially:

| ❌ Issue | 💡 Example |
|---|---|
| **Logical Contradictions** | Age = 22 vs Experience = 15 years |
| **Semantic Inconsistencies** | Degree = Islamic Law vs Job = Senior Software Engineer |
| **Cross-Field Conflicts** | Unrealistic salary vs job type |

### 📉 These issues lead to:

- 🔴 Poor data quality
- 💸 Expensive manual cleaning
- ⏳ Delayed decision-making

---

## 🎯 Objectives

Fahes is designed to:

- ✅ Perform **real-time validation** during data entry
- 🌐 Understand **bilingual inputs** (Arabic + English)
- 💡 Provide **clear Arabic explanations** instead of rejection
- 🔄 Support **real-time validation** & **batch file validation** (CSV uploads)
- 📊 Improve overall **data integrity** before analysis

---

## ⚙️ Core Features

| Feature | Description |
|---|---|
| 🔴 **Field Highlighting** | Automatically highlights incorrect fields in real-time |
| 📊 **Confidence Score** | Numeric score (0–1) indicating data reliability |
| 🧩 **Error Classification** | Detects logical vs semantic inconsistencies |
| 💬 **Arabic Explanation** | Explains errors in simple Arabic language |

---

## 🚀 Getting Started

### 1️⃣ Prerequisites

Make sure you have **Python 3.9+** installed, then install all required dependencies:

```bash
pip install pandas sentence-transformers
```

### 2️⃣ Clone the Repository

```bash
git clone https://github.com/your-username/fahes.git
cd fahes
```

### 3️⃣ Verify Project Structure

Ensure all files are in the **same directory** before running:

```
fahes/
├── run_fahis_system.py        ← Main entry point
├── rule_engine.py             ← Rule-based validation
├── semantic_checker.py        ← Semantic similarity model
├── error_classifier.py        ← Error aggregation layer
├── confidence_score.py        ← Confidence score calculator
├── explanation_generator.py   ← Arabic explanation generator
└── fahis_mock_data.csv        ← Survey dataset
```

---

## ▶️ How to Run

### 🔥 Run the Full Pipeline (Recommended)

Runs all modules end-to-end and prints results for every survey record:

```bash
python run_fahis_system.py
```

**Expected output:**
```
Loading data...
Loading model, please wait...
Model loaded successfully!
Running Fahis System...

===== FINAL RESULTS =====

==================================================
ID: 3 | Name: سارة
Status: Has Issues ❌
- [rule_engine] years_experience → خطأ منطقي
- [semantic_model] major + job_title → تناقض دلالي

Explanation:
تم اكتشاف عدد من التناقضات في البيانات المدخلة:
• هناك عدم توافق منطقي في الحقل 'years_experience' مقارنة بالعلاقات الطبيعية بين البيانات.
• يوجد تعارض دلالي بين التخصص والوظيفة بناءً على تحليل المعنى.

Confidence Score: 0.46
...
===== DONE =====
```

---

### 🧩 Run Individual Modules

You can also run each module independently for testing or development:

#### Rule Engine — Logical & Outlier Validation
```bash
python rule_engine.py
```
> Detects logical contradictions, missing fields, and salary outliers.
> Prints per-row errors and overall detection accuracy.

---

#### Semantic Checker — Major vs Job Title Mismatch
```bash
python semantic_checker.py
```
> Loads the multilingual model and checks every record for semantic mismatches.
> ⚠️ Requires internet access on first run to download model weights (~90 MB).

---

#### Error Classifier — Merged Classification Report
```bash
python error_classifier.py
```
> Combines rule engine + semantic model outputs into one unified report.
> Prints a clean/error status for each record and overall accuracy.

---

### 📊 Confidence Score — Module Reference

`confidence_score.py` is a utility module and is **not run directly**.
It is imported and called by `run_fahis_system.py` and `error_classifier.py`.

**Score interpretation:**

| Score | Meaning |
|---|---|
| `1.0` | ✅ No errors — fully trustworthy |
| `0.7 – 0.99` | 🟡 Minor issues — mostly reliable |
| `0.4 – 0.69` | 🟠 Moderate problems — review recommended |
| `< 0.4` | 🔴 Severe issues — do not use as-is |

---

### 💬 Explanation Generator — Module Reference

`explanation_generator.py` is a utility module and is **not run directly**.
It is imported by `run_fahis_system.py` to produce Arabic error descriptions.

---

## 🗂️ Dataset Format

The system expects a CSV file named `fahis_mock_data.csv` with the following columns:

| Column | Type | Description |
|---|---|---|
| `id` | int | Unique record identifier |
| `name` | str | Respondent name |
| `age` | int | Respondent age |
| `education` | str | Education level (Arabic or English) |
| `major` | str | Academic major |
| `job_title` | str | Current job title |
| `years_experience` | int | Years of work experience |
| `salary` | float | Monthly salary (SAR) |
| `error_type` | str | Ground-truth label (for evaluation) |

---

## 🧠 System Architecture

Fahes combines **rule-based logic** + **AI semantic understanding**:

### 1️⃣ Rule Engine
- Detects explicit contradictions
- Fast and deterministic

### 2️⃣ Semantic Similarity Model
- Uses multilingual embeddings
- Detects hidden inconsistencies

### 3️⃣ Confidence Score Engine
- Combines rule-based and semantic outputs into a unified score

---

## 🔄 Workflow

```
User Input (Form / CSV)
        ↓
Rule Engine Validation
        ↓
Semantic Analysis Model
        ↓
Error Classification
        ↓
Confidence Score Calculation
        ↓
Arabic Explanation Generation
        ↓
UI Output (Highlight + Insights)
```

---

## 🛠️ Tech Stack

| Category | Technology |
|---|---|
| 💻 **Frontend** | HTML, CSS, JavaScript |
| ⚙️ **Backend** | Python (FastAPI) |
| 📊 **Data Processing** | Pandas, NumPy |
| 🤖 **NLP Model** | HuggingFace Transformers |
| 🧠 **LLM** | Allam (SDAIA) |
| 🧪 **Dev Tools** | VS Code, Git |

---

## 👩‍💻 Team Structure & Task Distribution

> The project follows a **modular pipeline architecture**, ensuring parallel development and clear ownership.

---

### 🧩 Phase 1 — Data Generation & Survey Schema
> 👩‍💻 **Responsible:** Renad Al-Aufi (CS)

**Tasks:**
- Design survey schema
- Generate synthetic data (20–30 records)
- Inject intentional inconsistencies
- Export JSON & CSV

**Deliverables:**

```
📄 data_schema.py
📄 mock_data_generator.py
📄 mock_surveys.json
📄 mock_surveys.csv
```

---

### ⚙️ Phase 2 — Rule-Based Validation Engine
> 👩‍💻 **Responsible:** Ghaid Al-Oqaili (CS)

**Tasks:**
- Build rule engine
- Load rules from JSON
- Detect logical inconsistencies

**Deliverables:**

```
📄 rule_engine.py
📄 rules.json
```

---

### 🧠 Phase 3 — Semantic Analysis Model
> 👩‍💻 **Responsible:** Leen Al-Masri (AI Engineer)

**Tasks:**
- Load transformer model
- Generate embeddings
- Compute similarity
- Define threshold

**Model:** `paraphrase-multilingual-MiniLM-L12-v2`

**Deliverables:**

```
📄 semantic_checker.py
📄 embedding_utils.py
```

---

### 🧩 Phase 4 — Error Classification
> 👩‍💻 **Responsible:** Leen Al-Masri (AI Engineer)

**Tasks:** Classify errors into:

| 🏷️ Error Type |
|---|
| Logical Error |
| Semantic Mismatch |
| Missing Data |
| Outlier Value |

**Deliverable:**

```
📄 error_classifier.py
```

---

### 📊 Phase 5 — Confidence Score Calculation
> 👩‍💻 **Responsible:** Shahad Al-Obeid (AI)

**Tasks:**
- Compute confidence score
- Combine rule + semantic outputs

**Deliverable:**

```
📄 confidence_score.py
```

---

### 💬 Phase 6 — Explanation Generation
> 👩‍💻 **Responsible:** Shahad Al-Obeid (AI)

**Tasks:**
- Generate Arabic explanations
- Use templates or LLM

**Deliverable:**

```
📄 explanation_generator.py
```

---

### 🖥️ Phase 7 — System Integration & UI
> 👩‍💻 **Responsible:** Rahaf Al-Shammari (Software Engineer)

**Objective:** Integrate all modules into a unified pipeline and build user interface.

**Pipeline Flow:**

```
Survey Input → Rule Engine → Semantic Model
      → Error Classification → Confidence Score
      → Explanation → UI Display
```

**UI Features:**
- Survey input form
- Error highlighting
- Error type display
- Confidence score display
- CSV upload support

**Tech Stack:** Gradio, Pandas

**Deliverables:**

```
📄 pipeline.py
📄 app.py
📄 ui.py
```

---

## ⚡ Parallel Development Strategy

After **Phase 1** is complete, the following can proceed simultaneously:

```
Phase 1 Complete
     ├──▶ CS  → Rule Engine       (Phase 2)
     └──▶ AI  → Semantic Model    (Phase 3)
```

---

## 🔄 Final System Flow

```
Input Survey
     ↓
Rule Engine
     ↓
Semantic Model
     ↓
Error Classification
     ↓
Confidence Score
     ↓
Explanation
     ↓
User Interface
```

---

## 💡 Value & Impact

| ✨ Benefit | 💬 Description |
|---|---|
| 📈 **Data Quality** | Improves data quality at the source |
| 💰 **Cost Reduction** | Reduces cost of data cleaning |
| ⚡ **Faster Decisions** | Enables faster decision-making |
| 🤖 **Hybrid Intelligence** | Combines AI + logic in one system |

---

## 🔮 Future Enhancements

- 🔗 Real-time integrations
- 🧬 Advanced ML models
- 🌍 Multi-domain expansion
- 🏛️ Government deployment

---

## 📄 License

> Developed for **research and academic purposes**.

---

<div align="center">

Made with ❤️ by the **Fahes Team**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Gradio](https://img.shields.io/badge/Gradio-FF7C00?style=flat-square&logo=gradio&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)

</div>

<p align="center"> Made with ❤️ by Fahes Team </p> ```
