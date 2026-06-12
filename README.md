[English](README.en.md) | **繁體中文**

# IT Diagnostic Agent — 智慧 IT 故障排除助手

> 互動式決策樹 + 深度排查引導 + AI 診斷，專為 IT 工程師設計的免費開源工具

![License](https://img.shields.io/badge/license-MIT-green)
![Static](https://img.shields.io/badge/deploy-static%20HTML-blue)
![Multi-LLM](https://img.shields.io/badge/LLM-Claude%20%7C%20Gemini%20%7C%20OpenAI%20%7C%20Ollama-orange)

---

## 功能概覽

- **互動式決策樹** — 涵蓋網路、硬體、軟體三大診斷模組
- **深度排查引導** — 引導式 YES/NO 步驟流程，適合凌晨三點腦袋不清醒時使用
- **Runbook 模式** — 隱藏 AI 面板，純決策樹介面，適合企業內部 SOP 展示
- **多模型支援** — Claude、Gemini、OpenAI 相容、Ollama 本地模型
- **Ollama 確認提示** — 切換本地模型時自動提示部署檢查清單
- **深色 / 淺色主題** — 一鍵切換，偏好自動儲存
- **零依賴部署** — 純靜態 HTML，不需後端
- **繁體中文 / English 雙語介面**

---

## 深度排查引導

點擊「🔍 深度排查」按鈕進入引導式步驟模式：

- **逐步 YES/NO 引導**，一次只看一個問題，不會資訊過載
- **技術細節可展開**，包含具體指令、線序、Beep 碼等參考資訊
- **三種結果類型**：
  - ✓ **已解決** — 找到問題根因，給出修復步驟
  - → **建議處理步驟** — 中間診斷結果，可繼續下一步或詢問 AI
  - ⚠ **升級二線** — 超出一線範圍，提供升級時需準備的資訊
- **可退回上一步**，不怕走錯路
- **詢問 AI 按鈕** — 直接把當前診斷情境帶入 AI 對話

### 目前支援的深度排查場景

| 場景 | 步驟數 | 涵蓋內容 |
|------|--------|---------|
| 🖥️ 主機不開機 | 8 步 | 電源 → PSU → POST/Beep → RAM → 主板目視 → 最小系統 → CMOS 重置 |
| 🌐 網路斷線 | 8 步 | 範圍確認 → 燈號 → 測線器/線序 → IP 取得 → Ping 閘道 → Ping 8.8.8.8 → DNS |
| 🖨️ 印表機無法列印 | 8 步 | 電源 → 卡紙/耗材 → Ping IP → 列印佇列 → 其他電腦測試 → 測試頁 → 驅動 → GPO |

---

## 支援的 AI 模型

| Provider | 說明 | API Key |
|----------|------|---------|
| Claude (Anthropic) | 預設，診斷品質最佳 | ✅ 需要 |
| Gemini (Google) | 速度快，成本低 | ✅ 需要 |
| OpenAI 相容介面 | 支援 Kimi、Groq、DeepSeek 等 | ✅ 需要 |
| **Ollama（本地）** | 完全離線，零成本，資料不離開公司 | ❌ 不需要 |

### 建議的本地模型

| 模型 | 參數量 | 適用情境 |
|------|--------|---------|
| Gemma 3 12B | 12B | 個人使用，速度快 |
| Gemma 3 72B | 72B | 高品質診斷，需較高記憶體 |
| Gemma 4 E2B / E4B | 2B / 4B | 低資源環境，輕量部署 |
| Qwen3 8B | 8B | 中文優化，適合華文環境 |
| Qwen3.6 35B-A3B | 35B | 高品質，MoE 架構省資源 |

---

## 三階段企業導入建議

### 第一階段：純 Runbook 模式
點擊右上角 📋 按鈕開啟 Runbook 模式，隱藏 AI 面板。
- 零資安風險，不連任何外部服務
- 搭配深度排查引導，讓新人也能獨立排障

### 第二階段：雲端 LLM（低敏感度案例）
適合：印表機、Outlook、DNS、Wi-Fi、NAS。
**注意**：不要輸入帳號密碼、IP 位址表、AD 管理帳號等敏感資訊。

### 第三階段：本地模型（資安要求高的環境）
使用 Ollama 在本機或內網跑模型，資料完全不離開公司。

---

## 快速開始

### GitHub Pages（推薦）
1. Fork 此 repository
2. Settings → Pages → Source 選 `main` branch
3. 訪問 `https://你的帳號.github.io/it-diagnostic-agent`

### 本機使用
```bash
git clone https://github.com/richchang0721-boop/it-diagnostic-agent.git
open index.html
```

---

## Ollama 本地模型設定

### 本機部署
```bash
# 安裝 Ollama
curl -fsSL https://ollama.com/install.sh | sh

# 下載模型
ollama pull gemma3:12b
ollama pull qwen3:8b
ollama pull gemma4:e2b

# 啟動服務
ollama serve
# 端點：http://localhost:11434
```

### 區網部署（全公司共用）
```bash
# 允許外部連線
export OLLAMA_HOST=0.0.0.0
ollama serve

# 員工端點設定：http://192.168.x.x:11434
```

### 帳密控管建議

| 方案 | 說明 | 難度 |
|------|------|------|
| 網路層隔離 | Ollama 只綁定內網 IP | ⭐ 簡單 |
| VPN 控管 | 需連 VPN 才能存取，整合現有 AD | ⭐⭐ 中等 |
| Nginx + Basic Auth | 反向代理加帳密驗證 | ⭐⭐ 中等 |
| OpenID / LDAP | 整合 AD 帳號，企業級 | ⭐⭐⭐ 複雜 |

---

## 涵蓋範圍

### 網路
- CCTV / IP Camera / NVR（PoE、影像斷線、遠端存取）
- Wi-Fi / AP / 802.1X
- DNS 解析失敗
- ISP 線路故障與備援切換

### 硬體
- 伺服器 / PC（POST、開機、效能）
- NAS（RAID 降級、SMB/NFS 存取）
- 印表機（網路列印、驅動、Print Spooler）

### 軟體
| 系統 | 涵蓋範圍 |
|------|----------|
| Active Directory | 帳號鎖定、GPO、DC 複寫、FSMO 轉移 |
| SQL Server | 連線失敗、效能優化、備份還原 |
| Exchange Server | 郵件佇列、SPF/DKIM、遷移至 M365 |
| Office | 部署、KMS 授權、修復 |
| Outlook | Autodiscover、OST 修復、OAuth 2.0 |

---

## 授權

MIT License — 自由使用、修改、商業用途均可

---

## 資源

- [Anthropic API](https://console.anthropic.com)
- [Gemini API](https://aistudio.google.com)
- [Ollama 官網](https://ollama.com)
- [線上試用](https://richchang0721-boop.github.io/it-diagnostic-agent)
