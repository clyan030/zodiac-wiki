# Wiki Log

## [2026-11-11] init | 建立 wiki 架構
- 建立 CLAUDE.md、wiki/index.md、wiki/log.md、wiki/synthesis/contradictions.md
- 主題：你的星座其實可能不是你的星座：歲差與黃道十二宮

## [2026-11-12] check | 取得 8 篇原始資料，核對 raw/SOURCES.md（補記）
- 補記原因：上一輪抓取資料存入 raw/ 時沒有寫 log，於此補上。
- 新增 raw 檔：iau-constellations.md、astro4edu-constellation.md、astro4edu-ophiuchus.md、nasa-tumblr-zodiac.md、smithsonian-zodiac.md、taipei-edu-13-constellations.pdf、wiki-sidereal-tropical.md、kerykeion-tropical-sidereal.md
- 取得時的狀況：
  - IAU 原網址回傳 404（網站改版）→ 改抓 Wayback Machine 2026-07-22 存檔
  - NASA Tumblr 原網址對自動抓取回傳 403 → 改抓 www.tumblr.com 的同一篇貼文
  - 英文維基用純文字 API 抓取時，日期對照表被刪掉 → 改抓渲染後 HTML
  - 中文維基〈歲差〉的數學公式轉文字後損壞（只影響〈成因／方程式〉一節）
- 發現 SOURCES.md 錯誤（原清單由 AI 依搜尋摘要產生，未逐篇打開原文）：
  1. 「歲差週期約 26,000 年」：8 篇原文都沒有這個數字
  2. 「兩系統每世紀差約 1.4°」：英文維基條目（rev 1379052685）沒有這句，原文是 about 1 degree every 72 years
  3. Smithsonian 標題寫成網址 slug〈…the Stars Did〉，實際標題是〈NASA Didn’t Change Your Astrological Sign, Blame It on Earth’s Wobbly Rotation〉
  4. NASA 貼文標題寫成〈Zodiac〉（網址 slug），實際標題是〈Constellations and the Calendar〉

## [2026-11-12] check | 依使用者指示修正 SOURCES.md、contradictions.md、CLAUDE.md
- 使用者指示：修正 SOURCES.md 錯誤並註明「原清單由 AI 依搜尋摘要產生，未逐篇驗證」；把三項來源差異寫進 contradictions.md；CLAUDE.md 新增「來源可信度」與「取得資料」兩條規則。
- 修正 raw/SOURCES.md：
  - 頂端加註「原清單由 AI 依搜尋摘要產生，未逐篇驗證」與 2026-11-12 核對說明
  - 刪除「26,000 年」與「每世紀 1.4°」；第 7 列改寫為原文說法（約每 72 年 1°、日期對照表）；小提醒的週期改列已核對的數值
  - Smithsonian 改為實際標題
  - 使用者未列出、但同類的錯誤一併修正：NASA 標題改為實際標題；IAU 列由「Delporte 1930 劃定」改為「1928 年 IAU 核准、1930 年出版」（依 IAU 原文）；IAU、NASA 兩列註明實際取得方式
- 更新 wiki/synthesis/contradictions.md（新增 3 項，各列來源、等級、處理方式）：
  1. 歲差週期與速率：週期沒有 ①② 級來源，④ 級彼此不一致 → 寫範圍「約 25,700～25,800 年」並列各說法，標待補；速率採 ② 級 taipei-edu「約 72 年 1°」
  2. 蛇夫座日期：大致一致 → 內文採 ② 級 astro4edu「11 月下旬到 12 月中旬」；smithsonian（11/30）與英文維基（11/29）差 1 天，並列
  3. 1928 年 IAU：taipei-edu 稱 IAU 在 1928 年「認定蛇夫座為第十三個黃道星座」，與 ① 級 IAU 原文不符（1928 年核准的是星座邊界）→ 採 IAU
- 撰寫 contradictions.md 時自己犯的錯（已修正）：
  - 初稿寫「IAU 原文沒有提到黃道」→ 回頭搜尋原文，發現有星群名稱「the Golden Gate of the Ecliptic」→ 改為「沒有討論黃道」並註明這個例外
  - 初稿有兩句原文沒寫的推論（「黃道穿過蛇夫座是劃完邊界的結果」「2011 年新聞不是 IAU 的決議」）、一句對 71／72 年差異的猜測 → 都已刪除或改成照錄原文
- 修改 CLAUDE.md：
  - 新增「來源可信度」：四個等級、衝突時採信較高者但兩邊都記錄、同等級衝突不選邊；附目前 raw 檔的分級表
  - 新增「操作零：取得資料」：寫進 SOURCES.md 的事實必須先打開原文確認，不可依搜尋摘要或記憶
  - 為了讓規則前後一致，另外改了三處：
    - 「不可自行挑一個」那條原本用 26,000 當例子 → 改成已核對的數字，並指向可信度規則
    - 目錄結構註明 SOURCES.md 是 raw/「不可修改」的例外
    - Log 格式補上 check 類型
- 待使用者判斷：astro4edu 兩篇列為 ② 級（理由：中文版是未審核的自動轉譯）而非 ① 級，是否同意

## [2026-11-12] ingest | IAU〈The Constellations〉（raw/iau-constellations.md）
- 新增：wiki/sources/iau-constellations.md、wiki/concepts/天文星座.md、wiki/entities/IAU.md
- 更新：
  - wiki/index.md：列入三個新頁面
  - wiki/synthesis/contradictions.md：新增第 4 項；修正 astro4edu 的分級說明；第 2 項標「待與英文版交叉核對」
  - CLAUDE.md：修正「來源可信度」分級表中 astro4edu 的分級
- 討論時使用者修正：
  1. 1922／1930 的出入（討論第 5 點）：照建議記入 contradictions.md 第 4 項，並依使用者指示標記「低嚴重度：可能是採用年 vs 出版年的表述差異，待其他來源確認」。
  2. astro4edu 分級（討論第 6 點，也就是上一筆 check 留下的待判斷事項）：
     - 我原本寫「中文版為未審核的自動轉譯，故列 ②」，這是錯的。
     - 使用者指出：astro4edu 是 IAU 天文教育辦公室（OAE），頁面標示「英文定義已審核、中文翻譯待審核」，不是自動轉譯。
     - 分級改為：英文原文 ①、中文翻譯版 ②；用到中文版的關鍵事實時，要與英文版交叉核對。已更新 CLAUDE.md 與 contradictions.md。
     - 回頭核對原文：詞彙頁寫的是「automated transliteration of the simplified Chinese translation」，也就是簡體中文人工翻譯後，再自動轉成繁體。「自動」指的只是簡繁轉換，不是翻譯本身；我寫成「自動轉譯」，讀起來像機器翻譯，是用詞錯誤。
     - 另外：蛇夫座星圖頁只標示翻譯狀態「Not yet approved by a reviewer」，raw 檔中沒有英文說明是否審核過的標示（「英文定義已審核」是詞彙頁才有的）。
- 其他決定（使用者同意照建議）：
  - concept／entity 頁用中文檔名，source 頁沿用 raw 檔名
  - Delporte 寫在 IAU 頁，不另立頁面
  - 蛇夫座頁等 ingest astro4edu-ophiuchus 時再建
  - 中文星座名與機構名引用 taipei-edu／astro4edu，不自行翻譯（本次：「蛇夫座」引 taipei-edu 第 14 頁，「國際天文學聯合會」引 taipei-edu 第 17 頁）
- 連帶產生的待辦：contradictions.md 第 2 項暫採 astro4edu 中文版的「11 月下旬到 12 月中旬」，依新規則需與英文版交叉核對，但 raw/ 目前沒有 astro4edu 英文版。

## [2026-11-12] lint | 發現 4 個問題，自動修正 4 個
- 檢查範圍：wiki/ 全部頁面（sources 1、concepts 1、entities 1、synthesis 1）
- 1. index：4 個頁面都已列入，沒有指向不存在的頁面 ✓
- 2. [[連結]]：無斷連 ✓
- 3. frontmatter 完整；sources 欄位都對應到 raw/ 檔案；type 與資料夾一致 ✓
- 3. 數字／日期出處：4 行缺少同一行的出處標註 → 已補「（來源：…）」
  - entities/IAU.md「注意」段 2 行（1928、1922／1930）
  - synthesis/contradictions.md 2 行（歷史估計值 25,461／25,960；1928／1930 年份）
  - 其餘被標記的行已逐一看過：有的在已標出處的上層條列下，有的在含來源欄的表格中，有的行內已寫明來源名稱，不算問題。
- 4. 用語：「宮」出現 3 次（黃道宮、黃道十二宮、Schmidt 14 宮），都是正確用法；「第十三個黃道星座」只出現在引號內的引述 ✓
- 5. 數字一致性：88、1922／1925／1928／1930 在 iau-constellations、天文星座、IAU、contradictions 四頁一致 ✓
- 6. 未記錄的來源衝突：無（目前只 ingest 一篇，內部的 1922／1930 出入已記為第 4 項）✓
- 待辦（不算 lint 錯誤）：contradictions 第 1 項（歲差週期待補 ① 級來源）、第 2 項（astro4edu 待英文版交叉核對）、第 4 項（待其他來源確認）

