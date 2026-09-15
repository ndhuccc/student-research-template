# 論文與文獻管理規範

## 中文說明

此目錄存放文獻筆記、引用資料、論文草稿與修訂紀錄。目標是讓教授能理解學生如何從文獻形成研究問題、如何追蹤論文版本，以及任何結論引用了哪些來源。

### 建議結構與命名

~~~text
papers/
├─ README.md
├─ literature-notes/
│  └─ 2024-smith-retrieval-augmentation.md
├─ drafts/
│  └─ image-classification-study/
│     ├─ README.md
│     ├─ manuscript.tex 或 manuscript.md
│     ├─ references.bib
│     └─ figures/
└─ references/
   └─ reading-list.md
~~~

- 文獻筆記命名：**YYYY-firstauthor-short-title.md**，例如 **2024-smith-retrieval-augmentation.md**。
- 論文草稿以 **paper-slug/** 為資料夾，例如 **drafts/image-classification-study/**。
- 優先保存可比較差異的原始稿，例如 Markdown、LaTeX、BibTeX 與圖表來源；PDF 可作為交付品，但不能是唯一來源。
- Word 文件若必須使用，檔名應包含日期與版本，例如 **2026-09-18_manuscript_v03.docx**，並在草稿 README 中說明其對應版本。

### 文獻筆記必要內容與範例

每一份文獻筆記至少包含完整引用、研究問題、主要貢獻、方法與資料、關鍵證據、限制、與自己研究的關聯，以及可延伸的問題。

~~~markdown
# Smith et al. 2024 — Retrieval Augmentation

## Citation

Smith, A., et al. (2024). Retrieval Augmentation for Reliable Generation. Conference Name.

## 研究問題

如何降低生成模型在專業問答中的無依據回答？

## 主要貢獻

- 提出檢索與生成交替的 pipeline。
- 在三個 benchmark 上改善 factuality。

## 方法與證據

- 資料：公開 QA benchmark。
- 指標：exact match、citation precision、human factuality score。
- 關鍵結果：加入 retrieval 後 citation precision 提升 8 個百分點。

## 限制

- 對低資源語言沒有充分評估。
- 對檢索失敗的錯誤傳遞分析不足。

## 與本研究的關聯

可作為 projects/retrieval-baseline/ 的 baseline 設計參考。

## 待追問問題

若資料庫更新頻率提高，retrieval cache 如何失效與重建？
~~~

### 論文草稿 README 必要內容

每個草稿資料夾的 README 應說明：

1. 論文題目、目標投稿場域與目前狀態。
2. 主稿來源檔、PDF 交付檔、引用資料與圖表來源的位置。
3. 目前版本對應的 branch、commit、技術報告與資料版本。
4. 作者分工、審查待辦、已知缺口與下一個里程碑。
5. 建置或輸出 PDF 的命令。

### 著作權與研究倫理

- 不要任意提交無授權的全文論文、付費資料庫下載內容或受限制附件。
- 可保存自己的文獻筆記、合法取得的書目資料與連結。
- 涉及人類受試者、病歷、問卷或其他敏感研究材料時，依教授、IRB 與機構規定管理存取權。

---

# Papers and Literature Management Guide

## English Guide

This directory stores literature notes, citation material, manuscript drafts, and revision records. Its purpose is to let a supervisor understand how literature informs the research question, how manuscript versions are tracked, and which sources support each claim.

### Recommended Structure and Naming

~~~text
papers/
├─ README.md
├─ literature-notes/
├─ drafts/
│  └─ paper-slug/
└─ references/
~~~

- Name literature notes **YYYY-firstauthor-short-title.md**, for example **2024-smith-retrieval-augmentation.md**.
- Store a manuscript in a **paper-slug/** folder, for example **drafts/image-classification-study/**.
- Prefer diff-friendly source formats such as Markdown, LaTeX, BibTeX, and source figures. A PDF may be a deliverable but should not be the only source.
- If Word is required, include date and version in the filename, for example **2026-09-18_manuscript_v03.docx**, and explain the corresponding version in the draft README.

### Required Literature-Note Content and Example

Every literature note must include full citation, research question, main contribution, method and data, key evidence, limitations, relevance to the student's work, and follow-up questions.

~~~markdown
# Smith et al. 2024 — Retrieval Augmentation

## Citation

Smith, A., et al. (2024). Retrieval Augmentation for Reliable Generation. Conference Name.

## Research Question

How can unsupported answers in domain question answering be reduced?

## Main Contributions

- Proposes an alternating retrieval-and-generation pipeline.
- Improves factuality on three benchmarks.

## Method and Evidence

- Data: public QA benchmarks.
- Metrics: exact match, citation precision, and human factuality score.
- Key result: retrieval improved citation precision by eight percentage points.

## Limitations

- Low-resource languages were not sufficiently evaluated.
- Error propagation after retrieval failure was underexplored.

## Relevance to This Research

Useful as a baseline design for projects/retrieval-baseline/.

## Follow-up Question

How should retrieval cache invalidation and rebuilding work when the database changes frequently?
~~~

### Required Manuscript-README Content

Each manuscript folder README should state:

1. Paper title, intended venue, and current status.
2. Locations of manuscript source, delivered PDF, bibliography, and source figures.
3. The branch, commit, technical reports, and data version behind the current version.
4. Author responsibilities, review tasks, known gaps, and the next milestone.
5. The command used to build or export the PDF.

### Copyright and Research Ethics

- Do not commit unauthorized full-text papers, paywalled database downloads, or restricted supplementary materials.
- Personal literature notes, legally obtained bibliographic records, and links are appropriate.
- Manage human-subject data, medical records, survey responses, and other sensitive research material according to supervisor, IRB, and institutional policy.
