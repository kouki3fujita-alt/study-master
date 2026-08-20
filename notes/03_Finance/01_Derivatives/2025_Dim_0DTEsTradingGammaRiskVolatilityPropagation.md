# 0DTEs: Trading, Gamma Risk and Volatility Propagation — Dim, Eraker, and Vilkov (2025)

## 書誌情報

- **論文**: Chukwuma Dim, Bjørn Eraker, Grigory Vilkov, “0DTEs: Trading, Gamma Risk and Volatility Propagation”
- **版**: SSRN 4692190、2025年6月6日改訂版、58ページ
- **SSRN**: [Abstract 4692190](https://ssrn.com/abstract=4692190)
- **リポジトリ内PDF**: [2025_Dim_0DTEsTradingGammaRiskVolatilityPropagation_SSRN4692190.pdf](../../../papers/03_Finance/01_Derivatives/2025_Dim_0DTEsTradingGammaRiskVolatilityPropagation_SSRN4692190.pdf)
- **キーワード**: 0DTE、SPX、SPY、market maker inventory gamma、delta hedging、intraday volatility

## 1. 研究質問と結論

SPXの0DTE取引の拡大は、ディーラーのデルタヘッジを通じて指数の変動を増幅しているのか、それとも市場を安定化しているのかを検証する。

結論は、推定されたマーケットメーカーの0DTE net gammaは平均的に正であり、より正のgammaはその後の日中ボラティリティ低下と結び付く、というものだ。正gammaならディーラーは上昇後に売り、下落後に買うため、日中のモメンタムを弱め反転を強める。負gamma局面には増幅の余地があるものの、標本全体を「0DTEが常に不安定化させる」と読む証拠ではない。

## 2. ガンマ・チャネル

小区間のデルタ変化は、主項だけを残せば

```math
d\Delta \simeq S\Gamma\,r
```

であり、ドルgammaを \(\$\Gamma=S^2\Gamma\) とすると、デルタを戻すための現物取引は

```math
\$\Delta \simeq \$\Gamma\,r
```

と書ける。ここで (r>0\) の後、

- **net gamma > 0** のディーラーは現物を売るため、上昇を抑え、下落後には買って反転を強める。
- **net gamma < 0** のディーラーは現物を買うため、上昇を追い、下落後には売ってモメンタムとボラティリティを増幅し得る。

ただし同じ「負gammaと将来高ボラティリティ」という相関は、私的情報を持つ顧客が先にoptionを買った場合にも生じる。著者らはこれをinformation channelと呼び、gamma channelと区別するためにcontrols、IV、ニュース前後の検定を行う。

## 3. データと識別

- **銘柄**: SPX、SPXW、SPY。0DTEと残存1日-1か月の長めのoptionを比較。
- **データ**: Cboe DataShopの30分bar、C1のopen-close trader-type別volume、約定データ。
- **期間**: bar・約定データは2012年-2024年4月、C1のtrader-type別open-closeデータは2021年-2023年6月。
- **変数**: optionごとのopen interest、delta、gammaから日中net gammaを再構成。高次のspeed/charmもrobustnessで確認。
- **設計**: 将来realized log varianceをnet gammaで説明し、時間帯固定効果、過去variance・return・volumeを制御。さらにinstrumental-variable、公開情報でgammaを予測できるか、重要ニュース前にgammaが変わるかを調べる。

在庫は個別ディーラーの帳簿を直接観測したものではなく、取引者区分・建玉・フローから構成した測定量である点が重要である。

## 4. 主要結果

1. 0DTE net gammaが1標準偏差上がると、将来のunderlying log varianceは **0.073標準偏差低下**する。これは残存1日-1か月optionのnet gammaに対する効果の約32%に相当する。
2. 標本の大半でマーケットメーカーは0DTEを**正gamma**で保有している。負gammaによる潜在的なvariance増幅はあり得るが、正gammaによる減衰効果より推定上65%小さい。
3. high gamma状態とlow gamma状態の間で日中momentum戦略の平均収益差は約 **10 bp/時**。high gammaでは反転、low gammaではモメンタムが強い。
4. 0DTE volumeの大きなjumpは、過去リターンを有意に伝播させない。0DTEと現物の同時取引量相関は2021年以前の0.25-0.30から2023-24年に0.58へ上がるが、それだけでは不安定化を意味しない。

## 5. 解釈上の注意

- **OIだけから符号は決まらない**: 顧客がlongかshortか、誰が反対側を持つか、dealerがどこまでdelta-neutralかは公開OIでは分からない。本論文のnet gammaは詳細なCboeデータと仮定を用いる測定である。
- **相関と因果を混同しない**: IVやnews検定はinformation channelへの反証を強めるが、全ての私的情報、OTCヘッジ、cross-asset hedgingを排除するものではない。
- **市場の平均とstressは別**: 平均的に正gammaでも、特定strikeへ巨大な集中があり負gammaへ反転した時間帯のtail riskは、平均係数だけでは評価できない。

## 6. 実務への含意

- 0DTE出来高の大きさを、それだけで「selloffを増幅する短gamma」と読まない。net gamma、moneyness、満期時刻、現物流動性、他満期の在庫を併せて見る。
- 日中のmean reversion戦略はpositive gamma局面と整合的だが、event timeではcharm、speed、流動性枯渇により関係が変わり得る。
- リスク管理では、日次OIだけでなくintraday position changeと、SPX・SPY・ES間のヘッジ代替を追う必要がある。

## 7. 次に検討したい問い

1. 2024年以降の0DTE比率上昇後も、正gamma優勢という結果は維持されるか。
2. ES先物、SPY、SPXのヘッジ先選択を直接観測すると、gamma channelの推定量はどう変わるか。
3. FOMC・CPI・オプション満期時刻で分けた場合、負gamma局面のtail propagationは平均より大きいか。
