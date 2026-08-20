# Investors' Net Buying Pressure and Implied Volatility Dynamics — Ryu et al. (2022)

## 書誌情報

- **論文名**: *Investors' Net Buying Pressure and Implied Volatility Dynamics*
- **著者**: Doojin Ryu, Robert I. Webb, Heejin Yang, Jinyoung Yu
- **掲載誌**: Borsa Istanbul Review, 22(4), 627-640
- **公刊年**: 2022
- **DOI**: https://doi.org/10.1016/j.bir.2021.09.004
- **原資料**: ScienceDirect
- **リポジトリ内PDF**: 未保存。指定ScienceDirect PDF URLは403を返し、PDF本文として検証できなかった。
- **キーワード**: net buying pressure, investor type, KOSPI200 options, direction learning, intraday seasonality

## 一言でいうと

KOSPI200オプション市場で、投資家タイプ別のnet buying pressureがIV変化をどう動かすかを再検証した論文。Bollen and Whaley (2004) を拡張し、先物ヘッジ需要、日中季節性、動的影響、制度変更を考慮すると、外国人投資家のオプション需要が方向学習型の情報を強く含み、国内個人は制度変更後に部分的に情報性を持つと示す。

## 1. 問題意識

NBPがIVを動かすとしても、それが在庫制約による一時的な需給効果なのか、情報を持つ投資家の取引なのかは区別する必要がある。KOSPI200市場は投資家区分データが豊富で、個人、国内機関、外国人を分けて検証できる。

## 2. 中核アイデア

投資家タイプ `inv` ごとに、call/putのATM近辺のNBPを測り、IV変化を説明する。

```math
\Delta \sigma_{i,t}^{ATM}
=
\alpha
+ \beta_1 RS_t
+ \beta_2 VS_t
+ \beta_3 FOI_{inv,t}
+ \gamma_C NBP_{inv,C,t}^{ATM}
+ \gamma_P NBP_{inv,P,t}^{ATM}
+ \rho \Delta \sigma_{i,t-1}^{ATM}
+ \varepsilon_{i,t}
```

ここで `FOI` は先物注文不均衡で、オプション取引が単なる先物ヘッジの副産物ではないかを制御する役割を持つ。

## 3. データと実証設計

- KOSPI200オプションと先物のintraday microstructureデータを使う。
- サンプルは2010年1月から2014年6月。
- 2012年の市場改革前後を分ける。
- 投資家タイプを個人、国内機関、外国人に分ける。
- 日中季節性と先物ヘッジ需要を制御し、NBPがIV変化へ与える影響を推定する。

## 4. 主要結果

- 外国人投資家のATM call/put NBPは、同じタイプのIVを押し上げ、反対タイプのIVを押し下げる方向学習型の符号を持つ。
- 外国人投資家の需要は、市場改革前後を通じて有意な情報を含む。
- 国内個人投資家の需要は、改革後に部分的にIV dynamicsを説明する。
- 先物ヘッジ需要や日中季節性を考慮しても、投資家タイプ別NBPの情報性は残る。

## 5. 解釈

Kang and Park (2008) の方向学習仮説を、投資家タイプ、ヘッジ需要、制度変更まで含めて精緻化した研究である。オプション注文フローを読む際には、単にcall買い/put買いを見るだけでなく、誰が取引しているのか、先物で同時にヘッジしているのか、市場制度が変わったかを考慮する必要がある。

## 6. 限界

- 指定ScienceDirect PDFは403で取得できず、ノートは公式ページの書誌情報・要旨・公開本文断片に基づく。
- KOSPI200固有の投資家区分データを使うため、米国市場では同じ粒度で再現しにくい。
- 投資家区分が情報優位性を直接示すわけではない。
- 先物ヘッジを制御しても、他市場・OTC・マルチレッグのヘッジは完全には見えない。

## 7. 次に検討すべき問い

- 米国OPRA/CATで投資家区分に近い情報を使うと、Ryu et al.型の推定は可能か。
- 0DTE市場では外国人/機関に相当する大口フローとリテールフローでIVインパクトは違うか。
- 先物注文不均衡を入れたとき、option NBPの情報性はどの満期で最も残るか。
- 方向学習型のNBPは、翌日OI変化やディーラーgamma推定と整合するか。

## BibTeX

```bibtex
@article{RyuWebbYangYu2022,
  author  = {Ryu, Doojin and Webb, Robert I. and Yang, Heejin and Yu, Jinyoung},
  title   = {Investors' Net Buying Pressure and Implied Volatility Dynamics},
  journal = {Borsa Istanbul Review},
  volume  = {22},
  number  = {4},
  pages   = {627--640},
  year    = {2022},
  doi     = {10.1016/j.bir.2021.09.004}
}
```
