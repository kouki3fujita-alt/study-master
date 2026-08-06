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
| 市場マイクロストラクチャー | [Futures Markets, Regulation and Volatility](notes/03_Finance/01_Derivatives/1994_Bacha_FuturesMarketsRegulationVolatility.md) | Obiyathulla Bacha, Anne Fremault Vila | 1994 | 日経225先物の複数市場への上場を利用し、先物導入・規制・満期日が現物ボラティリティへ与える影響を検証する |
| 金融計量・相関モデル | [Ten Things You Should Know about the Dynamic Conditional Correlation Representation](notes/03_Finance/01_Derivatives/2013_Caporin_TenThingsDCC.md) | Massimiliano Caporin, Michael McAleer | 2013 | DCCを厳密なモデルではなくフィルターとして捉えるべき理由を10の理論的・実証的注意点から整理する |
| 商品・分散リスク | [Variance Risk in Commodity Markets](notes/03_Finance/01_Derivatives/2017_Prokopczuk_VarianceRiskCommodityMarkets.md) | Marcel Prokopczuk, Lazaros Symeonidis, Chardin Wese Simen | 2017（2014年稿） | 21商品市場の合成分散スワップを調べ、商品分散リスクが先物価格リスクとは別のリスクであることを示す |
| 暗号資産・分散リスク | [The Bitcoin VIX and Its Variance Risk Premium](notes/03_Finance/01_Derivatives/2021_Alexander_Imeraj_BitcoinVIX.md) | Carol Alexander, Arben Imeraj | 2021 | DeribitオプションからBitcoin VIXの期間構造とVRPを構築し、ジャンプ誤差と危機時の分散投資便益を検証する |
| 社債・分散リスク | [Synthetic Options and Implied Volatility for the Corporate Bond Market](notes/03_Finance/01_Derivatives/2023_Chen_SyntheticCorporateBondOptions.md) | Steven Shu-Hsiu Chen, Hitesh Doshi, Sang Byung Seo | 2023 | CDXスワップションから社債指数オプションとCBVIXを合成し、社債VRPを測定する |

## この論文から伸びる研究テーマ

- Variance risk premium と将来株式リターン
- 指数分散と個別株分散の差、および dispersion trading
- VIX、variance swap、volatility swap の関係
- ジャンプ、左側テール、vol-of-vol の価格
- 分散リスク・プレミアムの期間構造
- Bitcoin VIX、暗号資産の分散期間構造、危機時の分散投資便益
- ショート・ボラティリティ戦略のテールリスク
- 株価指数先物の導入と現物市場ボラティリティ
- 証拠金・値幅制限・取引方式が価格発見と市場安定性へ与える影響
- DCC、BEKK、GARCCによる時変共分散・相関モデリング
- 二段階推定、モデルの正則条件、相関予測のout-of-sample比較

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
