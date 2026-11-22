# 🕒 甜點教學 LLM Wiki — 時間軸操作與檢查日誌 (Chronological Audit Log)

本檔案為 Append-only（只增不改）的時間軸紀錄，格式統一為 `## [YYYY-MM-DD] <operation> | <title>`，完整記錄每次 **Ingest（匯入）**、**Gate 1/2/3 檢查攔截紀錄**、**Lint（知識庫健檢）** 與 **Query（簡報生成）** 的執行軌跡。

---

## [2026-11-22] schema | 初始化 AGENTS.md 與 Dual-Loop Graph 架構
- **執行動作**：與使用者進行「先討論、後生成」需求訪談，確認以「跨流派食譜研發比對」與「初學者系統化教學備課」為雙核心，建立 [`AGENTS.md`](../AGENTS.md)。
- **架構決策**：設計 **Loop 1 (Ingest & Lint Loop)** 與 **Loop 2 (Query-to-Slide Loop)**，並將最常出錯的「非標準單位與烘焙百分比基準不一致」設為 **Gate 1（Shift-Left 檢查前移點）**。

## [2026-11-22] ingest | Raw 01: 瑪德蓮 (Madeleine) 兩大名廚流派對比與凸肚臍熱力學機制
- **原始檔案**：[`raw/01-madeleine-ph-vs-classic.md`](../raw/01-madeleine-ph-vs-classic.md)
- **🛡️ Gate 1 檢查攔截與修正紀錄**：
  - ❌ **攔截異常**：原始文獻中 Pierre Hermé 配方使用非克數單位 `全蛋 4 顆` 與 `泡打粉 1.5 小匙 (tsp)`，無法直接與日本菓子學校配方（`全蛋 150g`、`泡打粉 6g`）進行烘焙百分比並排計算。
  - 🔧 **自動換算修正**：依 `AGENTS.md` 標準係數將 `4 顆全蛋` 換算為 `200g`（50g/顆）、`1.5 tsp 泡打粉` 換算為 `6g`（4g/tsp），以低筋麵粉 `200g = 100%` 算出 PH 流派總液粉比為 `125%`（含 25% 牛奶），高於日系的 `100%`。
- **連動新建/更新頁面 (7 頁)**：[`recipes/madeleine.md`](recipes/madeleine.md)、[`techniques/emulsion-science.md`](techniques/emulsion-science.md)、[`techniques/starch-gelatinization-and-resting.md`](techniques/starch-gelatinization-and-resting.md)、[`ingredients/butter-and-fats.md`](ingredients/butter-and-fats.md)、[`ingredients/flours-and-nut-powders.md`](ingredients/flours-and-nut-powders.md)、[`troubleshooting/common-baking-failures.md`](troubleshooting/common-baking-failures.md)、[`chefs/pierre-herme-and-schools.md`](chefs/pierre-herme-and-schools.md)。

## [2026-11-22] ingest | Raw 02: 費南雪 (Financier) 與焦化奶油 (Beurre Noisette) 的梅納反應科學
- **原始檔案**：[`raw/02-financier-beurre-noisette-science.md`](../raw/02-financier-beurre-noisette-science.md)
- **🛡️ Gate 1 檢查攔截與修正紀錄**：
  - ❌ **攔截異常**：1. 費南雪同時含有低筋麵粉（50~60g）與杏仁粉（60~70g），若僅以低筋麵粉為 100% 會導致糖油百分比暴增至 250%~300%，無法與瑪德蓮比較；2. 流派 A 奶油標註為「焦化前生重 180g」，流派 B 標註為「焦化過濾後淨重 140g」，基準不一致。
  - 🔧 **自動換算修正**：1. 統一以 **總粉量（低粉 + 杏仁粉 = 120g = 100%）** 為烘焙百分比基準；2. 依發酵奶油含水 16% 加上鍋壁損耗，將流派 A 生重 `180g` 換算標註為 `焦化後淨重約 148g (123.3%)`，使兩流派油脂比（123.3% vs 116.7%）可精準對齊比較。
