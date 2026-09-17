# 🩺 Maamta AI (مامتا اے آئی)
> **Source-Grounded Maternal & Newborn Health Triage Assistant for Pakistan**

Maamta AI is an evidence-grounded, zero-hallucination maternal and newborn triage application designed to support mothers, families, and frontline healthcare workers across Pakistan. Built strictly on approved national clinical guidelines and institutional protocols, it provides reliable guidance for emergency symptom detection, antenatal care, maternal and newborn health, and nutrition.

Supporting authentic Pakistani Roman Urdu and English, Maamta AI makes clinically grounded information more accessible while helping users recognize potential risks and take appropriate next steps.

---
## 🌟 Key Features

* **🛡️ Zero Hallucination (Strict Source Grounding):** Responses are strictly generated from approved clinical guidelines using TF-IDF passage retrieval. If evidence is missing, the system adheres to strict clinical safety guardrails.
* **🚨 Rule-Based Danger Sign Detection:** Employs explicit regex matching for critical obstetric complications (e.g., severe PPH, eclampsia/convulsions, visual disturbances, foul discharge, sepsis) to immediately flag emergencies.
* **🗣️ Authentic Pakistani Roman Urdu & English:** Supports full natural language comprehension without Hindi code-switching, ensuring culturally accurate communication for Pakistani households and healthcare providers.
* **📋 Compulsory Clinical Intake & Vitals:** Integrates a mandatory patient profile (gestational age, maternal age, BP, pulse, bleeding status, active symptoms) to ensure safe and contextual triaging.
* **🎨 Responsive Maternal-Care Interface:** Designed with a modern, high-contrast, theme-adaptive UI (supporting both Dark and Light modes) with soft maternal-tech accents.

---

## 📚 Grounded Clinical Guidelines

Maamta AI answers queries strictly using institutional and national guideline documents placed in the `guidelines/` directory:

1. **Managing Complications in Pregnancy and Childbirth (MCPC):** Clinical protocols for pregnancy, labour complications, and newborn emergencies.
2. **Postpartum Haemorrhage (PPH) Guidelines:** Management of postpartum bleeding and obstetric shock.
3. **National Preterm Labour & Antenatal Corticosteroids Guidelines:** Protocols on dexamethasone/betamethasone and preterm birth care.
4. **National Immunization Policy (EPI Pakistan):** Schedules for BCG, Polio, Pentavalent, PCV, Td, and child immunization.
5. **Nutrition During Pregnancy (Aga Khan University Hospital - AKUH):** Nutritional recommendations, calorie needs, iron/folic acid guidelines, and management of morning sickness, nausea, constipation, and heartburn.

---

## 🏗️ Technical Architecture

* **Framework:** Streamlit
* **Retrieval Pipeline:** `scikit-learn` (`TfidfVectorizer`, Cosine Similarity)
* **Text Extraction & Chunking:** `pypdf` (Sliding window chunking: 180 words, 35 overlap)
* **LLM Engine:** Groq API (`openai/gpt-oss-120b`)
* **Styling:** Modular CSS (`style.css`) using native Streamlit CSS theme variables.

---

## 📂 Project Structure

```text
├── guidelines/                       # Approved PDF guideline documents
│   ├── MCPC_Guidelines.pdf
│   ├── PPH_Management.pdf
│   ├── Preterm_Labour_Guidelines.pdf
│   ├── National_Immunization_Policy.pdf
│   └── Nutrition_During_Pregnancy_AKUH.pdf
├── .streamlit/
│   └── secrets.toml                  # API keys and secret configurations
├── app.py                            # Streamlit core application logic
├── style.css                         # Modular CSS design & responsive layout
├── requirements.txt                  # Python dependencies
└── README.md                         # Project documentation

Clone the Repository
Bash
git clone [https://github.com/](https://github.com/)<your-username>/Maamta_AI.git
cd Maamta_AI

Create and Activate a Virtual Environment
Bash

# Windows
python -m venv venv
venv\Scripts\activate

# Linux / macOS
python3 -m venv venv
source venv/bin/activate

Install Dependencies
Bash
pip install -r requirements.txt
4. Configure API Keys
Create a .streamlit/secrets.toml file in the project root:

Ini, TOML
GROQ_API_KEY = "your-groq-api-key-here"
GROQ_MODEL = "openai/gpt-oss-120b"

5. Add Guidelines
Place the approved national PDF guideline files into the guidelines/ folder.

6. Run the Application
Bash
streamlit run app.py

🔒 Safety & Medical Disclaimer
Maamta AI is designed solely for informational, triage, and educational purposes based on authorized clinical documentation. It does not provide a conclusive diagnosis, medical prescription, or replace consultation with a qualified obstetrician, pediatrician, or medical doctor. In the event of acute maternal or neonatal danger signs, users must seek immediate emergency medical care.
