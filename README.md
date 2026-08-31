# IntelliCrew – Agentic Workforce Intelligence Platform 🤖👥

An **agentic, production-grade workforce portal** that unifies hiring, workforce visibility, and reporting in one place. Built with **FastAPI, LangGraph, and Gemini 3.1 Flash Lite**, IntelliCrew routes each request to a specialized AI agent through role-based HR and Manager dashboards, with every agent run logged for full auditability.

---

## 📌 Overview

**IntelliCrew** is an agent-driven platform where HR and managers log in to role-based dashboards, and a **LangGraph orchestrator** routes each request to the right specialized agent — resume parsing, video summarization, centralized reporting, skill-gap ranking, or email. It brings hiring, workforce analytics, and reporting together under a single secure entry point.

This project demonstrates how to build a **multi-agent, orchestrated AI system** with clean role-based access, persistent logging, and a real-world workforce use case.

---

## ✨ Key Features

- 🔐 **Role-Based Access** – Single sign-on with role-based routing for HR and Manager dashboards.
- 📄 **Resume Agent** – Parses name, skills, experience, and role from PDF/DOCX, stores structured data, and embeds resumes into ChromaDB.
- 🎥 **Video Summarization Agent** – Uses YouTube captions or Whisper transcription, then summarizes in chunks via Gemini.
- 📊 **Centralized Report Agent** – Computes org-wide KPIs and utilization, renders polished PDF reports with ReportLab.
- 🎯 **Skill-Gap Analysis Agent** – Scores and ranks talent by required vs current skills, generating a ranked shortlist.
- 📧 **Mail Agent** – Composes and sends selection emails over SMTP, with full audit logging.
- 🗄️ **Full Auditability** – Every resume, summary, and agent run is persisted in SQLite.

---

## 🛠️ Technology Stack

| Layer | Technology |
|-------|-----------|
| **Backend & API** | FastAPI (async REST framework) |
| **Orchestration** | LangGraph (multi-agent routing & state) |
| **AI / LLM** | Gemini 3.1 Flash Lite (extract, summarize, rank) |
| **Transcription** | Whisper (audio → text) |
| **Vector Store** | ChromaDB (resume vector embeddings) |
| **Data & Storage** | SQLite (primary relational store) |
| **Reporting** | ReportLab (PDF report generation) |
| **Communication** | SMTP (email delivery to staff) |

---

## 🧩 The Agents

IntelliCrew is powered by five specialized agents, orchestrated by LangGraph:

### 1. Resume Agent
`Upload Resume → Extract Info → Store in SQLite → Embed to ChromaDB`
HR uploads a candidate PDF/DOCX; the agent extracts structured fields and vectorizes each resume.

### 2. Video Summarization Agent
`Detect Source → Transcribe → Summarize in Chunks → Store Summary`
Branches on YouTube URL vs local file; long videos are re-summarized in groups.

### 3. Centralized Report Agent
`Aggregate Data → Org-wide Metrics → Generate PDF → Deliver to Dashboard`
Pulls active, completed, and bench data to build a leadership-ready report.

### 4. Skill-Gap Analysis Agent
`Analyze Skills → Rank Employees → Project Skill Report → Manager Selects`
Compares required vs current skills for a project and ranks candidates.

### 5. Mail Agent
`Compose Email → Send via SMTP → Employee Notified → Audit in mail_log`
Builds a selection email with reason and role details, then logs it.

---

## 🏗️ Architecture Layers

```
Access Layer        → Login Portal + Role-Based Routing (HR / Manager)
Application Layer    → Dual Dashboards
Orchestration Layer  → LangGraph Agent Orchestrator
AI & Services Layer  → Resume · Video · Report · Skill-Gap · Mail Agents
Data Layer           → SQLite logs + ChromaDB embeddings (full audit trail)
```

---

## 👥 Roles & Permissions

- **HR Dashboard** – Full access. Sees total, bench, and project data, and can upload resumes.
- **Manager Dashboard** – Analytics, reports, and skill-gap. All modules **except** resume upload.
- Permissions are enforced per role, so each user sees only what they should.

---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone <your-repo-url>
cd intellicrew
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Set Up Environment Variables
Create a `.env` file with your keys:
```
GOOGLE_API_KEY=your_gemini_api_key
SMTP_HOST=your_smtp_host
SMTP_USER=your_email
SMTP_PASSWORD=your_password
```

### 4. Run the Application
```bash
uvicorn app.main:app --reload
```

Then open the portal in your browser and log in as HR or Manager.

---

## 🗃️ Data & Logs

Every action is persisted for full auditability, including:
- `employees` – Structured candidate/employee records
- `resume_logs` – Resume embeddings and processing history
- `video_summarization_log` – Video transcripts and summaries
- `mail_log` – Email recipient, reason, and delivery status

---

## 🎯 Future Improvements

- Add more agents (e.g., interview scheduling, performance tracking).
- Migrate from SQLite to PostgreSQL for larger scale.
- Add a real-time notifications system.
- Containerize with Docker for easy deployment.

---

## 👤 Author

**Lakshya Garg**  
Software Engineer

**Team AI Innovators**

---

⭐ If you found this project helpful, feel free to star the repository!
