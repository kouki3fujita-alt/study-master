# How Active Is Your Fund Manager? A New Measure That Predicts Performance — Cremers and Petajisto (2009)

## 書誌情報

- **論文**: K. J. Martijn Cremers and Antti Petajisto, “How Active Is Your Fund Manager? A New Measure That Predicts Performance”
- **掲載誌**: *The Review of Financial Studies*, Vol. 22, No. 9, pp. 3329-3365, 2009
- **DOI**: [10.1093/rfs/hhp057](https://doi.org/10.1093/rfs/hhp057)
- **SSRN**: [Abstract 891719](https://ssrn.com/abstract=891719)
- **手元PDF**: [2009_Cremers_ActiveSharePredictsPerformance.pdf](../../../papers/03_Finance/03_Systematic_Trading/2009_Cremers_ActiveSharePredictsPerformance.pdf)（37ページ、公刊版）
- **キーワード**: Active Share、tracking error、mutual funds、closet indexing、stock picking、benchmark selection

## 1. 一言でいうと

アクティブ投信がベンチマークとどれだけ保有銘柄を異ならせているかを **Active Share** で測り、米国国内株式投信では高Active Shareのファンドが費用・取引コスト控除後もベンチマークを上回る一方、非インデックス投信なのに低Active Shareの「closet indexer」は費用負けしやすいと示した研究である。

## 2. Active Shareとtracking errorの違い

銘柄 $i$ の投信・ベンチマーク比率をそれぞれ $w_{f,i}, w_{b,i}$ とすると、

```math
\operatorname{Active\ Share}
=\frac{1}{2}\sum_{i=1}^{N}|w_{f,i}-w_{b,i}|.
```

重み差を2で割るため、ベンチマークと保有が全く重ならないlong-only投信は100%となる。これは投信を「100%のベンチマーク + ゼロ純投資のactive long-short book」に分解したときの、後者の大きさである。

一方、tracking errorは $R_f-R_b$ の時系列ボラティリティであり、セクターrotationなどのfactor betを強く反映する。分散されたstock pickerは個別銘柄の差を大きく取ってもtracking errorが低くなり得るため、両指標を二次元で使う必要がある。

## 3. データと設計

- **対象**: 1980-2003年の米国国内株式mutual fund。
- **保有データ**: Thomson Financial CDA/SpectrumのSEC提出・任意開示を基にした四半期保有。
- **ベンチマーク候補**: S&P/Barra、Russell、Wilshireの計19指数。各ファンドに対し、標本全体でActive Shareが最小となる指数を割り当てる。
- **収益**: CRSP mutual-fund databaseの月次net return（fees、expenses、brokerage commissions控除後）と指数の配当込み収益。
- **分類**: Active Shareと日次収益から測る6か月tracking errorの二次元ソート。高AS・低TEはdiversified stock picker、高AS・高TEはconcentrated stock picker、低AS・高TEはfactor bet、低AS・低TEはcloset indexerに近い。

## 4. 主な結果

1. 高Active Share群のbenchmark-adjusted returnは費用・取引コスト前で年率1.51-2.40%、控除後でも1.13-1.15%のプラスと報告する。
2. 低Active Share群は控除後で年率 -1.42%から -1.83%のbenchmark underperformanceとなる。
3. tracking error単独は投信収益と有意に関係しない。高い変動性が選別能力を意味するわけではない。
4. 高AS・高直近収益の群は、費用控除後で年率5.10%（$t=3.67$）、Carhart four-factor調整後で3.50%（$t=3.29$）の持続的outperformanceを示す。
5. 1990年代には純粋なindex fundだけでなくAS 20-60%のcloset indexerの資産シェアも増え、2003年には全資産の約30%に達したと報告する。

## 5. 実務での使い方

- Active Shareは「アクティブか」の必要条件を測る指標であって、単独の銘柄選択能力スコアではない。費用、turnover、capacity、チーム変更を併せて確認する。
- 低AS・高feeのファンドは、実質的なindex exposureに対して高い手数料を払うcloset indexingの候補となる。
- benchmark選択が結果を左右する。投信が自己申告する指数ではなく、保有から妥当なベンチマークを検証するという設計は、現代のmanager evaluationにも有用である。
- ETFやlong-only株式戦略に移植する場合、保有開示の遅れ、デリバティブ、現金、securities lending、複数ベンチマークを明示的に扱う必要がある。

## 6. 限界と批判点

1. 高ASはoutperformanceの十分条件ではない。集中リスクやcapacity制約を伴い得る。
2. 1980-2003年の米国投信に基づく結果で、ETF普及後や他国市場へ自動的に一般化できない。
3. ベンチマークを最小ASで推定すると、真の運用目的と異なる指数を選ぶリスクが残る。著者らも自己申告ベンチマークの戦略的選択可能性を指摘する。
4. Carhart alphaとの乖離は、比較対象のベンチマーク自体にfactor alphaがあるというモデル設定上の問題を示す。benchmark-relative performanceとfactor-model alphaを同じ結論として扱わない。

## 7. 次に検討したい問い

- holdings-based Active Shareを月次ではなく日次のlook-through exposureで計算すると、実際のactive riskをどこまで改善できるか。
- 近年のETF・SMAsで高ASと費用後alphaの関係は残るか。
- 0DTEやoption overlayを使う投信では、株式保有ASにデルタ換算オプションエクスポージャーをどう加えるべきか。