## [2026-11-12] check | 新規則在 ingest 前攔下一筆尚未核對的事實；取得 astro4edu 英文版
- 攔截經過：
  - contradictions.md 第 2 項已經採用 astro4edu 中文翻譯版（②）的蛇夫座日期「十一月下旬到十二月中旬」，當時 raw/ 沒有英文版，這筆事實處於「已寫進 wiki、但沒核對」的狀態。
  - 新規則（取得資料階段的驗證：寫進來的事實要先打開原文確認；中文翻譯版的關鍵事實要與英文原文交叉核對）在 ingest astro4edu 之前攔下了這筆事實。
  - 使用者決定先抓英文版、核對完再 ingest。
- 新增 raw：astro4edu-constellation-en.md、astro4edu-ophiuchus-en.md（2026-11-12 打開原文確認；保留範圍與中文版相同）
- 改名（使用者指示）：
  - astro4edu-constellation.md → astro4edu-constellation-zh.md
  - astro4edu-ophiuchus.md → astro4edu-ophiuchus-zh.md
  - 檔案內容沒有改。本 log 之前紀錄裡的舊檔名維持原樣（log 只能追加）。
- 交叉核對結果：
  - 蛇夫座日期：英文版「The Sun is in Ophiuchus from late November to mid December」與中文版「十一月下旬到十二月中旬」**一致**。contradictions.md 第 2 項改採 ① 級英文版，「待核對」解除。
  - 核對時另外發現：詞彙頁的中譯有兩處與英文原文不符（「The Zodiac」譯成「黃道十二宮」；「asterisms」譯成「小行星」）。這兩處尚未用在 wiki 裡，留到 ingest astro4edu-constellation 時處理。
- 分級（使用者指示）：
  - astro4edu-ophiuchus-en 列 ①，註記「審核狀態未標示」（英文頁面沒有任何審核說明）
  - astro4edu-constellation-en 列 ①（頁面標示「This term and its definition have been approved by a research astronomer and a teacher」）
  - 兩個 -zh 檔列 ②
- 更新：
  - raw/SOURCES.md 第 2、3 列：改成中英兩個檔名，補上英文原文網址和已核對的說法
  - CLAUDE.md：分級表改用 -en／-zh 檔名；依使用者指示新增一條「中英兩版合併成一次 ingest、一個 source 頁，頁內附中英關鍵事實對照表」
  - contradictions.md：frontmatter sources 改用新檔名；第 1 項「沒有寫週期」的來源補上英文版；第 2 項加入英文版一列並改採 ①；第 3 項引用改為 astro4edu-constellation-en
- 改名後確認：所有 wiki 頁 frontmatter 的 sources 都對應得到 raw 檔，沒有斷連。wiki 裡還剩兩處沒有後綴的「astro4edu-constellation」「astro4edu-ophiuchus」，指的是 source 頁名稱（依新規則不加語言後綴），不需要改。

## [2026-11-12] ingest | astro4edu 詞彙「Constellation／星座」（raw/astro4edu-constellation-en.md ＋ -zh.md）
- 新增：
  - wiki/sources/astro4edu-constellation.md（附中英關鍵事實對照表）
  - wiki/concepts/黃道.md
  - wiki/synthesis/名稱對照表.md
- 更新：
  - wiki/concepts/天文星座.md：補「與黃道的關係」；88 個與定義加上第二個出處；用語註記指向名稱對照表
  - wiki/synthesis/contradictions.md：新增第 5 項
  - wiki/index.md
  - CLAUDE.md 用語規則：新增 2 條
- 討論時使用者修正：
  1. 中文星座名（討論第 1 點）：
     - 我原本建議逐一決定，以人馬座、寶瓶座為主。
     - 使用者改為：不要逐一決定，直接建立 wiki/synthesis/名稱對照表.md，欄位「天文名稱｜民間通稱｜英文星座名（拉丁）｜英文黃道宮名｜出處」。
     - 天文名稱以臺北 PDF 為準，逐列附出處；查不到的留空、標「待查」，不自己填。特別檢查人馬／射手、寶瓶／水瓶、室女／處女、白羊／牡羊。
  2. CLAUDE.md 用語規則新增兩條（使用者指示）：
     - 英文也要區分：天文星座用拉丁名（Scorpius），黃道宮用英文宮名（Scorpio）。
     - wiki 內文一律用天文名稱，第一次出現時註明民間通稱。
- 照建議執行：建立黃道概念頁；Scorpio 的註記寫在 source 頁，也寫進名稱對照表的查核紀錄。
- 名稱查核結果：
  - 人馬／射手、寶瓶／水瓶、室女／處女：臺北 PDF 第 20 頁「星座名稱」欄是人馬座、寶瓶座、室女座。民間通稱射手座、水瓶座、處女座見同一份 PDF 第 2 頁的星座運勢排行插圖。
  - 白羊／牡羊：「牡羊座」在 raw 中查無，標待查；只有中文〈歲差〉用「牡羊宮」指黃道宮，同段的天文星座寫「白羊座」。
  - 蛇夫座的民間通稱：raw 中查無，標待查。
  - 另外發現：臺北 PDF 的黃道宮中文名前後不一（第 5 頁室女宮／人馬宮／寶瓶宮，第 20 頁處女宮／射手宮／水瓶宮）。名稱對照表沒有宮名欄位，先記為待處理。
  - 限制：第 2 頁運勢排行是插圖裡的文字，PDF 文字層沒有，由我人工判讀，已在對照表的出處代號 T2 註明。
- 中英核對結果（記入 contradictions.md 第 5 項）：
  - 2 處關鍵中譯錯誤：the Zodiac 譯成「黃道十二宮」；asterisms 譯成「小行星」
  - 2 處次要：Scorpio 漏譯；天蠍座星圖說明筆誤成「天秤座」
  - 其餘關鍵事實（88 個、多邊形定義、黃道定義、13 個名單、天秤座／天蠍座／獵戶座的太陽時段）中英一致

## [2026-11-12] lint | 發現 1 個問題，自動修正 0 個
- 檢查範圍：wiki/ 全部頁面（sources 2、concepts 2、entities 1、synthesis 2）
- 1. index：7 個頁面都已列入，沒有指向不存在的頁面 ✓
- 2. [[連結]]：無斷連 ✓
- 3. frontmatter 完整，sources 都對應到 raw 檔，type 與資料夾一致 ✓
- 3. 數字／日期出處：被標記的行已逐一看過，都在已標出處的上層條列下、在含來源欄的表格中，或行內已寫明來源名稱，不算問題 ✓
- 4. 用語（本次新增兩項檢查）：
  - 民間通稱（射手座、水瓶座、處女座、牡羊座）出現在名稱對照表以外的地方，都是「民間通稱」註記，或對中文翻譯原文的引述 ✓
  - 英文 Scorpio 出現在名稱對照表以外的地方，都是引述 astro4edu 英文原文「often commonly called Scorpio」✓
  - 「宮」的用法都正確；「黃道十二宮」只出現在對錯誤中譯的引述中 ✓
- 5. 數字一致性：88、13、天秤座與天蠍座的太陽時段，在 astro4edu-constellation、黃道、天文星座、contradictions 四頁一致 ✓
- 6. **未記錄的來源衝突（內容性問題，回報使用者決定）**：
  - 「與黃道重疊的星座有 13 個」（astro4edu-constellation-en，①）vs smithsonian-zodiac（③）轉述 Phil Plait：「there are 21 different constellations that fit this arbitrary definition」。
  - smithsonian 沒有說明「this arbitrary definition」具體指什麼，無法判斷兩者是否在講同一件事。
  - 尚未記入 contradictions.md，待使用者決定。
  - 相關：nasa-tumblr-zodiac（①）也寫「the sun actually moves through 13 constellations」，與 astro4edu 一致。
  - 相關但不算衝突：wiki-sidereal-tropical（④）註 iii 說黃道沒有穿過 Cetus 的邊界，但最近只差 9 角分，太陽邊緣約在 3 月 27–28 日短暫進入 Cetus。

## [2026-11-12] check | 處理上一筆 lint 的發現：13 vs 21
- 使用者決定（同意建議）：
  - 現在就記入 contradictions.md 第 6 項，標「待釐清：定義不明」。
  - wiki 內文繼續用 ① 級的「13 個」。
  - 等 ingest smithsonian-zodiac 時，再決定要不要依操作零把 Phil Plait 的原文加進 raw/。
