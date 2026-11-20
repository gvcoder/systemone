# System One Model Apps

This repository contains two Node.js applications built with `@receptron/laya` (Laya System-1 decision model):

1. **[`email-classifier/`](./email-classifier/)** — Console-based email & ticket classification scripts.
2. **[`travel-planner/`](./travel-planner/)** — **WanderWise**, a full-stack deterministic multi-agent travel planning web app.

---

## 1. Email Classifier (`email-classifier/`)

A Node.js (ES Modules) console application that uses `@receptron/laya` to run local ONNX System-1 classification on email subjects and bodies.

### Files
- `email_category_clx.js` — Categorizes sample emails into `Inbox`, `Updates`, `Promotion`, or `Spam`, outputting the chosen category, class probabilities, and input token usage.
- `email_clx.js` — Evaluates a customer support/refund email across three dimensions: `department` (`choice`: `billing`, `support`, `sales`), `urgency` (`score`), and `churn_risk` (`noul`).
- `classification_design.md` — Design specification for the Email Category Classifier.
- `package.json` / `package-lock.json` — Project manifest (`@receptron/laya`).

### Setup & Run
```bash
cd email-classifier
npm install
node email_category_clx.js
# or
node email_clx.js
```

---

## 2. Travel Planner (`travel-planner/` — WanderWise)

A full-stack Node.js, Express, and SQLite web application implementing a **Deterministic Finite State Machine (FSM) Orchestrator** paired with specialized micro-agents, combining `@receptron/laya` with `@google/genai` (Google Gemini).

### Files
- `server.js` — Express server, SQLite initialization (`initDB()`), demo trip seeding, and REST API endpoints.
- `orchestrator.js` — Deterministic FSM transition router (`runTripPipeline`).
- `agents.js` — Specialized travel planning agents.
- `parser.js`, `laya_classifier.js`, `gemini_service.js` — Hybrid NLP/LLM entity extraction, classification, and chat/synthesis.
- `db.js` — SQLite (`better-sqlite3`) persistence layer.
- `public/` — Frontend UI (`index.html`, `app.js`, `style.css`).
- `../design.md` — Software Design Specification for WanderWise.

### Setup & Run
```bash
cd travel-planner
npm install
npm start
# or for development with nodemon:
npm run dev
```
