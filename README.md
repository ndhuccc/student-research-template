# 學生研究 Repository 樣板

## 中文說明

這是一位學生一份的研究 Repository 樣板，用來保存研究程式碼、週報、實驗紀錄、論文草稿與技術報告。每位學生應透過 GitHub 的 **Use this template** 建立自己的 **private repository**，再將指導教授加入 collaborator 或 reviewer。

### 開始使用

1. 使用此樣板建立 private repository，名稱建議為 **學生識別-research**，例如 **hsiao-hui-research**。
2. 將 repository clone 到自己的研究工作電腦。
3. 依專案實際需求補上安裝、執行與測試指令。
4. 每週新增一份週報；重要實驗或設計決策都應有可追溯的 commit。
5. 請教授審查前，先 push 最新 branch 或 main。

~~~powershell
git status --short --branch
git pull --ff-only
# 依本研究專案的 README 安裝與執行
git add <需要提交的檔案>
git diff --cached --check
git commit -m "docs: add weekly report for 2026-W38"
git push
~~~

### 目錄導覽

| 目錄 | 用途 | 必要規則 |
| --- | --- | --- |
| **weekly-reports/** | 每週研究週報。 | 使用 **YYYY/YYYY-Www.md**；每週一份正式報告。 |
| **projects/** | 程式碼、設定、測試與可重現腳本。 | 子目錄不可再次執行 git init。 |
| **data/** | 資料說明、manifest、schema、checksum 與可合法分享的 sample。 | 不提交受限原始資料、個資或 live database。 |
| **notebooks/** | 探索性分析 notebook。 | 正式結果仍應能以 scripts 重跑。 |
| **papers/** | 文獻筆記、引用資料與論文草稿。 | 注意全文論文與附件的著作權。 |
| **reports/** | 技術報告、實驗摘要、設計紀錄與成果圖表。 | 使用日期、專案、類型與版本的命名規則。 |

### 可重現性與協作規則

- 每個可報告的實驗應記錄資料版本、branch、commit、設定檔、random seed、主要命令與輸出位置。
- **main** 應保持可讀且盡可能可執行；重大工作請使用 **exp/** 或 **feature/** branch。
- 一個 commit 應表達一個可理解的變更，例如 **exp: compare learning rates**。
- 絕不提交 API key、密碼、token、個資、未核准原始資料、巨大模型權重或大型資料庫檔案。
- 不要在 **projects/** 下建立 nested repository。若子專案需要獨立成 repo，請先和教授確認邊界與 review 流程。

---

# Student Research Repository Template

## English Guide

This is a one-student-per-repository template for research code, weekly reports, experiment records, paper drafts, and technical reports. Each student should use GitHub **Use this template** to create an individual **private repository**, then add the supervisor as a collaborator or reviewer.

### Getting Started

1. Create a private repository from this template. Use a name such as **student-id-research** or **hsiao-hui-research**.
2. Clone the repository to the local research workspace.
3. Replace generic setup, execution, and test instructions with project-specific commands.
4. Add one formal weekly report every reporting period and commit important experimental or design decisions.
5. Push the latest branch or main before requesting supervisor review.

~~~powershell
git status --short --branch
git pull --ff-only
# Install and run according to this research project's README
git add <files-to-submit>
git diff --cached --check
git commit -m "docs: add weekly report for 2026-W38"
git push
~~~

### Directory Guide

| Directory | Purpose | Required rule |
| --- | --- | --- |
| **weekly-reports/** | Formal weekly research reports. | Use **YYYY/YYYY-Www.md**; submit one report per week. |
| **projects/** | Source code, configurations, tests, and reproducible scripts. | Do not run git init inside a project subdirectory. |
| **data/** | Data documentation, manifests, schemas, checksums, and safe samples. | Do not commit restricted raw data, personal data, or live databases. |
| **notebooks/** | Exploratory notebooks. | Reportable results must still be reproducible from scripts. |
| **papers/** | Literature notes, citations, and manuscript drafts. | Respect copyright for full papers and supplementary files. |
| **reports/** | Technical reports, experiment summaries, design records, and figures. | Use date, project, report type, and version in the file name. |

### Reproducibility and Collaboration Rules

- Every reportable experiment should record data version, branch, commit, configuration, random seed, primary command, and output location.
- Keep **main** readable and as runnable as practical. Use **exp/** or **feature/** branches for substantial work.
- One commit should express one understandable change, for example **exp: compare learning rates**.
- Never commit API keys, passwords, tokens, personal data, unapproved raw data, large model weights, or live database files.
- Do not create nested repositories inside **projects/**. Discuss repository boundaries and review workflow with the supervisor before splitting a subproject into a separate repository.