- 修正：contradictions.md 新增第 6 項。照錄 smithsonian 的前後文：「this arbitrary definition」指的是前一句的「the definition of a zodiacal sign」，但文中仍沒有說明判定標準。
- 我自己犯的錯：上一輪回覆使用者時寫了「鯨魚座（Cetus）」，這個中文名是我自己翻的。回頭搜尋 raw，查無「鯨魚」，違反「中文星座名不自行翻譯」的決定。這個名稱沒有寫進 wiki；contradictions.md 第 6 項寫成「Cetus（中文名待查）」。

## [2026-11-16] ingest | astro4edu〈Ophiuchus Constellation Map／蛇夫座星圖〉（raw/astro4edu-ophiuchus-en.md ＋ -zh.md）
- 新增：
  - wiki/sources/astro4edu-ophiuchus.md（附中英關鍵事實對照表，共 12 列）
  - wiki/entities/蛇夫座.md（之前約定在這次 ingest 建立）
- 更新：
  - wiki/concepts/黃道.md：
    - 蛇夫座那一條改成實際日期「11 月下旬到 12 月中旬」
    - 補「不屬於傳統的 12 個黃道星座，但位在黃道上」
    - 黃道定義、「黃道線在天上看不到」補第二個出處（astro4edu-ophiuchus-en）
    - 表格中的蛇夫座連到 [[蛇夫座]]
  - wiki/concepts/天文星座.md：兩處蛇夫座連到 [[蛇夫座]]
  - wiki/synthesis/contradictions.md：
    - 第 5 項改名為「astro4edu 中譯與英文原文不符」，分成 5a（詞彙「星座」，原有 4 列）和 5b（蛇夫座星圖，新增 2 列次要問題）
    - 第 2 項補上寫入的頁面
  - wiki/index.md
- 討論時使用者修正：無。使用者回覆「照建議」，依建議執行：
  1. 周邊星座（武仙座、巨蛇頭、巨蛇尾）的中文名只出現在中文翻譯版（②），不在名稱對照表裡 → wiki 內文不寫周邊星座，只在 source 頁的對照表照錄原文。名稱對照表不新增。
  2. 蛇夫座星圖的兩處中譯小問題（漏譯「黃道線」；相關詞彙把 Zodiac 譯成「黃道十二宮」）→ 併入 contradictions 第 5 項，不另開新項。
- 中英核對結果：
  - 與黃道的關係、黃道定義、太陽在蛇夫座的日期、其他行星、周邊星座、可見性（4 項）、球狀星團：中英一致。
  - 2 處次要問題，記入 contradictions 第 5b 項。
- 用語處理：英文原文「traditional twelve zodiac constellations」講的是天文星座，不是黃道宮。wiki 寫成「傳統的 12 個黃道星座」，不寫「十二宮」。這點記在 source 頁的註記。
- 沒有摘錄的內容：
  - 星圖的讀圖說明（赤經、赤緯、視星等、希臘字母），與本主題無關。
  - 球狀星團只寫在 source 頁，蛇夫座實體頁不寫。
- 限制：
  - 討論報告提到臺北 PDF 第 16 頁有「巨蛇座(Serpens)」。這次寫入時，環境沒有 PDF 讀取工具，無法重新打開 PDF 核對，所以這一點沒有寫進 wiki。
  - 蛇夫座實體頁的天文名稱引用第 14 頁「蛇夫座(Ophiuchus)」，沿用上一輪 ingest 已核對、記在名稱對照表 T14 的結果。
- 日期：這次操作在 2026-11-16 進行，新寫和修改的頁面 updated 改為 2026-11-16。raw 檔的 retrieved 仍是 2026-11-12。

## [2026-11-16] lint | 發現 0 個問題，自動修正 0 個
- 檢查範圍：wiki/ 全部頁面（sources 3、concepts 2、entities 2、synthesis 2）
- 1. index：9 個頁面都已列入，沒有指向不存在的頁面 ✓
- 2. [[連結]]：無斷連（新增的 [[蛇夫座]]、[[astro4edu-ophiuchus]] 都能對應） ✓
- 3. frontmatter：完整，sources 都對應到 raw 檔，type 與資料夾一致 ✓
- 3. 數字／日期出處：新被標記的行逐一看過：
  - astro4edu-ophiuchus 的網址行、對照表中的日期與球狀星團列（表格本身就是兩版原文的引述）、「12 個」的用語註記
  - 都不需要另外加出處 ✓
- 4. 用語：
  - 新增的「宮」都是對錯誤中譯「黃道十二宮」的引述，或是「黃道宮（sign）」的區分說明 ✓
  - 沒有新的民間通稱，也沒有新的英文宮名 ✓
- 5. 數字一致性：
  - 蛇夫座日期在 astro4edu-ophiuchus、蛇夫座、黃道、contradictions 四頁一致：一般寫「11 月下旬到 12 月中旬」，精確日期寫「約 11 月 29 日或 30 日到 12 月 17 日」
  - 「13 個」與「傳統的 12 個黃道星座」的寫法各頁一致 ✓
- 6. 未記錄的來源衝突：無。蛇夫座星圖的內容與 iau-constellations、astro4edu-constellation、contradictions 第 2、3 項都一致 ✓

## [2026-11-16] ingest | NASA〈Constellations and the Calendar〉（raw/nasa-tumblr-zodiac.md）
- 新增：
  - wiki/sources/nasa-tumblr-zodiac.md
  - wiki/concepts/黃道宮.md（sign）：巴比倫人的由來、黃道宮跟天文星座對不齊、3,000 年後天空移動。宮的度數、各宮中文名、歲差原因留待補。
- 更新：
  - wiki/concepts/黃道.md：
    - 新增〈黃道帶（zodiac）〉段落（NASA 的說明）
    - 「太陽經過 13 個星座」加上 NASA 作第二個出處
    - 例子加上室女座 45 天、天蠍座 7 天
    - 待補改成指向 [[黃道宮]]
  - wiki/concepts/天文星座.md：
    - 定義段並列 NASA 的說法（一群星星）和 IAU 的正式定義（區域）
    - 「星星彼此無關」加上 NASA 作第二個出處
    - 新增「星座形狀變化非常慢」
  - wiki/entities/蛇夫座.md：新增〈為什麼傳統只有 12 個〉（巴比倫人排除蛇夫座）；待補只剩「蛇夫座在占星各系統中的地位」
  - wiki/synthesis/contradictions.md：新增第 7 項「星座的定義：有邊界的區域 vs 一群星星」（同級 ①，不選邊）
  - wiki/synthesis/名稱對照表.md：新增〈用語：zodiac、黃道帶、黃道宮〉段落
  - wiki/index.md
- 討論時使用者修正：無。使用者回覆「照建議」，三個待決定事項都照建議處理：
  1. 星座的定義（iau-constellations、astro4edu-constellation-en vs nasa-tumblr-zodiac，都是 ①）：
     - 記入 contradictions 第 7 項，標「同級說法不同」
     - 天文星座頁並列兩種說法，各標出處，wiki 不判斷哪個對
  2. NASA 對占星的評價句（「It's not considered a science」「have no effect on the ordinary activities of humans」）：
     - source 頁照錄原文，標明是 NASA 的說法
     - concept 頁和簡報只寫天文學、占星學兩者的定義，不寫評價句
  3. 「zodiac」的中文：
     - 天空中那一圈區域寫「黃道帶（zodiac）」，用詞出處是 wiki-sidereal-tropical 中文〈歲差〉〈作用〉「傳統的12個黃道帶星座」（④）
     - signs of the zodiac 寫「黃道宮（sign）」
     - 「黃道十二宮」只在引述原文時出現
     - 寫進名稱對照表的用語段落
- 核對結果：
  - 一致：太陽經過 13 個星座（astro4edu-en）、天蠍座時間很短（astro4edu-en）、星座裡的星星彼此無關（IAU）
  - 待 ingest 維基時比對：室女座 45 天（英文維基 IAU 欄 Sep 16 – Oct 30）、獅子座約 7/23–8/22（英文維基「回歸黃道」欄的 Leo 也是 Jul 23 – Aug 22）。天數沒有自行計算寫進 wiki。
  - 重複：smithsonian-zodiac 直接引用了本篇「切披薩」那一段，等 ingest smithsonian 時標成轉引。
- 寫入時的用語處理：
  - 原文「born under the constellation Leo」，wiki 寫「在獅子座下出生」並附原文。
  - Orion 的中文名「獵戶座」引自 astro4edu-constellation-zh。
  - 本篇沒有用「歲差（precession）」，wiki 也不把它的「地球自轉軸指的方向改變」直接連到歲差頁（歲差頁還沒建立）。

## [2026-11-16] lint | 發現 0 個問題，自動修正 0 個
- 檢查範圍：wiki/ 全部頁面（sources 4、concepts 3、entities 2、synthesis 2）
- 1. index：11 個頁面都已列入，沒有指向不存在的頁面 ✓
- 2. [[連結]]：無斷連（新增的 [[黃道宮]]、[[nasa-tumblr-zodiac]] 都能對應） ✓
- 3. frontmatter：完整，sources 都對應到 raw 檔，type 與資料夾一致 ✓
- 3. 數字／日期出處：新被標記的行逐一看過：
  - nasa-tumblr-zodiac 和蛇夫座的被標記行，都在已標「（來源：nasa-tumblr-zodiac）」的上層條列下
  - 黃道、黃道宮被標記的是指向其他頁面的說明，或「待補」行
  - 都不需要另外加出處 ✓
