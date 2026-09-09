# 🛡️ AI Agent Infrastructure

[![Ubuntu 24.04](https://img.shields.io/badge/os-Ubuntu_24.04-blue.svg)](https://ubuntu.com/)
[![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=flat&logo=docker&logoColor=white)](https://docker.com/)
[![Python](https://img.shields.io/badge/python-3.11+-blue.svg)](https://python.org/)
[![Ollama Cloud](https://img.shields.io/badge/ollama-cloud-green.svg)](https://ollama.com/)
[![OpenClaw](https://img.shields.io/badge/agent-OpenClaw-purple.svg)](https://openclaw.ai/)
[![Hermes](https://img.shields.io/badge/agent-Hermes-orange.svg)](https://hermes-agent.dev/)

Production infrastructure for **autonomous AI agents** — dual-agent architecture combining infrastructure automation, security, and monitoring.

---

## 🏗️ Architecture

```
┌──────────────┐     ┌──────────────┐
│  OpenClaw    │     │   Hermes     │
│  Gateway     │────▶│   Gateway    │
│  (port 18789)│     │  (managed)   │
└──────┬───────┘     └──────┬───────┘
       │                    │
       ▼                    ▼
┌──────────────┐     ┌──────────────┐
│  OpenClaw    │     │   Kratos     │
│  (Agent)     │     │   (Agent)    │
│  Web/        │     │   Infra/     │
│  Automation  │     │   Sysadmin   │
└──────────────┘     └──────────────┘
```

Two independent agent frameworks running side by side, each serving a distinct role.

---

## 🤖 Agents

| Agent | Framework | Role | Domain |
|-------|-----------|------|--------|
| **OpenClaw** | OpenClaw | Web automation, notebook execution, agent orchestration | Browser control, code execution, workflow automation |
| **Kratos** | Hermes | Infrastructure automation, security, monitoring | Docker, GitHub ops, system health, LLM serving |

Both agents communicate via an internal VPN and share access to the same service stack.

---

## 🐳 Services

| Service | Purpose | Status |
|---------|---------|--------|
| **OpenWebUI** | Web interface for LLM interaction | ✅ Running (port 3000) |
| **SearXNG** | Privacy-first search aggregation | ✅ Running (port 8082) |
| **Pi-hole** | Network-level ad blocking and DNS | ✅ Running (port 53, 8443) |
| **NGINX** | Reverse proxy and TLS termination | ✅ Running (port 80, 443) |
| **WireGuard** | Secure VPN for internal agent communication | ✅ Running (wg0) |
| **Engraphis Dashboard** | Memory/knowledge graph UI | ✅ Running (port 8700) |
| **Ollama Cloud** | LLM inference backend | ☁️ Cloud proxy |
| **OpenClaw Gateway** | Agent gateway | ✅ Running (port 18789) |
| **Hermes Gateway** | Agent gateway | ✅ Running (managed) |

### Listening Ports

| Port | Service |
|------|---------|
| 53 | Pi-hole FTL |
| 80 | NGINX |
| 443 | NGINX |
| 3000 | Docker proxy (OpenWebUI) |
| 8082 | Docker proxy (SearXNG) |
| 8700 | Engraphis Dashboard |
| 18789 | OpenClaw Gateway |
| 54322 | SSH |

---

## 🔐 Security

- **SSH** — Custom port (54322), fail2ban brute-force protection
- **Firewall** — UFW with filtered traffic rules
- **VPN** — WireGuard for internal agent communication (wg0 active)
- **Monitoring** — Daily health digests via Telegram, RAM watchdog
- **Hardening** — Regular security audits, minimal attack surface

---

## 🚀 Agent Capabilities

### OpenClaw — Web Automation & Orchestration

- **Browser automation** — Navigate, click, snapshot, vision analysis
- **Code execution** — Run Python/bash in isolated sessions
- **Notebook operations** — Edit, run, manage Jupyter-style workflows
- **GitHub integration** — PR reviews, issues, releases via MCP
- **Cron orchestration** — Scheduled jobs, health checks, automation
- **File management** — Read, write, patch, search across filesystem

### Kratos (Hermes) — Infrastructure Automation

- **Docker lifecycle** — Deploy, update, rollback containers
- **Security auditing** — SSH, ports, users, Docker, fail2ban
- **Health monitoring** — Telegram alerts, daily digests, RAM watchdog
- **Gateway management** — OpenClaw and Hermes gateways
- **LLM serving** — Ollama Cloud proxy, model routing
- **Engraphis memory** — Persistent cross-session knowledge graph
- **GitHub operations** — Auth, repo management, issues, code review

---

## 🛠️ Installed Tooling

| Category | Tools |
|----------|-------|
| **AI/ML** | Ollama Cloud, OpenWebUI, OpenClaw, Hermes, Engraphis MCP |
| **Data Science** | Python 3.11, pandas, numpy, scipy, scikit-learn, PyTorch |
| **DevOps** | Docker, Docker Compose, WireGuard, fail2ban, UFW, NGINX |
| **Monitoring** | Custom health scripts, Telegram alerts, cron, RAM watchdog |
| **Code** | GitHub CLI, Git, Node.js |
| **Search** | SearXNG (privacy-first aggregation) |

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

### OpenClaw Skills

| Category | Skills |
|----------|--------|
| **Automation** | Browser control, code execution, notebook operations |
| **Orchestration** | Cron jobs, task delegation, multi-agent workflows |
| **GitHub** | PR management, code review, issue tracking |

---

## ⚙️ System Status

- **OS:** Ubuntu 24.04 LTS
- **Active Services:** Docker, fail2ban, UFW, SSH, NGINX, Pi-hole, WireGuard, OpenClaw Gateway, Hermes Gateway, Engraphis Dashboard
- **Docker Containers:** OpenWebUI, SearXNG
- **Agent Frameworks:** OpenClaw Gateway, Hermes Gateway, Engraphis MCP
- **LLM Backend:** Ollama Cloud (no local inference container)
- **Daily Health Digest:** Automated Telegram delivery at 08:00 daily

---

## 📊 Recent Optimizations

- **Health digest format** — Clean, plain-label layout with service-name mapping for firewall and listening ports
- **RAM watchdog** — 30-minute interval memory monitoring via cron
- **Cron consolidation** — `no_agent=true` for script-only jobs, eliminating LLM rate-limit failures
- **Port hygiene** — Removed stale UFW rules for orphaned ports (11434, 8899)
- **GitHub auth** — Rotated PAT with minimal required scopes (`read:org`, `repo`, `workflow`)

---

**Repository:** https://github.com/nicola-murgia/ai-agent-infrastructure
**Owner:** Nicola Murgia
