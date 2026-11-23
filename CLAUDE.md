# CLAUDE.md — 「你的星座其實可能不是你的星座」LLM Wiki 規則

## 專案目標
建立一個關於「歲差與黃道十二宮」的 LLM Wiki，再以 wiki 為唯一知識來源，
產生一份給「完全沒學過天文的人」看的教學 HTML 簡報。

## 目錄結構
```
raw/              原始資料（不可修改，只能新增；SOURCES.md 清單除外，修改須記入 log）
wiki/
  index.md        所有 wiki 頁面目錄（每次 ingest 後更新）
  log.md          操作紀錄（只能往下追加，不可刪改）
  sources/        每篇原始資料一頁摘要
  concepts/       概念頁（黃道、歲差、春分點、回歸黃道、恆星黃道…）
  entities/       人物/機構/星座頁（喜帕恰斯、IAU、蛇夫座…）
  synthesis/      跨來源整理（比較表、常見誤解、矛盾紀錄）
slides/           簡報大綱與檢查紀錄
docs/index.html   最終教學簡報（給 GitHub Pages）
```

## 用語規則（本主題最容易出錯，務必遵守）
- 「星座」有兩種意思，必須區分：
  - **天文星座（constellation）**：IAU 劃定的天空區域，寫作「白羊座、蛇夫座」。
  - **黃道宮／占星星座（sign）**：把黃道平均切成 12 等分（每份 30°），寫作「白羊宮」。
  - **英文也要區分**：天文星座用拉丁名（例：Scorpius、Capricornus），黃道宮用英文宮名（例：Scorpio、Capricorn）。
- 中文星座名以 `wiki/synthesis/名稱對照表.md` 的「天文名稱」為準。wiki 內文**一律用天文名稱**，
  第一次出現時註明民間通稱，例：人馬座（民間通稱射手座）。
- 第一次出現時要附英文（例：歲差 precession、春分點 vernal equinox）。
- 「回歸黃道（tropical zodiac）」與「恆星黃道（sidereal zodiac）」不可混用。
- 對占星學保持中立：只說明天文事實與占星各系統的定義，不嘲諷、不評價個人信仰。

## Wiki 頁面格式
每頁開頭必須有 frontmatter：
```yaml
---
title: 頁面標題
type: source | concept | entity | synthesis
sources: [raw 檔名, ...]      # 這頁的內容來自哪些原始資料
updated: YYYY-MM-DD
---
```
- 內文中的每個事實（尤其是數字、日期、人名）要標註出處，例：`（來源：nasa-spaceplace）`。
- 頁面之間用 `[[頁面名稱]]` 互相連結。
- 若不同來源說法不同（例：歲差週期 25,722 / 25,772 / 25,800 年），
  不可憑感覺挑一個：依下方「來源可信度」處理，並寫進 `synthesis/contradictions.md` 列出各來源說法。

## 來源可信度
等級由高到低：
1. **官方機構原文**（IAU、NASA）
2. **教育機構**
3. **新聞**
4. **其他**（維基百科、占星網站等）

- 來源衝突時，wiki 內文**採信等級較高者**；但**兩邊說法都要記錄**在 `synthesis/contradictions.md`，並註明各自的等級。
- 同等級互相衝突，或沒有高等級來源時：不選邊，並列各說法，標「待補較高等級來源」。
- 目前 raw/ 的分級：
  | 等級 | raw 檔 |
  |---|---|
  | ① 官方機構原文 | iau-constellations、nasa-tumblr-zodiac、astro4edu-constellation-en（英文定義已審核）、astro4edu-ophiuchus-en（審核狀態未標示） |
  | ② 教育機構 | astro4edu-constellation-zh、astro4edu-ophiuchus-zh（**中文翻譯版**，頁面標示翻譯待審核）、taipei-edu-13-constellations |
  | ③ 新聞 | smithsonian-zodiac、slate-plait-zodiac（Slate 的 Bad Astronomy 專欄） |
  | ④ 其他 | wiki-sidereal-tropical、kerykeion-tropical-sidereal |
- astro4edu 是 IAU 天文教育辦公室（OAE）的網站。英文原文列 ①，中文翻譯版列 ②。
  用到中文版的關鍵事實（數字、日期、定義）時，**必須與英文版交叉核對**；說法不同時以英文版為準，並記入 contradictions.md。
