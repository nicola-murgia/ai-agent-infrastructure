# 🛡️ AI Agent Infrastructure

[![Ubuntu 24.04](https://img.shields.io/badge/os-Ubuntu_24.04-blue.svg)](https://ubuntu.com/)
[![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=flat&logo=docker&logoColor=white)](https://docker.com/)
[![Python](https://img.shields.io/badge/python-3.11+-blue.svg)](https://python.org/)
[![WireGuard](https://img.shields.io/badge/vpn-WireGuard-purple.svg)](https://www.wireguard.com/)

Production infrastructure for **autonomous AI agents** — bioinformatics pipelines + infrastructure automation.

---

## 🖥️ Hardware (Hetzner VPS)

| Component | Specification |
|-----------|---------------|
| CPU | AMD EPYC-Genoa (4 vCPU) |
| RAM | 7.6 GB |
| Disk | 150 GB SSD (57 GB free) |
| Network | WireGuard VPN (10.7.0.0/24) |

---

## 🤖 Agents

| Agent | Role | Framework | Skills |
|-------|------|-----------|--------|
| **Goro** | Career strategy, data analysis & bioinformatics | OpenClaw | Job search, CV/cover letter, data pipelines (Python/R), ML, scRNA-seq, behavioral analysis, scientific writing, literature monitoring, email drafting, docx generation, humanizer |
| **Kratos** | Infrastructure automation | Hermes | Docker, GitHub MCP, security, monitoring |

**Communication:** Internal WireGuard network (`10.7.0.1`).

---

## 🔐 Security

| Service | Status | Port |
|---------|--------|------|
| SSH | Custom port | `<PORT>` (fail2ban protected) |
| fail2ban | Active | SSH brute-force protection |
| UFW | Active | Filtered traffic |
| WireGuard | Active | Internal subnet (10.7.0.0/24) |

---

## 🐳 Docker Services

| Container | Image | Status | Port | Purpose |
|-----------|-------|--------|------|---------|
| `ollama` | `ollama/ollama` | Running | `11434` | Local LLM inference |
| `open-webui` | `open-webui/open-webui` | Running + healthy | `3000` | Web UI for LLMs |
| `openclaw-searxng` | `searxng/searxng` | Running | `8082` | Private search proxy |
| `litellm-litellm` | `litellm/litellm:main-stable` | Running | `4000` (via 10.7.0.1) | Multi-provider LLM routing |
| `postgres` | `postgres:16-alpine` | Running | `5432` | Litellm database |
| `manifest` | `manifestdotbuild/manifest` | Running | `3001` | Manifest platform |

---

## 📦 Installed Tools

| Category | Tools |
|----------|-------|
| **AI/ML** | Ollama, LiteLLM, OpenWebUI, OpenClaw |
| **Bioinformatics** |  Scanpy, pysradb, sra-tools, STAR, featureCounts, DeepLabCut, SimBA, Keypoint MoSeq, scikit-learn, PyTorch, pandas, numpy, scipy, matplotlib, seaborn, plotly, lme4, ggplot2, tidyverse, Snakemake, MLflow, python-docx, Jupyter  |
| **DevOps** | Docker, Docker Compose, WireGuard, fail2ban, UFW, NGINX |
| **Monitoring** | Custom health scripts, Telegram alerts, Cron jobs |
| **Code** | GitHub CLI, Git, Python 3.11 |

---

## 🚀 Automation Capabilities

### Goro (Data Analysis & Bioinformatics)
- **Literature monitoring** — PubMed, bioRxiv, arXiv keyword alerts
- **Data analysis** — Python (pandas, numpy, scipy, matplotlib, seaborn, scikit-learn) and R (tidyverse, ggplot2, lme4, emmeans)
- **Behavioral pipelines** — DeepLabCut, SimBA, Keypoint MoSeq post-processing
- **scRNA-seq** — Scanpy, STAR, featureCounts, pysradb
- **ML pipelines** — PyTorch, HuggingFace, clustering, dimensionality reduction
- **Scientific writing** — Manuscripts, grants, reports (American English, direct style)
- **AI text humanizer** — Strip AI-isms, add voice and personality
- **Book-to-skill** — Convert PDF/EPUB/DOCX into structured agent knowledge bases
- **File transfer** — Auto-send any format via Telegram

### Kratos (Infrastructure)
- Docker container lifecycle (deploy, update, rollback)
- GitHub operations (PR reviews, issues, releases via MCP)
- Security auditing (SSH, ports, users, Docker)
- Health monitoring (Telegram alerts, daily digests)
- OpenClaw gateway management
- Local LLM serving (Ollama, LiteLLM)

---

## ⚙️ System Status

- **OS:** Ubuntu 24.04.4 LTS (kernel 6.8.0-124-generic)
- **Memory:** 1.8/7.6 GB used (33%)
- **Disk:** 88/150 GB used (61%)
- **Active Services:** Docker, fail2ban, UFW, ssh, NGINX, Pi-hole, WireGuard

---

## 📚 Skills Loading (Kratos)

| Category | Skills |
|----------|--------|
| **DevOps** | `kratos-fail2ban`, `kratos-deploy`, `kratos-docker`, `kratos-sysops`, `kratos-alerts` |
| **Security** | `kratos-security`, `github-code-review`, `github-pr-workflow` |
| **GitHub** | `github-auth`, `github-repo-management`, `github-issues`, `codebase-inspection` |
| **MLOps** | `vastai-gpu-offload`, `hermes-agent`, `ai-gateway-configuration` |

---

## 🔗 Services Endpoints

| Service | URL | Access |
|---------|-----|--------|
| OpenWebUI | `http://<VPS>:3000` | Public |
| LiteLLM Proxy | `http://10.7.0.1:4000` | WireGuard internal |
| SearXNG | `http://127.0.0.1:8082` | Local only |
| OpenClaw Gateway | `http://127.0.0.1:18789` | Local (token auth) |
| Manifest | `http://<VPS>:3001` | Public |

---

**Repository:** https://github.com/nicola-murgia/ai-agent-infrastructure  
**Owner:** Nicola Murgia
