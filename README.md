# study-master

研究論文のPDF、実務記事の参照情報、再読・実装・発展研究に使うための議論ノートを管理するリポジトリです。

## ディレクトリ構成

```text
papers/                         # 手元で管理する論文PDF
├─ 01_AI/
│  ├─ 01_LLM/
│  ├─ 02_RAG/
│  └─ 03_Agent/
├─ 02_Systems/
│  ├─ 01_Distributed/
│  └─ 02_Database/
├─ 03_Finance/
│  ├─ 01_Derivatives/
│  ├─ 02_Fixed_Income/
│  └─ 03_Systematic_Trading/
└─ 99_Others/

articles/                       # Web記事・実務解説の参照情報
└─ 03_Finance/
   └─ 01_Market_Microstructure/

notes/                          # 議論・要約・批判的検討
└─ 03_Finance/
   ├─ 01_Derivatives/
   ├─ 03_Systematic_Trading/
   └─ 04_Practitioner_Articles/
```

PDFの命名規則は `YYYY_FirstAuthor_ShortTitle.pdf` とします。例: `2009_Carr_VarianceRiskPremiums.pdf`。
記事参照ファイルの命名規則は `YYYY_Source_ShortTitle.md` とし、本文全文は複製せず、原文URLと分析ノートへのリンクを保存します。

## ノートの収録項目

各ノートには、必ず次の項目を収録します。

- 論文名・記事名、著者・発行者、掲載誌・媒体、原文リンク
- 問題意識と結論の短い要約
- 中核となるアイデアと数式
- データと実証設計
- 主要結果
- 解釈上の注意、限界、批判点
- 次に検討すべき問い

## 論文一覧

### クオンツ運用・CTA・モメンタム

| 分野 | 論文 | 著者 | 掲載年 | 一言でいうと |
|---|---|---|---:|---|
| CTA・トレンドフォロー | [The Risk in Hedge Fund Strategies: Theory and Evidence from Trend Followers](notes/03_Finance/03_Systematic_Trading/2001_Fung_Hsieh_RiskTrendFollowers.md) | William Fung, David A. Hsieh | 2001 | トレンドフォロー収益をルックバック・ストラドル型の非線形ペイオフとして捉え、通常の資産指数よりPTFSがCTA収益をよく説明することを示す |
| 農産物先物・COT | [The Adequacy of Speculation in Agricultural Futures Markets: Too Much of a Good Thing?](notes/03_Finance/03_Systematic_Trading/2008_Sanders_AdequacySpeculationAgriculturalFutures.md) | Dwight R. Sanders, Scott H. Irwin, Robert P. Merrin | 2008（2010年公刊版あり） | COT/CIT/BPデータで指数ファンド拡大後もWorkingのspeculative indexは概ね歴史的範囲内にあり、投機抑制はヘッジ流動性の便益と比較すべきだと示す |
| COT・先物ポジショニング（実務書） | [The Commitments of Traders Bible: How to Profit from Insider Market Intelligence](notes/03_Finance/03_Systematic_Trading/2008_Briese_CommitmentsTradersBible.md) | Stephen Briese | 2008 | CFTCのCOTレポートをcommercial hedgers、large speculators、small tradersの実ポジション情報として読み、COT IndexやMovement Indexで市場転換を探す実務フレームを整理する |
| CTA・時系列モメンタム | [Time Series Momentum](notes/03_Finance/03_Systematic_Trading/2012_Moskowitz_TimeSeriesMomentum.md) | Tobias J. Moskowitz, Yao Hua Ooi, Lasse Heje Pedersen | 2012 | 58本の先物・フォワードで過去12か月リターンが次月リターンを正に予測し、CTA/managed futuresのトレンドフォロー収益源を横断資産で示す |
| 日中モメンタム・ヘッジ需要 | [Hedging Demand and Market Intraday Momentum](notes/03_Finance/03_Systematic_Trading/2021_Baltussen_HedgingDemandIntradayMomentum.md) | Guido Baltussen, Zhi Da, Sten Lammers, Martin Martens | 2021 | 60本超の先物で引け直前30分リターンがその日ここまでのリターンに正に予測され、short gammaやレバレッジETFのヘッジ需要が一時的価格圧力を生むことを示す |
| DeFi・AMM市場構造 | [Automated Market Making and Loss-Versus-Rebalancing](notes/03_Finance/03_Systematic_Trading/2024_Milionis_AutomatedMarketMakingLVR.md) | Jason Milionis, Ciamac C. Moallemi, Tim Roughgarden, Anthony Lee Zhang | 2024 | AMM LPの逆選択コストをrebalancing strategyとの差分であるLVRとして定義し、価格ボラティリティと限界流動性からLP損失・手数料設計を評価する |
| CTA・市場マイクロストラクチャー | [Is Trend Still Your Friend?: A Microstructural Account of the Demise of Short-Term Trend-Following](notes/03_Finance/03_Systematic_Trading/2026_Kurth_DemiseShortTermTrendFollowing.md) | Jutta G. Kurth, Zoltan Eisler, Adam Rej, Jean-Philippe Bouchaud | 2026 | 2008年以降の短期トレンド崩壊がsmall-tick先物に集中し、HFT流動性の引き上げが自己実現的なprice-impact loopを断ったというマイクロストラクチャー仮説を示す |

