**English** | [繁體中文](README.md)

# IT Diagnostic Agent — Smart IT Troubleshooting Assistant

> Interactive decision tree + Claude AI — a free, open-source diagnostic tool built for IT engineers

![License](https://img.shields.io/badge/license-MIT-green)
![Static](https://img.shields.io/badge/deploy-static%20HTML-blue)
![Claude](https://img.shields.io/badge/powered%20by-Claude%20API-orange)

---

## Features

- **Interactive Decision Tree** — Network, Hardware, and Software diagnostic modules
- **Claude AI Integration** — Enter your own API Key and call Claude directly from the browser for AI-powered diagnostic advice
- **Zero-dependency Deployment** — Pure static HTML, no backend or server required — just fork and use
- **Chat History** — Automatically saved to browser localStorage
- **Traditional Chinese UI** — Designed for Taiwan / Hong Kong IT environments

## Coverage

### Network Issues
- CCTV / IP Camera / NVR troubleshooting
- Wi-Fi / AP / 802.1X authentication problems
- DNS resolution failures
- ISP line outages and failover switching

### Hardware Issues
- Server / PC (POST failures, boot issues, performance)
- NAS (Synology / QNAP RAID degradation, access issues)
- Printers (network printing, drivers, Print Spooler)
- Hardware RMA process

### Software Issues
| System | Coverage |
|--------|----------|
| Active Directory | Account lockout, GPO, DC replication, FSMO transfer |
| SQL Server | Connection failures, performance tuning, backup/restore, Always On |
| Exchange Server | Mail queue, SPF/DKIM, migration to M365 |
| Office | Deployment, KMS licensing, repair |
| Outlook | Autodiscover, OST repair, OAuth 2.0 |

---

## Quick Start

### Option 1: GitHub Pages (Recommended)

1. Fork this repository
2. Go to Settings → Pages → Source, select `main` branch
3. Wait a few minutes, then visit `https://your-username.github.io/it-diagnostic-agent`

### Option 2: Run Locally

```bash
git clone https://github.com/your-username/it-diagnostic-agent.git
cd it-diagnostic-agent
# Open index.html directly in your browser
open index.html
```

### Get an API Key

1. Go to [console.anthropic.com](https://console.anthropic.com)
2. Create an account and generate an API Key (free credits for new accounts)
3. Click "Set API Key" in the top-right corner of the tool and paste it in

> **Privacy Note**: Your API Key is stored only in your browser's `localStorage` and is never sent to any third-party server. Every conversation calls the Anthropic API directly from your browser.

---

## Architecture

```
index.html (single file)
├── Pure HTML/CSS/JS — no external dependencies
├── Decision Tree UI — interactive expandable nodes
├── Claude API calls — direct fetch() to api.anthropic.com
└── localStorage — API Key and chat history storage
```

**Why a single HTML file?**
- Anyone can download and use it immediately — no `npm install` needed
- Zero-config GitHub Pages deployment
- Easy to fork and customize

---

## Customization

### Modify Diagnostic Content

Find the relevant `tree-section` in `index.html` and edit the node content directly:

```html
<div class="node-card" onclick="toggleCard(this)">
  <div class="node-badge badge-blue">Your Category</div>
  <div class="nc-title">Issue Title</div>
  <div class="nc-sub">Short description</div>
  <div class="node-detail">
    <!-- Add your diagnostic steps here -->
  </div>
</div>
```

### Modify the AI System Prompt

Find the `SYSTEM_PROMPT` variable and adjust the AI's response style and area of expertise:

```javascript
const SYSTEM_PROMPT = `You are a senior IT engineer...`;
```

### Add a New Language

Copy the entire HTML file and replace the Chinese text with your target language.

---

## Screenshots

*(Add screenshots after deployment)*

---

## Contributing

PRs are welcome! Areas especially needed:
- More diagnostic scenarios (VMware, Hyper-V, Linux Server)
- Additional language versions
- ITSM tool integrations for other regions (Jira, ServiceNow)

---

## License

MIT License — free to use, modify, and use commercially

---

## Resources

- [Anthropic API Docs](https://docs.anthropic.com)
- [Claude Models Overview](https://docs.anthropic.com/en/docs/models-overview)
