# Cross-Sectional Variation of Risk-targeting Option Portfolios — Wu and Xu (2026)

## 書誌情報

- **論文**: Liuren Wu, Yaofei Xu, “Cross-Sectional Variation of Risk-targeting Option Portfolios”
- **掲載誌**: *The Review of Asset Pricing Studies*, Vol. 16, No. 1, pp. 133-161, 2026
- **DOI**: [10.1093/rapstu/raaf012](https://doi.org/10.1093/rapstu/raaf012)
- **SSRN**: [Abstract 4922029](https://ssrn.com/abstract=4922029)
- **手元PDF**: 2024年11月25日版、48ページ。2026年公刊版とは表・組版・最終校正に差があり得る。
- **リポジトリ内PDF**: [2026_Wu_CrossSectionalRiskTargetingOptionPortfolios_SSRN4922029.pdf](../../../papers/03_Finance/01_Derivatives/2026_Wu_CrossSectionalRiskTargetingOptionPortfolios_SSRN4922029.pdf)
- **キーワード**: option portfolios、dimension reduction、vega、gamma、volga、vanna、market price of risk

## 1. 研究質問と結論

銘柄ごとに行使価格・満期・契約数が全く異なる大量の個別株オプションを、比較可能な少数のrisk factorへ圧縮し、その時点のmarket price of riskが将来のoption excess returnを予測するかを問う。

著者らは、各銘柄のoption surfaceをvega、gamma、volga、vannaという4つのrisk-targeting portfoliosに集約する。各時点・各銘柄で得た4つのrisk priceは対応する翌月のdelta-hedged excess returnと正に関係し、そのrisk priceに比例してlong-shortを組むと4次元全てで高いrisk-adjusted returnが得られると報告する。ポイントは、単一strike・単一満期を選ぶ代わりに、surface全体から銘柄固有のrisk exposureを正規化して比較することにある。

## 2. 4次元へのrisk attribution

Black-Scholes-Merton表示 (B(t,S,I)\) でoptionのデルタを消すと、残る局所変動は概念的に

```math
dB- B_S dS
\approx B_I dI
+\frac12 B_{SS}(dS)^2
+\frac12 B_{II}(dI)^2
+B_{SI}dS\,dI
```

となる。4項は順に、

- **vega**: IV水準変化、
- **gamma**: 現物リターンの二次変動、
- **volga**: IV変化の二次変動、
- **vanna**: 現物とIV変化の共分散、

へのcash exposureを表す。歴史的なvariance/covariance forecastで各exposureをrisk-adjustし、銘柄 (i\) の全契約を行、4つのriskを列とする行列 (X_{t,i}\) を作る。time decay (y_{t,i}\) に対し

```math
y_{t,i}=X_{t,i}b_{t,i}+e_{t,i}
```

を回帰し、係数から各riskのmarket priceを推定する。第 (k\) riskのみunit exposure、他をneutralにするportfolio weightは概念的に

```math
w_{t,i,k}=X_{t,i}(X_{t,i}'X_{t,i})^{-1}e_k
```

で構成される。ここでgamma・volgaの係数はzero-premium下の基準値との差として解釈するため、係数水準とrisk premiumの符号を混同しない必要がある。

## 3. データと実証設計

- **データ**: OptionMetricsの米国個別株オプション。
- **期間**: 1996年1月-2021年12月。最初の1年はmoment forecastに使い、月1回、次月の通常満期の30日前に観測する。
- **規模**: 1997-2021年の299か月、3,691銘柄、計16,947,489契約。
- **pricing regression**: 契約群のtime decayを4次元risk exposureへ回帰。
- **return regression**: 同じweightsで翌月のdelta-hedged excess returnを作り、当日のrisk priceが翌月returnを説明するかcross-sectionで検定。
- **期待仮説**: (f_{t+1,k}=a_{t+1,k}+b_{t+1,k}\eta_{t,k}+\varepsilon\) で、理想的には (a=0,b=1\) となる。

## 4. 主要結果

1. 4次元のpricing regressionは高い説明力を持ち、銘柄横断のR-squaredの10-90 percentile rangeは平均96.7%-99.8%、medianは99.2%と報告される。
2. 翌月return regressionでもmedian R-squaredは83.7%で、4次元exposureがcontract-level return variationを大きく圧縮する。
3. 4riskすべてで、事前のmarket price of riskと事後の対応portfolio returnのcross-sectional slopeは正で有意。ただし平均slopeは1未満、interceptも常にゼロではないため、完全なexpectation hypothesisではない。
4. market priceに比例したlong-short portfoliosは、aggregate risk exposureを残す場合・neutralにする場合の双方で正の平均excess returnを示す。

## 5. 解釈と実務的含意

この枠組みは、「IVが高い」「skewが急だ」というsurface全体を一つの印象で扱う代わりに、どのrisk dimensionへどれだけ価格が付いているかを銘柄別に比較可能にする。例えばgammaとvolgaを売り、vannaを買うというaggregateな平均と、個別銘柄のrisk priceは同じではない。aggregate premiumが弱くてもcross-sectionのdispersionが大きければ、横断long-shortの情報源になり得る。

一方でportfolio weightsは多数の契約と推定行列の逆行列に依存する。実運用では、流動性の低いwing、bid-ask、shortability、contract multiplier、greek推定誤差を入れない高い理論上のinformation ratioは、そのまま実現可能収益ではない。

## 6. 限界と批判点

1. BMS greeksとhistorical moment forecastsに依存するため、smile dynamics、jump、liquidity shockのmisspecificationがrisk priceへ混入し得る。
2. 高いin-sample (R^2\) は次期投資可能性を保証しない。return forecastの取引費用後out-of-sample検証が決定的に重要である。
3. cross-sectional price of riskは、リスク補償だけでなくmeasurement errorや一時的mispricingを含み得る。
4. 手元PDFは2024年working versionである。2026年公刊版との数値・表番号を混ぜない。

## 7. 次に検討したい問い

1. 各risk-targeting portfolioを実際のNBBOで執行した後もlong-short returnは残るか。
2. retail flow、dealer inventory、earnings eventを加えると、vega/vanna risk priceのcross-sectional dispersionを説明できるか。
3. 0DTEやcrypto optionにも同じ4次元圧縮が安定して働くか。
