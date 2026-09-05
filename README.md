# MediParse AI

### AI Revenue Recovery Agent for Healthcare Claims

MediParse AI is an AI-powered **Revenue Recovery Agent** that helps identify, diagnose, and recover revenue at risk in healthcare insurance claims.

It processes documents such as hospital bills, insurance authorizations, discharge summaries, prescriptions, and settlement records to detect discrepancies and determine what action should be taken.

> **Detect → Diagnose → Decide → Recover → Verify → Audit**

---

## 🎯 Problem

Healthcare claim information is distributed across multiple documents. Manual comparison can lead to:

* Delayed claim processing
* Billing discrepancies
* Underpayments
* Missing documentation
* Revenue leakage
* Manual reconciliation effort

Example:

```text
Hospital Bill       ₹85,000
Insurance Approved  ₹80,000
Settlement Received ₹68,000
                    ───────
Revenue at Risk     ₹12,000
```

MediParse AI investigates the evidence behind the discrepancy instead of simply flagging it.

---

## 🤖 How It Works

```text
Documents
    ↓
OCR / AI Extraction
    ↓
Structured Claim Data
    ↓
Revenue Risk Detection
    ↓
Root-Cause Analysis
    ↓
Recovery Decision
    ↓
Policy / Guardrails
    ↓
Recovery Workflow
    ↓
Outcome Verification
    ↓
Audit Trail
```

The **AI handles document understanding and reasoning**, while deterministic policies control financial actions.

> **The AI reasons. The policy engine controls.**

---

## ✨ Key Features

### 📄 AI Document Parsing

Extracts clinical and financial information from:

* PDFs
* Scanned bills
* Prescriptions
* Discharge summaries
* Insurance authorization documents

### 💰 Revenue-at-Risk Detection

Identifies potential:

* Settlement mismatches
* Underpayments
* Billing discrepancies
* Coding/documentation mismatches
* Missing authorization
* Financial/TDS discrepancies

### 🧠 Root-Cause Analysis

Correlates evidence across multiple documents to determine the probable reason for a revenue discrepancy.

### ⚡ Bounded Recovery Workflow

Recovery actions are controlled through deterministic policies.

```text
High confidence + complete evidence
        ↓
    Auto workflow

Medium confidence
        ↓
   Human approval

Low confidence / conflicting evidence
        ↓
      STOP
     ESCALATE
```

### 👤 Human-in-the-Loop

Uncertain or high-risk cases are escalated instead of allowing unrestricted AI action.

### 📊 Recovery Analytics

Tracks:

* Revenue at risk
* Amount recovered
* Recovery rate
* Outstanding revenue
* Human escalations
* Processing latency

### 📝 Audit Trail

Records:

* Claim ID
* Evidence
* Confidence
* Policy version
* Decision
* Action
* Human approval
* Outcome

---

# 🧪 Example

**Synthetic demonstration claim**

```text
Claim #1042

Hospital Bill:       ₹85,000
Insurance Approved:  ₹80,000
Settlement:          ₹68,000

Revenue at Risk:     ₹12,000
```

The agent analyzes:

```text
Hospital Bill
      +
Authorization
      +
Discharge Summary
      +
Prescription
      +
Settlement Record
```

Example result:

```text
Revenue at Risk:       ₹12,000
Confidence:             96%
Evidence Completeness:  94%

Probable Cause:
Settlement / Claim mismatch

Decision:
Eligible for recovery workflow
```

> Demonstration data is synthetic/de-identified and does not represent a real patient's claim.

---

# 🏗️ Architecture

```text
Documents
   ↓
Document Processing
   ↓
AI Extraction
   ↓
Revenue Risk Detector
   ↓
Root-Cause Analyzer
   ↓
AI Recovery Agent
   ↓
Policy / Guardrails
   ├── Auto Action
   ├── Human Review
   └── Stop
   ↓
Recovery Workflow
   ↓
Outcome Verification
   ↓
Audit Log + Analytics
```

---

# 🛠️ Tech Stack

| Layer               | Technology            |
| ------------------- | --------------------- |
| Frontend            | React + Vite          |
| Backend             | Python + FastAPI      |
| AI                  | Gemini / Groq         |
| Document Processing | PyMuPDF + pdfplumber  |
| Database            | Supabase + PostgreSQL |
| Styling             | Custom CSS            |
| Deployment          | Vercel + FastAPI      |

---

# 📁 Project Structure

