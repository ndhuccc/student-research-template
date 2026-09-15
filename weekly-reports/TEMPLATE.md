# YYYY-Www Weekly Report / 第 YYYY 年第 ww 週週報

> **使用方式 / How to use**：將本檔複製到 **weekly-reports/YYYY/YYYY-Www.md**，以實際內容取代所有中括號提示。實際繳交可使用中文或英文，但不得省略必填章節。每個重要實驗都必須有自足的「實驗方法」敘述；程式碼、設定檔與輸出連結只能作為佐證。
>
> Copy this file to **weekly-reports/YYYY/YYYY-Www.md** and replace all bracketed prompts with actual content. The submitted report may be in Chinese or English, but no required section may be omitted. Every material experiment needs a self-contained **Experimental Method** description; links to code, configuration, and outputs are supporting evidence only.

---

## 中文版

## 1. 基本資訊

| 欄位 | 內容 |
| --- | --- |
| 學生 | [姓名] |
| 週次 | [YYYY-Www；ISO week，週一至週日] |
| 日期範圍 | [YYYY-MM-DD] 至 [YYYY-MM-DD] |
| 研究主題 | [本週工作所屬研究題目] |
| 整體狀態 | [🟢 正常 / 🟡 有風險 / 🔴 受阻] |
| 工作分支／基準 commit | [branch 名稱；短 SHA] |
| 報告更新日期 | [YYYY-MM-DD] |

## 2. 一頁摘要

- **本週研究問題或重點：** [用一至兩句說明本週要回答的問題或完成的關鍵工作。]
- **最重要結果：** [量化結果或明確產出；若無結果，說明原因。]
- **進度判斷：** [相對於原定計畫，正常、落後或受阻；說明最重要原因。]
- **需要教授決策／協助：** [具體問題、所需資訊或決策期限；若無則寫「本週無」。]

## 3. 本週目標與完成度

| 目標 | 完成度 | 狀態 | 完成事項或偏差原因 | 證據 |
| --- | ---: | --- | --- | --- |
| [可驗收目標 1] | [%] | [完成／進行中／受阻] | [做了什麼；若未完成，為何偏離] | [commit、檔案、圖表或輸出連結] |
| [可驗收目標 2] | [%] | [完成／進行中／受阻] | [做了什麼；若未完成，為何偏離] | [commit、檔案、圖表或輸出連結] |

## 4. 實驗方法（必填）

> 即使本週沒有執行實驗，也要寫明原因、已完成的準備工作、預定開始時間與預計方法。不要只貼程式碼、指令或連結。

### 4.1 方法摘要

[以一段 4–8 句的文字，讓未讀程式碼的教授理解：研究問題／假設、比較對象、資料、主要流程、控制條件、評估指標與目前結果的解讀範圍。]

### 4.2 實驗方法表

| 項目 | 本週實際內容 |
| --- | --- |
| 實驗名稱／研究問題 | [名稱；明確描述要比較、驗證或量測的問題] |
| 假設與預期 | [預期什麼結果，以及為何合理] |
| Baseline／對照組 | [比較基準、控制組或前一版本] |
| 處理組／變動因素 | [本週改變的自變項及各水準；若多項，逐項列出] |
| 固定條件 | [模型、資料切分、訓練步數、儀器條件等不能隨組別改變的因素] |
| 實驗單位與重複 | [樣本單位、每組樣本數、重複次數、random seed；未完成時要說明] |
| 資料版本與來源 | [資料集名稱、版本／快照 ID、取得位置、授權或敏感資料處理方式] |
| 資料切分與前處理 | [train/validation/test 切分、樣本數、清理、標準化、增強、排除規則] |
| 方法／系統流程 | [用編號步驟或清楚文字描述模型、演算法、儀器或資料管線；說明本週相對 baseline 的改動] |
| 重要設定 | [設定檔路徑、關鍵超參數、版本、硬體／軟體環境；解釋各設定的角色] |
| 執行程序 | [可重現的主要步驟或命令；不要只貼長指令，說明每一步目的] |
| 評估指標與判定規則 | [指標、計算資料切分、較佳／成功判定；統計檢定或信賴區間（若適用）] |
| 偏差、例外與限制 | [與原計畫不同之處、資料異常、失敗條件、尚未完成的重複與可重現性限制] |
| 佐證位置 | [commit SHA、config、notebook、輸出資料夾、圖表；只作佐證，不取代上述說明] |

