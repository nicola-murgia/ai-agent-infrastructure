# VPS AI Platform: Infrastructure Overview

[![Ubuntu 24.04](https://img.shields.io/badge/os-Ubuntu_24.04-blue.svg)](https://ubuntu.com/)
[![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=flat&logo=docker&logoColor=white)](https://docker.com/)
[![Python](https://img.shields.io/badge/python-3.11+-blue.svg)](https://python.org/)

Production infrastructure for autonomous AI agents: bioinformatics pipelines + sysadmin automation.

---

## 🖥️ Hardware (Hetzner VPS)

| Component | Specification |
|-----------|---------------|
| CPU | AMD EPYC-Genoa (4 vCPU) |
| RAM | 7.6 GB |
| Disk | 150 GB SSD (57 GB free) |
| Network | WireGuard VPN |

---

## 🤖 Agents

| Agent | Role | Framework | Skills |
|-------|------|-----------|--------|
| **Goro** | Bioinformatics automation | OpenClaw | Python pipeline writing, code generation, tool orchestration |
| **Kratos** | Infrastructure automation | Hermes | Docker, GitHub MCP, security, monitoring |

**Communication:** Internal WireGuard network.

---

## 🔐 Security

| Service | Status | Port |
|---------|--------|------|
| SSH | Custom port | `<PORT>` (fail2ban protected) |
| fail2ban | Active | SSH brute-force protection |
| UFW | Active | Filtered traffic |
| WireGuard | Active | Internal subnet |

---

## 🐳 Docker Services

| Container | Image | Status | Port | Purpose |
|-----------|-------|--------|------|---------|
| `ollama` | `ollama/ollama` | Running | `<PORT>` | Local LLM inference |
| `open-webui` | `open-webui/open-webui` | Running + healthy | `<PORT>` | Web UI for LLMs |
| `litellm` | `litellm/litellm` | Stopped | `<PORT>` | Unified LLM gateway |
| `searxng` | `searxng/searxng` | Running | `<IP ADDRESS>:<PORT>` | Private search proxy |

---

## 📦 Installed Tools

| Category | Tools |
|----------|-------|
| **AI/ML** | Ollama, LiteLLM, OpenWebUI |
| **Bioinformatics** | Scanpy, pysradb, sra-tools, STAR, featureCounts |
| **DevOps** | Docker, Docker Compose, WireGuard, fail2ban, UFW |
| **Monitoring** | Custom health scripts, Telegram alerts |
| **Code** | GitHub CLI, Git, Python 3.11 |

---

## 🚀 Automation Capabilities

### Goro (Bioinformatics)
- Python pipeline generation (scRNA-seq, alignment, counting, DE analysis)
- Code execution via Jupyter or CLI
- Tool orchestration (Scanpy, pysradb, sra-tools)

### Kratos (Infrastructure)
- Docker container lifecycle (deploy, update, rollback)
- GitHub operations (PR reviews, issues, releases)
- Security auditing (SSH, ports, users, Docker)
- Health monitoring (Telegram alerts, daily digests)

---

## ⚙️ System Status

- **OS:** Ubuntu 24.04.4 LTS (kernel 6.8.0-124-generic)
- **Memory:** 1.8/7.6 GB used (33%)
- **Disk:** 88/150 GB used (61%)
- **Active Services:** Docker, fail2ban, UFW, ssh, nginx, Pi-hole

---

## 📚 Skills Loading (Kratos)

- `kratos-fail2ban` — SSH protection
- `kratos-alerts` — Telegram notifications
- `kratos-deploy` — Docker deployments
- `kratos-docker` — Container management
- `kratos-security` — Security auditing
- `kratos-sysops` — System monitoring
- `github-*` — GitHub automation
- `vastai-gpu-offload` — GPU provisioning
- `hermes-agent` — Agent configuration
- `ai-gateway-configuration` — LLM gateway setup

---

**Repository:** https://github.com/nicola-murgia/ai-agent-infrastructure  
**Owner:** Nicola Murgia
