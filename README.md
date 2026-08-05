# study-master

研究論文のPDFと、論文を再読・実装・発展研究に使うための議論ノートを管理するリポジトリです。

## ディレクトリ構成

```text
papers/                         # 手元で管理する論文PDF
├─ 01_AI/
│  ├─ 01_LLM/
│  ├─ 02_RAG/
│  └─ 03_Agent/
├─ 02_Systems/
│  ├─ 01_Distributed/
│  └─ 02_Database/
├─ 03_Finance/
│  ├─ 01_Derivatives/
│  └─ 02_Fixed_Income/
└─ 99_Others/

notes/                          # 議論・要約・批判的検討
└─ 03_Finance/
   └─ 01_Derivatives/
```

PDFの命名規則は `YYYY_FirstAuthor_ShortTitle.pdf` とします。例: `2009_Carr_VarianceRiskPremiums.pdf`。

## ノートの収録項目

各ノートには、必ず次の項目を収録します。

- 論文名、著者、掲載誌、原論文リンク
- 問題意識と結論の短い要約
- 中核となるアイデアと数式
- データと実証設計
- 主要結果
- 解釈上の注意、限界、批判点
- 次に検討すべき問い

## 論文一覧

| 分野 | 論文 | 著者 | 掲載年 | 一言でいうと |
|---|---|---|---:|---|
| ボラティリティ・デリバティブ | [Variance Risk Premiums](notes/03_Finance/01_Derivatives/2009_Carr_VarianceRiskPremiums.md) | Peter Carr, Liuren Wu | 2009 | オプションから合成した分散スワップ・レートと実現分散を比較し、市場分散の保険料を直接測定する |

## この論文から伸びる研究テーマ

- Variance risk premium と将来株式リターン
- 指数分散と個別株分散の差、および dispersion trading
- VIX、variance swap、volatility swap の関係
- ジャンプ、左側テール、vol-of-vol の価格
- 分散リスク・プレミアムの期間構造
- ショート・ボラティリティ戦略のテールリスク

## 表記上の注意

Variance risk premium は文献によって符号が逆です。Carr and Wu (2009) は

$$
RP_{t,T}=RV_{t,T}-SW_{t,T}
$$

と定義するため、分散ロングが保険料を支払う通常の状態では負になります。近年よく使われる

$$
VRP_t=SW_{t,T}-E_t^P[RV_{t,T}]
$$

という定義では、同じ現象が正の値になります。各ノートでは、必ず採用した符号規約を明示します。