- 4. 用語：
  - 新增的「宮」都是「黃道宮（sign）」的正確用法，或對「黃道十二宮」的引述說明 ✓
  - 新出現的「處女座」都有「民間通稱」註記 ✓
  - 沒有新的英文宮名 ✓
- 5. 數字一致性：13 個、室女座 45 天、天蠍座 7 天、3,000 年、約 7/23–8/22，在 nasa-tumblr-zodiac、黃道宮、黃道、蛇夫座各頁一致 ✓
- 6. 未記錄的來源衝突：wiki 內沒有 ✓
  - 預告（還沒 ingest 的 raw 之間，不在 wiki 裡）：smithsonian-zodiac（③）說「the Babylonians didn't realize that the Earth's rotation was a bit wobbly」；中文〈歲差〉（④）〈歷史／巴比倫人〉說「有一種觀點認為巴比倫人已經知到歲差」，同一條目的參考資料有 Neugebauer〈The Alleged Babylonian Discovery of the Precession of the Equinoxes〉。等 ingest 這兩篇時再判斷是否記入 contradictions。

## [2026-11-16] ingest | Smithsonian〈NASA Didn’t Change Your Astrological Sign, Blame It on Earth's Wobbly Rotation〉（raw/smithsonian-zodiac.md）
- 新增：
  - wiki/sources/smithsonian-zodiac.md：每一點都標明原本是誰說的。轉引的對象包括 NASA Tumblr、NASA SpacePlace、Washington Post、BBC、Slate、Minnesota Star-Tribune。
  - wiki/synthesis/常見誤解.md：先放 3 條，分別是「NASA 改了黃道宮」（2016）、「第 13 個星座符號：蛇夫座」（2011）、「IAU 在 1928 年認定蛇夫座」
- 更新：
  - wiki/concepts/黃道宮.md：〈3,000 年後〉補上 Smithsonian 對「自轉晃動」的說法，以及 Cantillo 對 BBC 的引述；註明巴比倫人知不知道地軸會晃，wiki 不寫（見第 9 項）；連到常見誤解
  - wiki/entities/蛇夫座.md：Serpent-Bearer 加上第二個出處；新增〈新聞中的蛇夫座〉（2011 年新聞，以及誰最早認出蛇夫座見第 8 項）；連到常見誤解
  - wiki/sources/nasa-tumblr-zodiac.md：「重複」那條改成已處理；關係表加上第 8 項
  - wiki/synthesis/contradictions.md：
    - 第 6 項記下 Slate 原文的決定
    - 新增第 8 項「誰最早認出蛇夫座」（可能衝突）
    - 新增第 9 項「巴比倫人知不知道地軸會晃」（③ vs ④，待補較高等級來源）
  - wiki/index.md
- 討論時使用者修正：無。使用者回覆「照建議」，三個待決定事項都照建議處理：
  1. Phil Plait 的 Slate 原文：
     - 這一輪先寫 smithsonian，第 6 項維持「待釐清」。
     - 寫完後依操作零抓 Slate 原文存進 raw/（③），並更新 SOURCES.md 和 CLAUDE.md 的分級表，在 log 記一筆 check。
     - 下一輪 ingest 時再處理第 6 項。
  2. 誰最早認出蛇夫座（NASA ① 說巴比倫人的記載中就有；Smithsonian ③ 說最早由古希臘人認出）：記入第 8 項，標「可能衝突」，wiki 兩種起源說法都不寫。
  3. 巴比倫人知不知道地軸會晃（Smithsonian ③ vs 中文〈歲差〉④）：記入第 9 項，標「待補較高等級來源」；wiki 內文不寫，只寫 ① 和 ③ 一致的「地軸方向改變 → 星座位置偏移」。
- 照前例處理：作者的評價句（「astrology is not a science」「stars aren't the best of judges」等）比照 nasa-tumblr-zodiac，只在 source 頁照錄並標明出處。
- 核對結果：
  - 一致：約 3,000 年前、地軸改變導致星座位置偏移、Serpent-Bearer
  - 「切披薩」那一段是直接引用 NASA 原文，已標成轉引
  - Cantillo 對 BBC 說的是「we did the math」，NASA 原文是「we just did the math」。用字略有不同，是不同場合的引述，不算矛盾
- 用語處理：
  - 「zodiacal constellations」寫成黃道星座（天文星座）
  - 「zodiac sign」「Astrological Sign」寫成黃道宮
  - 「13th star symbol」照錄原文，不譯成「宮」

## [2026-11-16] lint | 發現 0 個問題，自動修正 1 個（補出處）
- 檢查範圍：wiki/ 全部頁面（sources 5、concepts 3、entities 2、synthesis 3）
- 1. index：13 個頁面都已列入，沒有指向不存在的頁面 ✓
- 2. [[連結]]：無斷連（新增的 [[smithsonian-zodiac]]、[[常見誤解]] 都能對應） ✓
- 3. frontmatter：完整，sources 都對應到 raw 檔，type 與資料夾一致 ✓
- 3. 數字／日期出處：
  - smithsonian-zodiac、蛇夫座被標記的行，都在已標出處的上層條列下 ✓
  - 自動修正：contradictions 第 9 項「同一段中文〈歲差〉的其他內容」底下的條列原本沒有寫出處，在段落標題補上「來源：wiki-sidereal-tropical Part B〈歷史／巴比倫人〉」
- 4. 用語：
  - 新增的「宮」都是黃道宮（sign）的正確用法：「zodiacal sign」「zodiac sign」寫成黃道宮
  - 「13th star symbol」沒有譯成「宮」 ✓
  - 沒有新的民間通稱，也沒有新的英文宮名 ✓
- 5. 數字一致性：21 個、11/30–12/17、約 3,000 年、Serpent-Bearer，在 smithsonian-zodiac、蛇夫座、常見誤解、contradictions 各頁一致 ✓
- 6. 未記錄的來源衝突：這一輪發現的兩個（第 8、9 項）都已記錄；沒有其他 ✓

## [2026-11-16] check | 操作零：取得 Phil Plait 的 Slate 原文（新增 raw/slate-plait-zodiac.md）
- 原因：ingest smithsonian-zodiac 時決定（使用者同意建議）。contradictions 第 6 項「13 vs 21」的「21」是 smithsonian 轉引 Phil Plait 的說法，要看原文才能判斷。
- 取得：
  - smithsonian 連結的原網址 http://www.slate.com/blogs/bad_astronomy/2016/09/26/no_nasa_didn_t_change_your_astrological_sign.html 現在會轉到 https://slate.com/technology/2016/09/no-nasa-didn-t-change-your-astrological-sign.html ，回傳 200，內文完整。
  - HTML 轉 Markdown 後，刪去廣告、留言連結、Slate Plus 贈閱提示、影片區塊、頁尾提示；內文未刪減。
- 依操作零打開原文確認的事實：
  - 標題〈No, NASA Didn’t Change Your Astrological Sign〉；作者 Phil Plait；發布日期 2016-09-26；專欄 Bad Astronomy。這幾項取自頁面的結構化資料，頁面標題列也一致。
  - 「21」的原文是「Worse, there aren’t really 13 zodiacal constellations. By some counts, there are as many as 21!」，並連到 ips-planetarium.org 的一篇文章（網址含 mosley1999b）。**原文沒有說明怎麼算出 21 個。**
- 修改：
  - raw/SOURCES.md：新增第 9 列（排在第 8 列之後）
  - CLAUDE.md 分級表：③ 新聞加入 slate-plait-zodiac
- 對 contradictions 第 6 項的影響（先記下，下一輪 ingest 時再處理）：
  - 原文只寫「by some counts」，判定標準在它連結的 IPS 文章裡。
  - 所以第 6 項的「定義不明」光靠 Slate 原文還沒辦法釐清。

## [2026-11-16] ingest | Slate〈No, NASA Didn’t Change Your Astrological Sign〉（Phil Plait，raw/slate-plait-zodiac.md）
- 新增：wiki/sources/slate-plait-zodiac.md
- 更新：
  - wiki/synthesis/contradictions.md：
    - 第 6 項：加入 Slate 原文一列，記下這一輪的結果
    - 第 8 項：加入 Slate 一列（③，說法跟 smithsonian 相同），狀態不變
    - 總表的第 6、8 列、frontmatter
  - wiki/sources/smithsonian-zodiac.md：第 6 點補上「21」的原文寫法，關係表同步
  - wiki/concepts/黃道.md：加入 Plait 對黃道的說明（③，補充說法）
  - wiki/concepts/黃道宮.md：
    - 加入「地球像陀螺晃動」和古今 3 月下旬的例子
    - 註明「星座沒有變」和「天空移動了」講的是不同的事
  - wiki/entities/蛇夫座.md：
    - 加入「太陽在蛇夫座比在天蠍座久」（③，與 ① 的數據方向一致）
    - 英文名第三個出處
    - 2016 年「第 13 個黃道宮」的說法和 Plait 的反駁
  - wiki/synthesis/常見誤解.md：
    - 第 1 條補上 Plait 的三點反駁、SpacePlace 2016 年 1 月更新、「星座沒有變」和「天空移動了」要分清楚
    - 第 2 條補上第二個出處
  - wiki/index.md
