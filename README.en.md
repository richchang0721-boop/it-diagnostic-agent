**English** | [繁體中文](README.md)

# IT Diagnostic Agent — Smart IT Troubleshooting Assistant

> Interactive decision tree + guided deep diagnosis + AI — free, open-source, built for IT engineers

![License](https://img.shields.io/badge/license-MIT-green)
![Static](https://img.shields.io/badge/deploy-static%20HTML-blue)
![Multi-LLM](https://img.shields.io/badge/LLM-Claude%20%7C%20Gemini%20%7C%20OpenAI%20%7C%20Ollama-orange)

---

## Features

- **Interactive Decision Tree** — Network, Hardware, Software diagnostic modules
- **Guided Deep Diagnosis** — Step-by-step YES/NO flow, perfect for 3am troubleshooting
- **Runbook Mode** — Hide AI panel, pure decision tree for enterprise SOP demos
- **Multi-Model Support** — Claude, Gemini, OpenAI-compatible, Ollama local models
- **Ollama Setup Guide** — Confirmation checklist when switching to local model
- **Dark / Light Theme** — One-click toggle, saved automatically
- **Zero-dependency** — Pure static HTML, no backend required
- **Traditional Chinese / English** bilingual interface

---

## Guided Deep Diagnosis

Click the **🔍 Deep Diagnosis** button to enter guided step mode:

- **Step-by-step YES/NO questions** — one question at a time, no information overload
- **Expandable technical details** — commands, cable color codes, beep codes, etc.
- **Three result types**:
  - ✓ **Resolved** — Root cause found, fix steps provided
  - → **Recommended Action** — Intermediate result, continue or Ask AI
  - ⚠ **Escalate** — Beyond L1 scope, includes what to prepare for L2
- **Back button** — Step back if you went the wrong way
- **Ask AI button** — Sends current diagnostic context directly to AI chat

### Supported Deep Diagnosis Scenarios

| Scenario | Steps | Coverage |
|----------|-------|----------|
| 🖥️ PC/Server Won't Boot | 8 steps | Power → PSU → POST/Beep → RAM → Board visual → Minimal config → CMOS reset |
| 🌐 Network Disconnection | 8 steps | Scope → Link light → Cable tester/568B → IP → Ping gateway → Ping 8.8.8.8 → DNS |
| 🖨️ Printer Not Printing | 8 steps | Power → Jam/supplies → Ping IP → Print queue → Test from other PC → Self-test → Driver → GPO |

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

### Phase 1: Runbook Mode Only
Click the 📋 button to enable Runbook Mode — hides AI panel.
- Zero security risk, no external connections
- Pair with Guided Deep Diagnosis for new staff independence

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
curl -fsSL https://ollama.com/install.sh | sh

# Pull models
ollama pull gemma3:12b
ollama pull qwen3:8b
ollama pull gemma4:e2b

# Start service
ollama serve
# Endpoint: http://localhost:11434
```

### LAN Deployment (Company-wide)
```bash
# Allow external connections
export OLLAMA_HOST=0.0.0.0
ollama serve

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