```text
mediparse-ai/
│
├── backend/
│   ├── main.py
│   ├── ai_pipeline.py
│   ├── rcm_engine.py
│   ├── storage.py
│   └── extractor.py
│
├── frontend/
│   ├── src/
│   │   ├── api.js
│   │   ├── components/
│   │   └── pages/
│   └── package.json
│
└── README.md
```

---

# 🚀 Setup & Installation

## Prerequisites

Install:

* Python 3.10+
* Node.js 18+
* npm
* Git

You also need:

* Supabase project
* Gemini or Groq API key

---

## 1. Clone the Repository

```bash
git clone https://github.com/mishraadarsh27/mediparse-ai.git

cd mediparse-ai
```

---

## 2. Backend Setup

```bash
cd backend
```

Create a virtual environment:

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## 3. Configure Environment Variables

Create:

```text
backend/.env
```

Add:

```env
SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_key
GEMINI_API_KEY=your_gemini_api_key
```

If using Groq:

```env
GROQ_API_KEY=your_groq_api_key
```

Do not commit `.env` to GitHub.

---

## 4. Start Backend

From the `backend` directory:

```bash
python main.py
```

The FastAPI server will start on the configured local port.

---

## 5. Frontend Setup

Open a new terminal:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Open the local URL displayed by Vite in your browser.

---

# 🔐 Security

The prototype uses:

* Environment variables for API credentials
* Role-based access
* Evidence-based decisions
* Deterministic recovery policies
* Confidence thresholds
* Human approval
* Stopping rules
* Audit logging

The LLM does not receive unrestricted authority over financial operations.

---

# 📊 Evaluation

MediParse AI should be evaluated using synthetic/de-identified claim batches.

Important metrics:

### Detection

* Precision
* Recall
* Root-cause accuracy

### Recovery

* Recovery rate
* Amount recovered
* Recovery-action precision

### Reliability

* False-positive rate
* Human escalation rate
* Stopping-rule compliance

### Performance

* Extraction latency
* Agent decision latency
* End-to-end latency

### Auditability

* Evidence completeness
* Decision-log completeness
* Action-log completeness

> **The primary outcome is money recovered safely, not the number of alerts generated.**

---

# 🎯 Razorpay AI Buildathon — Track 03

MediParse AI is designed around the **AI Revenue Recovery** workflow:

| Razorpay Requirement   | MediParse AI             |
| ---------------------- | ------------------------ |
| Detect revenue at risk | Revenue-risk detector    |
| Determine why          | Root-cause analyzer      |
| Select intervention    | Recovery decision engine |
| Execute                | Recovery workflow        |
| Bounded actions        | Policy engine            |
| Escalation             | Human-in-the-loop        |
| Stopping rules         | Risk/confidence policies |
| Measure outcome        | Money recovered          |
| Auditability           | Audit trail              |

Official Buildathon:

https://razorpay.com/buildathon/

---

# 🌐 Beyond Healthcare

Healthcare is the initial proof environment, but the core architecture is domain-independent:

```text
Detect
  ↓
Diagnose
  ↓
Decide
  ↓
Recover
  ↓
Verify
```

The same architecture could potentially support:

* SaaS subscription recovery
* E-commerce payment recovery
* B2B invoice recovery
* Insurance claims
* Marketplace settlements
* Payment recovery

### Healthcare is the proof environment.

### Revenue recovery is the platform.

---

# 📚 Real-World Context

The document workflow is inspired by publicly available Indian health-insurance claim requirements.

**Niva Bupa:**
https://transactions.nivabupa.com/claims/pages/claimdocupload.aspx

**HDFC ERGO:**
https://www.hdfcergo.com/claim/register-health-insurance-claim/document-check-list

These sources are used for understanding realistic claim-document structures.

All demonstration claim data is synthetic/de-identified.

---

# ⚠️ Disclaimer

MediParse AI is a prototype.

It does not provide medical advice or unrestricted financial decision-making.

Production deployment would require appropriate security, privacy, regulatory, integration, and operational controls.

---

# 👥 Team

**MediParse AI**

* Aman Kumar
* Ajeet Soni
* Aman Pratap
* Adarsh Kumar

---

## ⭐ Core Idea

> **MediParse AI doesn't just find where revenue is lost. It determines why the revenue is at risk, selects a bounded recovery action, verifies the outcome, and maintains an auditable record.**

**Detect → Diagnose → Recover → Verify**