### 4.3 方法變更紀錄（相對於前一週或 baseline）

| 變更 | 原因 | 可能影響 | 是否需要重跑／補驗證 |
| --- | --- | --- | --- |
| [例如：learning rate 由 1e-4 改為 1e-3] | [原因] | [可能影響] | [是／否；說明] |

## 5. 結果與可追溯證據

| 項目 | 結果 | 相對基準 | 證據位置 | 狀態與注意事項 |
| --- | --- | --- | --- | --- |
| [指標／產出] | [數值、圖表摘要或檔案] | [提升／下降多少；或不適用] | [commit、路徑、圖表連結] | [正式／初步；異常或限制] |

## 6. 解讀、限制與下一個技術判斷

- **可支持的結論：** [結果支持什麼；務必對應資料、方法與指標。]
- **不可宣稱或尚待驗證：** [例如只跑一個 seed、未在 test set 驗證、樣本數不足。]
- **失敗／異常與可能原因：** [列出至少一項重要觀察，或寫「本週未觀察到重大異常」。]
- **下一個技術判斷：** [根據結果，下一步要保留、修改、淘汰或比較什麼。]

## 7. 風險、阻礙與需要協助

| 風險或阻礙 | 影響 | 已採取／計畫措施 | 需要的協助 | 預計解除日期 |
| --- | --- | --- | --- | --- |
| [事項；若無寫「本週無重大風險」] | [高／中／低及原因] | [具體行動] | [具體問題或「無」] | [YYYY-MM-DD] |

## 8. 下週計畫與驗收標準

| 優先級 | 工作 | 可驗收交付物 | 截止日 | 驗收標準 |
| --- | --- | --- | --- |
| P0 | [最重要工作] | [檔案、結果、PR、圖表等] | [YYYY-MM-DD] | [可客觀檢查的條件] |
| P1 | [次要工作] | [檔案、結果、PR、圖表等] | [YYYY-MM-DD] | [可客觀檢查的條件] |

## 9. 給教授的具體問題

1. [可回答、可決策的問題；附上必要背景與希望回覆期限。]
2. [若無問題，寫「本週無；下週將依計畫執行。」]

## 10. 教授回饋與修正紀錄

| 日期 | 教授回饋 | 學生回應／採取動作 | 狀態 |
| --- | --- | --- | --- |
| [YYYY-MM-DD] | [待教授填寫] | [收到後填寫] | [待處理／完成] |

---

## English Version

## 1. Metadata

