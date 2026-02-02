# 🤖 ApplyPro - Autonomous AI Job Hunter

**Status:** Live in Production 🟢

An intelligent automation agent that manages the entire job application pipeline. It autonomously ingests job alerts, filters out noise, uses LLMs to score relevance against my resume, and drafts tailored cover letters.

## 🏗 Architecture
* **Orchestrator:** n8n (Self-Hosted)
* **Intelligence:** OpenAI GPT-4o-mini (JSON Mode)
* **Data Layer:** Google Sheets & Gmail API
* **Notifications:** Telegram Bot API

## ⚙️ The Workflow
1.  **Ingestion:** Monitors Gmail for specific job keywords on a daily schedule.
2.  **Sanitization:** Extracts redirect links and validates URL integrity.
3.  **AI Analysis:**
    * **Context:** Loads my resume into the LLM context window.
    * **Reasoning:** GPT-4o-mini analyzes the Job Description vs. Resume.
    * **Scoring:** Assigns a 0-10 relevance score with a "Why" justification.
4.  **Action:**
    * If Score > 7: Sends a real-time **Telegram Push Notification**.
    * All Jobs: Upserted to Google Sheets for analytics and record-keeping.

## 🚀 Impact
* **90% reduction** in manual job searching time.
* **Zero API waste:** Logic filters ensure expensive LLM calls are only made on valid links.
* **Scalable:** Capable of processing 100+ job alerts per minute.

## 🔧 How to Run
1.  Download `ApplyPro.json` from this repo.
2.  Import into n8n.
3.  Configure Credentials (OpenAI, Google, Telegram).
4.  Update the "Set Resume" node with your own profile.