- 討論時使用者修正：無。使用者回覆「照建議」，兩個待決定事項都照建議處理：
  1. IPS 文章（Mosley 1999，「21」的出處）：
     - 這一輪先不追，第 6 項維持「待釐清」。
     - 註明原網址回傳 403、Wayback 有 2018-05-02 存檔（還沒讀）。
     - 之後如果要追，等級建議列 ②。
  2. 「you would’ve been an Aries / you’d be a Pisces」的寫法：
     - 前一句講的是「the dates the Sun is in a given constellation」，所以寫成天文星座：「出生時太陽在白羊座；今天則在雙魚座」，並附原文。
- 核對結果：
  - smithsonian 的「this arbitrary definition」是它自己的轉述，Slate 原文只寫「By some counts, there are as many as 21」，判定標準在它連結的 IPS 文章裡。第 6 項仍然定義不明。
  - 一致：
    - 地球晃動會改變日期（NASA、smithsonian）
    - 黃道的說明（astro4edu-en）
    - the serpent bearer（IAU）
    - 2011 年也發生過（smithsonian）
    - 太陽在蛇夫座比在天蠍座久：與 NASA 的天蠍座 7 天、astro4edu 的蛇夫座 11 月下旬到 12 月中旬方向一致，沒有自行計算天數
  - 待 ingest 維基時比對：古今 3 月下旬的例子（英文維基 IAU 欄：Pisces Mar 11 – Apr 18）。
- 不採用：Plait 引用的 Yahoo 文章裡有「November 29 and December 17」。Plait 是把這篇當錯誤示範引用的，但沒有指出具體哪一句錯，所以不加入 contradictions 第 2 項，只在 source 頁照錄。
- 照前例處理：作者的評價句只在 source 頁照錄，例如「Astrology isn't science; it's nonsense」「pseudoscience … like a zombie」。
- 用語處理：Yahoo 文章的「a new, 13th sign」寫成「第 13 個黃道宮」（sign＝黃道宮）。

## [2026-11-16] lint | 發現 0 個問題，自動修正 0 個
- 檢查範圍：wiki/ 全部頁面（sources 6、concepts 3、entities 2、synthesis 3）
- 1. index：14 個頁面都已列入，沒有指向不存在的頁面 ✓
- 2. [[連結]]：無斷連 ✓
- 3. frontmatter：完整，sources 都對應到 raw 檔（含新增的 slate-plait-zodiac），type 與資料夾一致 ✓
- 3. 數字／日期出處：slate-plait-zodiac 被標記的行，不是網址和取得經過，就是在已標出處的上層條列下，或是照錄的引文 ✓
- 4. 用語：
  - 新增的「宮」都是黃道宮（sign）的正確用法
  - 「13th sign」寫成黃道宮；「zodiacal constellations」寫成黃道星座 ✓
  - 沒有新的民間通稱，也沒有新的英文宮名 ✓
- 5. 數字一致性：
  - 21（By some counts）在 slate-plait-zodiac、smithsonian-zodiac、contradictions 一致
  - 古今 3 月下旬的例子在 slate-plait-zodiac、黃道宮一致
  - SpacePlace 2016 年 1 月更新、2011 年同類新聞，在 slate-plait-zodiac、常見誤解一致 ✓
- 6. 未記錄的來源衝突：無。本篇新增的說法都已併入第 6、8 項，或與既有來源一致 ✓

## [2026-11-16] ingest | 維基百科〈Sidereal and tropical astrology〉＋中文〈歲差〉（raw/wiki-sidereal-tropical.md）
- 新增（7 頁）：
  - wiki/sources/wiki-sidereal-tropical.md
  - wiki/concepts/歲差.md
  - wiki/concepts/春分點.md
  - wiki/concepts/回歸黃道.md
  - wiki/concepts/恆星黃道.md
  - wiki/entities/喜帕恰斯.md
  - wiki/synthesis/日期對照表.md
- 更新：
  - wiki/concepts/黃道宮.md：
    - 補上每宮 30°（④）、「牡羊宮為第一宮」的由來（與 NASA 的年代無法比對）
    - 新增〈兩種劃分系統〉
    - 補上「地軸指向改變就是歲差」、巨蟹宮大多對應雙子座
    - 待補改成指向新頁
  - wiki/entities/蛇夫座.md：新增〈在占星中的地位〉（註 ii；Schmidt 14 宮的 Dec 6 – Dec 31）
  - wiki/synthesis/contradictions.md：
    - 第 1 項補上週期「25,771 年」、歷史數值 36,000 年、速率 51″／50.39″／50.2″，以及「每 70.5 年 1 天」不是同一個量的說明
    - 第 6 項補上英文條目〈Further reading〉的 Mosley（1999）
    - 第 9 項註明已 ingest
    - 新增第 10 項（恆星黃道怎麼分，同一來源內部不一致）
    - 新增第 11 項（太陽進入 IAU 白羊座 April 19 vs Apr 18，次要）
  - wiki/entities/IAU.md：註明「國際天文聯合會」的寫法；IAU 劃邊界時沒有考慮占星用途（④）
  - wiki/concepts/黃道.md：加入英文條目的示意圖說明（黃道、天赤道、春分點）；待補改成指向歲差頁
  - wiki/concepts/天文星座.md：IAU 劃邊界時沒有考慮占星用途（④）
  - wiki/synthesis/名稱對照表.md：〈待處理〉補上宮名決定之前的暫行做法（見下方）
  - wiki/index.md
- 討論時使用者修正：無。使用者回覆「照建議」，三個待決定事項都照建議處理：
  1. 恆星黃道的定義（導言、註 ii、Lahiri 欄都是「12 宮 × 30°」 vs〈Astronomic zodiac〉的「不等分、依星座寬度」）：
     - 記入 contradictions 第 10 項
     - 恆星黃道頁兩種說法並列，不選邊，等 ingest Kerykeion 時交叉核對
  2. 日期相減的推算：
     - 允許，但只用在核對（source 頁、日期對照表的核對表），標明「推算」並寫出算式，不當成新事實寫進 concept 頁
     - 結果：室女座相差 44 天、含頭尾 45 天（NASA 45 天）；天蠍座相差 6 天、含頭尾 7 天（NASA 7 天）；蛇夫座相差 18 天，比天蠍座長（Plait）。三項都一致。
  3. 頁面範圍：7 頁都建。喜帕恰斯頁標明「只有 ④ 級來源」。
- 我自己決定、需要讓使用者知道的做法：
  - 黃道宮的中文名稱還沒決定，暫行做法如下（寫進名稱對照表〈待處理〉）：
    - 「白羊宮」照 CLAUDE.md 的例子寫。
    - 天文名稱和民間通稱相同的宮，寫「○○宮（英文宮名）」，例如天秤宮、雙魚宮、巨蟹宮。
    - 有爭議的三組（室女／處女、人馬／射手、寶瓶／水瓶）只寫英文宮名。日期對照表的宮名欄全部用英文。
  - 日期對照表的日期保留原表的英文寫法（例如「Mar 21 – Apr 19」），不改成中文日期，避免轉寫錯誤。寫完後用程式逐格比對 raw 原表，14 列全部一致。
  - 喜帕恰斯的英文名「Hipparchus」取自條目參考資料的篇名。
  - 不寫進 wiki 的內容：北極星的星名（不在名稱對照表中）、提到喜帕恰斯測量的亮星時只寫「條目寫『角宿一』」，以及古埃及、瑪雅、印度、拜火教、回歸線、氣候、公式、數值模型等段落。
- 無法比對：中文條目說黃道十二宮在「新巴比倫王朝時期」形成，NASA 說 3,000 多年前。raw 沒有新巴比倫王朝的年代，不用自己的常識判斷，只在 source 頁和黃道宮頁註記。
- 提醒：CLAUDE.md Lint 第 5 條提到「黃經差約 24°」，這份來源裡沒有 24°（只有 23°、約 30°、約 37°，基準各不相同）。等 ingest 臺北 PDF 時再看。

## [2026-11-16] lint | 發現 1 個問題，自動修正 1 個
- 檢查範圍：wiki/ 全部頁面（sources 7、concepts 7、entities 3、synthesis 4）
- 1. index：21 個頁面都已列入，沒有指向不存在的頁面 ✓
- 2. [[連結]]：無斷連 ✓
- 3. frontmatter：完整，sources 都對應到 raw 檔，type 與資料夾一致 ✓
  - 寫入時順手修正：春分點頁 frontmatter 原本多列了 slate-plait-zodiac（內文沒有引用），已刪除。