- 同一頁的中英兩版，raw 檔名分別加 `-en`／`-zh`，合併成**一次 ingest、一個 source 頁**（檔名不加語言後綴），
  頁內附「中英關鍵事實對照表」。
- 新增 raw 檔時，在這張表補上它的等級。

## 操作零：取得資料（收集 raw/、寫 SOURCES.md）
- 任何寫進 `raw/SOURCES.md` 的事實（標題、數字、日期、「這篇有提到 X」），**必須先打開原文確認**，
  不可依搜尋摘要或記憶填寫。
- 打不開原文、無法確認的，標「未驗證」，不可當成事實寫進清單。
- 修改 SOURCES.md 要在 `wiki/log.md` 記一筆 check。

## 操作一：Ingest（先討論、後生成）
當使用者說「ingest raw/xxx」時：
1. 讀取原始資料。
2. **先不要寫任何檔案**。用條列向使用者回報：
   - 這篇的 3–5 個重點
   - 會新增/修改哪些 wiki 頁面
   - 跟既有 wiki 內容是否有衝突或重複
   - 不確定、需要使用者判斷的地方
3. 等使用者確認或修正後，才開始寫：
   - 建立 `wiki/sources/<來源名>.md`
   - 新增或更新相關 concept / entity 頁
   - 更新 `wiki/index.md`
   - 在 `wiki/log.md` 追加紀錄
4. 寫完後自動執行一次 Lint，並回報結果。

## 操作二：Query
- 回答問題時**只能使用 wiki/ 內容**，不得使用自身常識補充。
- 每個論點附上 `[[頁面名稱]]`。
- wiki 沒有涵蓋的部分，明確回答「wiki 未涵蓋」，並建議要補哪種資料。
- 有長期價值的回答（比較、整理）可詢問使用者是否存入 `wiki/synthesis/`。

## 操作三：Lint（檢查）
檢查項目：
1. `index.md` 是否列出所有頁面、沒有指向不存在的頁面。
2. 是否有斷掉的 `[[連結]]`。
3. 每頁 frontmatter 是否完整；每個數字/日期是否有出處。
4. 用語是否違反「用語規則」（座／宮混用最常見）。
5. 同一個數字在不同頁面是否一致（如歲差週期、黃經差約 24°、蛇夫座日期）。
6. 是否有來源衝突尚未記錄到 `contradictions.md`。
結果寫入 `wiki/log.md`；能自動修的（如 index）直接修，內容性問題回報給使用者決定。

## 操作四：產生簡報（分三段，每段都要檢查）
1. **大綱**：根據 wiki 產生 `slides/outline.md`，每張投影片列出：
   標題、要教的一個重點、引用的 wiki 頁面。
   → 檢查：每個重點都有 wiki 出處？順序是否由淺入深？有沒有超出 wiki 的內容？
   → 不通過就修大綱（或回頭補 wiki），通過才進下一步。
2. **HTML**：根據大綱產生 `docs/index.html`（單一檔案、不依賴外部套件、可直接用瀏覽器開啟）。
   每張投影片的 `<section>` 加上 `data-source="頁面名稱"`，頁尾顯示出處。
   教學結構：引起動機的問題 → 基本概念 → 原理 → 例子 → 常見誤解 → 小結 → 小測驗。
3. **檢查**：逐張比對投影片內容與 wiki 原文；確認用語規則；確認初學者看得懂
   （出現專有名詞要先解釋）。結果寫入 `slides/check-report.md`，有問題回到第 1 或第 2 步。

## Log 格式
每筆紀錄以固定前綴開頭，方便 grep：
```
## [YYYY-MM-DD] ingest | 來源標題
- 新增：...
- 更新：...
- 討論時使用者修正：...

## [YYYY-MM-DD] lint | 發現 N 個問題，自動修正 M 個
- 問題：...

## [YYYY-MM-DD] slides | 第 N 輪 大綱/HTML/檢查
- 不通過原因：...
- 回到哪一步：...

## [YYYY-MM-DD] check | 檢查／修正的對象
- 發現：...
- 修正：...
```
**錯誤與修正一定要記錄**，這是作業反思的依據，不可省略或美化。
