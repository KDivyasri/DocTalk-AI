# 🧠 DocTalk AI: From Conversations to Care

> An end-to-end LLM-powered medical conversation assistant that transforms raw doctor-patient audio into structured clinical insights.

---

## 📌 Overview

**DocTalk AI** is a multi-stage pipeline that goes far beyond simple transcription. It processes real-world medical conversations through validation, reasoning, and feedback layers, simulating a clinical decision support system powered by OpenAI's latest models.

**One-line summary:**
> Built a production-style LLM pipeline that converts doctor–patient conversations into validated clinical insights, combining transcription, reasoning, and feedback into a unified system.

---

## 🚀 Pipeline Architecture

```
Audio Input (HF dataset / local file)
         ↓
Transcription (gpt-4o-mini-transcribe)
         ↓
Speaker Labeling + Formatting
         ↓
Transcript Validation
         ↓
Clinical Template Population
         ↓
Assessment & Plan (gpt-4o)
         ↓
Inconsistency Detection
         ↓
Doctor Feedback
         ↓
Patient Summary
```

---

## ⚙️ Pipeline Stages

### 🎙️ 1. Transcription + Speaker Detection
- Converts audio to text using `gpt-4o-mini-transcribe`
- Uses LLM prompting to label speakers as **Doctor** / **Patient**
- Handles noisy, real-world audio and edge cases (inaudible/unknown)

### ✅ 2. Transcript Validation
- Verifies transcription accuracy using LLM-based validation
- Adds line numbers for traceability
- Includes a **tampering test** by injecting incorrect terms to ensure validation robustness

### 📋 3. Clinical Template Population
- Extracts structured information into a SOAP-style clinical template
- Captures key details: symptoms, history, and patient context
- Restricts outputs strictly to transcript content to **prevent hallucinations**

### 🧠 4. Assessment & Plan (Reasoning Layer)
- Uses `gpt-4o` for higher-level clinical reasoning
- Generates likely diagnoses and recommended next steps
- Elevates the system from NLP → **decision-support behavior**

### ⚠️ 5. Patient Inconsistency Detection
- Identifies contradictions or unclear statements in patient responses
- Flags issues like conflicting symptoms or timeline mismatches

### 🧑‍⚕️ 6. Doctor Feedback Generation
- Evaluates the quality of the clinical interaction
- Highlights missed follow-ups or areas needing deeper exploration
- Provides constructive feedback to improve future consultations

### 📄 7. Patient-Friendly Summary
- Converts clinical insights into simple, non-technical language
- Produces clear, actionable next steps for the patient

---

## 🔄 Dynamic Input Handling

Designed a flexible input layer supporting:
- **Hugging Face medical audio datasets** — for dataset-driven experimentation
- **Local audio file uploads** — for real-world usage

The same pipeline works across both input modes without changing core logic.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Python |
| LLM Models | `gpt-4o`, `gpt-4o-mini`, `gpt-4o-mini-transcribe` |
| Data | Hugging Face Datasets |
| Methodology | Prompt Engineering & LLM Workflows |
| Environment | Jupyter Notebook (Google Colab) |

---

## 💡 Key Highlights

- **Multi-stage LLM pipeline** with modular, composable prompts
- **Validation loops** to reduce hallucinations and ensure clinical accuracy
- Designed for **noisy, real-world** medical conversations
- Combines **NLP, reasoning, and evaluation** in a single unified system
- **Dual data ingestion** — supports both dataset and direct user input

---

## 🎯 What Makes This Unique

Unlike typical transcription systems, DocTalk AI:

- Goes beyond speech-to-text into **clinical reasoning**
- Adds **quality checks and validation mechanisms** at multiple stages
- Simulates a **real-world AI assistant** for healthcare workflows
- Provides value to both clinicians (feedback, inconsistency flags) and patients (plain-language summaries)

---

## 🔮 Future Improvements

- [ ] **Streamlit UI** for interactive, browser-based usage
- [ ] **Batch processing** for large datasets
- [ ] **Confidence scoring** and evaluation metrics per stage
- [ ] **Enhanced speaker diarization** for multi-speaker conversations

---

## 📂 Project Structure

```
doctalk-ai/
├── notebook/
│   └── doctalk_pipeline.ipynb   # Main pipeline notebook
├── audio/
│   └── sample_conversation.mp3  # Sample input audio
├── outputs/
│   ├── transcript.txt
│   ├── clinical_template.json
│   └── patient_summary.txt
└── README.md
```

---

## 🏃 Getting Started

### Prerequisites
```bash
pip install openai datasets
```

### Set your OpenAI API key
```python
import openai
openai.api_key = "your-api-key-here"
```

### Run the pipeline
Open `notebook/doctalk_pipeline.ipynb` in Google Colab or Jupyter and run all cells. You can swap between a Hugging Face dataset or a local audio file using the input toggle at the top of the notebook.

---

## 📬 Contact

Built by **Divyasri Kadambi**