| Field | Content |
| --- | --- |
| Student | [Name] |
| Week | [YYYY-Www; ISO week, Monday through Sunday] |
| Date range | [YYYY-MM-DD] to [YYYY-MM-DD] |
| Research topic | [Research topic to which this week's work belongs] |
| Overall status | [🟢 On track / 🟡 At risk / 🔴 Blocked] |
| Working branch / baseline commit | [branch name; short SHA] |
| Report last updated | [YYYY-MM-DD] |

## 2. Executive Summary

- **This week's research question or focus:** [State the question to answer or key work to complete in one or two sentences.]
- **Most important result:** [Quantitative result or concrete output; if none, explain why.]
- **Progress assessment:** [On track, delayed, or blocked versus plan; give the primary reason.]
- **Decision or help needed from supervisor:** [Specific question, information, or decision deadline; write “None this week” if none.]

## 3. Objectives and Completion

| Objective | Completion | Status | Completed work or reason for deviation | Evidence |
| --- | ---: | --- | --- | --- |
| [Verifiable objective 1] | [%] | [Complete / In progress / Blocked] | [What was done; if unfinished, why it deviated] | [commit, file, figure, or output link] |
| [Verifiable objective 2] | [%] | [Complete / In progress / Blocked] | [What was done; if unfinished, why it deviated] | [commit, file, figure, or output link] |

## 4. Experimental Method (Required)

> Even if no experiment was run, state why, what preparation was completed, when it will start, and the intended method. Do not paste only code, commands, or links.

### 4.1 Method Summary

[Write one 4–8 sentence paragraph that lets a supervisor who has not read the code understand the research question/hypothesis, comparison, data, principal procedure, controlled conditions, evaluation metric, and the current scope of interpretation.]

### 4.2 Method Table

| Item | What was actually done this week |
| --- | --- |
| Experiment name / research question | [Name and explicit question to compare, test, or measure] |
| Hypothesis and expectation | [Expected result and why it is reasonable] |
| Baseline / control | [Comparison basis, control group, or prior version] |
| Treatment / factors changed | [Independent variable(s) changed this week and their levels] |
| Conditions held fixed | [Model, data split, training steps, instrument conditions, and other factors that must not vary across groups] |
| Experimental unit and repetition | [Unit of observation, samples per group, repetitions, random seeds; explain any incomplete coverage] |
| Data version and source | [Dataset name, version/snapshot ID, source location, license or sensitive-data handling] |
| Split and preprocessing | [Train/validation/test split, counts, cleaning, normalization, augmentation, exclusion rules] |
| Method / system procedure | [Numbered steps or clear prose for the model, algorithm, instrument, or data pipeline; state changes from baseline] |
| Material settings | [Config path, key hyperparameters, versions, hardware/software environment; explain each setting's role] |
| Execution procedure | [Reproducible primary steps or commands; explain the purpose of each step rather than pasting a long command alone] |
| Metrics and decision rule | [Metrics, data split used, rule for better/success; statistical test or confidence interval where applicable] |
| Deviations, exceptions, and limitations | [Departure from plan, data anomaly, failure condition, incomplete repetitions, and reproducibility limits] |
| Evidence locations | [Commit SHA, config, notebook, output folder, figures; supporting evidence only, not a replacement for the description] |

### 4.3 Method Change Log (relative to prior week or baseline)

| Change | Reason | Possible impact | Rerun / further validation needed? |
| --- | --- | --- | --- |
| [For example, learning rate changed from 1e-4 to 1e-3] | [Reason] | [Possible impact] | [Yes / No; explain] |

## 5. Results and Traceable Evidence

| Item | Result | Relative to baseline | Evidence location | Status and caveats |
| --- | --- | --- | --- | --- |
| [Metric/output] | [Value, figure summary, or file] | [Amount improved/declined, or N/A] | [commit, path, figure link] | [Final/preliminary; anomaly or limitation] |

## 6. Interpretation, Limitations, and Next Technical Decision

- **Supported conclusion:** [What the result supports; tie it to the data, method, and metric.]
- **What cannot yet be claimed / needs verification:** [For example, only one seed, no test-set evaluation, insufficient sample size.]
- **Failure/anomaly and plausible cause:** [State at least one material observation, or “No material anomaly observed this week.”]
- **Next technical decision:** [Based on the result, what to retain, change, eliminate, or compare next.]

## 7. Risks, Blockers, and Help Needed

| Risk or blocker | Impact | Action taken / planned | Help needed | Expected resolution date |
| --- | --- | --- | --- | --- |
| [Item; write “No material risk this week” if none] | [High/Medium/Low and why] | [Concrete action] | [Specific question or “None”] | [YYYY-MM-DD] |

## 8. Next-week Plan and Acceptance Criteria

| Priority | Work | Verifiable deliverable | Due date | Acceptance criterion |
| --- | --- | --- | --- |
| P0 | [Most important work] | [File, result, PR, figure, etc.] | [YYYY-MM-DD] | [Objectively checkable condition] |
| P1 | [Secondary work] | [File, result, PR, figure, etc.] | [YYYY-MM-DD] | [Objectively checkable condition] |

## 9. Specific Questions for the Supervisor

1. [A question that can be answered or decided; add needed context and requested response date.]
2. [If none, write “None this week; I will proceed as planned next week.”]

## 10. Supervisor Feedback and Correction Log

| Date | Supervisor feedback | Student response / action | Status |
| --- | --- | --- | --- |
| [YYYY-MM-DD] | [To be completed by supervisor] | [Complete after feedback] | [Open / Done] |