### デリバティブ・オプション・ボラティリティ

| 分野 | 論文 | 著者 | 掲載年 | 一言でいうと |
|---|---|---|---:|---|
| 株式ボラティリティ・非対称性 | [Asymmetric Volatility and Risk in Equity Markets](notes/03_Finance/01_Derivatives/1997_Bekaert_AsymmetricVolatilityRiskEquityMarkets.md) | Geert Bekaert, Guojun Wu | 1997（2000年公刊版あり） | Nikkei 225構成銘柄で負リターン後にボラティリティと共分散が非対称に上がる現象を検証し、leverage effectよりvolatility feedbackの説明力が大きいことを示す |
| ボラティリティ予測 | [The Relation between Implied and Realized Volatility](notes/03_Finance/01_Derivatives/1998_Christensen_Prabhala_ImpliedRealizedVolatility.md) | Bent Jesper Christensen, Nagpurnanand R. Prabhala | 1998 | 非重複月次標本と測定誤差補正により、OEX ATM IVが過去RVを上回り、その情報を包含することを示す |
| オプション期待収益・ボラティリティリスク | [Expected Option Returns](notes/03_Finance/01_Derivatives/2001_Coval_ExpectedOptionReturns.md) | Joshua D. Coval, Tyler Shumway | 2001 | コールとプットの方向リスクを相殺したゼロベータ・ストラドルでも平均約3%の週次損失が残り、システマティックなボラティリティリスクが価格付けされている可能性を示す |
| 相関リスク・デリバティブ | [Option-Implied Correlations and the Price of Correlation Risk](notes/03_Finance/01_Derivatives/2005_Driessen_OptionImpliedCorrelations.md) | Joost Driessen, Pascal Maenhout, Grigory Vilkov | 2005（2009年公刊版あり） | 指数と構成銘柄のモデルフリー・インプライド分散から平均相関を逆算し、相関上昇保険の価格とdispersion tradingの源泉を示す |
| オプション需給・仲介者制約 | [Demand-Based Option Pricing](notes/03_Finance/01_Derivatives/2005_Garleanu_DemandBasedOptionPricing.md) | Nicolae Garleanu, Lasse Heje Pedersen, Allen M. Poteshman | 2005（2009年公刊版あり） | ディーラーがオプションを完全ヘッジできない場合、エンドユーザー需要がヘッジ不能部分の分散・共分散に応じて価格とsmirkへ反映されることを理論・実証で示す |
| 株式リターン予測・分散リスク | [Expected Stock Returns and Variance Risk Premia](notes/03_Finance/01_Derivatives/2007_Bollerslev_ExpectedStockReturnsVarianceRiskPremia.md) | Tim Bollerslev, Hao Zhou | 2007（2009年公刊版あり） | model-free implied varianceと高頻度realized varianceの差が四半期S&P 500超過リターンを強く予測し、市場全体のrisk aversion proxyとして機能することを示す |
| オプション注文フロー・情報取引 | [Volatility Information Trading in the Option Market](notes/03_Finance/01_Derivatives/2008_Ni_VolatilityInformationTradingOptionMarket.md) | Sophie X. Ni, Jun Pan, Allen M. Poteshman | 2008（2005年SSRN稿） | 非マーケットメーカーのvega加重ネット・ボラティリティ需要が将来実現ボラティリティを予測し、決算前の情報非対称性が高い局面では価格インパクトも大きくなることを示す |
| 指数オプション収益 | [Understanding Index Option Returns](notes/03_Finance/01_Derivatives/2009_Broadie_UnderstandingIndexOptionReturns.md) | Mark Broadie, Mikhail Chernov, Michael Johannes | 2009 | OTMプット売りの高収益は標準的オプション価格モデルの有限標本分布と比べると必ずしもmispricingではなく、ATMストラドルの方が難しいパズルだと示す |
| ボラティリティ・デリバティブ | [Variance Risk Premiums](notes/03_Finance/01_Derivatives/2009_Carr_VarianceRiskPremiums.md) | Peter Carr, Liuren Wu | 2009 | オプションから合成した分散スワップ・レートと実現分散を比較し、市場分散の保険料を直接測定する |
| 日経225オプション・実現ボラティリティ | [Pricing Nikkei 225 Options Using Realized Volatility](notes/03_Finance/01_Derivatives/2011_Ubukata_PricingNikkei225OptionsRealizedVolatility.md) | Masato Ubukata, Toshiaki Watanabe | 2011（2014年公刊版あり） | 高頻度データ由来のrealized volatilityをARFIMAX/HARXでモデル化し、日経225プット価格付けではHansen-Lunde型の非取引時間調整が効くことを示す |
| テールリスク・リターン予測 | [Tail Risk Premia and Return Predictability](notes/03_Finance/01_Derivatives/2015_Bollerslev_TailRiskPremiaReturnPredictability.md) | Tim Bollerslev, Viktor Todorov, Lai Xu | 2015 | 分散リスク・プレミアムの予測力の多くが、OTMプットに表れる左側ジャンプテール補償、すなわちmarket fearsに由来することを示す |
| 個別株オプション・情報取引 | [What Does the Individual Option Volatility Smirk Tell Us About Future Equity Returns?](notes/03_Finance/01_Derivatives/2010_Xing_OptionVolatilitySmirkEquityReturns.md) | Yuhang Xing, Xiaoyan Zhang, Rui Zhao | 2010 | OTMプットIVとATMコールIVの差が大きい銘柄ほど将来リターンと決算サプライズが悪く、オプション市場の悪材料が現物市場に先行することを示す |
| 商品・分散リスク | [Variance Risk in Commodity Markets](notes/03_Finance/01_Derivatives/2017_Prokopczuk_VarianceRiskCommodityMarkets.md) | Marcel Prokopczuk, Lazaros Symeonidis, Chardin Wese Simen | 2017（2014年稿） | 21商品市場の合成分散スワップを調べ、商品分散リスクが先物価格リスクとは別のリスクであることを示す |
| 暗号資産・分散リスク | [The Bitcoin VIX and Its Variance Risk Premium](notes/03_Finance/01_Derivatives/2021_Alexander_Imeraj_BitcoinVIX.md) | Carol Alexander, Arben Imeraj | 2021 | DeribitオプションからBitcoin VIXの期間構造とVRPを構築し、ジャンプ誤差と危機時の分散投資便益を検証する |
| 暗号資産オプション・流動性 | [Illiquid Bitcoin Options](notes/03_Finance/01_Derivatives/2022_Guo_IlliquidBitcoinOptions.md) | Yang Guo, Jiasun Li, Mei Luo, Yintian Wang | 2022 | LedgerXの規制下Bitcoinオプションは株式オプションより約10倍非流動的で、投資家がネット売り手のため非流動性と売り注文不均衡が後続デルタヘッジ収益のプレミアムを強めることを示す |
| 社債・分散リスク | [Synthetic Options and Implied Volatility for the Corporate Bond Market](notes/03_Finance/01_Derivatives/2023_Chen_SyntheticCorporateBondOptions.md) | Steven Shu-Hsiu Chen, Hitesh Doshi, Sang Byung Seo | 2023 | CDXスワップションから社債指数オプションとCBVIXを合成し、社債VRPを測定する |
| 暗号資産・インバースオプション | [Valuation and Hedging of Cryptocurrency Inverse Options](notes/03_Finance/01_Derivatives/2024_Lucic_ValuationHedgingCryptoInverseOptions.md) | Vladimir Lucic, Artur Sepp | 2024 | Deribit等で使われるコイン建てinverse optionをフォワード・ニュメレール下のvanilla optionとして整理し、USD/Coin会計とデルタヘッジ戦略のリスクプレミアムを検証する |
| VIX・満期補間 | [VIX Maturity Interpolation](notes/03_Finance/01_Derivatives/2024_Andersen_VIXMaturityInterpolation.md) | Torben G. Andersen, Oleg Bondarenko, Maria T. Gonzalez-Perez | 2024 | 月次オプションだけの旧VIXに生じる満期補間誤差を測定し、週次オプション導入が30日VIXの誤差を約10分の1へ縮小した一方、VIX9Dには曜日バイアスが残ることを示す |
| 暗号資産・ジャンプリスク | [Jump Risk Premia in the Presence of Clustered Jumps](notes/03_Finance/01_Derivatives/2025_Liu_JumpRiskPremiaClusteredJumps.md) | Francis Liu, Natalie Packham, Artur Sepp | 2025 | 正負ジャンプの群発を二変量Hawkes過程でモデル化し、BTCのジャンプ・プレミアを先物ベーシスとオプション収益へ結び付ける |
| VIX・指数算出方法（公式資料） | [Cboe Volatility Index Mathematics Methodology](notes/03_Finance/01_Derivatives/2026_Cboe_VolatilityIndexMathematicsMethodology.md) | Cboe | 2026 | VIX型指数をOTMオプション群から構築する分散複製式、一定満期補間、金利処理、気配値フィルターを定める公式数学仕様 |

