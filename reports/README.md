# 技術報告規範

## 中文說明

此目錄存放可供教授審查、可供未來自己或他人重現的技術報告。技術報告應把研究問題、方法、證據、結論與限制連結起來；它不是只貼圖或只列結果的簡報備忘錄。

### 命名與位置規則

- 技術報告位置：**reports/YYYY/**。
- Markdown 原始檔命名：**YYYY-MM-DD_<project-slug>_<report-type>_vNN.md**。
- 可選擇將同版的 PDF 放在相同目錄，使用相同檔名與 **.pdf** 副檔名。
- **project-slug** 使用小寫英文與連字號，例如 **image-classification**。
- **report-type** 使用：**experiment**、**design**、**reproduction**、**milestone** 或 **technical**。
- **vNN** 為兩位數版本，例如 **v01**、**v02**。重大結論修訂必須遞增版本號，不使用 final-final 或新版 2 等模糊名稱。

範例：

~~~text
reports/2026/2026-09-18_image-classification_experiment_v01.md
reports/2026/2026-09-18_image-classification_experiment_v01.pdf
~~~

### 必要內容格式

每一份技術報告至少包含：

1. **基本資料**：標題、作者、日期、報告類型、專案、狀態、branch 與 commit。
2. **摘要與研究問題**：說明為何做這件事，以及最重要的可驗證結論。
3. **材料與方法**：資料版本、軟硬體環境、方法、設定檔與主要命令。
4. **結果與證據**：表格、圖表、輸出檔案及其位置；不可只描述結論。
5. **分析與限制**：區分觀察、解釋與尚未證實的推論。
6. **可重現性**：提供重跑步驟、預期輸出、資料取得條件與已知差異。
7. **決策、待辦與審查需求**：說明由結果導出的決策、未解問題與需要教授回饋的事項。
8. **參考資料與變更紀錄**：列出資料、文獻或相關 issue／週報。

### 詳細範例

~~~markdown
---
title: Learning-rate sweep for image classification
authors: Hsiao-Hui Hsu
date: 2026-09-18
report_type: experiment
project: image-classification
status: draft
branch: exp/learning-rate
code_commit: abc1234
data_manifest: data/manifest.csv
---

# Learning-rate sweep for image classification

## 摘要

在 CIFAR-10 v1 上比較三個 learning rate。seed 42 的結果顯示 0.001 優於 0.0001，但尚未完成多 seed 驗證，因此此結論暫定。

## 研究問題與成功標準

問題：在固定模型與資料切分下，哪個 learning rate 可提高 validation accuracy，且不造成訓練不穩定？

成功標準：每個設定完成五個 random seed，回報平均值、標準差與 macro F1。

## 材料與方法

| 項目 | 內容 |
| --- | --- |
| 資料 | cifar10-v1；見 data/manifest.csv |
| 程式 | commit abc1234 |
| 設定 | projects/image-classification/configs/exp-001-lr-sweep.yaml |
| 執行 | python scripts/train.py --config configs/exp-001-lr-sweep.yaml --seed 42 |
| 環境 | Python 3.11；PyTorch 2.4；CUDA 12.1 |

## 結果

| Learning rate | Seed | Validation accuracy | Macro F1 | 備註 |
| --- | --- | --- | --- | --- |
| 0.0001 | 42 | 0.801 | 0.794 | 收斂緩慢 |
| 0.001 | 42 | 0.842 | 0.837 | 目前最佳 |
| 0.01 | 42 | N/A | N/A | 未收斂 |

圖表：reports/2026/figures/lr-sweep-v01.png
完整結果：reports/2026/results/lr-sweep-v01.csv

## 分析與限制

觀察：0.001 在單一 seed 下最高；0.01 未收斂。

限制：每個設定只有一個 seed，結果無法估計穩定性或統計差異。

決策：先完成五個 seed 的比較，再決定是否納入 scheduler 實驗。

## 可重現性

1. 依 projects/image-classification/README.md 安裝環境。
2. 取得 data/manifest.csv 指定的資料版本。
3. 執行本報告中的命令；預期輸出位於 reports/2026/results/。

## 教授審查需求

請確認應先完成多 seed 驗證，或先擴充 scheduler 實驗。

## 變更紀錄

- v01：初版，包含 seed 42 的 learning-rate sweep。
~~~

---

# Technical Report Guide

## English Guide

This directory stores technical reports that a supervisor can review and that the author or another researcher can reproduce later. A technical report must connect the research question, method, evidence, conclusion, and limitation. It is not merely a slide-note with figures or results.

### Naming and Location Rules

- Store technical reports in **reports/YYYY/**.
- Name Markdown sources **YYYY-MM-DD_<project-slug>_<report-type>_vNN.md**.
- An optional PDF of the same revision may use the identical base name with the **.pdf** extension.
- Use lowercase letters and hyphens for **project-slug**, for example **image-classification**.
- Use one of these values for **report-type**: **experiment**, **design**, **reproduction**, **milestone**, or **technical**.
- Use a two-digit **vNN** revision such as **v01** or **v02**. Increment the version when a material conclusion changes; do not use ambiguous names such as final-final.

Example:

~~~text
reports/2026/2026-09-18_image-classification_experiment_v01.md
reports/2026/2026-09-18_image-classification_experiment_v01.pdf
~~~

### Required Report Structure

Each technical report must include:

1. **Metadata**: title, author, date, report type, project, status, branch, and commit.
2. **Abstract and research question**: why the work was done and the most important verifiable conclusion.
3. **Materials and methods**: data version, software or hardware environment, method, configuration, and primary command.
4. **Results and evidence**: tables, figures, output files, and their locations; conclusions alone are insufficient.
5. **Analysis and limitations**: separate observations, interpretations, and unverified inferences.
6. **Reproducibility**: rerun steps, expected outputs, data-access conditions, and known differences.
7. **Decisions, next work, and review request**: actions justified by the result, open issues, and specific supervisor feedback needed.
8. **References and change log**: relevant data, literature, issues, or weekly reports.

### Detailed Example

~~~markdown
---
title: Learning-rate sweep for image classification
authors: Hsiao-Hui Hsu
date: 2026-09-18
report_type: experiment
project: image-classification
status: draft
branch: exp/learning-rate
code_commit: abc1234
data_manifest: data/manifest.csv
---

# Learning-rate sweep for image classification

## Abstract

Three learning rates were compared on CIFAR-10 v1. With seed 42, 0.001 outperformed 0.0001, but multi-seed validation is incomplete and the conclusion remains provisional.

## Research Question and Success Criterion

Question: with a fixed model and data split, which learning rate improves validation accuracy without unstable training?

Success criterion: complete five random seeds per setting and report mean, standard deviation, and macro F1.

## Materials and Methods

| Item | Value |
| --- | --- |
| Data | cifar10-v1; see data/manifest.csv |
| Code | commit abc1234 |
| Configuration | projects/image-classification/configs/exp-001-lr-sweep.yaml |
| Command | python scripts/train.py --config configs/exp-001-lr-sweep.yaml --seed 42 |
| Environment | Python 3.11; PyTorch 2.4; CUDA 12.1 |

## Results

| Learning rate | Seed | Validation accuracy | Macro F1 | Note |
| --- | --- | --- | --- | --- |
| 0.0001 | 42 | 0.801 | 0.794 | Slow convergence |
| 0.001 | 42 | 0.842 | 0.837 | Best so far |
| 0.01 | 42 | N/A | N/A | Did not converge |

Figure: reports/2026/figures/lr-sweep-v01.png
Full results: reports/2026/results/lr-sweep-v01.csv

## Analysis and Limitations

Observation: 0.001 was highest for one seed, while 0.01 did not converge.

Limitation: each setting has only one seed, so stability and statistical differences cannot yet be assessed.

Decision: complete five-seed comparisons before deciding whether to add scheduler experiments.

## Reproducibility

1. Install the environment described in projects/image-classification/README.md.
2. Obtain the data version listed in data/manifest.csv.
3. Run the command in this report. Expected outputs are under reports/2026/results/.

## Supervisor Review Request

Please advise whether multi-seed validation or scheduler expansion should be prioritized.

## Change Log

- v01: initial learning-rate sweep with seed 42.
~~~