- **連動新建/更新頁面 (8 頁)**：[`recipes/financier.md`](recipes/financier.md)、[`recipes/madeleine.md`](recipes/madeleine.md)（新增雙向對比連結）、[`techniques/maillard-and-beurre-noisette.md`](techniques/maillard-and-beurre-noisette.md)、[`ingredients/butter-and-fats.md`](ingredients/butter-and-fats.md)、[`ingredients/flours-and-nut-powders.md`](ingredients/flours-and-nut-powders.md)、[`ingredients/sugars-and-invert-syrup.md`](ingredients/sugars-and-invert-syrup.md)、[`troubleshooting/common-baking-failures.md`](troubleshooting/common-baking-failures.md)、[`glossary.md`](glossary.md)。

## [2026-11-22] ingest | Raw 03: 波爾多可麗露 (Canelé) 澱粉糊化、靜置 48 小時與白頭排錯科學
- **原始檔案**：[`raw/03-canele-bordeaux-starch-gelatinization.md`](../raw/03-canele-bordeaux-starch-gelatinization.md)
- **🛡️ Gate 1 檢查攔截與修正紀錄**：
  - ❌ **攔截異常**：波爾多傳統銅模公會配方記載為 `全脂牛奶 2 杯`、`全蛋 2 顆`、`蛋黃 2 顆`。
  - 🔧 **自動換算修正**：換算為 `牛奶 500g (500%)`、`全蛋 100g (100%)`、`蛋黃 40g (40%)`；流派 B 總粉量以 `低粉 85g + 高粉 15g = 100g (100%)` 計算，得出可麗露驚人的 **670%~680% 總液粉比**。
  - 💡 **跨頁矛盾標註（Synthesis Insight）**：發現可麗露與瑪德蓮雖皆需長時間 4°C 冷藏靜置，但**瑪德蓮需 8°C 冰麵糊入爐（製造溫差求凸肚臍），可麗露卻必須回溫至 16~18°C 常溫入爐（消除溫差防暴衝白頭）**！已將此重大對比寫入 [`techniques/starch-gelatinization-and-resting.md`](techniques/starch-gelatinization-and-resting.md)。
- **連動新建/更新頁面 (7 頁)**：[`recipes/canele.md`](recipes/canele.md)、[`techniques/starch-gelatinization-and-resting.md`](techniques/starch-gelatinization-and-resting.md)、[`techniques/maillard-and-beurre-noisette.md`](techniques/maillard-and-beurre-noisette.md)、[`ingredients/butter-and-fats.md`](ingredients/butter-and-fats.md)、[`ingredients/flours-and-nut-powders.md`](ingredients/flours-and-nut-powders.md)、[`troubleshooting/common-baking-failures.md`](troubleshooting/common-baking-failures.md)、[`glossary.md`](glossary.md)。

## [2026-11-22] ingest | Raw 04: 馬卡龍 (Macaron) 法式 vs 義式蛋白霜流派對比與空心排錯
- **原始檔案**：[`raw/04-macaron-meringue-schools-troubleshooting.md`](../raw/04-macaron-meringue-schools-troubleshooting.md)
- **🛡️ Gate 1 檢查攔截與修正紀錄**：
  - ❌ **攔截異常**：馬卡龍完全不含小麥麵粉，且義式流派將蛋白拆分為兩段（37g 拌粉 + 37g 打發）。
  - 🔧 **自動換算修正**：以唯一堅果粉骨架 **細杏仁粉 `100g = 100%`** 為烘焙百分比基準（TPT = 杏仁粉 100% + 純糖粉 100%），並將義式流派兩段蛋白合併標註總蛋白比為 `74% (37%+37%)`，對比法式流派的 `80%`。
