# 資料管理規範

## 中文說明

此目錄用來記錄資料的來源、版本、授權、存取條件、schema、checksum 與可合法分享的小型 sample。研究資料是否能被追溯，直接影響實驗是否可信；因此資料說明與程式碼一樣重要。

### 允許與禁止存放的內容

可以存放：

- data/README.md 的資料總覽與取得說明。
- data/manifest.csv 的版本清單與來源資訊。
- schema、欄位字典、資料前處理規格與小型匿名 sample。
- checksum、下載腳本或資料建置腳本。

不可存放：

- 個資、受限資料、未授權原始資料、access token、帳密或連線字串。
- live database、巨大 raw data、模型 checkpoint 或可由 script 重建的暫存結果。
- 沒有來源、授權或版本資訊的資料檔案。

### 建議結構與命名

~~~text
data/
├─ README.md
├─ manifest.csv
├─ schemas/
│  └─ image-labels-v1.md
├─ samples/
│  └─ cifar10-v1-sample.csv
└─ scripts/
   └─ build-processed-data.py
~~~

- 資料識別使用 **dataset-slug-vNN**，例如 **cifar10-v1**、**lab-survey-anonymized-v02**。
- 原始受限資料的位置只記錄受控儲存位置的識別名稱，例如 **lab-drive:restricted/cifar10-v1**，不可寫入帶 token 的 URL。
- 每次改變資料內容、標註規則或前處理規格時，建立新版本並更新 manifest。

### manifest.csv 必要欄位

| 欄位 | 說明 |
| --- | --- |
| dataset_id | 唯一版本識別，例如 cifar10-v1。 |
| description | 資料用途與內容摘要。 |
| source | 原始來源或受控儲存識別。 |
| version_date | 資料版本日期。 |
| access_level | public、internal、restricted 或 confidential。 |
| license_or_approval | 授權、IRB 或核准依據。 |
| checksum | 檔案或封存檔 checksum；若不適用請說明。 |
| local_or_controlled_location | 本機相對位置或受控位置識別；不可包含秘密。 |
| preprocessing | 產生此版本的 script 或規格。 |
| notes | 限制、已知偏差或使用注意事項。 |

### 詳細範例

~~~csv
dataset_id,description,source,version_date,access_level,license_or_approval,checksum,local_or_controlled_location,preprocessing,notes
cifar10-v1,CIFAR-10 baseline dataset,https://www.cs.toronto.edu/~kriz/cifar.html,2026-09-14,public,CIFAR-10 terms,SHA256:abc123...,lab-drive:datasets/cifar10-v1,scripts/build-cifar10.py,Use the fixed train-validation split in configs.
lab-survey-anonymized-v02,Anonymized student survey features,lab-drive:restricted/survey-v02,2026-09-15,restricted,IRB-2026-015,SHA256:def456...,lab-drive:restricted/survey-v02,scripts/anonymize-survey.py,Access requires supervisor approval.
~~~

### 資料 README 必要內容

1. 研究中使用哪些資料集及其 dataset_id。
2. 如何合法取得資料、誰可存取、是否需要教授或 IRB 核准。
3. 欄位、標籤、切分與前處理規則。
4. checksum、版本與資料品質限制。
5. 哪個程式或設定會使用該資料版本。

---

# Data Management Guide

## English Guide

This directory records data source, version, license, access condition, schema, checksum, and legally shareable small samples. Data traceability is essential to experimental credibility, so data documentation is as important as code.

### Allowed and Prohibited Content

Allowed:

- A data overview and acquisition guide in data/README.md.
- Version and source information in data/manifest.csv.
- Schemas, data dictionaries, preprocessing specifications, and small anonymized samples.
- Checksums, download scripts, or dataset-build scripts.

Prohibited:

- Personal data, restricted data, unauthorized raw data, access tokens, passwords, or connection strings.
- Live databases, large raw data, model checkpoints, or temporary results that a script can regenerate.
- Data files without source, license, or version information.

### Recommended Structure and Naming

~~~text
data/
├─ README.md
├─ manifest.csv
├─ schemas/
├─ samples/
└─ scripts/
~~~

- Use **dataset-slug-vNN** as the data identifier, for example **cifar10-v1** or **lab-survey-anonymized-v02**.
- For restricted raw data, record only a controlled-storage identifier such as **lab-drive:restricted/cifar10-v1**. Never include a token-bearing URL.
- Create a new version and update the manifest whenever content, labels, or preprocessing rules change.

### Required manifest.csv Fields

| Field | Description |
| --- | --- |
| dataset_id | Unique version identifier, for example cifar10-v1. |
| description | Purpose and concise content summary. |
| source | Original source or controlled-storage identifier. |
| version_date | Dataset version date. |
| access_level | public, internal, restricted, or confidential. |
| license_or_approval | License, IRB, or approval basis. |
| checksum | File or archive checksum; explain if not applicable. |
| local_or_controlled_location | Relative local path or controlled identifier; never a secret. |
| preprocessing | Script or specification that produced the version. |
| notes | Limitations, known biases, or conditions of use. |

### Detailed Example

~~~csv
dataset_id,description,source,version_date,access_level,license_or_approval,checksum,local_or_controlled_location,preprocessing,notes
cifar10-v1,CIFAR-10 baseline dataset,https://www.cs.toronto.edu/~kriz/cifar.html,2026-09-14,public,CIFAR-10 terms,SHA256:abc123...,lab-drive:datasets/cifar10-v1,scripts/build-cifar10.py,Use the fixed train-validation split in configs.
lab-survey-anonymized-v02,Anonymized student survey features,lab-drive:restricted/survey-v02,2026-09-15,restricted,IRB-2026-015,SHA256:def456...,lab-drive:restricted/survey-v02,scripts/anonymize-survey.py,Access requires supervisor approval.
~~~

### Required Data README Content

1. Datasets used by the research and their dataset_id values.
2. Legal acquisition steps, access rights, and whether supervisor or IRB approval is required.
3. Fields, labels, splits, and preprocessing rules.
4. Checksums, versions, and data-quality limitations.
5. Which scripts or configurations use each data version.
