# Reassessing Liquidity: Beyond Order Book Depth — CME Group (2025)

## 書誌情報

- **記事**: “Reassessing Liquidity: Beyond Order Book Depth”
- **発行者**: CME Group
- **年**: 2025
- **原文**: [CME Group article](https://www.cmegroup.com/articles/2025/reassessing-liquidity-beyond-order-book-depth.html)
- **種別**: 取引所による実務記事・市場構造レポート
- **対象市場**: E-mini S&P 500 futures
- **手元保存上の注意**: Web記事は本文を複製せず、記事URLと分析ノートのみを保存する。CME Groupページの直接取得は403となったため、取得可能なページ本文ビューで内容確認した。

## 1. 一言でいうと

2025年4月初旬の関税ショック局面におけるE-mini S&P 500 futuresの流動性を、order book depthだけでなく、出来高、fill quality、price dispersion、trading rate、market impactで再評価する記事である。中心的な主張は、板の見かけ上の厚みが急減しても、それだけで「流動性が消えた」と判断するのは不十分であり、約定品質と市場インパクトを見ると、流動性はリスクに応じて合理的に再価格付けされていた、というもの。

## 2. 問題意識

市場ストレス時には、上位板のorder book depthが減りやすい。そのため、市場参加者は「流動性が消えた」と判断しがちである。しかし、板に静止している数量だけを見ると、注文更新速度、実際の約定量、約定価格の到着価格からの乖離を見落とす。

この記事は、流動性を「大量の取引を大きな価格インパクトなしに執行できる能力」と定義し、単一指標ではなく複数指標で評価すべきだと論じる。

## 3. 主要な観察

### 3.1 2025年4月のボラティリティ上昇

2025年4月初旬、新しい米国関税 regime の発表を契機に株式市場ボラティリティが急上昇した。E-mini S&P 500 futuresは2025年2月の高値から20%超下落し、その後、価格と流動性の両面で大きく回復した。

### 3.2 出来高は急増した

2025年4月7日のE-mini S&P 500 futures出来高は、Q1 2025の平均日次出来高を99%超上回った。出来高だけで見れば、市場はむしろ活発であり、売買の成立能力は高かった。

### 3.3 Order book depthは大きく減った

一方、上位3レベルの平均板厚は大きく低下した。10:00-10:15 ETのウィンドウでは、2025年3月31日の週に前週比で約27%低下し、4月7日のピークボラティリティ週にはさらに68%低下した。

この事実だけを見ると流動性悪化に見える。しかし、記事は「板に置かれた待機注文量」と「実際に注文を吸収する能力」は同じではないとする。

## 4. Fill qualityとprice dispersion

### 4.1 Price dispersionの測定

記事は、近接した時間内に成立した取引価格の範囲をfill qualityの代理指標として使う。E-mini S&P 500 futuresは連続取引であり、1秒内に成立した価格水準の数を見れば、その1秒でどれだけ価格が散らばったかを測れる。

低流動性なら、同じ取引速度でもより多くの価格水準を通過しやすい。逆に、板が薄く見えてもquote refreshが速ければ、価格を大きく動かさずに高い取引速度を処理できる。

### 4.2 April 7のfill quality低下は観測されるが一時的

2025年4月7日の週は、同じ取引速度に対するprice dispersionが3月中旬より大きかった。cash openでは、90パーセンタイルの取引数量に対する平均価格水準数が、3月17日の約4.1から4月7日の約10.8へ上がった。これは約6.7 ticksの悪化に相当する。

ただし、この悪化は一時的だった。4月21日にはprice dispersionが長期平均に戻りつつあり、ボラティリティ低下に応じて取引コストも速やかに低下した。

## 5. 2020年COVID局面との比較

記事は、2020年3月16日のCOVIDショックと2025年4月7日の関税ショックを比較する。どちらも出来高とボラティリティが高い期間だが、basis pointベースの市場インパクトは2025年の方が小さかった。

- 2020年3月16日: 約33百万ドル想定元本に対して約10bpsのインパクト
- 2025年4月7日: 約59百万ドル想定元本に対して約5.4bpsのインパクト

価格水準と想定元本の増加を正規化すると、2025年の市場インパクトはCOVIDピーク時より低かった。記事はこれを、E-mini S&P 500 futures市場の流動性・リスク吸収能力の改善として読む。

## 6. Square-root market impact model

記事は、実務で広く使われるsquare-root型の市場インパクト式を使い、2025年4月の実現インパクトが期待インパクトと整合的かを確認する。

```math
\mathrm{Estimated\ Impact}
=
\mathrm{Spread\ Cost}
+
\mathrm{Factor}
\times
\mathrm{Daily\ Vol}
\times
\sqrt{\frac{\mathrm{Order\ Quantity}}{\mathrm{ADTV}}}
```

このモデルでは、日次ボラティリティ、bid-ask spread、90パーセンタイル注文サイズ、5日平均出来高を使う。4月7日の実現インパクトは期待値よりやや大きいが、方向性としてはモデルが示す「ボラティリティ上昇に応じた合理的な取引コスト上昇」と整合する。

## 7. この資料の貢献

1. 流動性評価をorder book depth単独から、fill qualityとmarket impact中心へ広げる。
2. ストレス時の板厚低下を、quote refreshと約定能力の観点で再解釈する。
3. 2025年4月の関税ショック局面を、2020年COVIDショックとbpインパクトで比較する。
4. 実務的なsquare-root impact modelをE-mini S&P 500 futuresの実データに当てる。
5. 「板が薄い = 流動性がない」という単純化を避ける実務的なフレームを提供する。

## 8. 限界と批判点

1. **取引所記事である**: CME自身の市場解説であり、独立査読研究ではない。
2. **商品範囲が限定的**: 主にE-mini S&P 500 futuresを対象としており、他資産・他取引所へ一般化するには追加検証が必要である。
3. **データ粒度の開示に限界**: 記事形式のため、すべての推定仕様や再現用データが完全に開示されているわけではない。
4. **Depth以外の指標にも選択バイアスがある**: fill qualityやprice dispersionも、注文分割、取引参加者構成、時間帯選択で変わる。
5. **square-root modelは経験則**: 使いやすいが、流動性供給者の在庫制約や不連続ジャンプを構造的に識別するモデルではない。

## 9. 実務への含意

- ストレス時の流動性評価では、order book depth、出来高、price dispersion、market impact、quote refreshを同時に見る。
- Execution TCAでは、到着価格からの乖離をnotional/bpsベースで比較し、価格水準変化を正規化する。
- 板厚が減っても、出来高とfill qualityが維持されていれば「流動性消失」ではなく「リスク再価格付け」と解釈できる場合がある。
- 0DTEやディーラーガンマ分析で市場影響を語る場合も、想定元本ではなく実際のmarket impactを測る必要がある。
- Baltussen et al. (2021)の日中モメンタム、Kurth et al. (2026)の板厚・price impact、Cboe 0DTEレポートと接続しやすい。

## 10. 次に検討すべき問い

- CMEのprice dispersion指標を、自前のtick dataで再現できるか。
- E-mini S&P 500 futures以外、Treasury futures、Nikkei futures、VIX futuresでも同じ結論になるか。
- Order book depth、quote refresh、realized spread、market impactのどれが翌日の流動性を最もよく予測するか。
- 0DTE出来高やdealer gammaが高い日には、price dispersionとmarket impactがどの程度変わるか。
- Square-root impact modelの係数は、ボラティリティ regime、時間帯、イベント種別でどう変わるか。

## 11. 総合評価

この記事は、論文ではないが、先物市場の実務的な流動性評価を整理するうえで有用である。特に、ストレス局面でorder book depthだけを見ると市場機能を過小評価しやすい点、fill qualityとmarket impactで見ると流動性は完全に消えたのではなくボラティリティに応じて再価格付けされたと読める点が重要である。市場マイクロストラクチャー系の研究ノートに、実務記事カテゴリとして残す価値がある。