- **連動新建/更新頁面 (7 頁)**：[`recipes/macaron.md`](recipes/macaron.md)、[`techniques/meringue-aerating-systems.md`](techniques/meringue-aerating-systems.md)、[`ingredients/flours-and-nut-powders.md`](ingredients/flours-and-nut-powders.md)、[`ingredients/sugars-and-invert-syrup.md`](ingredients/sugars-and-invert-syrup.md)、[`chefs/pierre-herme-and-schools.md`](chefs/pierre-herme-and-schools.md)、[`troubleshooting/common-baking-failures.md`](troubleshooting/common-baking-failures.md)、[`glossary.md`](glossary.md)。

## [2026-11-22] ingest | Raw 05: 法式兩大靈魂內餡 — 卡士達醬澱粉酶危機與甘納許乳化科學
- **原始檔案**：[`raw/05-creme-patissiere-ganache-emulsion.md`](../raw/05-creme-patissiere-ganache-emulsion.md)
- **🛡️ Gate 1 檢查攔截與修正紀錄**：
  - ❌ **攔截異常**：1. Ferrandi 卡士達配方記載 `蛋黃 5 顆`；2. 卡士達僅含 45g 澱粉（9%）、甘納許完全無粉（0%），若套用「總粉量=100%」會導致百分比失真或除以零錯誤。
  - 🔧 **自動換算修正**：1. `5 顆蛋黃` 標準化為 `100g`（20g/顆）；2. 依 `AGENTS.md` 無粉/液態系統規範，採用 **「總重百分比（Total Weight = 100%）」** 並列「對牛奶基準（牛奶=100%） / 巧鮮比（1:1 vs 1:1.5）」。
- **連動新建/更新頁面 (8 頁)**：[`recipes/creme-patissiere-and-ganache.md`](recipes/creme-patissiere-and-ganache.md)、[`techniques/starch-gelatinization-and-resting.md`](techniques/starch-gelatinization-and-resting.md)、[`techniques/emulsion-science.md`](techniques/emulsion-science.md)、[`ingredients/butter-and-fats.md`](ingredients/butter-and-fats.md)、[`ingredients/flours-and-nut-powders.md`](ingredients/flours-and-nut-powders.md)、[`ingredients/sugars-and-invert-syrup.md`](ingredients/sugars-and-invert-syrup.md)、[`troubleshooting/common-baking-failures.md`](troubleshooting/common-baking-failures.md)、[`glossary.md`](glossary.md)。

## [2026-11-22] lint | Gate 2 全局知識庫結構、雙向連結與孤兒頁面健檢
- **檢查範圍**：`wiki/` 下共 15 個知識頁面與 `index.md`、`glossary.md`。
- **檢查結果**：
  - ✅ **YAML Frontmatter 完整性**：100% 頁面皆含 `title`, `aliases`, `category`, `tags`, `sources_count`, `last_updated`。
  - ✅ **跨頁雙向連結（Zero Orphans）**：所有食譜頁（`recipes/`）與技法頁（`techniques/`）、原料頁（`ingredients/`）、排錯頁（`troubleshooting/`）皆已建立雙向標準 Markdown 相對路徑連結，無任何孤兒頁面。
  - ✅ **教學備課區塊檢核**：所有核心頁面皆具備「💡 給初學者的原理白話文」、「⚠️ 學員最常犯的錯誤」與「🎯 課堂示範檢核點」。

## [2026-11-22] query | Loop 2 執行：編纂初學者教學教案並生成互動式教學 HTML 簡報
- **查詢目標**：為原本不熟悉烘焙科學的初學者，從 Wiki 萃取知識製作《從 4 大烘焙科學看懂法式甜點與名廚配方》教學型 HTML 簡報。
- **🛡️ Gate 3 教學檢核結果**：通過認知負荷檢查（所有法文術語皆配對生活白話比喻）與事實一致性核對（所有烘焙百分比與溫度數據皆與 Wiki 矩陣 100% 吻合）。
- **產出成果**：
  1. 沉澱教案頁面：[`wiki/courses/french-pastry-science-101.md`](courses/french-pastry-science-101.md)
  2. 生成互動式 HTML 簡報：[`slides/index.html`](../slides/index.html)
