# Agents Architecture — AI Agent 架構詳解

七份互相連結的深度架構解說(繁體中文)。分兩類:**CLI/助理框架**(OpenClaw、Hermes Agent、Claude Code、Grok Build)與**多 Bot 平台**(Grok Bot 0.18、CopilotKit OpenBot)。
純靜態 HTML(內嵌 CSS/JS、相對連結、無建置步驟、無外部相依)。

| 檔案 | 主題 | 重點 |
|------|------|------|
| `index.html` | 入口頁 | 兩分區導覽(4 框架 + 2 多 Bot 平台)+ 比較入口 |
| `openclaw-architecture.html` | OpenClaw | gateway 控制平面、一切皆 plugin、13 元件詳解 |
| `hermes-architecture.html` | Hermes Agent | ★ 自我學習閉環、6 backend、Kanban;含**四框架比較頁 + 多 Bot 平台附錄** |
| `claude-code-architecture.html` | Claude Code | ★ 12 harness 機制、🔍 幕後揭密(逆向研究 v2.1.88) |
| `grok-build-architecture.html` | Grok Build | ★ Actor Runtime(無鎖)、★ 生產級工程亮點、🔍 84-crate 工作區(公開鏡像) |
| `grok-build-explained.html` | Grok Build 原始碼解說 | 21 節逐節走過 repo 佈局、agent 迴圈、工具系統、沙箱、全 crate 索引 |
| `grokbot/grok-bot-0.18-architecture.html` | Grok Bot 0.18 | ★ Bot 間 5 條通訊通道、★ 群聊 round-robin / chief-member 之答、🔍 逐檔證據 |
| `grokbot/openbot-vs-grokbot.html` | OpenBot vs Grok Bot | 兩種「多 Bot」的差異、治理是機制還是 prompt、🧱 移植藍圖 |

四個框架各用三條思路貫穿(訊息旅程 / 由下而上 / 元件詳解),右上角可在四份間自由切換;`grokbot/` 兩份互指並可回到入口頁。

> ⚠️ **別搞混**:`grok-build-*`(xAI 官方 Rust **CLI coding agent**)與 `grokbot/`(**Electron 桌面多 Bot App**)是兩個完全不同的東西,只是名字像。

## 本機預覽

任一靜態伺服器即可,例如:

```bash
python -m http.server 8080
# 開 http://localhost:8080/
```

或直接用瀏覽器開 `index.html`(相對連結在 `file://` 下也能運作)。

## 部署到 Render

本 repo 含 `render.yaml`(Blueprint),部署為 **Static Site**:

1. Render → **New** → **Blueprint** → 連到本 GitHub repo。
2. Render 讀 `render.yaml` 自動建立靜態站(無建置指令、發佈路徑為 repo 根目錄)。
3. 完成後 `index.html` 即為首頁;`/openclaw`、`/hermes`、`/claude-code`、`/grok`、`/grok-explained`、`/grok-bot`、`/openbot` 為簡短網址。

> 或手動建立:New → **Static Site** → Build Command 留空 → Publish Directory 填 `.`。

## 來源與免責

- OpenClaw / Hermes 內容整理自各自開源 repo 的 `docs/`、`src/` 等(2026 年快照)。
- Claude Code 內容基於**第三方公開逆向研究**(`sanbuphy/learn-coding-agent`,對象 v2.1.88),**非 Anthropic 官方資料,可能過時或有誤**。
- Grok Build 內容整理自 xAI **公開原始碼鏡像**(`xai-org/grok-build`,對應 monorepo commit `2ec0f0c8` 快照)的 README、`crates/` 原始碼與 user-guide;**非 xAI 官方文件,可能過時**。
- Grok Bot 0.18 內容整理自社群的**非官方逆向重建** `b-nnett/grok-bot-0.18-reconstructed`(針對 **0.18.0 單一版本快照**)。可信度分級:`source/`(控制平面與執行平面)**高** —— 多數生成檔帶 `@evidence` 註解與 region SHA-256;模組命名與檔案位置 **中**;`frontend/src/recovered/` **低** —— 原版未附前端原始碼或 source map,**renderer 未還原**。**非原廠 monorepo、非官方版本**;雲端後端內部實作不涵蓋。
- OpenBot 內容整理自官方開源 repo `CopilotKit/OpenBot`(MIT、**自述 alpha**)。注意其原始碼註解常描述**尚未實作**的功能(bot-to-bot hops、routines),對照頁已標「已規劃未實作」。CopilotKit Intelligence 為外部服務,只能從 client 呼叫看見介面。
- 與 Grok Bot / OpenBot 的對照比的是**設計選擇,不是成熟度**(官方 alpha 開源專案 vs 出貨商業產品的非官方逆向重建,程式碼量差 2–5 倍)。
- 僅供技術研究與教育交流,請勿用於商業用途。所有商標與智慧財產權屬各自公司。
