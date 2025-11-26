# 📘 n8n Automations Repository

This repository contains all the **n8n workflows** I am building and maintaining.
It serves as a collection of workflow automations that handle AI processing, translation, document automation, code execution, and more.

Every workflow is exported directly from n8n as a JSON file so anyone can import, modify, or contribute.

---

## 📑 Table of Contents

1. [About This Repository](#about-this-repository)
2. [Workflows Included](#workflows-included)

   * [1. GPT Auto-Generate & Execute Workflow](#1-gpt-auto-generate--execute-workflow)
   * [2. Korean Novel Translation Pipeline](#2-korean-novel-translation--consistency-pipeline)
3. [Setup & Installation](#setup--installation)
4. [How to Import These Workflows](#how-to-import-these-workflows)
5. [Folder Structure](#folder-structure)
6. [Contributing](#contributing)
7. [License](#license)

---

# 📌 About This Repository

This repo contains n8n workflows I have:

* Built
* Used in production
* Currently improving
* Planning to expand

These workflows automate complex processes such as:

* AI-generated code creation
* Automated script execution
* AI-powered translation
* Google Docs syncing
* Email notifications
* Consistency checks

The goal is to make reusable, high-quality automations that anyone can import and extend.

---

# 🚀 Workflows Included

Below are the automations currently in this repository, with complete explanations of what they do.

---

## **1. GPT Auto-Generate & Execute Workflow**

**File:** `gpt-autogenerate (2).json`
**Category:** AI / Code Automation

### 🎯 Purpose

This workflow takes uploaded problem files, processes them using an LLM (via Ollama API), generates Python code, and automatically executes it with sample and large input datasets.

### 🧠 Key Features

* Accepts **problem statement**, **sample input**, **sample output** via webhook
* Extracts file contents automatically
* Sends data to AI model for **Python code generation**
* Saves generated code locally
* Executes the code with provided large input
* Returns output to the user
* Allows large file uploads through a secondary webhook

### 🧩 Workflow Breakdown

| Step                           | Description                                   |
| ------------------------------ | --------------------------------------------- |
| **Webhook Trigger**            | Receives problem files via POST request       |
| **Extract File Content**       | Converts uploaded binaries into readable text |
| **Ollama API Call**            | Generates Python code from the problem        |
| **Save Code**                  | Saves generated code into `code.txt`          |
| **Run Generated Code**         | Executes Python code and captures output      |
| **Upload Large Input Webhook** | Accepts big datasets for stress-testing code  |
| **Load Output & Respond**      | Returns output as file download               |

### ⭐ Why This Workflow Exists

To fully automate the pipeline of:
**problem → AI → code → run → output**
without any manual work.

---

## **2. Korean Novel Translation & Consistency Pipeline**

**File:** `My workflow.json`
**Category:** AI / Translation Automation

### 🎯 Purpose

A fully automated multi-step system that translates Korean historical novel chapters, corrects naming inconsistencies, and stores results in Google Docs.

### 🧠 Key Features

* Reads **character & place databases** from Google Docs
* Supports **chapter-by-chapter control** (approve / skip / stop)
* Performs accurate Korean → English translation (DeepSeek)
* Applies consistency checks (names, places, romanization)
* Creates Google Docs automatically
* Sends completion email for each translated chapter

### 🧩 Workflow Breakdown

| Step                     | Description                                |
| ------------------------ | ------------------------------------------ |
| **Parse Names Database** | Extracts characters/places from Google Doc |
| **Decision Webhook**     | Accept / skip / stop                       |
| **Translate Chapter**    | High-quality AI translation                |
| **Process Translation**  | Cleans + formats for consistency model     |
| **Consistency Check**    | Ensures names/places match database        |
| **Create Google Doc**    | Creates chapter file                       |
| **Add Content to Doc**   | Inserts the corrected translation          |
| **Email Notification**   | Sends summary + Google Doc link            |

### ⭐ Why This Workflow Exists

To automate everything needed for long-form translations:

* No repeated manual corrections
* No inconsistent names
* No copy-pasting into Google Docs
* Smooth chapter progression
* Clean translation storage

---

# ⚙️ Setup & Installation

### 1. Install n8n

You can install n8n via:

```bash
npm install n8n -g
```

or Docker:

```bash
docker run -it --rm -p 5678:5678 n8nio/n8n
```

### 2. Required Credentials

Some workflows require global credentials:

#### 🔑 Ollama API

Needed for LLM calls (DeepSeek / Claude / local models).

#### 🔑 Google Docs OAuth2

Required for:

* Reading names database
* Creating/editing documents

#### 🔑 Gmail OAuth2

Required only if you enable email notifications.

---

# 📥 How to Import These Workflows

1. Open your n8n dashboard
2. Click **Workflows → Import from File**
3. Select any JSON file from this repo
4. Review nodes and connect your credentials
5. Hit **Activate**

You're ready to use the automation.

---

# 📁 Folder Structure

```
n8n-automations/
│
├── workflows/
│     ├── gpt-autogenerate.json
│     ├── my-workflow.json
│
└── README.md
```

---

# 🤝 Contributing

Contributions are welcome!
If you’d like to add your own n8n workflow or improve an existing one:

### 🔧 How to Contribute

1. **Fork** the repository
2. Create a branch:

   ```bash
   git checkout -b feature/new-workflow
   ```
3. Add your workflow JSON under `/workflows`
4. Update the README if needed
5. Submit a pull request

### ✔ Accepted Contributions

* New n8n workflows
* Enhancements to existing workflows
* Bug fixes
* Documentation improvements

---

# 📜 License

This repository is released under the **MIT License**.
Feel free to use, modify, and distribute the workflows.
