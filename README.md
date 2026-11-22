# 🍰 法式甜點科學與跨流派教學知識庫 (French Pastry Science & Teaching LLM Wiki)

> **作業主題**：用 LLM Wiki 做一份教學 HTML 簡報  
> **GitHub 儲存庫連結**：https://github.com/Iris040407/Dessert-LLM-Wiki  
> **🌟 最外層 LLM Wiki 教學簡報總入口 (`index.html`)**：**https://iris040407.github.io/Dessert-LLM-Wiki/**  
> **🖥️ 5 份獨立單元簡報 ＋ 1 份綜合總論簡報線上直達連結**：
> - 🏠 **[最外層 Wiki 簡報總中心 (`index.html`)](https://iris040407.github.io/Dessert-LLM-Wiki/)** ｜ 🗂️ **[最外層全局索引 (`index.md`)](index.md)**
> - 🐚 **[簡報 01：瑪德蓮專題 (`slides/01-madeleine.html`)](https://iris040407.github.io/Dessert-LLM-Wiki/slides/01-madeleine.html)**
> - 🧱 **[簡報 02：費南雪與焦化奶油專題 (`slides/02-financier.html`)](https://iris040407.github.io/Dessert-LLM-Wiki/slides/02-financier.html)**
> - 🔔 **[簡報 03：波爾多可麗露糊化與白頭專題 (`slides/03-canele.html`)](https://iris040407.github.io/Dessert-LLM-Wiki/slides/03-canele.html)**
> - 🍬 **[簡報 04：法式馬卡龍蛋白霜物理專題 (`slides/04-macaron.html`)](https://iris040407.github.io/Dessert-LLM-Wiki/slides/04-macaron.html)**
> - 🍮 **[簡報 05：卡士達醬澱粉酶與甘納許乳化專題 (`slides/05-creams-and-ganache.html`)](https://iris040407.github.io/Dessert-LLM-Wiki/slides/05-creams-and-ganache.html)**
> - 📊 **[綜合總論簡報：法式甜點科學 101 (`slides/index.html`)](https://iris040407.github.io/Dessert-LLM-Wiki/slides/index.html)** *(含互動診斷室與隨堂測驗)*
> - 📜 **[完整作業繳交報告 (`HOMEWORK_REPORT.md`)](HOMEWORK_REPORT.md)** ｜ ⚙️ **[核心規範 (`AGENTS.md`)](AGENTS.md)** ｜ 🕒 **[檢查日誌 (`wiki/log.md`)](wiki/log.md)**

---

## 一、LLM Wiki 主題與簡短介紹

傳統上看甜點食譜或使用一般 RAG 問答時，初學者常面臨三大痛點：
1. **食譜單位與份量各自為政**：A 名廚寫「全蛋 4 顆、泡打粉 1.5 小匙」，B 學校寫「全蛋 150g、泡打粉 6g」，無法直接並排比較水份、油脂與糖粉比例。
2. **只給步驟不講科學原理**：食譜只寫「冷藏靜置過夜」、「煮到冒大泡」，卻沒解釋背後的物理化學機制，導致新手稍微改動溫度就翻車（如瑪德蓮沒肚臍、可麗露白頭、馬卡龍空心、卡士達隔天化水）。
3. **跨食譜的矛盾無人整理**：例如「為什麼瑪德蓮跟可麗露都要冷藏靜置過夜，但瑪德蓮要 8°C 冰麵糊入爐，可麗露卻必須回溫到 18°C 常溫入爐？」

本專案參考 Andrej Karpathy 的 **LLM Wiki** 架構，採用**「先討論、後生成」**的方式與 Agent 共同制定 [`AGENTS.md`](AGENTS.md)，匯入（Ingest）**5 篇涵蓋法式常溫蛋糕、銅模甜點、蛋白霜與基礎內餡的原始文獻（`raw/01` ~ `raw/05`）**，由 LLM 自動執行單位標準化、計算**烘焙百分比（總粉量=100%）**，編譯並維護出 **16 個高度網狀互連的 Markdown 知識頁面（`wiki/`）**，最後再以此 Wiki 為唯一知識來源，產出一份讓零基礎新手也能秒懂的 **10 頁互動式教學 HTML 簡報（[`slides/index.html`](slides/index.html)）**。

---

## 二、專案目錄結構與 Wiki 成果連結

```text
Dessert/
├── AGENTS.md                 # 核心 Schema 規範與 Loop/Graph 工作流定義
├── HOMEWORK_REPORT.md        # 作業繳交報告（含 Loop/Graph 設計說明、執行紀錄與反思）
├── raw/                      # 【第一層：不可變原始資料 (共 5 篇)】
│   ├── 01-madeleine-ph-vs-classic.md
│   ├── 02-financier-beurre-noisette-science.md
│   ├── 03-canele-bordeaux-starch-gelatinization.md
│   ├── 04-macaron-meringue-schools-troubleshooting.md
│   └── 05-creme-patissiere-ganache-emulsion.md
├── wiki/                     # 【第二層：LLM 維護知識庫 (共 16 頁)】
│   ├── index.md              # 全局內容目錄（Content-oriented Catalog）
│   ├── log.md                # 時間軸操作與檢查日誌（Chronological Audit Log）
│   ├── glossary.md           # 烘焙多語專有名詞對照表（繁中 / 法 / 英 / 日）
│   ├── recipes/              # 🍰 5 大甜點品項與跨流派配方對照矩陣頁
│   ├── techniques/           # 🥣 4 大烘焙技法與物理化學原理頁
│   ├── ingredients/          # 🧈 3 大原料與食材科學頁
│   ├── troubleshooting/      # 🔍 五大經典翻車排錯總表頁
│   ├── chefs/                # 👨‍🍳 主廚與三大烘焙流派體系比較頁
│   └── courses/              # 🎓 教學備課教案與簡報大綱沉澱頁
└── slides/                   # 【輸出層：互動式教學 HTML 簡報】
    └── index.html            # 基於 Wiki 生成的 10 頁初學者甜點科學教學簡報
```

---

## 三、Dual-Loop Graph 流程設計與檢查前移 (Shift-Left Validation)

```mermaid
flowchart TD
    subgraph Loop1["Loop 1: 知識擷取與編譯迴圈 (Ingest & Lint Loop — 重複執行 N 次)"]
        R["📥 1. 取得原始資料\n(raw/01 ~ 05.md)"] --> E["🔍 2. 萃取配方、工序、原理與排錯"]
        E --> G1{"🛡️ Gate 1: 單位標準化與百分比驗算\n(Shift-Left 檢查前移點!)"}
        G1 -- "❌ 未通過: 含顆/杯/小匙\n或百分比基準不一致" --> FIX1["🔧 自動標準化換算\n(全蛋50g/蛋黃20g/1杯250g)\n並重算烘焙百分比/總重百分比"]
        FIX1 --> G1
        G1 -- "✅ 通過" --> W["📝 3. 網狀寫入/更新 Wiki 頁面\n(單篇觸發 7~8 個跨分類頁面更新)"]
        W --> G2{"🛡️ Gate 2: 結構、雙語術語與雙向連結 Lint"}
        G2 -- "❌ 未通過: 缺相對連結\n或漏寫教學備課區塊" --> FIX2["🔧 補齊雙向 Markdown 連結、\nglossary.md 與白話教學專區"]
        FIX2 --> G2
        G2 -- "✅ 通過" --> IDX["🗂️ 4. 更新 index.md 與 log.md"]
    end

    subgraph Loop2["Loop 2: 查詢與教學 HTML 簡報生成迴圈 (Query-to-Slide Loop)"]
        IDX --> Q["🔎 5. 查詢 index.md 與目標 Wiki 頁面"]
        Q --> S["🧠 6. 整理 10 頁教學大綱、流派對比表與白話原理"]
        S --> G3{"🛡️ Gate 3: 教學認知負荷與事實一致性檢查"}
        G3 -- "❌ 未通過: 數據與 Wiki 不符\n或專有名詞未附白話比喻" --> FIX3["🔧 對齊 Wiki 配方矩陣數據\n並補齊生活化比喻後重新生成"]
        FIX3 --> G3
        G3 -- "✅ 通過" --> C["📄 7. 將教案沉澱回存至\nwiki/courses/"]
        C --> H["🖥️ 8. 產生互動式教學 HTML 簡報\n(slides/index.html)"]
    end
```

完整的 **Loop / Graph 設計說明**、**5 次 Ingest 的 Gate 1 攔截與換算檢查表**，以及 **實作反思（哪個節點最常出錯？如何將檢查往前移？）** 請參閱 **[`HOMEWORK_REPORT.md`](HOMEWORK_REPORT.md)**。
