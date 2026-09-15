# 週報規範

## 中文說明

週報是教授掌握研究進度、判斷實驗可信度、辨識風險並給予具體回饋的主要依據。週報應記錄可驗證的事實與研究判斷，不是工作流水帳；即使本週沒有得到正向結果，也要如實交代負面結果、失敗原因與下一步決策。

### 命名與位置規則

- 每週只建立一份正式週報；若同時進行多個子專案，將各子專案進度放在同一份週報中。
- 檔案位置：**weekly-reports/YYYY/YYYY-Www.md**。
- **YYYY** 是 ISO 週次所屬年度，**Www** 是兩位數 ISO 週次。
- 例如 2026 年第 38 週：**weekly-reports/2026/2026-W38.md**。
- 不要使用空格、中文檔名或含糊名稱，例如 **new-report.md**、**week2-final-final.md**。
- 送出後若需修正，保留原報告與 Git 歷史；在文件末尾新增「修正紀錄」，說明日期、原因與修正內容。

### 必要內容與撰寫原則

1. **摘要與整體狀態**：用 3 至 5 個條列說明最重要的完成事項、主要結論與目前狀態。
2. **本週目標與完成度**：每個目標要有可驗證的完成標準；標示完成、部分完成、未完成或取消。
3. **完成工作與證據**：連結 commit、branch、程式、設定、圖表、資料 manifest 或報告檔案。不要只寫「完成實驗」。
4. **實驗與分析紀錄**：記錄資料版本、設定檔、命令、random seed、評估指標與輸出位置。
5. **研究判斷**：區分觀察結果、推論與下一步決策；說明結果對研究問題的意義。
6. **問題與風險**：說明 blocker、影響、已嘗試作法、需要的協助與期限。
7. **下週計畫**：寫成可執行、可驗收的工作項目，包含預期交付物與成功標準。
8. **教授審查問題**：提出需要教授決策或回饋的具體問題，避免只寫「請老師指導」。

### 詳細範例

~~~markdown
# Weekly Research Report — 2026-W38

## 基本資料

| 欄位 | 內容 |
| --- | --- |
| 學生 | 徐小惠 |
| 期間 | 2026-09-14 至 2026-09-20 |
| 專案 | image-classification |
| Branch / 最新 commit | exp/learning-rate / abc1234 |
| 週報狀態 | submitted |

## 1. 本週摘要

- 完成 baseline 訓練流程與三組 learning rate 比較。
- learning rate 0.001 的 validation accuracy 為 0.842，優於 0.0001 的 0.801。
- 驗證結果在不同 random seed 間可能波動較大；目前不能宣稱最佳設定。
- 下週將固定資料切分、增加五個 seed，並比較 scheduler 的影響。

## 2. 目標與完成度

| 目標 | 完成標準 | 狀態 | 證據 |
| --- | --- | --- | --- |
| 建立 baseline | 可用單一命令訓練並輸出指標 | 完成 | commit abc1234；projects/image-classification/scripts/train.py |
| 比較 learning rate | 0.0001、0.001、0.01 各完成一次訓練 | 完成 | reports/2026/2026-09-18_image-classification_experiment_v01.md |
| 評估穩定性 | 每組至少五個 seed | 未完成 | 只完成 seed 42；原因見第 5 節 |

## 3. 完成工作與可追溯證據

- Training script：commit abc1234。
- 實驗設定：projects/image-classification/configs/exp-001-lr-sweep.yaml。
- 結果表：reports/2026/results/lr-sweep-v01.csv。
- 主要圖表：reports/2026/figures/lr-sweep-v01.png。

## 4. 實驗與分析

| 項目 | 內容 |
| --- | --- |
| 資料版本 | data/manifest.csv 中 dataset-id=cifar10-v1 |
| 程式 commit | abc1234 |
| 設定檔 | configs/exp-001-lr-sweep.yaml |
| 執行命令 | python scripts/train.py --config configs/exp-001-lr-sweep.yaml --seed 42 |
| 評估指標 | validation accuracy、macro F1 |
| 主要結果 | learning rate 0.001: accuracy 0.842；0.0001: 0.801；0.01: 未收斂 |

## 5. 研究判斷、問題與風險

觀察：0.001 在 seed 42 下表現最佳，但 0.01 未收斂。

判斷：目前證據僅來自一個 seed，尚不足以宣稱 0.001 為最佳 learning rate。

風險：訓練需要約 4 小時，五個 seed 的完整 sweep 可能超出下週 GPU 額度。

已嘗試：將 epoch 從 100 降為 30 進行 preliminary run，結果仍需完整訓練確認。

需要協助：請教授確認下週應優先完成五個 seed 的穩定性分析，或先比較 scheduler。

## 6. 下週計畫

| 項目 | 預期交付物 | 成功標準 |
| --- | --- | --- |
| 五個 seed 重複實驗 | 結果 CSV、平均值與標準差圖表 | 每組都有五次完整訓練 |
| 更新技術報告 | experiment report v02 | 可由 README 指令重現 |
| scheduler 比較 | 新設定檔與結果表 | 至少比較 cosine 與 step scheduler |

## 7. 教授審查問題

