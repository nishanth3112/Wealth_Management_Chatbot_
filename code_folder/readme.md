# 💼 Autonomous Agentic Wealth Management Chatbot

An **intelligent Wealth & Risk Assessment System** integrating **Agentic AI**, **LangChain**, and **Microsoft Fabric Lakehouse** to autonomously analyze financial data, generate investment strategies, and provide personalized risk mitigation recommendations.  

This project demonstrates an **end-to-end AI-powered financial platform** capable of dynamic decision-making using modular LangChain tools, Retrieval-Augmented Generation (RAG) models, and contextual memory for long-term portfolio intelligence.

---

## 🎯 Objective

To design an **Agentic AI-driven Wealth Management platform** that autonomously:
- Analyzes portfolio and transaction data  
- Evaluates risk exposure and diversification  
- Suggests tailored mitigation or reallocation strategies  
- Uses **LangChain reasoning and Microsoft Fabric Lakehouse** for large-scale, contextual, and real-time analysis  

---

## 🏗️ Architecture
<img width="936" height="312" alt="image" src="https://github.com/user-attachments/assets/19a8b385-5994-4e88-80de-a63a88edf768" />



This section will illustrate:
- Data ingestion into Microsoft Fabric Lakehouse  
- RAG + LangChain pipeline for Text-to-SQL and financial reasoning  
- Flask API + HTML UI chatbot  
- Vector DB (ChromaDB) for conversation memory  
- Agentic workflow orchestration (Intent Detection → Tool Selection → Execution → Response)  

---

## 🧠 Overview

This project forms **Phase 2** of the *Microsoft Fabric Financial Reporting Agent* initiative — extending from static reporting to intelligent financial reasoning using **Agentic AI**.

Agentic AI enables the system to:
- Break complex financial questions into modular sub-tasks  
- Dynamically invoke specialized LangChain tools (e.g., risk analysis, strategy generation)  
- Retain financial context across conversations using **ChromaDB**  
- Provide **autonomous**, **personalized**, and **goal-oriented** financial recommendations  

---

## 🧩 Key Components

| Component | Description |
|------------|-------------|
| **Microsoft Fabric Lakehouse** | Centralized cloud data repository for client portfolios, assets, transactions, and risk profiles |
| **LangChain Agent & Tools** | Modular tools for stock analysis, risk computation, and mitigation planning |
| **RAG (Text-to-SQL Model)** | Converts natural-language queries into executable SQL for Fabric Lakehouse |
| **Flask API + HTML UI** | Provides a web chatbot interface for real-time financial query interaction |
| **ChromaDB Memory** | Stores conversation context and user preferences for personalized responses |

---

## 🧮 Data Description

- **Wealth Assets Data:** Client portfolios (Stocks, Bonds, Real Estate, Alternative Investments)  
- **Financial Records:** Historical transactions and portfolio performance  
- **Risk Metrics:** Diversification indices, volatility measures, and exposure ratios  

---

## ⚙️ Tech Stack

- **Language:** Python 3.9 / 3.10  
- **Libraries:** `pandas`, `numpy`, `flask`, `langchain`, `openai`, `azure`  
- **Cloud Platform:** Microsoft Fabric (OneLake, Lakehouse, Fabric Data Warehouse)  
- **Model Framework:** Retrieval-Augmented Generation (RAG) + GPT  
- **Frontend:** HTML + CSS (chatbot UI)  

---

## 🔁 Approach & Workflow

### 1️⃣ Define Goal & Task Decomposition
- Assess financial risk and create mitigation strategies  
- Tasks → Stock analysis, Risk exposure quantification, Strategy generation, Feedback refinement  

### 2️⃣ Build the Agentic AI Framework
- Chain-of-Thought (CoT) reasoning for dynamic task selection  
- Intent classification (“Risk Analysis” / “Investment Planning” / Unknown)  

### 3️⃣ Create Modular Tools
- **Stock Position Tool:** Portfolio retrieval + volatility analysis  
- **Risk Calculator:** Diversification & historical risk metrics  
- **Mitigation Tool:** Portfolio reallocation & hedging strategies  
- **Feedback Loop:** Learn from user choices for future recommendations  

