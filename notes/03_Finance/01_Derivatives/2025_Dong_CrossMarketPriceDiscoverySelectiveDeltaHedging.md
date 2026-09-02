# Cross Market Price Discovery and Selective Delta Hedging in the Option Market — Dong (2025)

## 書誌情報

- **論文**: Yunjiang Dong, “Cross Market Price Discovery and Selective Delta Hedging in the Option Market”
- **版**: SSRN Working Paper No. 5529499、2025年9月25日版（2025年10月8日最終改訂）
- **SSRN**: [Abstract 5529499](https://ssrn.com/abstract=5529499)
- **手元PDF**: [2025_Dong_CrossMarketPriceDiscoverySelectiveDeltaHedging_SSRN5529499.pdf](../../../papers/03_Finance/01_Derivatives/2025_Dong_CrossMarketPriceDiscoverySelectiveDeltaHedging_SSRN5529499.pdf)（44ページ）
- **キーワード**: OPRA、TAQ、price discovery、VAR、VECM、market maker、delta hedging、price impact

## 1. 一言でいうと

2020年のS&P 500構成銘柄のOPRA・TAQ約定データで、オプション1約定が5分間に原資産株価を平均0.56bp動かすことを示す。ただし効果は全取引に一様ではなく、single-legかつlimit-order-book（LOB）での方向性取引に集中し、auctionやmulti-leg取引はほぼ吸収される。約定後100ミリ秒以内の株式板活動もこの選別と整合し、マーケットメーカーが全フローではなく必要な取引だけを選択的にデルタヘッジする解釈を支持する。

## 2. データと測定

- **標本**: 2020年1月2日-10月21日のS&P 500構成銘柄。ETF・index optionsは除外。
- **データ**: OPRA option trade/quote、TAQ stock trade/quote、CRSP日次株価。
- **規模**: full sampleは約2.80億option trades。4-6分後に同一契約の取引があるliquid filtered sampleは約1.46億件。
- **価格インパクト**: option約定直後から5分までのunderlying price impact（PIU、bp）を計測。
- **属性**: call/put、moneyness、absolute delta、single-/multi-leg、auction/LOBを区別。VAR/VECMのimpulse responseとinformation share、約定後100msのstock trades・quote updatesも調べる。

## 3. 主な結果

1. 平均5分PIUは0.56bp（約1.55セント）で、株式約定の影響の約6分の1である。
2. price impactはmoneynessとabsolute deltaに単調に強く、single-leg・LOB取引で大きい。auctionはLOB比で5分PIUが0.56bp低い。
3. 100ms内に少なくとも一つの株式tradeまたはquote updateが起きる割合は45%。平均では4.59件、約720株（約9,000ドル）の株式反応が観測される。
4. VECMのinformation shareではoptions市場のaggregateな寄与はefficient-price varianceの3%未満。株式市場が主たる価格発見場所である一方、特定の方向性option tradeは高速な情報・ヘッジ経路になる。

## 4. 実務への含意

「option volumeが大きい」や「市場全体がshort gamma」といった集計指標ではなく、約定がsingle-legか、auctionか、delta exposureがどの程度かを区別して初めてspotへの影響を評価できる。OIや契約数だけから即時のhedge flowを断定することはできない。

## 5. 限界と批判点

1. 2020年のCOVID期かつS&P 500銘柄に限定され、平時・小型株・ETF・0DTEへ一般化できない。
2. 100msの株式反応はdelta hedgeと整合するが、同時情報を見た裁定者やクロスマーケットmarket makerを完全に識別するものではない。
3. 5分後に同契約取引があるfiltered sampleは流動性の高い契約へ選択される。
4. 本文はworking paperであり、公刊前に仕様・数値が改訂され得る。

## 6. 関連資料

- Jianfeng Hu, [Does Option Trading Convey Stock Price Information?](2014_Hu_OptionTradingConveyStockPriceInformation.md): option-induced stock imbalanceを日次で分解し、持続的予測力を情報として解釈。
- Chen et al., [Market Maker or Informed Trader?](2025_Chen_MarketMakerInformedTraderOptionReturns.md): 一時的reversalをinventory hedge経路として検証。
