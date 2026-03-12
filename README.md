<h1 align="center">
⛽ AI Crude Oil Trading Bot ⛽
</h1>
<p align="center">
  <a href="https://t.me/spidertrading100"><img src="https://img.shields.io/badge/Telegram-Group-26A5E4?style=for-the-badge&logo=telegram" alt="Telegram"></a>
</p>
<p align="center">
  <strong>AI-Native Quantitative Trading Platform for Crude Oil & Energy Commodities</strong>
</p>

<p align="center">
  <i>Describe your trading idea in natural language → AI writes the Python strategy → Backtest → Monitor.<br/>
  Self-hosted — your API keys and strategies never leave your machine.</i>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg?style=flat-square&logo=apache" alt="License"></a>
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Docker-One%20Click-2496ED?style=flat-square&logo=docker&logoColor=white" alt="Docker">
</p>

---

## Table of Contents

- [Quick Start](#-quick-start)
- [Why This Platform?](#-why-this-platform)
- [Key Features](#-key-features)
- [Supported Markets & Data Sources](#-supported-markets--data-sources)
- [Architecture](#-architecture)
- [Documentation](#-documentation)
- [Community & Support](#-community--support)
- [License](#-license)

---

## 🚀 Quick Start

> **Requirements**: [Docker](https://docs.docker.com/get-docker/) installed.

```bash
# 1. Clone
git clone https://github.com/your-org/ai-crude-oil-trading-bot.git
cd ai-crude-oil-trading-bot

# 2. Configure (edit admin password & AI API key)
cp backend_api_python/env.example backend_api_python/.env

# 3. Launch
docker-compose up -d --build
```

> **Windows PowerShell**: `Copy-Item backend_api_python\env.example -Destination backend_api_python\.env`

**Done!** Open **http://localhost:8888** | Default login: `quantdinger` / `123456` (change in `.env`)

<details>
<summary><b>📝 Key settings in backend_api_python/.env</b></summary>

```ini
# Required — Change for production!
ADMIN_USER=quantdinger
ADMIN_PASSWORD=your_secure_password
SECRET_KEY=your_random_secret_key

# Optional — Enable AI features (pick one)
OPENROUTER_API_KEY=your_key        # Recommended: 100+ models
OPENAI_API_KEY=your_key            # GPT-4o
DEEPSEEK_API_KEY=your_key          # Cost-effective
GOOGLE_GEMINI_API_KEY=your_key     # Gemini
```

</details>

---

## 🎯 Why This Platform?

| | |
|---|---|
| 🛢️ **Crude Oil Focus** | Built for WTI, Brent, and energy commodities — data, analysis, and strategies tuned for oil markets |
| 🤖 **AI-Powered** | Multi-agent analysis, natural-language strategy generation, and backtest optimization |
| 🐍 **Python-Native** | Full ecosystem (Pandas, NumPy, TA-Lib) — write or generate strategies in Python |
| 🔒 **Self-Hosted** | API keys & strategies stay on your server — privacy by design |
| 📊 **Professional Charts** | K-line charts with technical indicators, real-time visualization |
| ⚡ **2-Minute Deploy** | `docker-compose up -d` — production-ready, zero build |

---

## ✨ Key Features

### 🛢️ Crude Oil & Energy Commodities

- **WTI Crude Oil (CL)** — NYMEX futures
- **Brent Crude** — ICE benchmark
- **Natural Gas (NG)**, **Gold (GC)**, **Silver (SI)** — related commodities
- Data from yfinance, Finnhub, and exchange APIs

### 🤖 AI Strategy Workbench

> **No coding required.** Describe your idea in natural language — AI generates production-ready Python strategies.

```
💬 "I want a MACD crossover strategy with RSI filter on WTI 15min"
    ↓ AI generates Python code
    ↓ 📈 Visualize on K-line charts
    ↓ 🔄 Backtest with rich metrics
    ↓ 🚀 Deploy to monitoring & alerts
```

### 📈 Full Trading Lifecycle

| Step | What Happens |
|------|-------------|
| **1. 💬 Describe** | Tell AI your trading idea in natural language — or write Python directly |
| **2. 🤖 Generate** | AI creates the indicator & strategy code |
| **3. 📊 Visualize** | See signals on professional K-line charts |
| **4. 🔄 Backtest** | Rich metrics + AI suggests improvements |
| **5. 📡 Monitor** | Portfolio tracker, alerts via Telegram/Discord/Email/Webhook |

---

## 🔌 Supported Markets & Data Sources

### Crude Oil & Energy

| Symbol | Name | Exchange | Notes |
|:------:|:-----|:---------|:------|
| **CL** | WTI Crude Oil | NYMEX/CME | Primary focus |
| **BZ** | Brent Crude | ICE | Via data providers |
| **NG** | Natural Gas | NYMEX | Energy sector |
| **GC** | Gold | COMEX | Safe-haven correlation |
| **SI** | Silver | COMEX | Industrial + precious |

### Execution & Brokers

| Market | Broker/Source | Trading |
|--------|---------------|---------|
| **Crude Oil Futures** | Interactive Brokers (IBKR) | ✅ Via IBKR |
| **Oil CFDs** | MetaTrader 5 (MT5) | ✅ Via MT5 |
| **US Stocks** | IBKR, Yahoo Finance, Finnhub | ✅ Via IBKR |
| **Forex** | MT5, OANDA | ✅ Via MT5 |

> **Note**: Futures data is supported for analysis and backtesting. Live futures execution typically requires IBKR integration. See [IBKR Trading Guide](docs/IBKR_TRADING_GUIDE_EN.md) and [MT5 Trading Guide](docs/MT5_TRADING_GUIDE_EN.md).

---

## 🏗️ Architecture

### Tech Stack

| Layer | Technology |
|-------|-----------|
| **AI Engine** | Multi-agent analysis, RAG memory, 5+ LLM providers |
| **Backend** | Python 3.10+ · Flask · PostgreSQL 16 |
| **Frontend** | Vue.js · Ant Design · KlineCharts · ECharts |
| **Deploy** | Docker Compose · Nginx · One-click |

```
┌─────────────────────────────────────┐
│         Docker Compose              │
│  ┌───────────────────────────────┐  │
│  │  frontend (Nginx)  → :8888    │  │
│  └──────────────┬────────────────┘  │
│                 │ /api/* proxy       │
│  ┌──────────────▼────────────────┐  │
│  │  backend (Flask)   → :5000    │  │
│  └──────────────┬────────────────┘  │
│  ┌──────────────▼────────────────┐  │
│  │  postgres (PG 16)  → :5432    │  │
│  └───────────────────────────────┘  │
│  External: LLM APIs · Data providers │
└─────────────────────────────────────┘
```

### Repository Layout

```
ai-crude-oil-trading-bot/
├── backend_api_python/       # Backend API
│   ├── app/routes/           # API endpoints
│   ├── app/services/         # Business logic (AI, trading, data)
│   ├── migrations/init.sql   # Database schema
│   └── Dockerfile
├── frontend/                 # Vue.js frontend
│   ├── dist/                 # Pre-built static files
│   └── Dockerfile
├── docs/                     # Guides & tutorials
├── docker-compose.yml        # One-click deployment
└── LICENSE
```

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [Strategy Development Guide](docs/STRATEGY_DEV_GUIDE.md) | Python strategy development |
| [IBKR Trading Guide](docs/IBKR_TRADING_GUIDE_EN.md) | Interactive Brokers setup |
| [MT5 Trading Guide](docs/MT5_TRADING_GUIDE_EN.md) | MetaTrader 5 setup |
| [Multi-User Setup](docs/multi-user-setup.md) | PostgreSQL multi-user deployment |
| [Changelog](docs/CHANGELOG.md) | Version history |

---

## 🤝 Community & Support

<p align="center">
  <a href="https://t.me/spidertrading100"><img src="https://img.shields.io/badge/Telegram-Group-26A5E4?style=for-the-badge&logo=telegram" alt="Telegram"></a>
</p>
<div align="center">

| Channel | Link |
|---------|------|
| **Telegram** | [t.me/spidertrading100](https://t.me/spidertrading100) |
| **Email** | [martinsurgenor.hynx@gmail.com](mailto:martinsurgenor.hynx@gmail.com) |

---
</div>
## 💼 License

This project is licensed under the **Apache License 2.0**. See [LICENSE](LICENSE).

---

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

<p align="center"><sub>Built for crude oil traders who value data sovereignty and transparent systems.</sub></p>