### ポートフォリオ理論・ファクター・リスクモデル

| 分野 | 論文 | 著者 | 掲載年 | 一言でいうと |
|---|---|---|---:|---|
| 金融計量・相関モデル | [Ten Things You Should Know about the Dynamic Conditional Correlation Representation](notes/03_Finance/01_Derivatives/2013_Caporin_TenThingsDCC.md) | Massimiliano Caporin, Michael McAleer | 2013 | DCCを厳密なモデルではなくフィルターとして捉えるべき理由を10の理論的・実証的注意点から整理する |
| ボラティリティ・ターゲティング | [The Impact of Volatility Targeting](notes/03_Finance/03_Systematic_Trading/2018_Harvey_ImpactVolatilityTargeting.md) | Campbell R. Harvey, Edward Hoyle, Russell Korgaonkar, Sandy Rattray, Matthew Sargaison, Otto Van Hemert | 2018 | 60超の資産を検証し、逆ボラティリティ調整は株式・クレジットのSharpe ratioを改善する一方、より普遍的な効果はテールとvol of volの抑制だと示す |

### イベントドリブン・市場マイクロストラクチャー・注文フロー

| 分野 | 論文 | 著者 | 掲載年 | 一言でいうと |
|---|---|---|---:|---|
| 市場マイクロストラクチャー | [Futures Markets, Regulation and Volatility](notes/03_Finance/01_Derivatives/1994_Bacha_FuturesMarketsRegulationVolatility.md) | Obiyathulla Bacha, Anne Fremault Vila | 1994 | 日経225先物の複数市場への上場を利用し、先物導入・規制・満期日が現物ボラティリティへ与える影響を検証する |
| 決算イベント・オプション | [Earnings Announcements and Equity Options](notes/03_Finance/01_Derivatives/2004_Dubinsky_Johannes_EarningsAnnouncementsEquityOptions.md) | Andrew Dubinsky, Michael Johannes | 2004/2006 | 既知時刻の決算ジャンプをIV期間構造から抽出し、イベントジャンプを入れると短期オプションの価格誤差が大幅に縮小することを示す |
| 満期日・株価ピニング | [Stock Price Clustering on Option Expiration Dates](notes/03_Finance/01_Derivatives/2005_Ni_StockPriceClusteringOptionExpiration.md) | Sophie Xiaoyan Ni, Neil D. Pearson, Allen M. Poteshman | 2005 | 個別株オプション満期日に原資産終値が権利行使価格付近へ集まりやすく、デルタヘッジ再調整とオプション・ライターによる操作がその一因であることを示す |
| 空売りデータ・市場構造（当局資料） | [Understanding Short Sale Volume Data on FINRA’s Website](notes/03_Finance/03_Systematic_Trading/2019_FINRA_UnderstandingShortSaleVolume.md) | FINRA | 2019 | FINRAのshort sale volumeは公開取引フローであり、short interestというポジション残高ではなく、取引所データとの統合と報告構造の理解が不可欠だと説明する |
| オプション起点流動性（実務レポート） | [The Implied Order Book](notes/03_Finance/01_Derivatives/2020_SqueezeMetrics_ImpliedOrderBook.md) | SqueezeMetrics / GEX Ed. | 2020 | SPXオプション建玉からDDOI、GEX、VEX、GEX+を推定し、ディーラーの条件付きデルタヘッジ需要を「暗黙の板」として可視化する枠組みを示す |
| オプション・ヘッジ再調整 | [Does Option Trading Have a Pervasive Impact on Underlying Stock Prices?](notes/03_Finance/01_Derivatives/2020_Ni_PervasiveImpactOptionTrading.md) | Sophie Xiaoyan Ni, Neil D. Pearson, Allen M. Poteshman, Joshua S. White | 2020 | 個別株オプションのネット・ガンマを価格変化とポジション変化へ分解し、負のガンマ時のマーケットメーカー再ヘッジが原資産の変動と大幅価格変化を増幅する非情報経路を検証する |
| 市場構造・規制（当局レポート） | [Staff Report on Equity and Options Market Structure Conditions in Early 2021](notes/03_Finance/01_Derivatives/2021_SEC_EquityOptionsMarketStructureEarly2021.md) | SEC Staff | 2021 | 2021年1月のGameStop急騰をCAT等の当局データで検証し、ショートスクイーズが主因ではなくガンマスクイーズの証拠もないこと、取引制限がNSCC証拠金への反応であったことを示す |
| リテール・オプション取引 | [A Real Cost of Free Trades: Retail Option Trading Increases the Volatility of Underlying Securities](notes/03_Finance/01_Derivatives/2023_Lipson_RealCostFreeTradesRetailOptions.md) | Marc L. Lipson, Davide Tomio, Jiang Zhang | 2023（2026年改訂） | Robinhoodの手数料無料オプション導入を外生ショックとして、小売オプション取引がディーラーの動的ヘッジを通じて原資産ボラティリティを高め、流動性改善と価格発見低下を同時にもたらすことを示す |
| 0DTE・顧客指値注文（当局WP） | [Hope at a Reasonable Price: Customer Use of Limit Orders in the 0DTE Market](notes/03_Finance/01_Derivatives/2025_Fu_HopeReasonablePrice0DTE.md) | Lei Fu, Su Li, David K. Musto, Neil D. Pearson | 2025 | SPXW 0DTE市場で顧客がNMLOを使ってBBO上・BBO内で流動性供給し、広いquoted spreadから見えるほど高コストではないことをOPRAデータ補正後に示す |
| 0DTE・ディーラーガンマ | [0DTE Index Options and Market Volatility: How Large is Their Impact?](notes/03_Finance/01_Derivatives/2025_Amaya_0DTEIndexOptionsMarketVolatility.md) | Diego Amaya, Pedro A. Garcia-Ares, Neil D. Pearson, Aurelio Vasquez | 2025 | Cboe全取引記録からOMM集計ガンマを復元し、平均的なデルタヘッジは変動を抑える一方、負のガンマ局面では日次・30分ボラティリティを増幅するが最大効果も市場全体では異常に大きくないと示す |
| 0DTE・市場構造（取引所レポート） | [0DTEs Decoded: Positioning, Trends, and Market Impact](notes/03_Finance/01_Derivatives/2025_Cboe_0DTEsDecodedPositioningTrendsMarketImpact.md) | Cboe Derivatives Market Intelligence / Mandy Xu | 2025 | SPX 0DTEの出来高成長、リテール/機関推定比率、日中取引パターン、ストレス時の満期別シフト、net gammaに基づく市場影響評価を整理する |
| ガンマスクイーズ・理論モデル | [Beta-Dependent Gamma Feedback and Endogenous Volatility Amplification in Option Markets](notes/03_Finance/01_Derivatives/2025_Dai_BetaDependentGammaFeedback.md) | Haoying Dai | 2025 | デルタヘッジ由来のガンマフィードバックをbeta正規化ショックと結び付け、低beta・高ガンマ露出銘柄で不安定化条件に近づきやすいことを理論モデルで示す |
| 個人投資家・オプション需給 | [Retail Option Traders and the Implied Volatility Surface](notes/03_Finance/01_Derivatives/2026_Eaton_RetailOptionTradersIVSurface.md) | Gregory W. Eaton, T. Clifton Green, Brian S. Roseman, Yanbin Wu | 2026 | 証券会社の障害を外生ショックとして、個人の短期・OTM・コール需要がIVサーフェスを歪めることを示す |

