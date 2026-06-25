# Agents Architecture — 三大 AI Agent 框架架構詳解

三份互相連結的深度架構解說(繁體中文),涵蓋 **OpenClaw**、**Hermes Agent**、**Claude Code**。
純靜態 HTML(內嵌 CSS/JS、相對連結、無建置步驟、無外部相依)。

| 檔案 | 主題 | 重點 |
|------|------|------|
| `index.html` | 入口頁 | 三框架導覽 + 比較入口 |
| `openclaw-architecture.html` | OpenClaw | gateway 控制平面、一切皆 plugin、13 元件詳解 |
| `hermes-architecture.html` | Hermes Agent | ★ 自我學習閉環、6 backend、Kanban;含**三框架比較頁** |
| `claude-code-architecture.html` | Claude Code | ★ 12 harness 機制、🔍 幕後揭密(逆向研究 v2.1.88) |

每份用三條思路貫穿(訊息旅程 / 由下而上 / 元件詳解),右上角可在三份間自由切換。

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
3. 完成後 `index.html` 即為首頁;`/openclaw`、`/hermes`、`/claude-code` 為簡短網址。

> 或手動建立:New → **Static Site** → Build Command 留空 → Publish Directory 填 `.`。

## 來源與免責

- OpenClaw / Hermes 內容整理自各自開源 repo 的 `docs/`、`src/` 等(2026 年快照)。
- Claude Code 內容基於**第三方公開逆向研究**(`sanbuphy/learn-coding-agent`,對象 v2.1.88),**非 Anthropic 官方資料,可能過時或有誤**。
- 僅供技術研究與教育交流,請勿用於商業用途。所有商標與智慧財產權屬各自公司。
