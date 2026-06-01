# VPS AI Platform: Production Infrastructure Overview

[![Ubuntu 24.04](https://img.shields.io/badge/os-Ubuntu_24.04-blue.svg)](https://ubuntu.com/)
[![Linux Kernel](https://img.shields.io/badge/kernel-6.8.0-olive.svg)](https://kernel.org/)
[![Python](https://img.shields.io/badge/python-3.11+-blue.svg)](https://python.org/)
[![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=flat&logo=docker&logoColor=white)](https://docker.com/)
[![GitHub Actions](https://img.shields.io/badge/actions-%232671E5.svg?style=flat&logo=githubactions)](https://github.com/features/actions)

**Autonomous infrastructure: 24/7 AI agents for bioinformatics + sysadmin automation.**

---

## 🖥️ Hardware Spec (Hetzner VPS)

| Component | Specification |
|-----------|---------------|
| CPU | AMD EPYC-Genoa (4 vCPU) |
| RAM | 7.6 GB |
| Disk | 150 GB SSD (57 GB free) |
| Network | WireGuard VPN (10.7.0.0/24) |

---

## 🤖 Agent Architecture

| Agent | Role | Framework | Primary Skills |
|-------|------|-----------|----------------|
| **Goro** | Bioinformatics pipeline automation | OpenClaw | scRNA-seq, Vast.ai GPU offload, Scanpy |
| **Kratos** | Systems & infrastructure automation | Hermes (Kratos persona) | Docker, GitHub MCP, Hardening, Monitoring |

**Communication:** RPC/MCP over internal WireGuard network.

---

## 🔐 Security Configuration

| Service | Status | Port |
|---------|--------|------|
| SSH | Custom port | 54322 (rate-limited) |
| fail2ban | Active | SSH brute-force protection |
| UFW | Active | Allow: 54322/tcp, 443/tcp, WireGuard (51825/udp) |
| WireGuard | Active | `10.7.0.0/24` internal subnet |

**Hardening:**
- Non-standard SSH port (54322)
- Password authentication enabled (for CLI access)
- Root login permitted (internal use)
- Automatic updates (`unattended-upgrades`)
- Intrusion detection via fail2ban

---

## 🐳 Docker Services

| Container | Image | Status | Port | Purpose |
|-----------|-------|--------|------|---------|
| `ollama` | `ollama/ollama` | Running | `11434` | Local LLM inference |
| `open-webui` | `open-webui/open-webui` | Running + healthy | `3000` | Web UI for LLMs |
| `litellm` | `litellm/litellm` | Stopped | `4000` | Unified LLM gateway (LiteLLM) |
| `litellm-db` | `postgres:16` | Stopped | — | LiteLLM PostgreSQL backend |
| `searxng` | `searxng/searxng` | Running | `127.0.0.1:8082` | Private search proxy |

---

## 📦 Installed Software Stack

| Category | Tools |
|----------|-------|
| **AI/ML** | Ollama, LiteLLM, OpenWebUI, Scanpy, pysradb |
| **Bioinformatics** | sra-tools, STAR, featureCounts, MultiQC |
| **DevOps** | Docker, Docker Compose, WireGuard, fail2ban |
| **Monitoring** | Custom health scripts, Telegram alerts |
| **Infrastructure** | Nginx, Pi-hole FTL, Prometheus (via OpenTelemetry) |

---

## 🚀 Automation Capabilities

### Goro (Bioinformatics)
- **scRNA-seq pipeline:** SRA → FASTQ → Alignment → Counting → Scanpy → HTML report
- **Vast.ai GPU offload:** Auto-rent RTX 3090 instances, rsync data, shutdown after job
- **Notebook orchestration:** Generate interactive Jupyter notebooks with results

### Kratos (Infrastructure)
- **GitHub automation:** PR reviews, issue triage, releases via MCP server
- **Credential rotation:** Token lifecycle management
- **Health monitoring:** Daily Telegram digests, real-time alerts
- **Docker service management:** Deploy, update, rollback, scale

---

## 📈 System Metrics (Current)

- **Uptime:** 14 hours 35 minutes
- **CPU Load:** 0.07 (very low)
- **Memory:** 1.8/7.6 GB used (33%)
- **Disk:** 88/150 GB used (61%)

---

## 🛠️ Getting Started

1. **SSH access:**
   ```bash
   ssh -p 54322 root@<server-ip>
   ```

2. **Check services:**
   ```bash
   systemctl status docker fail2ban ufw
   docker ps
   ```

3. **View Telegram health digest:**
   - Daily at 08:00 (cron job)
   - Immediate alerts on anomalies

---

## 📚 Agent Capabilities Reference

### Skills Loaded (Kratos)
- `kratos-fail2ban` — SSH brute-force protection
- `kratos-alerts` — Telegram notifications & health digests
- `kratos-deploy` — Docker service deployments
- `kratos-docker` — Container lifecycle management
- `kratos-security` — Security auditing (SSH, ports, users, Docker)
- `kratos-sysops` — System diagnostics & monitoring
- `hermes-agent` — Agent framework configuration
- `ai-gateway-configuration` — LiteLLM/OpenClaw/Hermes gateway setup
- `github-*` — Repository, PR, issue management via MCP
- `vastai-gpu-offload` — GPU instance provisioning
- `jupyter-live-kernel` — Interactive data analysis

---

**Last updated:** 2026-06-01  
**Platform:** Hetzner VPS (Ubuntu 24.04 LTS)  
**Owner:** Nicola Murgia
