<p align="center">
  <img src="https://raw.githubusercontent.com/getbindu/create-bindu-agent/refs/heads/main/assets/light.svg" alt="bindu Logo" width="200">
</p>

<h1 align="center">finance-agent</h1>

<p align="center">
  <strong>This project builds an intelligent financial analysis agent that combines real-time market data and web search to generate structured, data-driven insights. It presents financial information in clear tables and concise summaries through an interactive playground interface, with flexible provider integration via OpenRouter.</strong>
</p>

<p align="center">
  <a href="https://github.com/Paraschamoli/finance-agent/actions/workflows/main.yml?query=branch%3Amain">
    <img src="https://img.shields.io/github/actions/workflow/status/Paraschamoli/finance-agent/main.yml?branch=main" alt="Build status">
  </a>
  <a href="https://img.shields.io/github/license/Paraschamoli/finance-agent">
    <img src="https://img.shields.io/github/license/Paraschamoli/finance-agent" alt="License">
  </a>
</p>

---

## 📖 Overview

This project builds an intelligent financial analysis agent that combines real-time market data and web search to generate structured, data-driven insights. It presents financial information in clear tables and concise summaries through an interactive playground interface, with flexible provider integration via OpenRouter.. Built on the [Bindu Agent Framework](https://github.com/getbindu/bindu) for the Internet of Agents.

**Key Capabilities:**
- � **Real-time Stock Data**: Fetch current prices, market cap, P/E ratios, and key financial metrics
- 🔍 **Market News Integration**: Access latest financial news and analyst recommendations
- 📈 **Technical Analysis**: Generate insights with properly formatted markdown tables
- � **Investment Research**: Combine data analysis with recent news for comprehensive insights
- 🎯 **Clean Output**: Structured, professional financial reports with disclaimers

---

## 🚀 Quick Start

### Prerequisites

- Python 3.10+
- [uv](https://github.com/astral-sh/uv) package manager
- API keys for OpenRouter and Mem0 (both have free tiers)

### Installation

```bash
# Clone the repository
git clone https://github.com/Paraschamoli/finance-agent.git
cd finance-agent

# Create virtual environment
uv venv --python 3.12.9
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
uv sync

# Configure environment
cp .env.example .env
```

### Configuration

Edit `.env` and add your API keys:

| Key | Get It From | Required |
|-----|-------------|----------|
| `OPENROUTER_API_KEY` | [OpenRouter](https://openrouter.ai/keys) | ✅ Yes |
| `MEM0_API_KEY` | [Mem0 Dashboard](https://app.mem0.ai/dashboard/api-keys) | If you want to use Mem0 tools |

### Run the Agent

```bash
# Start the agent
uv run python -m finance_agent

# Agent will be available at http://localhost:3773
```

### Github Setup

```bash
# Initialize git repository and commit your code
git init -b main
git add .
git commit -m "Initial commit"

# Create repository on GitHub and push (replace with your GitHub username)
gh repo create Paraschamoli/finance-agent --public --source=. --remote=origin --push
```

---

## 💡 Usage

### Example Queries

```bash
# Stock analysis
"analyze nvidia stock"
"what's the current price of AAPL"
"compare tesla and ford financials"

# Market research
"latest news about semiconductor stocks"
"analyst recommendations for microsoft"
"market trends in AI sector"

# Financial metrics
"show me key ratios for amazon"
"what's the P/E ratio of google"
"dividend yield analysis for Johnson & Johnson"
```

### Input Formats

**Plain Text:**
```
analyze nvidia stock
what's the current price of AAPL
latest news about semiconductor stocks
```

**JSON:**
```json
{
  "query": "analyze nvidia stock",
  "include_news": true,
  "timeframe": "1m"
}
```

### Output Structure

The agent returns structured output with:
- **Financial Tables**: Clean markdown tables with stock prices, ratios, and metrics
- **News Summaries**: Bullet-pointed highlights of recent market news
- **Analysis Insights**: Concise investment research with context
- **Professional Formatting**: Proper structure with disclaimers

---

## 🔌 API Usage

The agent exposes a RESTful API when running. Default endpoint: `http://localhost:3773`

### Quick Start

For complete API documentation, request/response formats, and examples, visit:

📚 **[Bindu API Reference - Send Message to Agent](https://docs.getbindu.com/api-reference/all-the-tasks/send-message-to-agent)**


### Additional Resources

- 📖 [Full API Documentation](https://docs.getbindu.com/api-reference/all-the-tasks/send-message-to-agent)
- 🔧 [API Reference](https://docs.getbindu.com)

---

## 🎯 Skills

### finance (v1.0.0)

**Primary Capability:**
- AI-powered financial analysis and market research
- Real-time stock data retrieval and analysis
- Integration with financial news sources

**Features:**
- Real-time stock price and market data via YFinance
- Latest financial news via DuckDuckGo search
- Professional markdown table formatting
- Comprehensive financial ratio analysis
- Analyst recommendation summaries

**Best Used For:**
- Stock analysis and investment research
- Market trend identification
- Financial ratio comparisons
- News-driven investment insights
- Quick financial data lookups

**Not Suitable For:**
- Real-time trading decisions
- Portfolio management
- Tax or legal financial advice
- High-frequency trading analysis

**Performance:**
- Average processing time: ~2-3 seconds
- Max concurrent requests: 10
- Memory per request: 256MB

---

## 🐳 Docker Deployment

### Local Docker Setup

```bash
# Build and run with Docker Compose
docker-compose up --build

# Agent will be available at http://localhost:3773
```

### Docker Configuration

The agent runs on port `3773` and requires:
- `OPENROUTER_API_KEY` environment variable
- `MEM0_API_KEY` environment variable

Configure these in your `.env` file before running.

### Production Deployment

```bash
# Use production compose file
docker-compose -f docker-compose.prod.yml up -d
```

---

## 🌐 Deploy to bindus.directory

Make your agent discoverable worldwide and enable agent-to-agent collaboration.

### Setup GitHub Secrets

```bash
# Authenticate with GitHub
gh auth login

# Set deployment secrets
gh secret set BINDU_API_TOKEN --body "<your-bindu-api-key>"
gh secret set DOCKERHUB_TOKEN --body "<your-dockerhub-token>"
```

Get your keys:
- **Bindu API Key**: [bindus.directory](https://bindus.directory) dashboard
- **Docker Hub Token**: [Docker Hub Security Settings](https://hub.docker.com/settings/security)

### Deploy

```bash
# Push to trigger automatic deployment
git push origin main
```

GitHub Actions will automatically:
1. Build your agent
2. Create Docker container
3. Push to Docker Hub
4. Register on bindus.directory

---

## 🛠️ Development

### Project Structure

```
finance-agent/
├── finance_agent/
│   ├── skills/
│   │   └── finance_agent/
│   │       ├── skill.yaml          # Skill configuration
│   │       └── __init__.py
│   ├── __init__.py
│   ├── __main__.py
│   ├── main.py                     # Agent entry point
│   └── agent_config.json           # Agent configuration
├── tests/
│   └── test_main.py
├── .env.example
├── docker-compose.yml
├── Dockerfile.agent
└── pyproject.toml
```

### Running Tests

```bash
make test              # Run all tests
make test-cov          # With coverage report
```

### Code Quality

```bash
make format            # Format code with ruff
make lint              # Run linters
make check             # Format + lint + test
```

### Pre-commit Hooks

```bash
# Install pre-commit hooks
uv run pre-commit install

# Run manually
uv run pre-commit run -a
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Powered by Bindu

Built with the [Bindu Agent Framework](https://github.com/getbindu/bindu)

**Why Bindu?**
- 🌐 **Internet of Agents**: A2A, AP2, X402 protocols for agent collaboration
- ⚡ **Zero-config setup**: From idea to production in minutes
- 🛠️ **Production-ready**: Built-in deployment, monitoring, and scaling

**Build Your Own Agent:**
```bash
uvx cookiecutter https://github.com/getbindu/create-bindu-agent.git
```

---

## 📚 Resources

- 📖 [Full Documentation](https://Paraschamoli.github.io/finance-agent/)
- 💻 [GitHub Repository](https://github.com/Paraschamoli/finance-agent/)
- 🐛 [Report Issues](https://github.com/Paraschamoli/finance-agent/issues)
- 💬 [Join Discord](https://discord.gg/3w5zuYUuwt)
- 🌐 [Agent Directory](https://bindus.directory)
- 📚 [Bindu Documentation](https://docs.getbindu.com)

---

<p align="center">
  <strong>Built with 💛 by the team from Amsterdam 🌷</strong>
</p>

<p align="center">
  <a href="https://github.com/Paraschamoli/finance-agent">⭐ Star this repo</a> •
  <a href="https://discord.gg/3w5zuYUuwt">💬 Join Discord</a> •
  <a href="https://bindus.directory">🌐 Agent Directory</a>
</p>

#   f i n a n c e - a g e n t 
 
 
