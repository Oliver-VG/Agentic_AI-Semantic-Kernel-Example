
# Semantic Kernel 1.x Stock Reminder Agent

This repository contains a Jupyter notebook, **`semantic_kernel_agent_SK1-V2.ipynb`**, that demonstrates how to build a **Semantic Kernel 1.x** agent using the Python `ChatCompletionAgent`.

The agent:

1. Takes a **US company name** from the user.
2. Uses an **OpenAI chat model** to infer the company’s **primary US stock ticker** (no external ticker API).
3. Calls a **`MarketDataPlugin`** tool to:
   - Download ~10 years of daily prices from **Stooq** (`https://stooq.com/`), and
   - Compute which **weekday** has the **lowest average closing price**.
4. Calls an **`OutlookPlugin`** tool to:
   - **Create (or simulate)** an Outlook reminder for that weekday **next week**.
5. Explains to the user what it did, step by step.

---

## Repository Contents

- `semantic_kernel_agent_SK1-V2.ipynb`
  - Imports and configuration  
  - `MarketDataPlugin` (Stooq market data analysis)  
  - `OutlookPlugin` (Outlook reminder creation/simulation)  
  - Agent configuration  
  - Helper function `run_agent_once(...)`  
  - Example interaction  

---

## Requirements

### Python
- Python **3.9+**

### Packages
```
pip install semantic-kernel requests python-dotenv pywin32
```

`pywin32` is optional unless you want **real Outlook** reminder creation.

### Environment Variables
Create `.env` or export:

```
OPENAI_API_KEY=your-key
```

---

## Model Configuration

Default:
```
CHAT_MODEL = "gpt-4.1-mini"
```

---

## Download & Run

### 1. Download the Notebook
- Download from GitHub via **Code → Download ZIP** or download the notebook directly.

### 2. (Optional) Virtual Environment
```
python -m venv .venv
source .venv/bin/activate      # Mac/Linux
.\.venv\Scriptsctivate       # Windows
```

### 3. Install Dependencies  
(see Requirements section)

### 4. Set API Key  
(see Environment Variables)

### 5. Open Notebook
Use Jupyter, JupyterLab, or VS Code.

### 6. Run All Cells  
Enter a company name when prompted.

---

## Architecture Overview

### MarketDataPlugin
Downloads ~10 years of daily OHLC data from **Stooq**, groups by weekday, and finds the weekday with the lowest average closing price.

### OutlookPlugin
Creates or **simulates** an Outlook reminder scheduled for the **same weekday next week**.

### ChatCompletionAgent
Uses Semantic Kernel to orchestrate:
1. Ticker inference  
2. Market analysis tool call  
3. Outlook reminder tool call  
4. Final explanation to the user  

---

## Troubleshooting

- **API key not found** → check `.env` or environment export  
- **semantic-kernel missing** → `pip install semantic-kernel`  
- **pywin32 missing** → install or accept simulation mode  
- **Stooq data empty** → ticker may not exist or be non‑US  

---

## License
Add your preferred license.

---

## Acknowledgements
- Microsoft Semantic Kernel  
- Stooq for historical market data  
