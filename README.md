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
| 相関リスク・デリバティブ | [Option-Implied Correlations and the Price of Correlation Risk](notes/03_Finance/01_Derivatives/2005_Driessen_OptionImpliedCorrelations.md) | Joost Driessen, Pascal Maenhout, Grigory Vilkov | 2005（2009年公刊版あり） | 指数と構成銘柄のモデルフリー・インプライド分散から平均相関を逆算し、相関上昇保険の価格とdispersion tradingの源泉を示す |
| 市場マイクロストラクチャー | [Futures Markets, Regulation and Volatility](notes/03_Finance/01_Derivatives/1994_Bacha_FuturesMarketsRegulationVolatility.md) | Obiyathulla Bacha, Anne Fremault Vila | 1994 | 日経225先物の複数市場への上場を利用し、先物導入・規制・満期日が現物ボラティリティへ与える影響を検証する |
| 金融計量・相関モデル | [Ten Things You Should Know about the Dynamic Conditional Correlation Representation](notes/03_Finance/01_Derivatives/2013_Caporin_TenThingsDCC.md) | Massimiliano Caporin, Michael McAleer | 2013 | DCCを厳密なモデルではなくフィルターとして捉えるべき理由を10の理論的・実証的注意点から整理する |
| 商品・分散リスク | [Variance Risk in Commodity Markets](notes/03_Finance/01_Derivatives/2017_Prokopczuk_VarianceRiskCommodityMarkets.md) | Marcel Prokopczuk, Lazaros Symeonidis, Chardin Wese Simen | 2017（2014年稿） | 21商品市場の合成分散スワップを調べ、商品分散リスクが先物価格リスクとは別のリスクであることを示す |
| 暗号資産・分散リスク | [The Bitcoin VIX and Its Variance Risk Premium](notes/03_Finance/01_Derivatives/2021_Alexander_Imeraj_BitcoinVIX.md) | Carol Alexander, Arben Imeraj | 2021 | DeribitオプションからBitcoin VIXの期間構造とVRPを構築し、ジャンプ誤差と危機時の分散投資便益を検証する |
| 社債・分散リスク | [Synthetic Options and Implied Volatility for the Corporate Bond Market](notes/03_Finance/01_Derivatives/2023_Chen_SyntheticCorporateBondOptions.md) | Steven Shu-Hsiu Chen, Hitesh Doshi, Sang Byung Seo | 2023 | CDXスワップションから社債指数オプションとCBVIXを合成し、社債VRPを測定する |
| ボラティリティ予測 | [The Relation between Implied and Realized Volatility](notes/03_Finance/01_Derivatives/1998_Christensen_Prabhala_ImpliedRealizedVolatility.md) | Bent Jesper Christensen, Nagpurnanand R. Prabhala | 1998 | 非重複月次標本と測定誤差補正により、OEX ATM IVが過去RVを上回り、その情報を包含することを示す |
| 決算イベント・オプション | [Earnings Announcements and Equity Options](notes/03_Finance/01_Derivatives/2004_Dubinsky_Johannes_EarningsAnnouncementsEquityOptions.md) | Andrew Dubinsky, Michael Johannes | 2004/2006 | 既知時刻の決算ジャンプをIV期間構造から抽出し、イベントジャンプを入れると短期オプションの価格誤差が大幅に縮小することを示す |
| 暗号資産・ジャンプリスク | [Jump Risk Premia in the Presence of Clustered Jumps](notes/03_Finance/01_Derivatives/2025_Liu_JumpRiskPremiaClusteredJumps.md) | Francis Liu, Natalie Packham, Artur Sepp | 2025 | 正負ジャンプの群発を二変量Hawkes過程でモデル化し、BTCのジャンプ・プレミアを先物ベーシスとオプション収益へ結び付ける |
| 個人投資家・オプション需給 | [Retail Option Traders and the Implied Volatility Surface](notes/03_Finance/01_Derivatives/2026_Eaton_RetailOptionTradersIVSurface.md) | Gregory W. Eaton, T. Clifton Green, Brian S. Roseman, Yanbin Wu | 2026 | 証券会社の障害を外生ショックとして、個人の短期・OTM・コール需要がIVサーフェスを歪めることを示す |
| 市場構造・規制（当局レポート） | [Staff Report on Equity and Options Market Structure Conditions in Early 2021](notes/03_Finance/01_Derivatives/2021_SEC_EquityOptionsMarketStructureEarly2021.md) | SEC Staff | 2021 | 2021年1月のGameStop急騰をCAT等の当局データで検証し、ショートスクイーズが主因ではなくガンマスクイーズの証拠もないこと、取引制限がNSCC証拠金への反応であったことを示す |

## この論文から伸びる研究テーマ

- Variance risk premium と将来株式リターン
- 指数分散と個別株分散の差、および dispersion trading
- Implied correlation、realized correlation、correlation risk premiumの識別
- 相関スワップ、sector dispersion、相関期間構造と0DTE
- 危機時の相関上昇、分散効果消失、ポートフォリオのストレス相関
- VIX、variance swap、volatility swap の関係
- ジャンプ、左側テール、vol-of-vol の価格
- 正負ジャンプの自己励起・交差励起、Hawkes過程、時変IVスキュー
- BTCのジャンプ・リスクプレミア、先物ベーシス、funding、デルタヘッジP&L
- 分散リスク・プレミアムの期間構造
- Bitcoin VIX、暗号資産の分散期間構造、危機時の分散投資便益
- ショート・ボラティリティ戦略のテールリスク
- 個人投資家のオプション需要、ディーラー在庫制約、IVサーフェスの形状
- インプライド・ボラティリティの実現ボラティリティ予測力、情報包含、測定誤差
- 重複予測窓、HAC・操作変数法、1987年暴落前後の構造変化
- 決算expected move、既知時刻ジャンプ、イベント分散リスク・プレミアム
- 決算前後のIV crush、カレンダースプレッド、確率的ボラティリティとの識別
- 0DTE・短期オプションの注文フローとIV期間構造
- 株価指数先物の導入と現物市場ボラティリティ
- 証拠金・値幅制限・取引方式が価格発見と市場安定性へ与える影響
- DCC、BEKK、GARCCによる時変共分散・相関モデリング
- 二段階推定、モデルの正則条件、相関予測のout-of-sample比較
- ミーム株、ソーシャルメディア、個人投資家の集団的取引と価格形成
- ショートスクイーズ、ガンマスクイーズ、空売り制約とバブル
- 空売り残高の再貸出による100%超、フェイル・トゥ・デリバー、裸空売りの識別
- PFOF、注文フローのセグメンテーション、内部化と執行品質の測定
- 清算機関の証拠金モデル、日中マージンコール、決済サイクル短縮（T+1）
- LULD、サーキットブレーカー、ボラティリティ急騰時の板の厚みとスプレッド
- 均等ウェイトETFの組入比率膨張、ETFの空売りとNAV乖離

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