### 4️⃣ Memory Management
- Store conversation embeddings in ChromaDB for context retention  

### 5️⃣ Decision Logic
- Intent → Tool mapping → Execution → Response via LangChain Agent  

### 6️⃣ Flask API + HTML UI
- `/query` endpoint to accept user inputs, run agent, and return results live  

---

## 🗂️ Project Structure

```
├─ Agent
│  ├─ agent.py
│  ├─ intent.py
│  ├─ memory.py
│  ├─ tools.py
├─ app.py
├─ connection.py
├─ CreateDataWarehouse
│  ├─ CreatingTables.sql
│  └─ InsertToSQL.py
├─ FinancialGoals
│  └─ RAGToSQL
│     ├─ FabricsRAG.py
│     ├─ Helper
│     │  ├─ Credentials.py
│     │  ├─ FabricsConnection.py
│     │  ├─ VannaObject.py
│     ├─ InferenceRAG.py
│     ├─ TrainRAG.py
│     ├─ VisualizeRAG.py
│     ├─ TrainingRAG-Artifact/
│     │  ├─ Documentation.txt
│     │  └─ Tables.json
│     ├─ training_summary.csv
├─ templates
│  └─ index.html
├─ requirements.txt
└─ README.md
```

---

## 🧱 Data Insertion Module

Populates the **Microsoft Fabric Lakehouse** with ~1 GB of dummy financial data for analysis.

Run:
```bash
python CreateDataWarehouse/InsertToSQL.py
```
> Make sure to update your Fabric connection string and install required libs (`pyodbc`, `faker`).

---

## 💬 Text-to-SQL Model (RAG)

Use **RAG To SQL** to convert user queries into SQL statements dynamically.

| Task | Script |
|------|--------|
| Train Model | `FinancialGoals/RAGToSQL/TrainRAG.py` |
| Inference on Queries | `FinancialGoals/RAGToSQL/InferenceRAG.py` |
| Integration with Fabric | `FinancialGoals/RAGToSQL/FabricsRAG.py` |

---

## 🔗 LangChain Integration

The **LangChain agent** coordinates between tools and memory modules to:
- Generate context-aware SQL queries  
- Combine portfolio data with user objectives  
- Manage multi-step financial reasoning  

Run:
```bash
python LangChainFabrics.py
```

---

## ⚡ Setup & Execution

### Prerequisites
1. **Python 3.9 or 3.10**  
2. **Microsoft Fabric Lakehouse Access**  
3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

---

### 🧩 Virtual Environment Setup

#### Windows
```bash
cd C:\path\to\project
python -m venv myenv
myenv\Scripts\activate
pip install -r requirements.txt
```

#### macOS/Linux
```bash
cd /path/to/project
python3.9 -m venv myenv
source myenv/bin/activate
pip install -r requirements.txt
```

---

### 🧠 Additional Configuration
1. Run `connection.py` to authenticate with Azure and generate a Fabric token.  
2. Copy the token → paste into `FinancialGoals/RAGToSQL/Helper/Credentials.py`.  
3. Run `app.py` to start the Flask server:
   ```bash
   python app.py
   ```
4. Open your browser at `http://127.0.0.1:5000/`.

---

## 💰 Cost Overview (Approx.)

| Component | Description | Free Tier | Est. Cost After Trial |
|------------|--------------|-----------|------------------------|
| **OpenAI GPT-4o API** | RAG Text-to-SQL queries (~100 queries) | — | ~$1.50 |
| **Azure SQL** | Financial data storage (50 GB) | — | ~$5.00 |
| **Microsoft Fabric** | Data Lakehouse (100 GB storage + light compute) | 60-day trial | ~$262.80 / mo for F2 SKU |
| **Network Egress** | 50 GB data transfer | — | ~$4.50 |

> **Total Experiment Cost:** ≈ $11 (using free tiers) → ≈ $280 post-trial

---

## 🏁 Project Takeaways
- Build autonomous financial agents using LangChain & Agentic AI  
- Implement RAG Text-to-SQL for natural language querying  
- Manage contextual memory with ChromaDB vector stores  
- Integrate Fabric Lakehouse for scalable data storage  
- Deploy Flask + HTML UI for interactive risk assessment  

---


