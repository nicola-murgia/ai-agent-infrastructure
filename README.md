# 🛡️ AI Agent Infrastructure

[![Ubuntu 24.04](https://img.shields.io/badge/os-Ubuntu_24.04-blue.svg)](https://ubuntu.com/)
[![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=flat&logo=docker&logoColor=white)](https://docker.com/)
[![Python](https://img.shields.io/badge/python-3.11+-blue.svg)](https://python.org/)
[![Ollama](https://img.shields.io/badge/ollama-local-green.svg)](https://ollama.com/)
[![OpenClaw](https://img.shields.io/badge/agent-OpenClaw-purple.svg)](https://openclaw.ai/)
[![Hermes](https://img.shields.io/badge/agent-Hermes-orange.svg)](https://hermes-agent.dev/)

Production infrastructure for **autonomous AI agents** — dual-agent architecture combining bioinformatics analysis and infrastructure automation.

---

## 🏗️ Architecture

```
┌──────────────┐     ┌──────────────┐
│  OpenClaw    │     │   Hermes     │
│  Gateway     │────▶│   Gateway    │
│  (port 1)    │     │  (port 2)    │
└──────┬───────┘     └──────┬───────┘
       │                     │
       ▼                     ▼
┌──────────────┐     ┌──────────────┐
│  Goro        │     │   Kratos     │
│  (Agent)     │     │   (Agent)    │
│  Data/       │     │   Infra/     │
│  Bioinfo     │     │   Sysadmin   │
└──────────────┘     └──────────────┘
```

Two independent agent frameworks running side by side, each serving a distinct role.

---

## 🤖 Agents

| Agent | Framework | Role | Domain |
|-------|-----------|------|--------|
| **Goro** | OpenClaw | Data analysis, bioinformatics, career strategy | Scientific computing, bio stats, ML pipelines, job search |
| **Kratos** | Hermes | Infrastructure automation, security, monitoring | Docker, GitHub ops, system health, LLM serving |

Both agents communicate via an internal VPN and share access to the same service stack.

---

## 🐳 Services

| Service | Purpose |
|---------|---------|
| **OpenWebUI** | Web interface for LLM interaction |
| **SearXNG** | Privacy-first search aggregation |
| **Ollama** | Local LLM inference server |
| **Pi-hole** | Network-level ad blocking and DNS |
| **NGINX** | Reverse proxy and TLS termination |
| **WireGuard** | Secure VPN for internal agent communication |

### Local LLM Models (Ollama)

| Model | Size | Quantization |
|-------|------|-------------|
| gpt-oss | 20.9B | MXFP4 |
| gemma4:e4b | 8.0B | Q4_K_M |
| gemma4:e2b | 5.1B | Q4_K_M |
| gemma4-12b | 11.9B | Q4_K_M |
| llama3.1 | 8.0B | Q4_K_M |
| mistral | 7.2B | Q4_K_M |
| qwen2.5:7b | 7.6B | Q4_K_M |
| qwen3.5:2b | 2.3B | Q8_0 |

Plus cloud-proxied models: DeepSeek V4 Pro, GLM-5.2, Kimi K2.7 Code.

---

## 🔐 Security

- **SSH** — Custom port, fail2ban brute-force protection
- **Firewall** — UFW with filtered traffic rules
- **VPN** — WireGuard for internal agent communication
- **Monitoring** — Daily health digests via Telegram alerts
- **Hardening** — Regular security audits, minimal attack surface

---

## 🚀 Agent Capabilities

### Goro (OpenClaw) — Data Analysis & Bioinformatics

- **Literature monitoring** — PubMed, bioRxiv, arXiv keyword alerts
- **Data analysis** — Python (pandas, numpy, scipy, scikit-learn) and R (tidyverse, ggplot2, lme4)
- **Bioinformatics** — Scanpy, STAR, featureCounts, pysradb, SRA tools
- **Behavioral pipelines** — DeepLabCut, SimBA, Keypoint MoSeq
- **Machine learning** — PyTorch, HuggingFace, clustering, dimensionality reduction
- **Scientific writing** — Manuscripts, grants, reports (American English, direct style)
- **AI text humanizer** — Strip AI-isms, add voice and personality
- **Book-to-skill** — Convert PDF/EPUB/DOCX into structured agent knowledge bases
- **File transfer** — Auto-send any format via Telegram
- **SFT dataset generation** — BioStat Copilot, ICH/GxP compliance data, CRF/Consort diagrams

### Kratos (Hermes) — Infrastructure Automation

- **Docker lifecycle** — Deploy, update, rollback containers
- **GitHub operations** — PR reviews, issues, releases via MCP
- **Security auditing** — SSH, ports, users, Docker
- **Health monitoring** — Telegram alerts, daily digests
- **Gateway management** — OpenClaw and Hermes gateways
- **Local LLM serving** — Ollama management, model serving
- **Cron orchestration** — Scheduled jobs, health checks, automation
- **Engraphis memory** — Persistent cross-session knowledge graph

---

## 🛠️ Installed Tooling

| Category | Tools |
|----------|-------|
| **AI/ML** | Ollama, OpenWebUI, OpenClaw, Hermes, LiteLLM |
| **Bioinformatics** | Scanpy, pysradb, SRA tools, STAR, featureCounts, DeepLabCut, SimBA, Keypoint MoSeq |
| **Data Science** | scikit-learn, PyTorch, pandas, numpy, scipy, matplotlib, seaborn, plotly |
| **R Stats** | lme4, ggplot2, tidyverse, Snakemake |
| **DevOps** | Docker, Docker Compose, WireGuard, fail2ban, UFW, NGINX |
| **Monitoring** | Custom health scripts, Telegram alerts, cron |
| **Code** | GitHub CLI, Git, Python 3.11, Node.js |

---

## 📚 Agent Skills

### Kratos Skills
| Category | Skills |
|----------|--------|
| **DevOps** | System operations, Docker management, web server operations, LLM web stack |
| **Security** | Security auditing, code review, PR workflow |
| **GitHub** | Auth, repo management, issues, codebase inspection |
| **MLOps** | GPU offload, local LLM inference, hardware procurement |
| **AI** | Hermes agent management, webhook subscriptions |

### Goro Skills
| Category | Skills |
|----------|--------|
| **Data Science** | Jupyter, data analysis, visualization |
| **Bioinformatics** | scRNA-seq pipelines, behavioral analysis, literature monitoring |
| **Writing** | Scientific writing, CV/cover letters, humanizer |
| **Research** | PubMed, arXiv, bioRxiv monitoring |

---

## ⚙️ System Status

- **OS:** Ubuntu 24.04 LTS
- **Active Services:** Docker, fail2ban, UFW, SSH, NGINX, Pi-hole, WireGuard
- **Docker Containers:** OpenWebUI, SearXNG
- **Agent Frameworks:** OpenClaw Gateway, Hermes Gateway, Engraphis MCP

---

**Repository:** https://github.com/nicola-murgia/ai-agent-infrastructure
**Owner:** Nicola Murgia