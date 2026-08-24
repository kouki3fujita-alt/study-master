# Option Pricing of Earnings Announcement Risks — Dubinsky et al. (2019)

## 書誌情報

- **論文**: *Option Pricing of Earnings Announcement Risks*
- **著者**: Andrew Dubinsky, Michael Johannes, Andreas Kaeck, Norman J. Seeger
- **掲載誌**: *The Review of Financial Studies*, 32(2), 646-687
- **年**: 2019（online 2018年）
- **DOI**: [10.1093/rfs/hhy060](https://doi.org/10.1093/rfs/hhy060)
- **原資料**: [Moonlight共有ページ](https://www.themoonlight.io/paper/b750fc54-70e0-4a64-b12e-d58144628bae)
- **リポジトリ内PDF**: [2019_Dubinsky_OptionPricingEarningsAnnouncementRisks.pdf](../../../papers/03_Finance/01_Derivatives/2019_Dubinsky_OptionPricingEarningsAnnouncementRisks.pdf)
- **キーワード**: earnings announcement, deterministic jump time, implied variance term structure, event volatility

## 一言でいうと

決算という時刻が分かっているが大きさが不確実なジャンプを株価モデルに入れ、満期の異なるオプションIVから決算日固有のrisk-neutral不確実性を分離する。決算不確実性は景気後退で大きくなり、事前推定値は実現決算日ボラティリティを強く予測する一方、投資家はそのジャンプ保険にプレミアムを支払う。

## 1. モデル

決算日 \(\tau_j\) は予め分かる。株価に通常のstochastic volatility/ランダムjumpに加え、決算日だけのランダムjumpを入れる。単純化すると、満期 \(T\) までに決算が1回あるとき、年率化implied varianceは

```math
\sigma^2_{t,T}=\sigma^2_{normal,t,T}+\frac{(\sigma_j^Q)^2}{T},
```

となる。\(\sigma_j^Q\) はrisk-neutralな決算日price uncertaintyである。従って決算直前には短期IVが上がり、決算通過後には不連続に低下し、決算をまたぐ短期満期ほどIV term structureは下向きになる。

2つの満期 \(T_1<T_2\) がともに決算をまたぐときには、normal varianceを差し引くことでterm-structure estimatorを作る。これはランダム時刻のPoisson jumpが主にskewを動かすのに対し、既知時刻のjumpはterm structureと時系列IV dropで識別される、という点が核心である。

## 2. データと設計

- 2000-2015年のactively traded US individual stocksとearnings announcement datesを用いる。
- 決算をまたぐ/またがない満期のIV term structure、及び決算後のIV低下からex ante/ex post estimatorを作る。
- Amazon、GE、IBM、Intel、Microsoft、Qualcomm等について、earnings jumpを含むSV/jump modelと含まないモデルの価格誤差を比較する。

## 3. 主要結果

- 平均決算不確実性は拡張期におおむね4-6%、2000-2002年・2008-2009年後退期には10-11%程度へ上昇する。
- option-implied決算日volatilityの平均は8.22%、実現決算日volatilityは7.42%で、約80bpのjump-risk premiumがある。
- 事前推定値と事後実現volatilityの相関は50%超、クロスセクションでは約85%で、analyst forecast dispersionより有用なvolatility情報を持つ。
- 決算jumpを導入すると、決算直前のSVモデルのpricing errorを50%以上下げるケースがある。通常のSVだけでは短期term structureを再現しにくい。

## 4. 実務的な読み方

決算前に短期ATM IVが上がることは、単に「IVが高いから売り有利」を意味しない。そこには市場が価格付けした既知時刻jumpのrisk-neutral varianceが入っている。比較では、同一銘柄の決算をまたぐ/またがない満期からevent varianceを差し引き、実現move、bid-ask、skew、overnight gapを別に追う必要がある。

## 5. 限界

- \(\sigma_j^Q\) はrisk-neutralの不確実性であり、平均予想株価変動や顧客別ポジションを直接示さない。
- 決算時刻の誤認、after-close/before-open、guidanceや同日マクロイベントの混在は推定を歪める。
- term-structure差分は満期補間、quote quality、通常varianceの平均回帰仮定に感応的である。
- オプション売りの超過収益を主張するには、jump tail、execution、margin、取引可能なstrike選択まで検証が必要である。

## 6. 次に検討すべき問い

- event varianceとpost-earnings-announcement drift、skew premiumはどう結び付くか。
- 0DTE/1DTEの普及で決算jumpの期限別price discoveryは変わったか。
- event-implied varianceをマクロ発表・選挙・FOMCへ同じ方法で移植できるか。

## BibTeX

```bibtex
@article{DubinskyJohannesKaeckSeeger2019,
  author  = {Dubinsky, Andrew and Johannes, Michael and Kaeck, Andreas and Seeger, Norman J.},
  title   = {Option Pricing of Earnings Announcement Risks},
  journal = {The Review of Financial Studies},
  volume  = {32}, number = {2}, pages = {646--687}, year = {2019},
  doi     = {10.1093/rfs/hhy060}
}
```
