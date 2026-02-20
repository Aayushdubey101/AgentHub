# n8n Workflows Collection ⚡

This directory contains production-ready n8n automation workflows designed for intelligent business automation and AI-powered decision systems.

Each workflow is exportable as a `.json` file and can be directly imported into your local or cloud n8n instance.

---

## 📂 Available Workflows

### 1️⃣ Product Review Smart Discount Agent

**File:** `product-review-smart-discount.json`

### 2️⃣ AI GitHub Parallel Reviewer

**File:** `github-codespace-working-automation.json`

---

## 🛒 Product Review Smart Discount Agent

An intelligent automation workflow that analyzes product reviews and automatically suggests smart discount strategies based on sentiment and rating performance.

---

## 🎯 Problem It Solves

E-commerce platforms often struggle to:
- Identify underperforming products
- Analyze customer sentiment at scale
- Decide optimal discount strategies
- React quickly to negative feedback

This workflow automates that entire decision pipeline.

---

## 🧠 How It Works

1. Fetch product reviews from database or API
2. Perform sentiment analysis using LLM
3. Identify products with negative or low ratings
4. Apply business logic conditions
5. Generate smart discount recommendations
6. Trigger action (email alert / API call / dashboard update)

---

## ✨ Features

- ✅ Sentiment Analysis (AI-powered)
- ✅ Conditional Business Logic
- ✅ Automated Discount Strategy Suggestion
- ✅ API Integration Ready
- ✅ Scalable Workflow Design
- ✅ Production-Ready Structure

---

## 🛠 Requirements

- n8n (local or cloud instance)
- API Keys (OpenAI / Anthropic if used)
- Database or Product Review API (optional depending on setup)

---

## 🚀 How to Use

1. Open your n8n dashboard  
2. Go to **Workflows → Import**
3. Upload `product-review-smart-discount.json`
4. Configure credentials (API keys, database, etc.)
5. Test the workflow
6. Activate it

---

## 🔌 Integration Possibilities

This workflow can be extended to integrate with:

- E-commerce platforms (Shopify, WooCommerce, etc.)
- PostgreSQL / MySQL databases
- Email automation systems
- Slack / Discord alerts
- CRM platforms
- Analytics dashboards

---

## 📈 Future Improvements

- Multi-product batch processing
- Automated A/B discount testing
- Dynamic pricing optimization
- Real-time streaming review analysis
- Integration with vector databases for review clustering

---

## 🏗 Architecture Philosophy

These workflows follow:

- Modular node design
- Clear logical branching
- Scalable structure
- Production deployment compatibility
- AI-first automation principles

---

## 📌 Contribution Guidelines

If you want to add a new workflow:

1. Add exported `.json` file in this directory
2. Update this README
3. Provide clear description and usage instructions
4. Keep workflows modular and reusable

---

## 🤖 AI GitHub Parallel Reviewer

A high-performance parallel code review and documentation agent that automatically analyzes codebases, adds professional inline comments, and generates a structured project map.

---

## 🎯 Problem It Solves

- Codebases often lack consistent documentation.
- Manual code reviews for large projects are time-consuming.
- Mapping out project structure for new developers is tedious.

---

## 🧠 How It Works

1. **Webhook Trigger:** Receives project files via a secure `POST` request.
2. **Parallel Processing:** Splits files and processes them concurrently using specialized AI agents:
    - **Commenter Agent:** Adds professional inline comments to the code.
    - **Structure Agent:** Generates architectural summaries for each file.
3. **Merging & Aggregation:** Recombines the outputs for a unified view.
4. **Final Compilation:** A compiler agent builds a unified `project-structure.md` and packages the commented files.
5. **JSON Response:** Returns the structured documentation and commented code back to the requester.

---

## ✨ Features

- ✅ Parallel AI Agent Execution
- ✅ Automated Inline Commenting
- ✅ Dynamic Project Structure Generation
- ✅ Scalable file processing
- ✅ Production-ready architecture

---

## 🛠 Setup & Requirements

1. **n8n Instance:** Local or cloud.
2. **OpenAI Credentials:** Required for AI agents (`GPT-4o-mini` recommended).
3. **Deployment:**
    - Import `github-codespace-working-automation.json`.
    - Configure your own OpenAI credentials in the model nodes.
    - Activate the workflow and copy the **Production Webhook URL**.

---

## 🚀 How to Run

Use a script like the one below (also provided in the workflow sticky notes) to securely transmit your codebase to n8n:

```python
import os
import json
import requests

# Set your production webhook URL as an environment variable
# export N8N_WEBHOOK_URL="https://your-n8n-domain/webhook/code-review"
WEBHOOK_URL = os.getenv("N8N_WEBHOOK_URL")

if not WEBHOOK_URL:
    raise ValueError("Please set N8N_WEBHOOK_URL environment variable.")

project_files = []

for root, dirs, files in os.walk("."):
    if ".git" in root or "__pycache__" in root:
        continue

    for file in files:
        file_path = os.path.join(root, file)
        try:
            with open(file_path, "r", encoding="utf-8") as f:
                project_files.append({
                    "file_name": file_path,
                    "content": f.read()
                })
        except:
            pass

payload = {
    "project": os.path.basename(os.getcwd()),
    "files": project_files
}

print(f"Sending {len(project_files)} files for AI review...")
response = requests.post(WEBHOOK_URL, json=payload, timeout=120)

print("Status:", response.status_code)
# The response contains 'project_structure_md' and 'commented_files'
```

---

## 🏗 Architecture Philosophy
 ⚡ using n8n and modern AI tooling.
