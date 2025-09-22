
# Executive Summary Assistant

This project is a **Flask web application** that uses **OpenAI GPT** to generate **executive summaries** for business proposals.

👉 You provide a **provider profile** (your company details) and a **client context** (client’s name, industry, goals, and the recipient’s role such as CEO/CFO/CTO/etc.).
👉 The app generates:

* **Value Selling Points (VSPs)** – short, powerful business phrases.
* **Executive Summary** – a polished, client-ready document with clear structure.
  👉 You can refine the summary in a **chat-like interface** and finally **download it as a Word (.docx) file**.

---

## 🗂 File Overview

### `app1.py`

* The **main backend Flask app**.
* Handles routes (`/setup`, `/`, `/result`).
* Connects to **SQLite database** (`companies.db`) to store provider profiles.
* Calls **OpenAI API** to generate Value Selling Points and Executive Summaries.
* Supports **refinement** of drafts and **export to DOCX**.

---

### `index.html`

* The **main input form** for creating a new executive summary.
* You select a provider company (from DB) and fill client details:

  * Client Name
  * Industry
  * Goals / Challenges
  * Proposed Modules
  * Execution Model
  * Additional Notes
  * **Recipient Role** (important: CEO, CFO, CTO, etc.)
* When submitted, the data goes to the backend → generates VSP + summary.

---

### `setup.html`

* Used to **create a new provider profile** (your company).
* Fields include:

  * Name
  * Industry
  * Services
  * Differentiators
  * Contact Email / Phone
  * Website
* Saved into the SQLite DB (`companies.db`).
* Profiles created here appear in the dropdown on the index page.

---

### `chat.html` (formerly `result.html`)

* The **chat-style result page**.
* Shows the conversation:

  * Left bubbles = user inputs (context, refine prompts).
  * Right bubbles = AI responses (summary, VSP).
* Has a text box at the bottom → you can **refine** the summary with new instructions.
* Has a **Download button** → saves the executive summary (and VSP/context) as **DOCX**, named `<CompanyName>_<RecipientRole>.docx`.

---

## 🚀 How to Run (Step-by-Step for Beginners)

### 1. Clone the project

```bash
git clone https://github.com/your-username/executive-summary-assistant.git
cd executive-summary-assistant
```

### 2. Create virtual environment & install dependencies

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Set environment variables

The app needs secrets for Flask and OpenAI.

#### macOS/Linux

```bash
export OPENAI_API_KEY="your-openai-key"
export FLASK_SECRET="a-strong-secret"
```

#### Windows (PowerShell)

```powershell
$env:OPENAI_API_KEY="your-openai-key"
$env:FLASK_SECRET="a-strong-secret"
```

### 4. Run the app

```bash
python app1.py
```

* Flask will start at **[http://127.0.0.1:5000/](http://127.0.0.1:5000/)**

### 5. Use the app

1. Go to **[http://127.0.0.1:5000/setup](http://127.0.0.1:5000/setup)** → create your provider profile (company).
2. Go to **[http://127.0.0.1:5000/](http://127.0.0.1:5000/)** → fill in client details + recipient role.
3. Submit → redirected to **chat page** with generated summary.
4. Refine if needed.
5. Click **Download** → get Word doc named like `ShekharHospital_CFO.docx`.

---

## 🧠 What This Project Does

* Helps consultants, sales teams, and providers quickly generate **professional executive summaries** with very little input.
* Ensures summaries:

  * Use **role-aware tone** (CEO = strategy, CFO = ROI, CTO = tech focus).
  * Always follow a **consistent structure** (Intro → Goals → Approach → Solution → Delivery → Why Us → CTA).
  * Reuse **business phrases from VSP** to avoid generic writing.
* Saves results into a **.docx file** you can attach to proposals immediately.

---

## ✅ Example

You enter:

* Provider: *GrowBeyond Tech*
* Client: *Shekhar Hospital*
* Industry: *Healthcare*
* Goals: *Improve patient scheduling, records management*
* Proposed Modules: *Zoho PMS + AI voice assistant*
* Role: *CFO*

The app generates:

* **VSP**: Case for Change, Business Value, Proposed Solution
* **Executive Summary** tailored for a **CFO** → highlights ROI, margins, EBITDA, cost savings
* **Downloadable DOCX**: "Exe.docx"

---


