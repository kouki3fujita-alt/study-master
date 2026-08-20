# The Information Content of Net Buying Pressure — Kang and Park (2008)

## 書誌情報

- **公刊版論文名**: *The Information Content of Net Buying Pressure: Evidence from the KOSPI 200 Index Option Market*
- **著者**: Jangkoo Kang, Hyoung-Jin Park
- **掲載誌**: Journal of Financial Markets, 11(1), 36-56
- **公刊年**: 2008
- **DOI**: https://doi.org/10.1016/j.finmar.2007.01.001
- **手元PDF版**: *The Impact of Net Buying Pressure on Implied Volatility: The Learning Hypothesis versus the Limits of Arbitrage Hypothesis*, SSRN稿、2005年3月15日
- **リポジトリ内PDF**: [2008_Kang_InformationContentNetBuyingPressure_SSRN686574.pdf](../../../papers/03_Finance/01_Derivatives/2008_Kang_InformationContentNetBuyingPressure_SSRN686574.pdf)
- **キーワード**: KOSPI 200 options, net buying pressure, direction learning, implied volatility, informed trading

## 一言でいうと

KOSPI 200オプション市場では、net buying pressureは単なる需給制約ではなく、方向情報を含む。call買い圧力はcall IVを上げ、put IVを下げ、put買い圧力は逆にput IVを上げ、call IVを下げる。これはBollen and Whaley型のlimits-to-arbitrageだけでは説明しにくく、方向情報を持つ投資家がまずオプション市場で取引するというdirection-learning仮説を支持する。

## 1. 問題意識

Bollen and Whaley (2004) は、S&P 500オプションのput需要がIV smileを押し上げると論じた。しかし、それは需給制約なのか、オプション市場が現物市場に先行して情報を反映しているのかを区別する必要がある。

本論文は、電子取引で個人投資家も活発なKOSPI 200オプション市場を使い、dailyとintradayの両方でNBPの情報内容を調べる。

## 2. 仮説の整理

limits-to-arbitrage仮説では、系列ごとの買い圧力が同じ系列のIVを押し上げ、その後反転する。

volatility-learning仮説では、投資家が将来ボラティリティ情報を持つため、call/putの両方のIVが同方向に動きやすい。

direction-learning仮説では、投資家が原資産方向の情報を持つ。上昇情報ならcall買いとput売り、下落情報ならput買いとcall売りが起きるため、call IVとput IVへの影響の符号が反対になりうる。

## 3. データと実証設計

- KOSPI 200指数オプションのdailyデータと5分足intradayデータを使う。
- moneyness別、call/put別、投資家区分別にNBPを計算する。
- IV変化を原資産リターン、出来高、NBP、ラグ付きIV変化で説明する。
- NBPが将来のKOSPI 200リターンを先行するかも検証する。

## 4. 主要結果

- dailyデータでは、Bollen-Whaley型の単純な需給仮説は強く支持されない。
- intradayでは、call買い圧力がcall IVを上げ、put IVを下げる。put買い圧力はput IVを上げ、call IVを下げる。
- callの正のNBPは次の5分の株価上昇、putの正のNBPは次の5分の株価下落と整合的である。
- NBPの効果は概ね短時間に集中し、方向情報が現物市場へ反映される過程として解釈される。

## 5. 解釈

この論文は、同じ「注文フローがIVを動かす」という事実でも、市場ごとに経済的意味が違うことを示す。S&P 500のOTM put需要は保険需要と在庫制約に近い一方、KOSPI 200では方向取引の情報伝達がより前面に出る。

したがって、NBPを使ってIVや原資産を読む場合、call/put別、投資家区分別、時間軸別に分けないと、需給効果と情報効果を混同しやすい。

## 6. 限界

- 手元PDFは2005年SSRN稿で、公刊版ではタイトルと構成が変わっている。
- KOSPI 200市場の投資家構成と取引制度は、米国SPX市場とは大きく異なる。
- intraday lead-lagは短期的で、長期予測力や投資可能性を意味しない。
- 取引コスト、板厚、執行可能数量を考慮した戦略評価ではない。

## 7. 次に検討すべき問い

- 米国0DTE市場でも、同一投資家区分のcall/put NBPは方向学習型の符号を示すか。
- ディーラーガンマが正/負の局面で、NBPのIVインパクトは変わるか。
- NBPと先物注文不均衡を同時に入れると、どちらが先に価格発見するか。
- 方向情報とボラティリティ情報を分けるため、delta-signedとvega-signedの二軸に分解できるか。

## BibTeX

```bibtex
@article{KangPark2008,
  author  = {Kang, Jangkoo and Park, Hyoung-Jin},
  title   = {The Information Content of Net Buying Pressure: Evidence from the KOSPI 200 Index Option Market},
  journal = {Journal of Financial Markets},
  volume  = {11},
  number  = {1},
  pages   = {36--56},
  year    = {2008},
  doi     = {10.1016/j.finmar.2007.01.001}
}
```
