## Original Repo: [https://github.com/HKUDS/AI-Trader](https://github.com/HKUDS/AI-Trader)

This repo foucs on the migrition and compatiability for Vertex API. Part of this repo inheirts from original one, but is not exactly executed if following the instruction below. Please find those instructions and detailed explaination in original `README.md` if you are interested.

Only `base_agent_hour` is reproduced.

## 🚀 Quick Start

### 📋 Prerequisites


- **Python 3.10+** 
- **API Keys**: 
  - Vertex API (for AI models)

### ⚡ One-Click Installation

```bash
# 1. Clone project
git clone https://github.com/adashima152/AI-Trader
cd AI-Trader

# 2. Install dependencies
pip install -r requirements.txt

# 3. Configure environment variables
cp .env.example .env
# Edit .env file and fill in your API keys
```

### 🔑 Environment Configuration

Create `.env` file and configure the following variables:

```bash
# 🤖 AI Model API Configuration
VERTEX_API_KEY=your_vertex_api_key

# ⚙️ System Configuration
RUNTIME_ENV_PATH=./runtime_env.json # Recommended to use absolute path

# 🌐 Service Port Configuration
MATH_HTTP_PORT=8000
SEARCH_HTTP_PORT=8001
TRADE_HTTP_PORT=8002
GETPRICE_HTTP_PORT=8003
CRYPTO_HTTP_PORT=8005

# 🧠 AI Agent Configuration
AGENT_MAX_STEP=30             # Maximum reasoning steps
```

### 📦 Dependencies

```bash
# Install production dependencies
pip install -r requirements.txt

# Or manually install core dependencies
pip install langchain langchain-openai langchain-mcp-adapters fastmcp python-dotenv requests numpy pandas tushare langchain_google_genai
```

## 🎮 Running Guide

### 🚀 Quick Start with Scripts

We provide convenient shell scripts in the `scripts/` directory for easy startup:

#### 🇺🇸 US Market (NASDAQ 100)
```bash
# One-click startup (complete workflow)
bash scripts/main.sh

# Or run step by step:
# bash scripts/main_step1.sh  # Step 1: Prepare data
bash scripts/main_step2.sh  # Step 2: Start MCP services
bash scripts/main_step3.sh  # Step 3: Run trading agent
```

#### 🌐 Web UI
```bash
# Start web interface
bash scripts/start_ui.sh
# Visit: http://localhost:8888
```

---

## ⚙️ Configuration Guide

### 📋 Configuration File Structure

```json
{
  "agent_type": "BaseAgent_Hour",
  "date_range": {
    "init_date": "2025-10-01 14:00:00",
    "end_date": "2025-11-07 19:00:00"
  },
  "models": [
    {
      "name": "claude-3.7-sonnet",
      "basemodel": "anthropic/claude-3.7-sonnet", 
      "signature": "claude-3.7-sonnet",
      "enabled": false,
      "openai_base_url": "Optional: YOUR_OPENAI_BASE_URL,you can write them in .env file",
      "openai_api_key": "Optional: YOUR_OPENAI_API_KEY,you can write them in .env file" 
    },
    {
      "name": "deepseek-chat-v3.1",
      "basemodel": "deepseek/deepseek-chat-v3.1",
      "signature": "deepseek-chat-v3.1",
      "enabled": false
    },
    {
      "name": "qwen3-max",
      "basemodel": "qwen/qwen3-max",
      "signature": "qwen3-max",
      "enabled": false
    },
    {
      "name": "gemini-2.5-flash",
      "basemodel": "google/gemini-2.5-flash",
      "signature": "gemini-2.5-flash",
      "enabled": true
    },
    {
      "name": "gpt-5",
      "basemodel": "openai/gpt-5",
      "signature": "gpt-5",
      "enabled": false
    }
  ],
  "agent_config": {
    "max_steps": 30,
    "max_retries": 3,
    "base_delay": 1.0,
    "initial_cash": 10000.0
  },
  "log_config": {
    "log_path": "./data/agent_data"
  }
}
```


## 📄 License

This project is licensed under the [MIT License](LICENSE).

