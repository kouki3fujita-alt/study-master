# Execution Risk in High-frequency Arbitrage — Kozhan and Tham (2012)

## 書誌情報

- **論文**: Roman Kozhan, Wing Wah Tham, “Execution Risk in High-frequency Arbitrage”
- **掲載誌**: *Management Science*, Vol. 58, No. 11, pp. 2131-2149, 2012
- **DOI**: [10.1287/mnsc.1120.1541](https://doi.org/10.1287/mnsc.1120.1541)
- **手元PDF**: SSRN 2030767、38ページ。公刊版の前稿であり、表記・最終校正に差があり得る。
- **リポジトリ内PDF**: [2012_Kozhan_ExecutionRiskHighFrequencyArbitrage_SSRN2030767.pdf](../../../papers/03_Finance/03_Systematic_Trading/2012_Kozhan_ExecutionRiskHighFrequencyArbitrage_SSRN2030767.pdf)
- **キーワード**: high-frequency trading、triangular arbitrage、execution risk、limit order book、crowding、FX

## 1. 研究質問と結論

完全に同じpayoffを持ちconvertibleな資産でさえ、高頻度arbitrageが瞬時に価格差を消さないのはなぜかを問う。

論文の答えは **execution risk** である。複数のarbitrageurが限られた最良気配の数量を同時に取りに行くと、片側だけ約定して残りを悪い価格で執行するリスクが生じる。競争相手が増えるほど、個人の市場参加確率は下がり、意外にもmispricingの即時解消確率も下がり得る。Reuters D3000のFX板では、手数料・spread・latencyを考慮してもtriangular arbitrageの価格差が残り、illiquidityが大きいほど乖離も大きいことを示す。

## 2. モデルの核

資産1と、同一payoffのportfolio (P\) がある。bid/askを使った取引費用控除後の乖離は

```math
A=\max\{0,\ P^b-P_1^a,\ P_1^b-P^a\}
```

である。最良気配の数量は有限で、同時に市場注文を出すarbitrageurが (k\) 人いるとする。最良価格を取れる確率を (\bar P_{i|k,\pi}\)、取れず二番気配までwalkする損失を (\Delta_i(w_i)\) とすると、対称mixed-strategy equilibriumのzero-profit条件は概念的に

```math
A=\sum_i \Delta_i(w_i)
\left(1-\bar P_{i|k,\pi}\right)
```

となる。乖離は「無料のprofit」ではなく、各脚で最良価格を逃す確率とその執行コストへの補償である。参加確率 (\pi<1\) なので、最良気配が尽きるほどの人数が参加しない状態が正の確率で残る。

```math
\Pr(\text{elimination})
=\sum_{s=n}^{k}\binom{k}{s}\pi^s(1-\pi)^{k-s}
```

は、供給 (n\) が限られると競争増加で必ずしも上がらない。

## 3. データと実証設計

- **市場**: Reuters Dealing 3000のspot FX limit order book。
- **通貨三角形**: EUR/USD、GBP/USD、EUR/GBP。
- **期間**: 2003年1月2日-2004年12月30日、tick-by-tick、時刻精度0.01秒。
- **観測**: 注文ID、価格、数量、hidden quantity、entry/removal、約定、板の最良・二番気配を追跡。
- **検定**: 1 pip以上のfee後triangular-arbitrage clusterを抽出し、乖離 (A\)、duration、spread、最良-二番気配差 (\Delta\)、板のslopeを分析。

40,166のprofitable clusterで、平均乖離は1.56 pips、median cluster durationは0.35秒である。これらは見かけ上のquote mismatchを全て収益機会と数えず、手数料を超えたclusterに絞った結果である。

## 4. 主要結果

1. 取引費用・latencyを考慮した後も、triangular-arbitrage deviationsは即時には消えない。
2. deviationはspread、最良-二番気配の距離、板slopeで測るilliquidityと正に関係する。
3. 大きい乖離、短いduration、高いliquidityのclusterほどmarket orderで終わりやすい。これはexecution riskが低いときにarbitrageurが参加しやすいという予測と整合する。
4. モデル上・経済評価上、競争者数が増えるほど片脚だけの約定に伴う損失が大きくなり得る。競争が常に市場効率を高めるという単純な結論への反例となる。

## 5. 実務への含意

- 三角裁定のmid-price edgeと、実際に全脚を同時に執行できるedgeは別物である。最低でもtop-of-book depth、二番気配、queue position、venue latency、reject/cancelの確率を評価する。
- 「競争者が多いから機会はすぐ消える」と仮定すると、crowdingが作るinventory riskを見落とす。極短期のbacktestにはpartial fillとleg riskが必要である。
- FXだけでなく、ETF-constituent、cash-futures、ADR、crypto cross-exchangeの裁定にも、同時性とlimited depthがある限り同じ論点がある。

## 6. 限界と批判点

1. データは2003-2004年のReuters D3000であり、現在のco-location、internalization、fragmented venue、latency raceへ量的に外挿できない。
2. 観測できる板は全市場流動性やhidden liquidityを完全には表さず、実際のarbitrageur数・queue positionも未観測である。
3. モデルはrisk-neutral・同質arbitrageur・同時市場注文を置く。速度、資本、risk limit、情報の非対称性は単純化されている。
4. 乖離の持続はexecution riskと整合するが、data-feed latencyやstale quote、credit constraintsなど他の要因を完全に排除する因果実験ではない。

## 7. 次に検討したい問い

1. 現代のmessage-level dataで、competition proxyとpartial-fill lossはどう推定できるか。
2. maker-taker feeやspeed bumpは、crowdingによる負の外部性を減らすのか、それとも持続時間を延ばすのか。
3. option-market makerのdelta hedgeとcross-asset arbitrageを統合すると、execution riskはintraday volatilityへどう波及するか。