- 3. 數字／日期出處：新被標記的行都看過，都不需要另外加出處：
  - 日期對照表、春分點的大月表、恆星黃道的比較表，來源都寫在表格下方
  - 回歸黃道的例子在已標出處的上層條列下
  - 其餘是「待補」行 ✓
- 4. 用語：
  - **問題（已自動修正）**：wiki-sidereal-tropical source 頁的關係表寫「IAU：Scorpio（天蠍座）」，用了黃道宮拼法指 IAU 的天文星座。已改成「天蠍座（Scorpius；原表該列標為 Scorpio）」。
  - 日期對照表「對應的黃道宮」欄的 Scorpio、Capricorn 是黃道宮，用法正確 ✓
  - 新增的「宮」都是黃道宮的正確用法；「黃道十二宮」「牡羊宮」只出現在引述中文條目時 ✓
  - 新出現的處女座、射手座、水瓶座都有「民間通稱」註記 ✓
- 5. 數字一致性：
  - 歲差週期「約 25,700～25,800 年」、速率「約 72 年 1°」在歲差、恆星黃道、喜帕恰斯、contradictions、index 一致
  - 太陽進入白羊座的 4/18 與 4/19 在春分點、日期對照表、source 頁、contradictions 第 11 項的寫法一致
  - 日期對照表與 raw 原表逐格比對一致 ✓
- 6. 未記錄的來源衝突：這一輪發現的都已記錄（第 10、11 項，以及第 1 項的新寫法）✓

## [2026-11-16] ingest | Kerykeion〈Tropical vs. Sidereal Astrology Explained〉（raw/kerykeion-tropical-sidereal.md）
- 新增：wiki/sources/kerykeion-tropical-sidereal.md（本 wiki 第一篇占星端立場的來源）
- 更新：
  - wiki/concepts/回歸黃道.md：
    - 補上占星端的說明：太陽往北穿過天赤道、12 等分、衡量季節關係、不宣稱描述星座位置、西方占星大多使用
    - 補上 285 年對齊、約 24°、換算例子
    - 新增〈對「回歸黃道過時」的不同看法〉
  - wiki/concepts/恆星黃道.md：
    - 新增〈占星端的說明〉（Jyotish）
    - ayanamsa 一節補上：版本差異、Lahiri 1955、約 24° 與 Sri Yukteswar 約 23°（ayanamsa 不同，不算矛盾）
    - 內部不一致表加上 Kerykeion 一列
    - 註明恆星黃道的白羊宮起點跟 IAU 白羊座邊界不是同一個東西
  - wiki/concepts/歲差.md：ayanamsa 每 72 年增加約 1°、現在約 24°；待補改成指向回歸黃道頁與第 12 項
  - wiki/concepts/春分點.md：加上「太陽往北穿過天赤道的那一刻」（④）
  - wiki/concepts/黃道宮.md：〈兩種劃分系統〉補上 285 年、約 24°、換算例子，以及第 12 項的連結
  - wiki/synthesis/contradictions.md：
    - 第 10 項補上 Kerykeion 的結果
    - 新增第 12 項「回歸黃道是否『過時』」（觀點差異，非事實矛盾）
  - wiki/index.md
- 討論時使用者修正：無。使用者回覆「照建議」，兩個待決定事項都照建議處理：
  1. 第 10 項：
     - Kerykeion 支持「12 宮＋ayanamsa 位移」：只說 12 個宮；換算例子推算後是整體平移 24°。但它沒有明說恆星黃道每宮 30°。
     - 〈Astronomic zodiac〉的說法沒有其他來源支持。
     - 三份都是 ④，仍然並列、不選邊，待補 ①② 級來源。
  2. 回歸黃道是否「過時」：
     - 記入第 12 項，標「觀點差異（非事實矛盾）」。
     - 事實層面寫成內文：黃道宮和星座現在對不上；回歸黃道以分點定義。
     - 詮釋並列在回歸黃道頁，不放進常見誤解頁。
- 照前例處理：Kerykeion 評價占星可靠性的句子（「reliable psychological and event-based interpretation」「equally reliable results」）只在 source 頁照錄。跟 NASA、Smithsonian、Slate 的批評句一樣處理。
- 推算核對（只用來核對）：
  - 白羊宮 5° → 雙魚宮 11°：(30 − 11) + 5 = 24
  - 金牛宮 28° → 金牛宮 4°：28 − 4 = 24
  - 285 年到 2026 年約 1,741 年，除以 72 約 24
  - 三項都跟本篇的「約 24°」一致
- 其他：
  - CLAUDE.md Lint 第 5 條的「黃經差約 24°」，目前的出處是本篇（④），等 ingest 臺北 PDF 時看有沒有 ② 級來源。
  - 「約 2,000 年前對齊」和「西元 285 年對齊」本篇自己兩種寫法都用，「2,000 年」是概數，不算矛盾。
  - 不摘錄：dashas、nakshatras 等印度占星細節，以及學習建議。

## [2026-11-16] lint | 發現 0 個問題，自動修正 0 個
- 檢查範圍：wiki/ 全部頁面（sources 8、concepts 7、entities 3、synthesis 4）
- 1. index：22 個頁面都已列入，沒有指向不存在的頁面 ✓
- 2. [[連結]]：無斷連 ✓
- 3. frontmatter：完整，sources 都對應到 raw 檔，type 與資料夾一致 ✓
- 3. 數字／日期出處：新被標記的行都在已標出處的上層條列下，或是推算核對表、比較表（來源寫在表下），或是指向其他頁面的說明 ✓
- 4. 用語：
  - 本篇的 Aries、Taurus、Pisces、Cancer、Libra、Capricorn 都是黃道宮，依名稱對照表的暫行做法寫成白羊宮、金牛宮、雙魚宮、巨蟹宮、天秤宮、摩羯宮。有爭議的三組沒有出現 ✓
  - 「the constellation of Aries」寫成白羊座 ✓
  - 沒有新的民間通稱 ✓
- 5. 數字一致性：
  - 約 24°、285 年、每 72 年 1°，在 kerykeion-tropical-sidereal、回歸黃道、恆星黃道、歲差、黃道宮一致
  - 23°（Sri Yukteswar）只出現在指名 Sri Yukteswar 的地方，並註明 ayanamsa 不同 ✓
- 6. 未記錄的來源衝突：本篇的分歧已記入第 10、12 項；其他說法都和既有來源一致 ✓

## [2026-11-17] check | 臺北 PDF 的讀取方式（poppler）與原文重新核對
- 背景：2026-11-16 的環境沒有 PDF 讀取工具（Read 回報 pdftoppm 未安裝，也沒有 pypdf），第 16 頁的「巨蛇座(Serpens)」無法重新核對，當時沒有寫進 wiki。
- 處理：
  - 使用者同意（「你用就好」）後，下載 poppler 26.09.0 的免安裝版，放在本次工作階段的暫存資料夾。
  - 以完整路徑執行，沒有修改系統 PATH，也沒有安裝到電腦的其他地方。
  - 第一次下載遇到暫時性錯誤，重試後成功。
- 用法：pdftoppm 把 20 頁轉成 80 dpi 的圖片（看插圖裡的字）；pdftotext -layout 抽出文字層；pdfinfo 讀檔案資訊。
- 核對結果：
  - 第 2 頁插圖（名稱對照表 T2 的民間通稱）：重新判讀，結果與名稱對照表一致。
  - 第 14 頁「蛇夫座(Ophiuchus)」（T14）：文字層一致。
  - 第 16 頁「巨蛇座(Serpens)」（T16）：文字層確認，這次補進名稱對照表。
  - 第 13 頁「大約72年會移動1度」（contradictions 第 1 項）、第 17 頁「11月30日」（第 2 項）和 1928 那句（第 3 項）：與既有紀錄一致。第 3 項原本的引文省略了括號裡的英文全名，這次改成完整原句。
  - raw/SOURCES.md 第 6 列的描述（有 tropical 與 sidereal 日期對照表、「歲差不會改變黃道位置」的說明）：與原文一致，不需修改。
  - PDF 檔案資訊的標題是「12星座為何變成13星座？」，第 1 頁寫「黃道12星座為什麼變成13星座？」（SOURCES.md 用的是後者）。記在 source 頁，不改 SOURCES.md。

## [2026-11-17] ingest | 臺北市教育局資源〈黃道12星座為什麼變成13星座？〉（raw/taipei-edu-13-constellations.pdf）
- 新增：
  - wiki/sources/taipei-edu-13-constellations.md
  - wiki/entities/依巴谷.md（由 喜帕恰斯.md 改名，見下方）