## 記事・実務解説一覧

### 市場構造・流動性・取引所レポート

| 分野 | 記事 | 発行者 | 掲載年 | 一言でいうと |
|---|---|---|---:|---|
| 先物流動性・市場インパクト | [Reassessing Liquidity: Beyond Order Book Depth](notes/03_Finance/04_Practitioner_Articles/2025_CME_ReassessingLiquidityBeyondOrderBookDepth.md) | CME Group | 2025 | 2025年4月の関税ショック局面で、E-mini S&P 500 futuresの流動性をorder book depthだけでなく、出来高、fill quality、price dispersion、square-root impact modelで評価する |

## この論文から伸びる研究テーマ

- Variance risk premium と将来株式リターン
- 指数分散と個別株分散の差、および dispersion trading
- Implied correlation、realized correlation、correlation risk premiumの識別
- 相関スワップ、sector dispersion、相関期間構造と0DTE
- 危機時の相関上昇、分散効果消失、ポートフォリオのストレス相関
- VIX、variance swap、volatility swap の関係
- VIXの離散複製、ストライク打切り、$\Delta K/K^2$ 重みと再現誤差
- 一定満期VIXにおける期間分散補間、分単位の時間計測、金利曲線補間
- VIXの指数レベル・オプション系列レベルの気配値フィルターと高頻度価格発見
- VIX方法書の版変更、ゼロbid・ask除外、長期系列の構造変化
- VIXMOとVIXWEの構造変化、満期補間誤差、total varianceとannualized variance
- VIX9D・VIX1Dの曜日効果、weekend variance、短期オプションの満期グリッド
- ジャンプ、左側テール、vol-of-vol の価格
- 正負ジャンプの自己励起・交差励起、Hawkes過程、時変IVスキュー
- BTCのジャンプ・リスクプレミア、先物ベーシス、funding、デルタヘッジP&L
- 分散リスク・プレミアムの期間構造
- Bitcoin VIX、暗号資産の分散期間構造、危機時の分散投資便益
- ショート・ボラティリティ戦略のテールリスク
- 個人投資家のオプション需要、ディーラー在庫制約、IVサーフェスの形状
- 個別株volatility smirk、OTMプットの情報取引、将来株式リターンと決算サプライズ
- インプライド・ボラティリティの実現ボラティリティ予測力、情報包含、測定誤差
- 重複予測窓、HAC・操作変数法、1987年暴落前後の構造変化
- オプション期待収益、暗黙のレバレッジ、Black–Scholes betaとCAPMの整合性
- ゼロベータ・ストラドル、ボラティリティ因子、クラッシュ中立化とpeso problem
- delta-hedged option return、gamma・vegaスケーリング、取引コストと証拠金制約
- 決算expected move、既知時刻ジャンプ、イベント分散リスク・プレミアム
- 決算前後のIV crush、カレンダースプレッド、確率的ボラティリティとの識別
- 0DTE・短期オプションの注文フローとIV期間構造
- OMM集計ガンマ、デルタヘッジ・フロー、S&P 500先物の一分実現ボラティリティ
- 正・負のディーラーガンマが市場変動を吸収・増幅する非対称性
- 0DTE出来高、系列別ネットポジション、ガンマスクイーズの識別
- gamma、vanna、charm、speedを使った満期直前ヘッジ需要の推定
- 株価指数先物の導入と現物市場ボラティリティ
- 証拠金・値幅制限・取引方式が価格発見と市場安定性へ与える影響
- DCC、BEKK、GARCCによる時変共分散・相関モデリング
- 二段階推定、モデルの正則条件、相関予測のout-of-sample比較
- ミーム株、ソーシャルメディア、個人投資家の集団的取引と価格形成
- ショートスクイーズ、ガンマスクイーズ、空売り制約とバブル
- 空売り残高の再貸出による100%超、フェイル・トゥ・デリバー、裸空売りの識別
- FINRA short sale volumeとshort interestの識別、フローとポジション残高の違い
- 取引所外出来高、trade reporting facility、取引所データの統合
- ディーラー仲介、公開対象外の相殺取引、空売り比率の測定誤差
- PFOF、注文フローのセグメンテーション、内部化と執行品質の測定
- 清算機関の証拠金モデル、日中マージンコール、決済サイクル短縮（T+1）
- LULD、サーキットブレーカー、ボラティリティ急騰時の板の厚みとスプレッド
- 均等ウェイトETFの組入比率膨張、ETFの空売りとNAV乖離
- CTA・トレンドフォローの非線形ベータ、正の歪度、危機時分散
- ルックバック・ストラドル、時系列モメンタム、ブレイクアウト戦略の対応関係
- PTFSによる戦略ベースのファクター分析とファンド別ベンチマーク
- 短期トレンド収益の2008–2009年構造変化、signal horizon別alpha decay、CTA capacity
- volatility-normalised tick size、板の疎密、HFTによるdepth withdrawal
- trend signal・aggressive order flow・price impactの自己実現的フィードバック
- market orderのslippageとlimit orderのmissed-opportunity cost・fill biasの比較
- ボラティリティ・ターゲティング、leverage effect、暗黙の短期モメンタム
- 逆ボラティリティ・サイジングがtail risk、vol of vol、最大ドローダウンへ与える効果
- CTA・risk parityにおける方向シグナルとリスク・スケーリングの収益分解

## 表記上の注意

Variance risk premium は文献によって符号が逆です。Carr and Wu (2009) は

```math
RP_{t,T}=RV_{t,T}-SW_{t,T}
```

と定義するため、分散ロングが保険料を支払う通常の状態では負になります。近年よく使われる

```math
VRP_t=SW_{t,T}-E_t^P[RV_{t,T}]
```

という定義では、同じ現象が正の値になります。各ノートでは、必ず採用した符号規約を明示します。
