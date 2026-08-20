# The Implied Volatility of ETF and Index Options — Ivanov, Whitworth and Zhang (2011)

## 書誌情報

- **論文名**: *The Implied Volatility of ETF and Index Options*
- **著者**: Stoyu I. Ivanov, Jeff Whitworth, Yi Zhang
- **掲載誌**: The International Journal of Business and Finance Research, 5(4), 35-44
- **公刊年**: 2011
- **原資料**: SSRN / IJBFR PDF
- **リポジトリ内PDF**: [2011_Ivanov_ImpliedVolatilityETFIndexOptions_SSRN1879583.pdf](../../../papers/03_Finance/01_Derivatives/2011_Ivanov_ImpliedVolatilityETFIndexOptions_SSRN1879583.pdf)
- **キーワード**: ETF options, index options, implied volatility, open interest, volatility smile

## 一言でいうと

SPY、DIA、QQQのETFオプションは、それぞれが追跡するS&P 500、Dow 30、NASDAQ 100の指数オプションと原資産リターン分布が非常に近いにもかかわらず、IV smileがより強く出る。特にdeep-in-the-moneyのETFオプションIVが指数オプションより高く、単純な実現分布差やopen interestによる需要代理変数だけでは説明しにくい。

## 1. 問題意識

ETFは指数に連動するが、ETFオプションは法的・取引上は個別株オプションに近い。指数オプションとETFオプションが同じリスクを反映するなら、IVサーフェスも近いはずである。しかし、取引制度、アメリカン/ヨーロピアンの違い、配当、投資家層、ヘッジ需要が異なるため、同一指数エクスポージャーでもオプション価格はずれうる。

## 2. 中核アイデア

ETFと指数の実現リターン分布がほぼ同じなら、IV差は原資産分布ではなく、オプション市場側の要因に由来する可能性が高い。

候補は主に3つである。

1. ETFと指数の実現分布差
2. open interestで代理される需要差
3. bid-ask spreadなどの取引コスト差

## 3. データと実証設計

- 対象はDiamonds (DIA)、Spiders (SPY)、Cubes/QQQと、それぞれの追跡指数。
- 1999年3月から2006年12月までの日次データを用いる。
- ETF価格は指数の16:00終値と時刻を合わせるため、16:00近辺のETF取引価格も使う。
- ETFオプションはアメリカン型なので、binomial modelでIVを計算する。
- IVをmoneyness別に比較し、open interestやbid-askを含む回帰で差を検証する。

## 4. 主要結果

- ETFと指数の実現リターン分布に有意な差はほとんどない。
- ETFオプションのIV smileは指数オプションより強く、特にdeep-in-the-moneyで差が大きい。
- open interestはBollen and Whaley型のnet buying pressureの粗い代理だが、IV差を十分には説明しない。
- bid-ask spreadはIVと有意に関係するが、ETF/指数の差を完全には消さない。

## 5. 解釈

同じ指数リスクでも、ETFオプションと指数オプションは完全な代替ではない。ETFオプションは株式型の取引単位・個人投資家アクセス・アメリカン型の特徴を持つため、指数オプションとは異なる需給と流動性プレミアムがIVに乗る。

0DTE ETFオプションや個別ETFの需給分析でも、指数オプションのIVやフローをそのまま代替データとして使うのは危険である。

## 6. 限界

- open interestはNBPそのものではなく、需要圧力の粗い代理にすぎない。
- サンプルはETFオプション市場が現在ほど大きくない2000年代前半である。
- intraday quoteや約定方向を使っていない。
- ETFの貸株、作成償還、配当処理、税制差を完全には分解していない。

## 7. 次に検討すべき問い

- SPY/SPX/SPXWの0DTE市場で、同じ満期・同じdeltaのIV差はどの程度残るか。
- ETFオプションのリテール比率、PFOF、内部化はIV smileをどう歪めるか。
- ETF貸株制約やhard-to-borrow状態はput-call parity差に表れるか。
- 指数オプションとETFオプションの相対価値取引は、取引コスト後に成立するか。

## BibTeX

```bibtex
@article{IvanovWhitworthZhang2011,
  author  = {Ivanov, Stoyu I. and Whitworth, Jeff and Zhang, Yi},
  title   = {The Implied Volatility of ETF and Index Options},
  journal = {The International Journal of Business and Finance Research},
  volume  = {5},
  number  = {4},
  pages   = {35--44},
  year    = {2011}
}
```