- 更新：
  - wiki/synthesis/名稱對照表.md：
    - 13 星座表新增「中文黃道宮名」欄；新增〈中文黃道宮名〉一節（決定、第 5 頁與第 20 頁的差異、牡羊宮）
    - 出處代號新增 T5、T16；T2 註明 2026-11-17 重新判讀
    - 新增〈其他星座名〉：巨蛇座（Serpens）
    - 〈待處理〉的宮名結案；Cetus 中文名也列進待處理
  - wiki/synthesis/日期對照表.md：
    - 回歸、恆星兩欄改用臺北第 20 頁（②）的日期，跟英文維基差 1 天的格標 ※
    - 宮名欄改成中文宮名＋英文宮名
    - 核對表新增 4 列（白羊宮與金牛宮、兩欄 vs 英文維基、兩欄天數、IAU 欄天數）
  - wiki/concepts/黃道宮.md：
    - 新增 12 宮名稱表
    - 每宮 30° 補上 ② 級來源；〈由來〉補上臺北的說法
    - 新增〈起點：春分點與白羊宮〉
    - 〈3,000 年後〉補上臺北第 13 頁；待補更新
  - wiki/concepts/春分點.md：② 級定義、起點、移動速率與古今位置；大月表核對；白羊宮的例子；頁首說明與待補更新
  - wiki/concepts/歲差.md：
    - ② 級定義、英文 Axial precession
    - 從依巴谷到現在將近 30°
    - 〈跟黃道的關係〉補上臺北第 18 頁，註明跟中文維基的 0.47″ 不算矛盾
    - 「歲差不改變黃道」的待補結案
  - wiki/concepts/黃道.md：② 級定義；臺北判斷蛇夫座在黃道上的方法；新增〈歲差會不會改變黃道〉；待補改成〈相關頁面〉
  - wiki/concepts/回歸黃道.md、恆星黃道.md：
    - 各宮日期補上 ② 級來源
    - 恆星黃道的內部不一致表加上臺北一列
    - 待補改成「定義的 ①② 級來源」
  - wiki/entities/蛇夫座.md：
    - 黃道穿過蛇夫座的腳、1825 年星圖
    - 新增〈蛇夫座的劃分〉（從天蠍座分出）
    - 1928 說法的出處
    - 待補：Kerykeion 沒有提到蛇夫座（搜尋原文確認）
  - wiki/synthesis/contradictions.md：
    - 第 1 項註明重新核對
    - 第 3 項改成完整原句
    - 第 8 項加入臺北的說法
    - 第 10 項加入臺北的核對
    - 第 12 項處理方式補上臺北第 19 頁
    - 新增第 13、14、15 項
  - wiki/sources/wiki-sidereal-tropical.md：連結改為 [[依巴谷]]
  - wiki/sources/kerykeion-tropical-sidereal.md：用語註記改成指向定案的宮名
  - wiki/index.md
- 改名：wiki/entities/喜帕恰斯.md → 依巴谷.md。
  - 所有 [[喜帕恰斯]] 連結改為 [[依巴谷]]（歲差、wiki-sidereal-tropical 兩處、index）。
  - 引用中文維基的章節名（例如〈喜帕恰斯的發現〉）照原文保留。
  - log 裡的舊紀錄不改。
- 討論時使用者修正：無。使用者回覆「照建議」，4 個待決定事項都照建議處理：
  1. 中文黃道宮名：採第 20 頁「正式中文」那一套（處女宮、射手宮、水瓶宮），宮跟座的名字因此分得開。2026-11-16 起的暫行做法（有爭議的三組只寫英文）結束。
  2. 實體頁依來源等級改名為「依巴谷」，註明中文維基作「喜帕恰斯」。
  3. 日期對照表的回歸、恆星兩欄改用臺北（②）的日期，差 1 天的地方記入第 13 項。欄名註明「臺北未註明 ayanamsa；英文維基註明 Lahiri」。
  4. 第 13 頁的宮／座混用記入第 15 項；wiki 只寫「現在春分時太陽在雙魚座」。
- 寫入時發現、跟討論報告不同的地方（我自己的修正）：
  1. 第 14 項：
     - 討論報告把它標成「衝突」。寫入時發現，要知道新巴比倫王朝的年代才能判斷兩邊是不是不同時代，但 raw 裡沒有這個年代，所以改標「可能衝突」。
     - 討論報告的表寫「第 8 頁：西元前 2 世紀的依巴谷」，看起來像是依巴谷訂了起點。原句其實沒有明寫是誰決定的，wiki 照原句寫。
  2. 「從依巴谷到現在將近 30°」的推算：討論報告寫「約 2,150 年 ÷ 72 ≈ 30」，但 2,150 年是我自己估的，沒有出處。寫入時改用第 13 頁圖中文字（公元前 200 年、公元 2000 年）：約 2,200 年 ÷ 72 ≈ 30.5，跟「將近 30 度」都是概數，一致。
  3. 第 10 項：討論報告沒有提到。寫入時用臺北 siderial 欄推算各宮天數（29–32 天，跟 tropical 欄相同），補進第 10 項的核對。狀態不變；要不要把臺北的表當作足夠的 ② 級證據，留給使用者決定。
  4. 討論報告說第 13 頁的宮座混用跟它自己的表不一致。寫入時多記了一點：如果用恆星黃道理解，「春分點移到雙魚宮內」說得通（推算用 Kerykeion 的 24°：回歸白羊宮 0° 約是恆星雙魚宮 6°）。PDF 沒說是哪一種，wiki 不替它選。
- 照前例處理：
  - 第 19 頁「占星術……並不是科學」只在 source 頁照錄；配圖和「森77」簡報一律不用。
  - 第 17 頁的 1928 那句只在 source 頁照錄，註明與 IAU 原文不符。
  - 第 16 頁的希臘神話只在 source 頁列出。
- 推算與程式核對（只用來核對）：
  - 日期對照表與第 20 頁、英文維基逐格比對：14 列全部一致；12 個 ※ 都標在差 1 天的格上，沒有多標或漏標。
  - 兩份來源的回歸、恆星兩欄：各宮 29–32 天，各自加總 365 天（非閏年）。
  - 西元前 2 世紀在大月表白羊座的期間（2000 BC – 100 BC）內，一致。
- 其他：
  - CLAUDE.md Lint 第 5 條的「黃經差約 24°」：臺北 PDF 沒有這個數字，目前仍只有 ④ 級來源（kerykeion-tropical-sidereal）。
  - 不摘錄：第 2 頁運勢排行的內容、第 6 頁插圖書頁上的小字、第 20 頁的 Symbol 與 Unicode code 欄。
- 日期：這次操作在 2026-11-17 進行，新寫和修改的頁面 updated 改為 2026-11-17。

## [2026-11-17] lint | 發現 3 個問題，自動修正 3 個
- 檢查範圍：wiki/ 全部頁面（sources 9、concepts 7、entities 3、synthesis 4）
- 1. index：23 個頁面都已列入，沒有指向不存在的頁面 ✓
- 2. [[連結]]：無斷連；改名後沒有殘留的 [[喜帕恰斯]] ✓
- 3. frontmatter：完整，sources 都對應到 raw 檔，type 與資料夾一致 ✓
- 3. 數字／日期出處：新被標記的行都看過，都不需要另外加出處：
  - 有的在已標出處的上層條列下
  - 有的是表格，來源寫在表下
  - 有的在 taipei-edu-13-constellations 自己的 source 頁 ✓
- 4. 用語：
  - **問題 1（已自動修正）**：黃道宮頁這次新寫的「臺北 PDF 的說法：黃道十二宮（The twelve ecliptic signs）起源於巴比倫」，「黃道十二宮」沒有加引號。已加引號，並註明「即黃道宮」。
  - **問題 2（已自動修正，舊問題）**：黃道宮頁「中文〈歲差〉說，黃道十二宮在新巴比倫王朝時期形成」和春分點頁「黃道十二宮形成時」，「黃道十二宮」都沒有加引號。這兩處是 2026-11-16 寫的，之前的 lint 是我人工看第 4 項的輸出，漏看了。已加引號。
  - **問題 3（已自動修正）**：春分點頁「以中氣點等分定義的牡羊宮」。宮名定案後，wiki 內文應寫「白羊宮」，已改成「白羊宮（原文作「牡羊宮」）」。source 頁和對照表裡的「牡羊宮」是摘錄或比較原文，保留。
  - 新出現的處女座、射手座、水瓶座都有「民間通稱」註記；處女宮、射手宮、水瓶宮是定案的宮名 ✓
  - 新出現的 Scorpio、Capricorn 都在黃道宮的欄位或宮名旁 ✓
- 5. 數字一致性：
  - 「約 72 年 1°」「將近 30°」「約 24°（只有 ④）」在各頁一致
  - 白羊宮回歸 3/21–4/19、恆星 4/14–5/14 在回歸黃道、恆星黃道、春分點、黃道宮、日期對照表一致
  - 英文維基那 12 個差 1 天的日期，只出現在 contradictions 第 13 項 ✓