1. 在 GPU 時間有限時，應先完成五個 seed 的穩定性分析，還是先擴充 scheduler 比較？
2. 目前的 validation accuracy 與 macro F1 是否足以作為主要評估指標？

## 修正紀錄

- 2026-09-21：將資料版本文字由 cifar10-v0 更正為 cifar10-v1；未改變實驗結果。
~~~

---

# Weekly Report Guide

## English Guide

Weekly reports are the primary evidence a supervisor uses to understand progress, assess experimental credibility, identify risks, and provide actionable feedback. A report should record verifiable facts and research reasoning rather than a task diary. Negative results and failed attempts must be reported honestly, together with the cause and the next decision.

### Naming and Location Rules

- Create one formal report per week. When multiple subprojects are active, summarize them in the same weekly report.
- Store reports at **weekly-reports/YYYY/YYYY-Www.md**.
- **YYYY** is the ISO week-year and **Www** is the two-digit ISO week number.
- Example for ISO week 38 of 2026: **weekly-reports/2026/2026-W38.md**.
- Do not use spaces, non-descriptive names, or names such as **new-report.md** or **week2-final-final.md**.
- If a submitted report needs correction, keep the original report and Git history. Add a correction log at the end with the date, reason, and change.

### Required Content and Writing Principles

1. **Executive summary and status**: summarize key deliverables, conclusions, and current state in 3 to 5 bullets.
2. **Objectives and completion**: each objective needs a verifiable completion criterion and an explicit status: complete, partial, incomplete, or cancelled.
3. **Completed work and evidence**: link commits, branches, code, configurations, figures, data manifests, or reports. Do not only state “experiment completed”.
4. **Experiments and analysis**: record data version, configuration, command, random seed, metrics, and output location for each major result.
5. **Research reasoning**: distinguish observations, inferences, and next decisions; explain what the result means for the research question.
6. **Problems and risks**: state the blocker, impact, attempts already made, help needed, and deadline.
7. **Next-week plan**: write executable and reviewable tasks with expected deliverables and success criteria.
8. **Questions for supervisor review**: ask concrete questions that require a decision or feedback. Do not write only “please advise”.

### Detailed Example

~~~markdown
# Weekly Research Report — 2026-W38

## Metadata

| Field | Value |
| --- | --- |
| Student | Hsiao-Hui Hsu |
| Period | 2026-09-14 to 2026-09-20 |
| Project | image-classification |
| Branch / latest commit | exp/learning-rate / abc1234 |
| Report status | submitted |

## 1. Executive Summary

- Completed the baseline training pipeline and compared three learning rates.
- Learning rate 0.001 achieved validation accuracy 0.842, above 0.801 for 0.0001.
- Results may vary across random seeds, so no best setting can yet be claimed.
- Next week: fix the data split, run five seeds, and compare schedulers.

## 2. Objectives and Completion

| Objective | Completion criterion | Status | Evidence |
| --- | --- | --- |
| Build baseline | A single command trains and emits metrics | Complete | commit abc1234; projects/image-classification/scripts/train.py |
| Compare learning rates | Train 0.0001, 0.001, and 0.01 once each | Complete | reports/2026/2026-09-18_image-classification_experiment_v01.md |
| Assess stability | At least five seeds per setting | Incomplete | Only seed 42 completed; see Section 5 |

## 3. Traceable Evidence

- Training script: commit abc1234.
- Configuration: projects/image-classification/configs/exp-001-lr-sweep.yaml.
- Result table: reports/2026/results/lr-sweep-v01.csv.
- Main figure: reports/2026/figures/lr-sweep-v01.png.

## 4. Experiment and Analysis

| Item | Value |
| --- | --- |
| Data version | dataset-id=cifar10-v1 in data/manifest.csv |
| Code commit | abc1234 |
| Configuration | configs/exp-001-lr-sweep.yaml |
| Command | python scripts/train.py --config configs/exp-001-lr-sweep.yaml --seed 42 |
| Metrics | validation accuracy; macro F1 |
| Main result | 0.001: 0.842 accuracy; 0.0001: 0.801; 0.01: did not converge |

## 5. Reasoning, Problems, and Risks

Observation: 0.001 performed best with seed 42, while 0.01 did not converge.

Interpretation: one seed is insufficient evidence to claim that 0.001 is the best learning rate.

Risk: one run takes about four GPU hours; a five-seed sweep may exceed the next week's GPU allocation.

Attempt: reduced epochs from 100 to 30 for a preliminary run. Full training is still required.

Help requested: please advise whether stability analysis or scheduler comparison should take priority next week.

## 6. Next-Week Plan

| Task | Expected deliverable | Success criterion |
| --- | --- | --- |
| Repeat five seeds | Result CSV and mean/standard-deviation figure | Five complete runs per setting |
| Update technical report | Experiment report v02 | Reproducible from README command |
| Compare schedulers | New configuration and result table | Compare cosine and step schedulers |

## 7. Questions for Supervisor Review

1. With limited GPU time, should I prioritize five-seed stability analysis or scheduler comparison?
2. Are validation accuracy and macro F1 sufficient as the primary metrics?

## Correction Log

- 2026-09-21: corrected the data version text from cifar10-v0 to cifar10-v1. Experimental results were unchanged.
~~~
