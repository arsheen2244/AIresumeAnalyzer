<div align="center">

# 🧾 AI Resume Analyzer

**Upload a resume and get an ATS‑compatibility score, the skills it found, a match against a target role, and specific fixes.**

![Status](https://img.shields.io/badge/status-design%20%2F%20planning-lightgrey)
![React](https://img.shields.io/badge/React-planned-61DAFB?logo=react&logoColor=black)
![Python](https://img.shields.io/badge/Python-NLP-3776AB?logo=python&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind%20CSS-planned-06B6D4?logo=tailwindcss&logoColor=white)

</div>

> [!NOTE]
> This repository holds the **design** for the project. The working implementation of these ideas lives in **[resume-compiler](https://github.com/arsheen2244/resume-compiler)**, an evidence‑checked resume analyzer built with Node.js, Express and a local Llama 3.2 model.

---

## ✨ Planned Features

| | Feature | What it means |
|:-:|--------|---------------|
| 📤 | **Resume upload & parsing** | PDF / DOCX → clean, structured text (sections, bullets, dates) |
| 📈 | **ATS score** | Formatting, keyword coverage and section completeness, scored 0–100 |
| 🧠 | **Skill extraction** | NLP / LLM pulls hard and soft skills and normalises synonyms (e.g. *JS* → *JavaScript*) |
| 🎯 | **Job‑role matching** | Compare against a job description: matched, missing and partially matched skills |
| 💡 | **Improvement suggestions** | Rewrite weak bullets with action verbs and measurable impact |
| 🔐 | **Accounts** | Sign in to keep a history of analyses |

## 🏗️ Proposed Architecture

```mermaid
flowchart LR
    U([👤 User]) -->|upload PDF/DOCX + JD| FE[Web UI<br/>React + Tailwind]
    FE -->|REST| API[Backend API]
    API --> P[Parser<br/>PDF/DOCX → text]
    P --> NLP[Skill extractor<br/>NLP / LLM]
    NLP --> SC[ATS scorer<br/>rules computed in code]
    NLP --> MT[JD matcher]
    SC & MT --> REC[Suggestion engine]
    REC --> API
    API <--> DB[(Database<br/>users · analyses)]
    API -->|score + report| FE
```

## 🔄 User Flow

```mermaid
sequenceDiagram
    actor User
    participant UI as Web UI
    participant API as Backend
    participant AI as NLP / LLM
    User->>UI: Upload resume (+ optional job description)
    UI->>API: POST /analyze
    API->>API: Parse document
    API->>AI: Extract skills and experience
    AI-->>API: Structured skills JSON
    API->>API: Compute ATS score and JD match
    API-->>UI: Score, matched/missing skills, suggestions
    UI-->>User: Interactive report
```

## 🧰 Candidate Tech Stack

| Layer | Options under consideration |
|------|----------------------------|
| Frontend | React / Next.js, Tailwind CSS |
| Backend | Flask (Python) or Node.js / Express |
| Database | PostgreSQL or MongoDB |
| AI / NLP | spaCy, an LLM API or a local model through Ollama, scikit‑learn |

## 🗺️ Roadmap

- [ ] Pick the stack and scaffold the frontend and backend
- [ ] PDF/DOCX parsing + skill extraction MVP
- [ ] ATS scoring rules + JD matching
- [ ] AI interview prep from the resume
- [ ] Real‑time job recommendations
- [ ] LinkedIn profile optimisation
- [ ] Multi‑language resumes
- [ ] Downloadable PDF report

---

<div align="center">Built by <a href="https://github.com/arsheen2244">Arsheen Inamdar</a></div>
