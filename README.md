


# 🏛️ ADGM Corporate Agent — Intelligent Document Review System


## 📌 Overview

**ADGM Corporate Agent** is an **AI-powered legal document reviewer** tailored for **ADGM (Abu Dhabi Global Market)** compliance.  
It ingests corporate documents, runs *Retrieval-Augmented Generation* (RAG) checks against ADGM references, **flags non-compliance**, inserts **inline comments**, and produces:

- ✅ Reviewed `.docx` with **inline comments**
- ✅ Structured **JSON summary** of issues
- ✅ Packaged **ZIP** for submission

---

## 🚀 Key Features

- **Multi-Document Upload** — handle multiple `.docx` legal files at once.
- **Automated Classification** — identify AoA, MoA, UBO, and more.
- **RAG-Based Compliance** — grounded in ADGM official references.
- **Inline Legal Comments** — insert precise, clause-level feedback.
- **Structured Output** — JSON report for automated workflows.
- **Packaging** — outputs zipped into `final_review_package.zip`.

---

## 🛠️ Tech Stack

- **Language:** Python 3.10+
- **Core AI:** LLM (OpenAI GPT-4o or local model)
- **Embeddings:** `text-embedding-3-small`
- **Vector Store:** FAISS / local DB
- **UI:** Gradio
- **Document Handling:** `python-docx`, `pandas`
- **Orchestration:** Custom parser + RAG engine + checker modules

---

## 📂 Project Structure

```

ADGM-Corporate-Agent/
│
├── app.py                # Main Gradio app
├── parser.py             # DOCX text & clause extraction
├── checker.py            # Rule-based + LLM compliance checks
├── commenter.py          # Inline DOCX comments
├── rag\_engine.py         # RAG index & retrieval
├── graph.py              # Document classification flow
│
├── data/
│   └── reference/        # ADGM regulation documents
│
├── examples/             # Sample DOCX inputs
├── outputs/              # Reviewed docs + JSON summaries
│
├── requirements.txt
├── .gitignore
├── .env.example
└── README.md

````

---

## 📋 Prerequisites

- Python **3.10+**
- `pip` installed
- OpenAI API key *(or local LLM endpoint)*
- ADGM reference documents (PDF/DOCX) for indexing

---

## ⚙️ Installation

```bash
# Clone repository
git clone <your-repo-url> adgm-corporate-agent
cd adgm-corporate-agent

# Create virtual environment
python -m venv .venv
source .venv/bin/activate      # macOS/Linux
.venv\Scripts\activate         # Windows

# Install dependencies
pip install -r requirements.txt

# Copy environment variables template
cp .env.example .env
# Fill in API keys & settings inside .env
````

---

## 🏗️ Build RAG Knowledge Base

```bash
python rag_engine.py build-index \
  --docs data/reference \
  --out data/vector_store
```

> 💡 **Tip:** Ensure your ADGM reference files are in `data/reference/` before running.

---

## ▶️ Run the Application

```bash
python app.py
```

* Open your browser → `http://localhost:7860`
* Upload one or more `.docx` files
* Click **Review** to start compliance analysis

---

## 📊 Example JSON Output

```json
{
  "process": "Company Incorporation",
  "documents_uploaded": 4,
  "required_documents": 5,
  "missing_document": "Register_of_Members_and_Directors.docx",
  "issues_found": [
    {
      "document": "Articles_of_Association.docx",
      "section": "Clause 3.1",
      "issue": "Jurisdiction clause does not specify ADGM",
      "severity": "High",
      "suggestion": "Update jurisdiction to ADGM Courts."
    }
  ]
}
```



## 🎥 Sample Demo Video

📹 **Watch the full 1-minute demo:**
[![Watch Demo](https://img.shields.io/badge/Demo-Video-red.svg)](https://drive.google.com/file/d/1gbi30u27IyB6fsupOPQPKYAd_LXBIaB9/view?usp=sharing)



---

## 📦 Packaging the Entire Codebase

When ready to **submit to recruiter or interviewer**:

```bash
# Ensure outputs are generated
python app.py   # run at least one review

# Create final submission ZIP
zip -r ADGM_Corporate_Agent_Submission.zip \
    app.py parser.py checker.py commenter.py rag_engine.py graph.py \
    requirements.txt .env.example .gitignore README.md \
    data/reference/ examples/ outputs/ final_review_package.zip
```

This `.zip` will include:

* **Full source code**
* **Examples & Outputs**
* **Reviewed documents & summary JSON**
* **All dependencies listed in `requirements.txt`**
* **Instructions inside `README.md`**

---

## 🧪 Testing

```bash
pytest
```

---

## 🔐 Security & Compliance Notes

* **Never commit `.env`** — keep API keys safe.
* Remove/redact real client data before sharing publicly.
* This tool **assists** but does not replace licensed legal review.

---

## 💡 Future Enhancements

* 📝 Clause Auto-Rewrite Suggestions
* 📎 Direct Citation Linking to ADGM Regulations
* 🗂️ Versioned RAG Index Rebuilds
* 👤 Role-Based Review Workflows
* 📊 Dashboard with Review Metrics

---

## 🤝 Contributing

Pull requests welcome!
For major changes, open an issue first to discuss your ideas.

---

## 📜 License

This project is licensed under the **MIT License** — see [LICENSE](LICENSE) for details.

---

> **Pro Tip for Recruiters:**
> Run `python app.py`, upload `examples/Articles_of_Association.docx`, and watch compliance review magic happen ✨

---




