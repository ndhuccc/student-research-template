# 週報規範 / Weekly Report Guide

## 中文說明

本目錄保存可供教授掌握研究進度、審查研究方法、留下回饋紀錄的週報。週報不是工作日誌；它應以可查核的證據，說明本週做了什麼、採用什麼方法、得到什麼結果、如何解讀，以及下一步需要教授決策或協助的事項。

**核心原則：教授應能只閱讀週報，就理解本週實驗或研究工作的主要方法，而不必先閱讀程式碼、設定檔或其他內外部文件。**程式碼與文件連結是佐證，不可取代方法敘述。

除非研究群另有規定，學生可用中文或英文撰寫實際週報；但必須保留本規範的章節順序、欄位與可追溯資訊。此目錄提供雙語樣板與雙語完整示例。

### 1. 檔案位置與命名

依年度存放，採 ISO week（週一至週日）命名：

~~~text
weekly-reports/
  README.md
  TEMPLATE.md
  examples/
    2026-W38.md
  2026/
    2026-W38.md
    2026-W39.md
~~~

正式檔名一律為 **YYYY-Www.md**，例如 **2026-W38.md**。同一週只維護一份正式週報；若提交後修正，直接更新該檔，並在「教授回饋與修正紀錄」留下日期與修正內容。

### 2. 每週提交流程

