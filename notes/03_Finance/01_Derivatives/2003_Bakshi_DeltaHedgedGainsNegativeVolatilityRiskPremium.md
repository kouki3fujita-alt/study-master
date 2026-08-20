# Delta-Hedged Gains and the Negative Market Volatility Risk Premium — Bakshi and Kapadia (2003)

## 書誌情報

- **論文**: Gurdip Bakshi, Nikunj Kapadia, “Delta-Hedged Gains and the Negative Market Volatility Risk Premium”
- **掲載誌**: *The Review of Financial Studies*, Vol. 16, No. 2, pp. 527-566, 2003
- **DOI**: [10.1093/rfs/hhg002](https://doi.org/10.1093/rfs/hhg002)
- **手元PDF**: 2001年4月9日版、48ページ。公刊版の前稿であり、表・組版の細部は公刊版と異なり得る。
- **リポジトリ内PDF**: [2003_Bakshi_DeltaHedgedGainsNegativeVolatilityRiskPremium_SSRN267106.pdf](../../../papers/03_Finance/01_Derivatives/2003_Bakshi_DeltaHedgedGainsNegativeVolatilityRiskPremium_SSRN267106.pdf)
- **キーワード**: delta hedge、vega、volatility risk premium、S&P 500 index options、jump risk

## 1. 研究質問と結論

指数オプションを買い、デルタを現物で相殺したポートフォリオの平均損益から、ボラティリティ・リスクプレミアム（VRP）の符号を識別できるかを問う。

著者らは、連続ヘッジかつvolatility riskが無価格ならデルタヘッジ損益の平均はゼロだが、S&P 500指数オプションではlong optionのデルタヘッジ損益が系統的に負であることを示す。stochastic volatilityモデルでは、その符号はvolatility risk premiumの符号と対応するため、結果は **市場VRPが負**、すなわち投資家が市場ボラティリティ保険にプレミアムを払っていることを支持する。

## 2. 中核アイデアと数式

コール (C_t\) を買い、(\Delta_t=\partial C_t/\partial S_t\) 株を売ってデルタを相殺する。金利を含めた区間損益を一般に

```math
\Pi_{t,t+\tau}
= C_{t+\tau}-C_t
-\sum_{n}\Delta_{t_n}(S_{t_{n+1}}-S_{t_n})
-\text{funding adjustment}
```

とする。定数ボラティリティの無摩擦Black-Scholes世界では連続ヘッジで (\Pi=0\) となる。離散ヘッジでも、その平均誤差は再ヘッジ回数 (N\) に対して小さい (O(1/N)\) と整理される。

stochastic volatilityでvolatility risk premiumを (\lambda_t(\sigma_t)\) とすると、概念的には

```math
E_t[\Pi_{t,t+\tau}]
\approx E_t\left[\int_t^{t+\tau}
\lambda_u(\sigma_u)\,
\frac{\partial C_u}{\partial \sigma_u}\,du\right]
```

となる。通常のvanilla optionではvega (\partial C/\partial\sigma>0\) なので、平均デルタヘッジ損益が負なら (\lambda<0\) と整合する。ATMではvegaが大きいため、負の損益もATM付近で最も大きく、moneynessが離れると弱まるという検定可能な予測が出る。

## 3. データと実証設計

- **対象**: CboeのS&P 500 European index calls・puts
- **期間**: 1988年1月-1995年12月
- **フィルター**: 残存14-60日、無裁定境界・IV 1%-100%などで除外
- **最終標本**: calls 36,237、puts 35,030 quotes
- **ヘッジ**: Black-Scholes deltaを日次で再調整し、配当・put-call parityから得た金利を反映
- **検定**: moneyness別のcross-section、GARCH(1,1)およびrolling volatilityを使うtime-series、risk-neutral skewness/kurtosisによるjump-fear control

## 4. 主要結果

1. long callのデルタ中立・正vega戦略は平均でゼロを有意に下回る。全moneyness・満期をならすとおよそ指数価値の **-0.05%**、ATM callでは **-0.13%**、ATM option価格の約 **8%** に相当する損失である。
2. 負の損益はATM近辺で大きく、OTM/ITMへ離れるほど小さい。これはvegaを介したVRP仮説と整合する。
3. 物理測度のボラティリティが高い局面ほど、ATMデルタヘッジ損益はより負になる。
4. risk-neutral skewness・kurtosisを入れてもVRP変数の説明力は残る。left-tail jump fearだけで系統的な損失を全て説明することは難しい。

## 5. 解釈

負のVRPは「ボラティリティの高い状態が、株式投資家にとって悪い状態と重なる」なら自然に生じる。ロング市場ポートフォリオの投資家は、クラッシュ時に上がりやすいIVへのエクスポージャーを欲しがるため、long optionの価格を押し上げる。その結果、デルタだけを消したlong optionは平均的に保険料を支払う。

ただし、これはlong straddleやlong gammaが常に損だという主張ではない。ジャンプ、vanna、離散ヘッジ誤差、bid-ask、event risk、取引タイミングが実現損益を大きく左右する。ここで識別しているのは、特定期間・市場の平均的なリスク補償である。

## 6. 限界と批判点

1. 実務のdeltaはモデル依存で、離散ヘッジ・bid/ask・market impactを完全には除去できない。
2. 負の平均損益はVRPと整合するが、jump risk premium、stochastic correlation、流動性制約を完全に分離する因果推定ではない。
3. 1988-1995年のSPX市場構造を、電子化後のSPXW・0DTE・ETF optionへ直接外挿できない。
4. 手元PDFは2001年の前稿である。引用・数値照合は2003年の公刊版を優先する。

## 7. 次に検討したい問い

1. VIX、variance swap、delta-hedged optionのVRP推定は、同一日のrisk-neutral情報でどこまで一致するか。
2. 0DTEの高gamma・charmを明示的に入れると、日中のデルタヘッジ損益とVRPの関係はどう変わるか。
3. 顧客・マーケットメーカー別の在庫データがあれば、保険需要とdealer inventory premiumを分けられるか。
