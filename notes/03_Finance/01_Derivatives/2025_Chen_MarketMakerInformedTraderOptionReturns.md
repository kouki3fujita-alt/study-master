# Market Maker or Informed Trader? Who Drive the Relationship Between Option Trading and Underlying Returns? — Chen et al. (2025)

## 書誌情報

- **論文**: Haiqiang Chen, Zimin Cheng, Yingxing Li, and Xiaoqun Liu, “Market Maker or Informed Trader? Who Drive the Relationship Between Option Trading and Underlying Returns? Evidence From Shanghai Stock Exchange 50 ETF Options”
- **掲載誌**: *Journal of Futures Markets*, Vol. 45, pp. 2377-2402, 2025
- **DOI**: [10.1002/fut.70038](https://doi.org/10.1002/fut.70038)
- **手元PDF**: [2025_Chen_MarketMakerInformedTraderOptionReturns.pdf](../../../papers/03_Finance/01_Derivatives/2025_Chen_MarketMakerInformedTraderOptionReturns.pdf)（26ページ、公刊版）
- **キーワード**: SSE 50 ETF options、order imbalance、delta hedging、gamma exposure、return reversal、market maker inventory

## 1. 一言でいうと

SSE 50 ETF optionの新規建てorder imbalanceは、callなら同日のETFリターンと正、putなら負に関係するが、翌期には素早く反転する。著者らは、この反転を情報トレーダーによる永続的価格発見よりも、マーケットメーカーのdelta hedgeが生む一時的な在庫・価格圧力として解釈する。

## 2. 注文不均衡と識別仮説

```math
CallOIB_t=
\frac{\sum_i(BuyVol^{call}_{i,t}-SellVol^{call}_{i,t})}
{\sum_i(BuyVol^{call}_{i,t}+SellVol^{call}_{i,t})}.
```

顧客のcall買いが増えると、反対側のマーケットメーカーはshort callとなり、デルタを中立化するためETFを買う。著者らは同時点と1期遅れのcall/put OIBをETF open-to-close returnへ回帰し、正の同時効果と負の翌期効果をhedging pressureの証拠として検証する。

## 3. データと設計

- **市場・期間**: SSE 50 ETF options、2015年2月9日-2025年2月9日、2,427取引日。
- **データ**: WINDの包括的なoption transaction-level dataと市場変数。
- **絞り込み**: 新規建て取引を中心に集計し、残存7日未満・100日超の契約、裁定条件に合わない契約を除外。
- **統制**: term spread、SSE Composite historical volatility、ETF turnover、Amihud illiquidity、put-call ratio、option-to-stock volume ratio、IV spread、smirk。
- **追加検証**: delta-weighted OIB、strike-to-spot weighting、out-of-sample strategy、5分realized volatility、OIからのmarket-maker net gamma推定、SSE ETF optionsへのpanel拡張。

## 4. 主な結果

1. call OIBは同日open-to-close ETFリターンと正、put OIBは負に関係する。
2. call OIBの1標準偏差上昇は同日約+0.59%、翌期約-0.18%と報告され、急速なreversalが確認される。putも対称なパターンだが規模は小さい。
3. reversalはcallで強く、call買いによりmarket makerへ生じるinventory pressureが大きいという解釈と整合する。
4. event study、out-of-sample、dynamic hedging、SSE ETF options panelでも、主結果は概ね維持されると報告する。

## 5. Hu (2014)との重要な対比

Hu (2014)は米国個別株でoption-induced imbalanceの効果が長期に反転しないことから情報経路を支持した。本論文は中国ETF市場で短期reversalを重視し、inventory hedge経路を支持する。商品、取引主体、買い/売り主導の定義、満期構造、流動性、測定頻度によって、情報とヘッジ圧力の相対的重要性が異なることを示す比較対象として扱うべきである。

## 6. 限界と実務への注意

1. OIBをmarket-maker inventory pressureのproxyとみなすため、顧客の既存ヘッジ、OTC、自己ヘッジ、multi-leg nettingを直接は観測しない。
2. 同日・翌期のreversalは因果的なdelta hedgeの完全な証明ではなく、流動性供給、ニュース反応、非同期取引でも生じ得る。
3. SSE 50 ETFの制度と中国のT+1株式決済は、米国の個別株・SPX 0DTEと異なる。
4. OIだけからnet gamma符号を推定する部分は顧客側のnet long/short仮定に依存する。

## 7. 実務への含意

- option flowの予測を使うなら、永続的information signalか一時的hedging pressureかを、リターンの反転ホライズンで分けて検証する。
- call/put契約数ではなく、signed delta、maturity、moneyness、流動性、既存gammaを別々に集計する。
