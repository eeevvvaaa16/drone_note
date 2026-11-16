# 小小無人機探索站

## 專案簡介
以原創童趣探索站呈現無人機學習筆記。橘色黏土無人機主視覺搭配天空藍與草地綠；內容採白話說明、比較表、情境例子與可展開答案。這次作業重點是 AGENTS.md 的可延伸規則，以及遵循規則製作的網站成果。

## 詳細版包含什麼
| 探索站 | 內容 | 原始文件 |
|---|---|---|
| 01 大無人機要做哪些檢驗 | 四類檢驗、五階段流程、50 小時要求適用脈絡、效期、改裝 | AC 107-002B，2025.12.01，15 頁 |
| 02 小一點的無人機規則一樣嗎 | 2／15／25 公斤分界、實驗室檢測、文件組、五階段、認可與進口 | AC 107-009A，2026.05.22，14 頁 |
| 03 要試飛了先準備什麼 | 申請資料、規劃與計畫、人員、場地、地面檢查、中止及應變 | AC 107-003A，2024.12.01，15 頁 |

每篇都有六個固定區塊與六題解析，合計 18 題。筆記是指定版本主文重點整理，不是官方逐條全文或完整申請清單。原始 PDF 保留原樣；缺少哪些附件見 sources/SOURCE-MAP.md。未查核後續修訂。

## 開啟網站
1. 解壓縮 ZIP。
2. 進入 drone-notes 資料夾，開啟 index.html。
3. 保留 assets、notes、sources 等資料夾，不可只傳送 index.html。

不需要安裝套件、不需要 API 金鑰，直接開檔即可使用。若開發工具需要本機網址，可在根目錄執行 python3 -m http.server 8000，再用瀏覽器開啟 http://localhost:8000；這只是本機測試，不是公開網站。

## 功能與限制
- 搜尋：搜尋首頁卡片的標題、摘要、文件編號與 data-keywords；不是 PDF 全文檢索。
- 分類：檢驗程序與試飛作業，會和搜尋條件同時套用。
- 閱讀路線：點選章節名稱跳到指定位置。
- 自我檢查：每篇六題，可展開參考答案，不保存分數。
- 來源回查：PDF 連結含頁次提示；瀏覽器 PDF 閱讀器是否支援自動定位可能不同。
- 原創主圖：AI 生成的裝飾插圖，不代表真實機型或工程構型。

## 主要檔案
AGENTS.md 是 AI 工作規則；templates/note-template.html 是完整頁面模板；templates/card-template.html 是首頁卡片片段；scripts/verify.py 是檔案檢查腳本。其餘目錄責任詳見 AGENTS.md 第 3 節。

## 如何請 AI 新增內容
可複製這段指令：

> 請先閱讀 AGENTS.md，使用我提供的來源新增一篇「無人機飛行前檢查」筆記。沿用六個固定區塊與六題解析，標明文件版本、PDF 頁次與原文章節。更新首頁卡片、關鍵字、README、SOURCE-MAP、相關閱讀與 CHANGELOG，執行檢查並回報尚未驗證事項。

AI 應複製模板，填完 {{...}} 佔位符，加入首頁卡片後才算完成。模板中的占位 PDF 連結刻意未指向特定文件，新增時必須替換。不可直接把模板當正式筆記發布。

## GitHub Pages 發布步驟
1. 在 GitHub 建立 repository，例如 drone-notes；課堂繳交若需老師無登入瀏覽，確認使用適合公開展示的設定與檔案。
2. 將 drone-notes 裡的內容放到 repository 根目錄，應直接看得到 index.html、AGENTS.md、assets/、notes/ 等。不要只上傳 ZIP，也不要多包一層同名資料夾。
3. 完成 commit，確認預設分支名稱，例如 main。
4. Settings → Pages → Source 選 Deploy from a branch；選正確分支與 / (root)，儲存。
5. 等待部署成功，從 Pages 頁面複製實際網站網址；別把 repository 網址當網站網址。
6. 實際開啟公開網站，檢查主圖、搜尋、筆記與來源 PDF，再把兩個連結填入 SUBMISSION.md。

介面名稱可能更新；設定依 GitHub 官方 Pages 文件：https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
此 ZIP 本身不代表已完成上傳或部署，也未填入虛構的公開網址。

## 常見問題
| 問題 | 先檢查 |
|---|---|
| 圖片或樣式消失 | assets 是否一起解壓／上傳；檔名大小寫是否一致 |
| GitHub 顯示 404 | 部署是否成功、分支及發布根目錄是否正確、有無 index.html |
| 新筆記搜尋不到 | 是否已加入 #cards；關鍵字是否在卡片文字或 data-keywords |
| 分類後看不到新筆記 | data-category 是否與選項值完全一致 |
| 新增頁面連結失效 | notes 內返回首頁與 assets／sources 應先 ../ |
| PDF 沒跳到指定頁 | 閱讀器可能忽略 #page；手動前往顯示的 PDF 實體頁次 |

## 驗收與維護
執行 python3 scripts/verify.py（僅標準函式庫）。如有 Node，可另執行 node --check assets/search.js。
再實際操作搜尋、分類、目錄、答案與 PDF；檢查桌面和手機版。檢查結果記在 QA.md，不可把未執行項目寫成通過。
修改內容須遵守來源版本與範圍；修改共用元件時同步模板。每批改動寫入 CHANGELOG.md。
