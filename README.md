# IT Diagnostic Agent — 智慧 IT 故障排除助手

> 互動式決策樹 + Claude AI，專為 IT 工程師設計的免費開源診斷工具

![License](https://img.shields.io/badge/license-MIT-green)
![Static](https://img.shields.io/badge/deploy-static%20HTML-blue)
![Claude](https://img.shields.io/badge/powered%20by-Claude%20API-orange)

---

## 功能概覽

- **互動式決策樹** — 涵蓋網路、硬體、軟體三大診斷模組
- **Claude AI 整合** — 輸入自己的 API Key，直接在瀏覽器呼叫 Claude 獲得 AI 診斷建議
- **零依賴部署** — 純靜態 HTML，不需後端、不需伺服器，fork 即可用
- **對話記錄** — 自動儲存於瀏覽器 localStorage
- **繁體中文介面** — 針對台灣/香港 IT 環境設計

## 涵蓋範圍

### 網路問題
- CCTV / IP Camera / NVR 故障排除
- Wi-Fi / AP / 802.1X 認證問題
- DNS 解析失敗
- ISP 線路故障與備援切換

### 硬體問題
- 主機 / 伺服器（POST、開機、效能）
- NAS（Synology / QNAP RAID 降級、存取問題）
- 印表機（網路列印、驅動、Print Spooler）
- 硬體 RMA 流程

### 軟體問題
| 系統 | 涵蓋範圍 |
|------|----------|
| Active Directory | 帳號鎖定、GPO、DC 複寫、FSMO 轉移 |
| SQL Server | 連線失敗、效能優化、備份還原、Always On |
| Exchange Server | 郵件佇列、SPF/DKIM、遷移至 M365 |
| Office | 安裝部署、KMS 授權、修復 |
| Outlook | Autodiscover、OST 修復、OAuth 2.0 |

---

## 快速開始

### 方法一：GitHub Pages（推薦）

1. Fork 此 repository
2. 進入 Settings → Pages → Source 選 `main` branch
3. 等待幾分鐘，訪問 `https://你的帳號.github.io/it-diagnostic-agent`

### 方法二：本機使用

```bash
git clone https://github.com/你的帳號/it-diagnostic-agent.git
cd it-diagnostic-agent
# 直接用瀏覽器開啟 index.html
open index.html
```

### 取得 API Key

1. 前往 [console.anthropic.com](https://console.anthropic.com)
2. 建立帳號並申請 API Key（新帳號有免費額度）
3. 在工具右上角點選「設定 API Key」貼上即可

> **隱私說明**：API Key 僅儲存於你的瀏覽器 `localStorage`，不會傳送至任何第三方伺服器。每次對話直接從瀏覽器呼叫 Anthropic API。

---

## 技術架構

```
index.html (單一檔案)
├── 純 HTML/CSS/JS — 無任何外部依賴
├── 決策樹 UI — 互動式節點展開
├── Claude API 呼叫 — 直接 fetch() 至 api.anthropic.com
└── localStorage — API Key 與對話記錄儲存
```

**為什麼選擇單一 HTML 檔案？**
- 任何人都可以直接下載使用，不需要 npm install
- GitHub Pages 零設定部署
- 方便 fork 後自訂內容

---

## 自訂與擴展

### 修改診斷內容

在 `index.html` 中找到對應的 `tree-section`，直接修改節點內容：

```html
<div class="node-card" onclick="toggleCard(this)">
  <div class="node-badge badge-blue">你的分類</div>
  <div class="nc-title">問題標題</div>
  <div class="nc-sub">簡短描述</div>
  <div class="node-detail">
    <!-- 加入你的診斷步驟 -->
  </div>
</div>
```

### 修改 AI System Prompt

找到 `SYSTEM_PROMPT` 變數，調整 AI 的回應風格與專業範疇：

```javascript
const SYSTEM_PROMPT = `你是一位資深 IT 工程師...`;
```

### 新增語言

複製整個 HTML，將中文部分替換為目標語言即可。

---

## 截圖

*（部署後可加入截圖）*

---

## 貢獻

歡迎 PR！特別需要：
- 更多診斷場景（VMware、Hyper-V、Linux Server）
- 英文版本
- 更多地區的 ITSM 工具整合（Jira、ServiceNow）

---

## 授權

MIT License — 自由使用、修改、商業用途均可

---

## 相關資源

- [Anthropic API 文件](https://docs.anthropic.com)
- [Claude Models 說明](https://docs.anthropic.com/en/docs/models-overview)
