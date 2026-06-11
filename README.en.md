**English** | [繁體中文](README.md)

# IT Diagnostic Agent — Smart IT Troubleshooting Assistant

> Interactive decision tree + AI diagnostics — free, open-source, built for IT engineers

![License](https://img.shields.io/badge/license-MIT-green)
![Static](https://img.shields.io/badge/deploy-static%20HTML-blue)
![Multi-LLM](https://img.shields.io/badge/LLM-Claude%20%7C%20Gemini%20%7C%20OpenAI%20%7C%20Ollama-orange)

---

## Features

- **Interactive Decision Tree** — Network, Hardware, Software diagnostic modules
- **Runbook Mode** — Hide AI panel, pure decision tree for enterprise SOP demos
- **Multi-Model Support** — Claude, Gemini, OpenAI-compatible, Ollama local models
- **Ollama Setup Guide** — Confirmation checklist when switching to local model
- **Dark / Light Theme** — One-click toggle, saved automatically
- **Zero-dependency** — Pure static HTML, no backend required
- **Traditional Chinese / English** bilingual interface

---

## Supported AI Models

| Provider | Notes | API Key |
|----------|-------|---------|
| Claude (Anthropic) | Default, best diagnostic quality | ✅ Required |
| Gemini (Google) | Fast, cost-efficient | ✅ Required |
| OpenAI-compatible | Works with Kimi, Groq, DeepSeek, etc. | ✅ Required |
| **Ollama (Local)** | Fully offline, zero cost, data stays on-premise | ❌ Not needed |

### Recommended Local Models

| Model | Params | Use Case |
|-------|--------|----------|
| Gemma 3 12B | 12B | Personal use, fast |
| Gemma 3 72B | 72B | High quality, needs more VRAM |
| Gemma 4 E2B / E4B | 2B / 4B | Low-resource, lightweight |
| Qwen3 8B | 8B | Chinese-optimized |
| Qwen3.6 35B-A3B | 35B | High quality MoE, efficient |

---

## Enterprise Deployment — 3 Phases

### Phase 1: Runbook Mode Only (Start Here)
Click the 📋 button to enable Runbook Mode — hides AI panel, shows decision tree only.
- Zero security risk, no external connections
- Let new staff follow the decision tree to validate your IT workflows

### Phase 2: Cloud LLM (Low-sensitivity cases)
Good for: Printers, Outlook, DNS, Wi-Fi, NAS.
**Never input**: passwords, IP tables, AD admin accounts, VPN configs.

### Phase 3: Local Model (High-security environments)
Run Ollama on-premise — data never leaves the company network.

---

## Quick Start

### GitHub Pages (Recommended)
1. Fork this repository
2. Settings → Pages → Source: `main` branch
3. Visit `https://your-username.github.io/it-diagnostic-agent`

### Run Locally
```bash
git clone https://github.com/richchang0721-boop/it-diagnostic-agent.git
open index.html
```

---

## Ollama Setup

### Local Deployment
```bash
# Install Ollama
curl -fsSL https://ollama.com/install.sh | sh   # Linux/Mac
# Windows: download installer from ollama.com

# Pull a model
ollama pull gemma3:12b       # Recommended starter
ollama pull qwen3:8b         # Chinese-optimized
ollama pull gemma4:e2b       # Lightweight

# Start service
ollama serve
# Endpoint: http://localhost:11434
```

### LAN Deployment (Company-wide)
```bash
# Allow external connections
export OLLAMA_HOST=0.0.0.0
ollama serve

# Open port 11434 in firewall
# Client endpoint: http://192.168.x.x:11434
```

### Access Control Options

| Method | Description | Complexity |
|--------|-------------|------------|
| Network isolation | Bind Ollama to internal IP only | ⭐ Easy |
| VPN control | Requires VPN, integrates with AD | ⭐⭐ Medium |
| Nginx + Basic Auth | Reverse proxy with password | ⭐⭐ Medium |
| OpenID / LDAP | AD account integration, enterprise-grade | ⭐⭐⭐ Complex |

---

## Coverage

### Network
- CCTV / IP Camera / NVR (PoE, offline cameras, remote access)
- Wi-Fi / AP / 802.1X authentication
- DNS resolution failures
- ISP outages and failover

### Hardware
- Server / PC (POST failures, boot issues, performance)
- NAS (RAID degradation, SMB/NFS access)
- Printers (network printing, drivers, Print Spooler)

### Software
| System | Coverage |
|--------|----------|
| Active Directory | Account lockout, GPO, DC replication, FSMO transfer |
| SQL Server | Connection failures, performance, backup/restore |
| Exchange Server | Mail queue, SPF/DKIM, migration to M365 |
| Office | Deployment, KMS licensing, repair |
| Outlook | Autodiscover, OST repair, OAuth 2.0 |

---

## License

MIT License — free to use, modify, and use commercially

---

## Resources

- [Anthropic API](https://console.anthropic.com)
- [Gemini API](https://aistudio.google.com)
- [Ollama](https://ollama.com)
- [Live Demo](https://richchang0721-boop.github.io/it-diagnostic-agent)
