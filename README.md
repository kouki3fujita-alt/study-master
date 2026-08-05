# study-master

論文PDFを大分類・中分類で管理するための最小リポジトリ構成です。

## 構成

```text
papers/
├─ 01_AI/
│  ├─ 01_LLM/
│  ├─ 02_RAG/
│  └─ 03_Agent/
├─ 02_Systems/
│  ├─ 01_Distributed/
│  └─ 02_Database/
└─ 99_Others/
```

## 分類ルール

- 大分類: `papers/<大分類>/`
- 中分類: `papers/<大分類>/<中分類>/`
- 新しい分野は同じ命名ルールで追加

## 命名規則（PDF）

`YYYY_FirstAuthor_ShortTitle.pdf`

例: `2023_Touvron_Llama2.pdf`
