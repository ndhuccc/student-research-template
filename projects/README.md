# 研究專案目錄規範

## 中文說明

此目錄存放研究專案的程式碼、設定、測試、執行腳本與專案說明。每個子目錄是一般資料夾，不是另一個 Git repository；學生的整體研究紀錄應保留在同一份學生 repo 中，讓教授可以從週報追到程式、設定與結果。

### 命名與位置規則

- 專案位置：**projects/<project-slug>/**。
- **project-slug** 使用小寫英文與連字號，例如 **image-classification**、**retrieval-baseline**。
- 不使用空格、中文名稱、final、test2 或 temp 等無法理解的資料夾名稱。
- 不要在任何子專案中執行 git init；這會形成 nested repository，破壞學生 repo 的完整追蹤。

### 建議結構

~~~text
projects/
└─ image-classification/
   ├─ README.md
   ├─ pyproject.toml 或 requirements.txt
   ├─ src/
   │  └─ package_name/
   ├─ scripts/
   │  ├─ train.py
   │  ├─ evaluate.py
   │  └─ reproduce.py
   ├─ configs/
   │  ├─ exp-001-baseline.yaml
   │  └─ exp-002-lr-sweep.yaml
   ├─ tests/
   ├─ docs/
   └─ assets/
~~~

### 每個專案必備文件與內容格式

1. **README.md**：專案名稱、研究範圍、資料需求、環境、安裝、主要入口、執行指令、測試、輸出位置、限制與維護者。
2. **pyproject.toml 或 requirements.txt**：可重現的依賴版本；不要同時維護兩份互相矛盾的套件清單。
3. **configs/**：實驗設定檔。檔名用 **exp-NNN-short-description.yaml**，並在報告中引用完整路徑。
4. **scripts/**：可從命令列執行的訓練、評估、資料前處理與重現腳本。每個腳本要有 --help 或 README 說明輸入與輸出。
5. **tests/**：單元測試、資料檢查或 smoke test。至少提供一個快速測試，讓教授能確認基本流程沒有壞掉。
6. **docs/**：設計決策、資料流程、模型架構或 API 說明。將長篇設計文件與程式碼分開。
7. **assets/**：小型、可合法公開的示意圖或 sample；不可存放大型 raw data、模型權重或秘密。

### 專案 README 詳細範例

~~~markdown
# Image Classification

## 研究範圍

比較不同 learning rate 與 scheduler 對 CIFAR-10 分類效能與穩定性的影響。

## 資料需求

- 資料識別：cifar10-v1，詳見 data/manifest.csv。
- 原始資料不存入 Git；依 data/README.md 的程序取得。

## 環境

- Python 3.11
- PyTorch 2.4
- 依賴：pip install -r requirements.txt

## 主要入口

- 訓練：scripts/train.py
- 評估：scripts/evaluate.py
- 重現 baseline：scripts/reproduce.py

## 執行範例

python scripts/train.py --config configs/exp-001-baseline.yaml --seed 42
python scripts/evaluate.py --checkpoint <local-checkpoint-path>

## 測試

python -m pytest tests -q

## 輸出

- 結果表：reports/2026/results/
- 圖表：reports/2026/figures/
- 技術報告：reports/2026/

## 限制與維護者

- GPU 訓練約需 4 小時；CPU 僅供 smoke test。
- 維護者：<學生姓名>；教授審查請見 weekly-reports/。
~~~

### 撰寫原則

- 程式碼、設定、週報與技術報告必須能互相連結。
- 任何會改變結論的參數都應放進 config，而不是只藏在程式碼內。
- 產生檔案、cache、local checkpoint 與大型輸出應由 .gitignore 排除；報告中記錄其位置與生成方式。
- 實驗失敗也應保留設定與摘要，並在週報或技術報告中說明原因。

---

# Research Project Directory Guide

## English Guide

This directory stores research source code, configurations, tests, executable scripts, and project documentation. Each subdirectory is an ordinary folder rather than another Git repository. The complete student repository should preserve links from weekly reports to code, configurations, and results.

### Naming and Location Rules

- Store a project at **projects/<project-slug>/**.
- Use lowercase letters and hyphens for **project-slug**, such as **image-classification** or **retrieval-baseline**.
- Avoid spaces, non-descriptive names, and folders such as final, test2, or temp.
- Do not run git init inside a project. It would create a nested repository and break unified history.

### Recommended Structure

~~~text
projects/
└─ image-classification/
   ├─ README.md
   ├─ pyproject.toml or requirements.txt
   ├─ src/
   ├─ scripts/
   ├─ configs/
   ├─ tests/
   ├─ docs/
   └─ assets/
~~~

### Required Files and Content

1. **README.md**: project name, scope, data requirements, environment, installation, entry points, commands, tests, outputs, limitations, and maintainer.
2. **pyproject.toml or requirements.txt**: reproducible dependency versions. Do not maintain two contradictory package lists.
3. **configs/**: experiment configurations. Name them **exp-NNN-short-description.yaml** and cite the full path in reports.
4. **scripts/**: command-line training, evaluation, preprocessing, and reproduction scripts. Each script needs --help or README documentation for inputs and outputs.
5. **tests/**: unit tests, data checks, or smoke tests. Provide at least one quick test for basic verification.
6. **docs/**: design decisions, data flow, model architecture, or API notes. Keep long design documents separate from code.
7. **assets/**: small, legally shareable diagrams or samples; never large raw data, model weights, or secrets.

### Project README Example

~~~markdown
# Image Classification

## Scope

Compare the effect of learning rates and schedulers on CIFAR-10 classification performance and stability.

## Data Requirement

- Data identifier: cifar10-v1; see data/manifest.csv.
- Raw data is not committed to Git. Obtain it according to data/README.md.

## Environment

- Python 3.11
- PyTorch 2.4
- Install with: pip install -r requirements.txt

## Entry Points

- Training: scripts/train.py
- Evaluation: scripts/evaluate.py
- Baseline reproduction: scripts/reproduce.py

## Example Commands

python scripts/train.py --config configs/exp-001-baseline.yaml --seed 42
python scripts/evaluate.py --checkpoint <local-checkpoint-path>

## Tests

python -m pytest tests -q

## Outputs

- Result tables: reports/2026/results/
- Figures: reports/2026/figures/
- Technical reports: reports/2026/

## Limitations and Maintainer

- GPU training takes about four hours; CPU is for smoke tests only.
- Maintainer: <student-name>; supervisor review is recorded in weekly-reports/.
~~~

### Writing Principles

- Code, configurations, weekly reports, and technical reports must link to one another.
- Any parameter that can change a conclusion belongs in a configuration file, not only inside code.
- Generated files, caches, local checkpoints, and large outputs should be ignored by .gitignore. Reports must describe their location and how to regenerate them.
- Keep configurations and concise summaries for failed experiments, and explain the failure in a weekly or technical report.
