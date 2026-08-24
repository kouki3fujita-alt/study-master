# The Factor Structure of 0DTE Option Returns — Dorion, Orlowski & Song (2026)

## 書誌情報

- **論文**: *The Factor Structure of 0DTE Option Returns*
- **著者**: Christian Dorion, Piotr Orlowski, Yuhan Song
- **種別**: SSRN working paper（2026年7月17日稿）
- **SSRN**: [7149778](https://ssrn.com/abstract=7149778)
- **原資料**: ユーザー提供PDF
- **リポジトリ内PDF**: [2026_Dorion_FactorStructure0DTEOptionReturns_SSRN7149778.pdf](../../../papers/03_Finance/01_Derivatives/2026_Dorion_FactorStructure0DTEOptionReturns_SSRN7149778.pdf)
- **キーワード**: 0DTE, SPX, conditional factor model, gamma warehousing, jump skewness, intraday alpha

## 一言でいうと

0DTEから15DTEのSPX optionを30分頻度で一つのconditional six-factor modelに載せ、短期option収益の大半は原資産の実現モーメントとvariance dynamicsで説明できると示す。0DTEに残るalphaは在庫・バランスシートと関係するが、極小の取引コストでfactor-neutral利益は消えるため、観測された残差をそのまま実行可能なmispricingとは読まない。

## 1. 因子構造

各30分のoption returnを、原資産リターンとその非線形モーメント、variance dynamicsでspanningする。概念的には

```math
r_{i,t+1}=\beta_{i,t}^{\top} f_{t+1}+\alpha_{i,t}+\varepsilon_{i,t+1},
```

で、\(f\) は実現一次・二次・三次モーメントと、spot variance、jump variance、variance term-structureの変化からなる6因子である。delta hedge後には方向因子の寄与を除き、gamma warehousingとjump-skewnessを主な補償対象として読む。

## 2. データと実証設計

- 2016年9月-2023年12月のCboe Option Intervals 1分quote、Tickdataのミリ秒ES futures、OptionMetrics zero curveを使う。
- PM-settled SPX、満期15営業日以下、9:45-15:45 ETの30分returnを対象とし、正の出来高・bid、OTM/ATM等のfilterを課す。
- 最終標本はputs約1,400万、calls約680万の30分return。0DTEと4-15DTEを同一モデルで比較する。

## 3. 主要結果

- six factorsは30分return変動の99.1%（put）・98.2%（call）を説明する。
- 0DTEでは実現二次モーメント、より長い満期ではspot-volatility変化の寄与が大きい。
- 0DTE alphaは大きく日中季節性を持つ。OTM callで年率-7.73%、ATM putで-4.63%に達する一方、より長い満期では絶対値3.16%未満。
- alphaはopen interest（集計inventory proxy）と、より弱くintermediary balance-sheet conditionに連動する。
- frictionless factor-neutral strategyのSharpeは1.4だが、quoted half-spreadの5%という小さなeffective transaction costで累積利益が消える。

## 4. 解釈

この論文のポイントは、0DTEの見かけの高収益/低収益を「リテールからmarket makerへの一方向transfer」と断定しないことにある。残差はinventory managementやknown-timing event riskのモデル欠落を示す診断信号になり得るが、実行コストを越えられなければalphaではない。OIはaggregate inventoryの粗いproxyで、顧客別意図・dealer net gammaの直接観測ではない。

## 5. 限界

- 2026年working paperであり、査読・改訂で仕様や数値は変わり得る。
- quote midpoint、filter、30分sampling、effective spread仮定に結果は感応的である。
- 2023年末までの標本のため、2024-2026年の0DTE構成比・market maker behaviorを確認していない。
- 因子の高い同時説明力は、out-of-sampleな収益予測力や取引可能性を保証しない。

## 6. 次に検討すべき問い

- 2024年以後の0DTE増加局面でもsix-factor priceと残差季節性は安定するか。
- FOMC・CPI・決算日などknown-timing eventを明示的に因子化すると0DTE alphaはどこまで縮むか。
- aggressor-signed option tradesと時刻整合したfutures flowを使えば、OI proxyよりinventory channelを識別できるか。

## BibTeX

```bibtex
@techreport{DorionOrlowskiSong2026,
  author = {Dorion, Christian and Orlowski, Piotr and Song, Yuhan},
  title  = {The Factor Structure of 0DTE Option Returns},
  type   = {SSRN Working Paper}, year = {2026},
  month  = jul, url = {https://ssrn.com/abstract=7149778}
}
```