- 6. 未記錄的來源衝突：這一輪發現的都已記錄（第 13、14、15 項，第 8、10 項的補充）。依巴谷／喜帕恰斯、天球赤道／天赤道、PDF 的兩個標題是名稱差異，記在各頁，不算事實矛盾 ✓

## [2026-11-17] slides | 第 1 輪 大綱
- 產生 slides/outline.md（23 張），依教學結構：引起動機 → 基本概念 → 原理 → 例子 → 常見誤解 → 小結 → 小測驗。
- 大綱開頭列出寫簡報要守的規則：宮／座用顏色區分、名稱、中立，以及 contradictions 第 1、6–10、12–15 項的限制。
- 不通過原因（逐張對照 wiki 原文時發現，4 個）：
  1. 第 12 張「大部分的日子在雙魚座」是我讀表推出來的結論，wiki 沒有這句（超出 wiki）。
  2. 第 20 張「常常不是同名的那個宮」，「常常」沒有出處（超出 wiki）。
  3. 「查查你的生日」排在兩套系統、蛇夫座之前，觀眾會先看到還沒解釋的名詞（順序）。
  4. 第 19 張「引用前要對照 IAU 原文」是我加的建議（超出 wiki）。
- 回到哪一步：第 1 步，修大綱。不需要回頭補 wiki。

## [2026-11-17] slides | 第 2 輪 大綱
- 修正：
  - 第 12、20 張改用 wiki 春分點頁的說法「同一個『白羊』，宮和座差了將近一個月」，第 20 張的「常常」改成「可能」。
  - 順序改成兩套系統（第 14 張）→ 蛇夫座（第 15 張）→ 查生日（第 16 張）。
  - 第 19 張改成「有些資料這樣寫，但 IAU 原文沒有」。
- 檢查結果：通過。每個重點都有 wiki 出處（逐張列在 outline.md 文末）；順序由淺入深；沒有發現新的超出 wiki 的內容。
- 要注意的地方：第 8 張把「投影到天球上的線」改成初學者的說法，避開「天球」；時間軸圖和查詢工具的資料直接取自日期對照表。
- 進入第 2 步：HTML。

## [2026-11-17] slides | 第 1 輪 HTML
- 產生 docs/index.html：單一檔案、不依賴外部套件，用瀏覽器直接開；23 張投影片，每張的 `<section>` 都有 data-source，頁尾顯示 wiki 出處和原始資料等級。
- 做法：
  - 時間軸圖（第 12、13、15 張）、宮名表（第 7 張）、生日查詢（第 16 張）的日期和名稱，由 build script 直接從 wiki 的日期對照表、名稱對照表讀出來產生，不手抄。
  - 示意圖（第 5、6、8、9、10 張）是 inline SVG。
- 用 headless Edge 截圖逐張看版面（1280×720 和手機寬 390px），發現並修正：
  1. 第 7 張的表在 1280×720 會超出畫面 → 改成兩個表並排，並且不讓表格內文字換行（只在寬螢幕）。
  2. 第 9 張的「自轉軸」標籤離軸太遠 → 移到軸旁邊。
  3. 第 5 張圖裡的字太小 → 放大。
  4. 第 3 張第一次出現「IAU」時沒有說明 → 改成「國際天文學聯合會（IAU）」。
  5. 第 17、23 張的英文引號、撇號用了中文全形字形 → 英文段落加 lang="en" 改用英文字型。
  6. 第 23 張「等級」欄標題被擠成直排 → 禁止換行。
- 用測試頁在 headless Edge 裡實際操作，結果都正常：
  - 小測驗 6 題：選錯會標出正確答案，選對顯示「答對了」。
  - 換頁按鈕、← → End 鍵正常，最後一張不會再往後。
  - 生日查詢：跨年（12/31、1/1）、2/29、交界日都正確。
- 測試時發現的措辭問題（已修正）：交界日（例如 4/18 同時是雙魚座最後一天、白羊座第一天）原本會說「兩者一致」，容易誤導。改成交界日只說明「兩個都列出來」的原因，不下一致或不一致的結論，並依日期先後列出兩個星座。
- 手機截圖一開始看起來右邊被切掉。查證後是 headless Edge 視窗最小寬度造成的假象，改用 390px 寬的 iframe 重測，版面正常。

## [2026-11-17] slides | 第 1 輪 檢查
- 檢查方式：
  - 逐張對照 wiki 原文，檢查用語和初學者看不看得懂。
  - 用 script 檢查 data-source 與頁尾是否一致、外部資源、數字出處、用語，並把查詢資料跟原始資料比對。
- 不通過原因（5 個）：
  1. 第 2 張「星座運勢常這樣說」，「常」是我加的；wiki 寫「會說」。
  2. 第 9 張頁尾的出處標示不夠精確：定義句出自中文維基（④），陀螺比喻出自 Slate（③）與中文維基（④）。
  3. 第 12 張在第 14 張解釋之前就用了「回歸黃道」。
  4. 第 8 張「春分那天」沒說是哪一天。
  5. 第 18 張「傳統的 12 個黃道星座」容易跟宮混淆。
- 回到哪一步：第 1 步（其中 4 個是大綱本身的寫法，大綱同步修改）和第 2 步。

## [2026-11-17] slides | 第 2 輪 檢查
- 不通過原因（2 個，全部重新截圖、人工重看時發現）：
  1. 第 20 張（大綱第 10、20 張）「兩千多年下來將近一個宮」：「兩千多年」是我自己換算的，wiki 寫的是「從依巴谷的年代到現在」。大綱第 2 輪檢查時也沒發現。
  2. 第 5 張示意圖的標籤「幾個月後的地球」，帶了 wiki 沒寫的時間長度。
- 為什麼第 1 輪沒抓到：數字檢查只比對阿拉伯數字。這一輪改用中文數字再掃一次全文。
- 回到哪一步：第 1 步和第 2 步。改成「從依巴谷的年代到現在，已經移動將近 30°」「繞到另一個位置的地球」。

## [2026-11-17] slides | 第 3 輪 檢查
- 結果：通過。詳見 slides/check-report.md。
  - 23 張逐張對照 wiki 原文。
  - 用語規則：黃道十二宮只在引號裡、民間通稱都有註記、英文宮名與拉丁名分開、宮與座的顏色沒有混用、沒有評價占星的字眼。
  - 初學者：每個名詞第一次出現都有解釋。
- 資料：
  - 查詢工具與時間軸的日期，跟臺北 PDF 第 20 頁文字層、英文維基原表逐格比對，0 處不符。
  - 一年 366 天每一天都對得到宮和座。
- 版面：最終版 23 張在 1280×720 下都在一個畫面內。偵測捲軸的方法先用故意超出的情況驗證過。
- 沒有測到：真正的手機與投影機、Firefox 與 Safari、列印、螢幕閱讀器。
- 其他：
  - docs/index.html 由 build script 從 wiki 的日期對照表、名稱對照表產生。script 放在本次工作階段的暫存資料夾，沒有放進專案；之後 wiki 的日期或名稱有改，需要重新產生或手動同步。
  - 第 9 張「為什麼會晃」、第 14 張「約 24°」只有 ④ 級來源，頁尾有標，留給使用者決定要不要保留。

## [2026-11-17] check | 作業繳交：loop／graph 說明頁與錯誤統計
- 起因：使用者提供第十週作業的要求。對照後，缺的是「loop／graph 說明」、「反思」，以及 Wiki 和簡報的連結。
- 新增：
  - docs/workflow.html：流程圖、各節點說明、重複次數、檢查點、設計理由、一次實際執行、反思、檢查往前移與 workflow 的修改。
  - docs/workflow-graph.png：流程圖的圖檔，給不能嵌網頁的繳交系統用。
  - 作業繳交.md：作業要求的 6 項，整理成可以直接貼上的文字。個人資料和網址留空，待使用者填。
- 錯誤統計的方法：
  - 把本 log 裡每一筆被記錄的錯誤（包括我自己發現的、使用者指出的、各項檢查抓到的）逐筆列出，共 42 筆。
  - 依「在哪個節點產生」和「被誰抓到」分類。逐筆清單在 workflow.html 第 7 節。
  - 不算進去的：使用者在討論時做的規則決定（例如建立名稱對照表），因為那是設計選擇，不是錯誤。
- 統計時發現 log 自己的不一致：2026-11-16 ingest smithsonian 之後那筆 lint，標題寫「發現 0 個問題，自動修正 1 個（補出處）」，內文卻有 1 處補出處。統計時算成 Lint 抓到 1 個問題。log 只能追加，所以原標題不改，記在這裡。
- 結果：
  - 37/42 發生在 AI 把來源改寫成文字的節點：討論報告、寫入 wiki、寫大綱、產生 HTML。
  - 最常見的類型是「自己多加了來源沒有的字或推論」，共 14 個。
  - 累計最多的節點是寫入 wiki（15 個，跑了 9 次）；單次最多的是寫大綱（1 次 10 個）。
- 還沒做：推上 GitHub、開啟 Pages。這需要使用者的帳號，而且會公開發布，等使用者決定。