1. 從 [TEMPLATE.md](TEMPLATE.md) 複製建立當週檔案。
2. 將檔案存入 **weekly-reports/YYYY/**，並完成所有必填章節。
3. 對每項完成工作附上可追溯證據：commit、設定檔、資料版本、實驗輸出、圖表或文件連結。
4. 以自己的文字完整描述「實驗方法」；不可只寫「詳見程式碼」或只貼指令。
5. 提交前確認連結、數值、日期、分支與下週可驗收成果正確，再 commit 與 push。
6. 教授回饋後，保留原週報內容，在「教授回饋與修正紀錄」補上回應與採取的動作。

### 3. 必填章節與審查目的

| 章節 | 必填內容 | 教授可據以判斷 |
| --- | --- | --- |
| 基本資訊 | 學生、週次、日期範圍、分支或 commit、整體狀態 | 報告涵蓋範圍與版本基準 |
| 一頁摘要 | 本週問題、最重要結果、進度判斷、需決策事項 | 是否需要優先介入 |
| 本週目標與完成度 | 目標、完成度、狀態、偏差原因 | 原定計畫是否如期推進 |
| 實驗方法（必填） | 研究問題、資料、設計、流程、設定、評估、偏差 | 方法是否合理、可重現、足以支持結論 |
| 結果與可追溯證據 | 數值、圖表、輸出位置、commit、設定檔 | 結果是否真實且可查核 |
| 解讀與限制 | 結論、比較、不能宣稱的事項、方法限制 | 推論是否過度、下一步是否合理 |
| 風險與阻礙 | 影響、處理方式、需要的協助、期限 | 如何排除風險與配置資源 |
| 下週計畫 | 可驗收交付物、截止日、驗收標準 | 下週如何檢查進度 |
| 教授回饋與修正紀錄 | 回饋、學生回應、採取動作、日期 | 指導脈絡是否閉環 |

### 4. 實驗方法：必要的自足說明

每一個本週新增、修改或重新執行的重要實驗，都要在「實驗方法」中以**一段摘要加上一張方法表**說明。讀者應能回答：「你比較了什麼？如何比較？哪些因素被固定？資料如何處理？結果如何評估？」

至少包含下列資訊：

1. **研究問題與假設**：要驗證或比較什麼；預期何種結果，以及理由。
2. **實驗設計**：baseline／對照組與各處理組；自變項、依變項、固定條件；重複次數、random seed、樣本選取或排除規則。
3. **資料與前處理**：資料集名稱、版本或快照、來源、切分方式、樣本量、清理、標準化、增強及排除條件。不得只寫「使用資料集 X」。
4. **方法或系統流程**：模型、演算法、儀器或資料處理管線的主要步驟；相對於 baseline 或前一週改動了什麼。必要時以簡短編號流程或圖示輔助。
5. **設定與執行環境**：設定檔路徑、重要參數、軟硬體環境、主要命令或操作步驟。連結可提供細節，但正文必須解釋參數的角色。
6. **評估與判定規則**：使用哪些指標、在哪個資料切分計算、判定成功或比較優劣的準則；若適用，說明統計檢定、信賴區間或重複實驗的處理方式。
7. **偏差與可重現性限制**：未完成的重複次數、資料異常、與原計畫不同之處、已知限制，以及下次如何補強。

**最低可接受寫法：**「以固定資料切分與 ResNet-18，比較 learning rate 1e-4、1e-3、1e-2；其他設定不變；使用 validation macro-F1 評估。」接著須補上資料版本、前處理、seed、重要訓練設定、結果位置與限制。

**不可接受寫法：**「調了 learning rate，結果變好，詳見 code。」這種寫法無法判斷比較條件、資料、評估方式或結論是否成立。

若本週沒有實驗，仍須在此章節寫明「本週未執行實驗」，並交代原因、完成了哪些研究設計或資料準備、預定何時開始、預期採用的方法。不可略過該章節。

### 5. 結果、解讀與證據的寫法

- **把事實與解讀分開。**先列出指標、圖表、輸出與版本，再說明你認為結果代表什麼。
- **寫明比較基準。**例如「較 baseline 高 1.8 個百分點」比「表現變好」可審查得多。
- **不要只報最佳結果。**同時說明失敗、異常、未完成實驗，及其可能原因。
- **避免過度推論。**只有單一 seed、尚未完成測試集評估或資料切分可能洩漏時，必須標示為初步結果。
- **證據要能定位。**記錄 commit SHA、檔案路徑、資料版本、實驗輸出位置與設定檔；不要以「最新版」或「在雲端資料夾」取代位置。

### 6. 品質檢查清單

提交前逐項確認：

- [ ] 檔名、年份、週次及日期範圍正確。
- [ ] 所有目標都有完成度與狀態；未完成項目有原因與處理方式。
- [ ] 每個重要實驗都有自足的「實驗方法」摘要與方法表。
- [ ] 已寫出資料版本、資料切分、baseline／控制條件、重要設定、seed／重複次數與評估規則。
- [ ] 所有數據、圖表、檔案路徑與 commit 可追溯。
- [ ] 已明確標示初步結果、限制、例外或與計畫的偏差。
- [ ] 下週工作有可驗收交付物、日期與驗收標準。
- [ ] 已提出真正需要教授回饋的問題，而不是只有「請指教」。

### 7. 可直接使用的檔案

- [TEMPLATE.md](TEMPLATE.md)：可直接複製的週報樣板，含每個欄位的填寫提示。
- [examples/2026-W38.md](examples/2026-W38.md)：一份完整示例，示範如何以自足方式敘述實驗方法、結果與限制。

---

## English Guide

This directory stores weekly reports that let the supervisor understand research progress, review the research method, and leave a durable feedback record. A weekly report is not a work log. It should use verifiable evidence to explain what was done, how it was done, what was found, how the findings should be interpreted, and what decision or support is needed next.

**Core principle: a supervisor should be able to understand the main method of this week's research or experiment by reading the report alone, without first reviewing code, configuration files, or other internal or external documents.** Links to code and documents are supporting evidence; they do not replace the method description.

Unless the research group specifies otherwise, students may write the submitted report in Chinese or English, but they must keep the required section order, fields, and traceability information. A bilingual template and a bilingual complete example are provided here.

### 1. Location and file names

Store reports by year and name them with the ISO week (Monday through Sunday):

~~~text
weekly-reports/
  README.md
  TEMPLATE.md
  examples/
    2026-W38.md
  2026/
    2026-W38.md
    2026-W39.md
~~~

The required filename is **YYYY-Www.md**, for example **2026-W38.md**. Maintain one official report per week. If a submitted report is corrected, update the same file and record the date and change in **Supervisor Feedback and Correction Log**.

### 2. Weekly submission workflow

1. Copy [TEMPLATE.md](TEMPLATE.md) to create the current week's report.
2. Save it under **weekly-reports/YYYY/** and complete every required section.
3. Attach traceable evidence to each completed item: commit, configuration, data version, experiment output, figure, or document link.
4. Describe the **Experimental Method** fully in your own words. Do not write only “see the code” or paste commands without explanation.
5. Before committing and pushing, verify links, values, dates, branches, and next-week acceptance criteria.
6. After supervisor feedback, retain the original report and add your response and action to **Supervisor Feedback and Correction Log**.

### 3. Required sections and review purpose

| Section | Required content | What the supervisor can assess |
| --- | --- | --- |
| Metadata | Student, week, date range, branch or commit, overall status | Scope and version baseline |
| Executive summary | This week's question, most important result, progress assessment, needed decisions | Whether early intervention is needed |
| Objectives and status | Objective, completion rate, state, and reason for deviations | Whether the plan is progressing as intended |
| Experimental Method (required) | Question, data, design, procedure, settings, evaluation, deviations | Whether the method is sound, reproducible, and supports the claim |
| Results and traceable evidence | Values, figures, output locations, commits, configurations | Whether the result is real and verifiable |
| Interpretation and limitations | Conclusion, comparison, non-claims, and method limits | Whether inference is excessive and next steps are justified |
| Risks and blockers | Impact, mitigation, requested help, deadline | How risk and resources should be managed |
| Next-week plan | Verifiable deliverable, due date, acceptance criterion | How progress will be checked next week |
| Supervisor feedback and correction log | Feedback, response, action, date | Whether the advising loop is closed |

### 4. Experimental Method: a self-contained account

For every important experiment that was added, changed, or rerun this week, write **one concise narrative summary plus one method table** in the **Experimental Method** section. A reader should be able to answer: What was compared? How was it compared? What was held fixed? How was the data handled? How were results evaluated?

Include at least the following:

1. **Research question and hypothesis:** What is being tested or compared, what result is expected, and why.
2. **Experimental design:** Baseline/control and treatment groups; independent and dependent variables; fixed conditions; repetitions, random seeds, and sample inclusion/exclusion rules.
3. **Data and preprocessing:** Dataset name, version or snapshot, source, split, sample counts, cleaning, normalization, augmentation, and exclusion criteria. “Dataset X was used” is not enough.
4. **Method or system procedure:** The principal steps of the model, algorithm, instrument, or data pipeline, and what changed relative to the baseline or prior week. Use a short numbered workflow or diagram if useful.
5. **Configuration and execution environment:** Configuration path, material parameters, software/hardware environment, and principal command or operating steps. Links may give details, but the report must explain the role of material parameters.
6. **Evaluation and decision rule:** Metrics, data split used for them, and rule for success or comparison. When relevant, state statistical testing, confidence intervals, or treatment of repeated runs.
7. **Deviations and reproducibility limits:** Incomplete repetitions, data anomalies, departures from plan, known limitations, and how the next iteration will address them.

**Minimum acceptable wording:** “With the data split and ResNet-18 fixed, we compared learning rates 1e-4, 1e-3, and 1e-2; all other settings were held constant; validation macro-F1 was the metric.” Then add the data version, preprocessing, seed, material training settings, output location, and limitations.

**Unacceptable wording:** “I tuned the learning rate; the result improved; see the code.” It does not reveal comparison conditions, data, evaluation, or whether the conclusion is justified.

If no experiment was run, do not omit this section. State **No experiment was run this week**, explain why, identify what design or data preparation was completed, state when experimentation will begin, and describe the intended method.

### 5. Writing results, interpretation, and evidence

- **Separate fact from interpretation.** Present metrics, figures, outputs, and versions before explaining what they may mean.
- **State the comparison basis.** “1.8 percentage points above the baseline” is reviewable; “better performance” is not.
- **Do not report only the best run.** Include failures, anomalies, unfinished experiments, and plausible causes.
- **Avoid overclaiming.** Mark findings as preliminary when only one seed was run, test evaluation is incomplete, or data splitting may leak information.
- **Make evidence locatable.** Record commit SHA, file path, data version, output location, and configuration. Do not use “latest version” or “in the cloud folder” as a location.

### 6. Pre-submission checklist

- [ ] Filename, year, week number, and date range are correct.
- [ ] Every objective has a completion rate and state; incomplete work has a reason and mitigation.
- [ ] Every material experiment has a self-contained Experimental Method summary and method table.
- [ ] Data version, split, baseline/control, material settings, seeds/repetitions, and evaluation rule are stated.
- [ ] Every number, figure, path, and commit is traceable.
- [ ] Preliminary findings, limitations, exceptions, and deviations are explicitly marked.
- [ ] Next week has a verifiable deliverable, date, and acceptance criterion.
- [ ] The report asks for concrete supervisor feedback rather than only “please advise.”

### 7. Ready-to-use files

- [TEMPLATE.md](TEMPLATE.md): A copy-ready weekly report template with writing prompts for every field.
- [examples/2026-W38.md](examples/2026-W38.md): A complete example showing a self-contained description of method, results, and limitations.
