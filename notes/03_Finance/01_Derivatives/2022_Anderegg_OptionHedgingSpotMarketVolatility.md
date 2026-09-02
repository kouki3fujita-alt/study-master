# The Impact of Option Hedging on the Spot Market Volatility — Anderegg, Ulmann, and Sornette (2022)

## 書誌情報

- **論文**: Benjamin Anderegg, Florian Ulmann, and Didier Sornette, “The Impact of Option Hedging on the Spot Market Volatility”
- **掲載誌**: *Journal of International Money and Finance*, Vol. 124, Article 102627, 2022
- **DOI**: [10.1016/j.jimonfin.2022.102627](https://doi.org/10.1016/j.jimonfin.2022.102627)
- **公開レコード**: [ETH Research Collection](https://doi.org/10.3929/ethz-b-000536212)（published version、CC BY 4.0と表示）
- **キーワード**: FX options、DTCC trade repository、delta hedging、gamma exposure、permanent price impact
- **PDF保存状況**: 指定されたScienceDirect一時URLとETH公開PDFは取得時に403だったため、本文PDFは保存していない。書誌・結論は出版社・ETHの恒久レコードで照合した。

## 1. 一言でいうと

FXオプションのマーケットメーカー（OMM）がショートガンマなら、現物為替を「上がれば買い、下がれば売る」方向へ再ヘッジするため、現物ボラティリティを増幅し得る。本論文はこのフィードバックを線形permanent-impact modelで導き、DTCC取引リポジトリから復元したFXオプションのOMM net gammaを使い、EUR/USDとUSD/JPYで検証する。

## 2. 経済メカニズム

オプション・マーケットメーカーのデルタを $\Delta^{OMM}$ とすると、価格変化に伴う再ヘッジ量は概念的に

```math
dH_t \simeq -\Gamma^{OMM}_t\,dS_t.
```

OMMがショートガンマ（$\Gamma^{OMM}<0$）なら、$dS_t>0$ のとき買い、$dS_t<0$ のとき売るprocyclicalなヘッジとなる。現物市場への線形permanent impactを $\lambda_t dH_t$ と置けば、価格ショックへの有効な増幅率は $\lambda_t\Gamma^{OMM}_t$ に依存し、short gammaでは実現ボラティリティが高く、long gammaでは低くなるという予測が得られる。

この議論は「全OIがディーラーのshort gamma」という仮定ではない。OMMとoption market taker（OMT）の露出差が、実際に現物でネットヘッジすべき量を決める。

## 3. データと設計

- **市場**: EUR/USD、USD/JPYのFXオプションと現物為替。
- **期間**: 2017年10月21日-2018年6月30日。
- **オプション・ポジション**: DTCC trade-repository dataから集計OMMのgamma exposureを復元。
- **モデル**: OMM/OMTの異なるhedge ratioと線形permanent price impactを組み合わせ、gamma exposureからspot volatilityへの条件付き関係を導出。
- **検証**: 復元したOMM gammaとspot realized volatilityの関係を推定し、符号・規模がモデル予測と整合するかを確認する。

## 4. 主な結果

1. 復元したaggregate OMM gammaは負であり、short-gammaヘッジがspot volatilityを増幅する予測と整合する。
2. OMM gamma exposureはspot volatilityに対して高い統計的有意性を持つと報告する。
3. OMM gammaが約 -1兆ドルのとき、EUR/USDのボラティリティは絶対値で約0.7%、USD/JPYでは約0.9%上がるとの推定である。
4. オプション市場のポジションは、情報ショックを発生させなくても、現物市場の価格インパクトを通じて変動を増幅・吸収し得る。

## 5. 実務への含意

- FX optionのgamma exposureは、IV水準だけでなく、spot流動性・ヘッジ実行量と組み合わせて見る。
- short gammaを根拠に方向を断定せず、OMM/OMTの配分、net delta、行使価格集中、spotの市場深度を同時に確認する。
- 公開OIだけでは取引主体の符号とOTC nettingを特定できない。研究のようなrepository-level dataなしに同じOMM gammaを復元したとは言えない。

## 6. 限界と批判点

1. 集計OMM/OMTというモデル化は、複数ディーラー・内部netting・cross-currency hedgeを単純化する。
2. permanent linear impactは便利な近似であり、stress時の流動性枯渇・非線形impactを完全には表さない。
3. 標本は約8か月、2通貨ペアに限られる。別regime・他通貨・上場指数オプションへの外挿は要検証である。
4. 本ライブラリーには本文PDFを保存できていないため、係数の定義・表番号を引用する際は公刊版を再照合する必要がある。

## 7. 関連資料

- Chen et al., [Market Maker or Informed Trader?](2025_Chen_MarketMakerInformedTraderOptionReturns.md): SSE 50 ETFでoption order imbalance後の一時的reversalを検証。
- Dong, [Cross Market Price Discovery and Selective Delta Hedging](2025_Dong_CrossMarketPriceDiscoverySelectiveDeltaHedging.md): 約定形態別に選択的なdelta hedgeを検証。
