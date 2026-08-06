# What Does the Individual Option Volatility Smirk Tell Us About Future Equity Returns?

## 書誌情報

- **論文名**: *What Does the Individual Option Volatility Smirk Tell Us About Future Equity Returns?*
- **著者**: Yuhang Xing, Xiaoyan Zhang, Rui Zhao
- **掲載誌**: *Journal of Financial and Quantitative Analysis*, 45(3), 641–662
- **発行年**: 2010年6月
- **DOI**: https://doi.org/10.1017/S0022109010000220
- **JSTOR**: https://www.jstor.org/stable/40930471
- **リポジトリ内PDF**: [2010_Xing_OptionVolatilitySmirkEquityReturns.pdf](../../../papers/03_Finance/01_Derivatives/2010_Xing_OptionVolatilitySmirkEquityReturns.pdf)
- **キーワード**: volatility smirk, implied volatility, informed trading, OTM put, return predictability, earnings surprise

## 一言でいうと

個別株オプションのOTMプットIVがATMコールIVよりどれだけ高いかを `SKEW` として測ると、smirkが急な銘柄ほど翌週から数か月先の株式リターンが低い。著者らは、悪材料を持つ情報トレーダーがレバレッジと空売り制約回避のためOTMプットを買い、その情報を現物株市場がゆっくり織り込むためだと解釈する。

## 1. 問いと直感

通常、同一満期の個別株オプションでは、低い権利行使価格のプットほどインプライド・ボラティリティ（IV）が高い。この左下がりの形をvolatility smirkと呼ぶ。本論文の問いは、smirkが単なるリスク中立分布や保険需要の形状なのか、それとも将来の現物株リターンに関する情報を含むのか、である。

情報を持つ投資家に悪材料がある場合、現物株を空売りする代わりにOTMプットを買うことがある。プットは少ない元本で大きな下方エクスポージャーを得られ、空売り制約も避けやすい。その買い需要がOTMプット価格とIVを押し上げる一方、現物市場が情報を直ちに反映しなければ、急なsmirkの後に株価が下落するはずである。

## 2. SKEWの定義

銘柄 $i$、週 $t$ の指標は次式である。

```math
SKEW_{i,t}=VOL^{OTMP}_{i,t}-VOL^{ATMC}_{i,t}.
```

- $VOL^{OTMP}$: OTMプットの平均IV。moneyness $K/S$ は0.80以上0.95未満
- $VOL^{ATMC}$: ATMコールの平均IV。moneyness $K/S$ は0.95以上1.05未満
- 満期: 10日以上60日以下

`SKEW` が大きいほどOTMプットがATMコールに対して割高で、左側のsmirkが急である。論文は水準差を採用しており、IV比率やrisk-neutral skewnessとは別の指標である。

## 3. データと標本

- **標本期間**: 1996年1月–2005年12月
- **オプション**: OptionMetrics
- **株価・リターン**: CRSP
- **財務情報**: Compustat
- **アナリスト予想**: IBES
- **頻度**: 毎週水曜日にsmirkを測定し、翌週以降のリターンを検証
- **標本規模**: 週平均約840社

主な品質フィルターは、株価5ドル超、IVが3%–200%、オプション価格のbid-ask midpointが0.125ドル超、open interestが正、残存満期10–60日である。異なる満期のオプションがある場合は、満期までの日数で重み付けして近い期間へ調整する。

標本の90%以上で `SKEW` は正である。平均6.40%、中央値4.76%、25パーセンタイル2.40%、75パーセンタイル8.43%であり、個別株にも左側smirkが広く存在する。

## 4. 実証方法

### 4.1 Fama–MacBeth横断面回帰

翌週の株式リターンを `SKEW` と既知のリターン予測変数へ回帰する。統制変数には、企業規模、book-to-market、過去リターン、株式出来高、オプション出来高・open interest、ATM IV、IV変化、risk-neutral skewnessなどを含める。

```math
R_{i,t+1}=a_t+b_tSKEW_{i,t}+\gamma_t'X_{i,t}+\varepsilon_{i,t+1}.
```

### 4.2 ポートフォリオ・ソート

毎週、銘柄を `SKEW` の低い順に5分位へ分け、翌週のvalue-weighted returnを測る。主要戦略はlow-SKEW銘柄を買い、high-SKEW銘柄を売るロング・ショートである。Fama–French 3ファクターalphaも計算する。

### 4.3 情報内容の検証

単なるリスクプレミアムではなく悪材料を表すかを確かめるため、将来のunexpected earningsとstandardized unexpected earningsをsmirk別に比較する。

## 5. 主要結果

### 5.1 Smirkが急な銘柄ほど翌週リターンが低い

Fama–MacBeth回帰における `SKEW` の係数は、単変量で−0.0061（t=−2.50）、10個の統制変数を含めると−0.0089（t=−3.86）である。サイズ、value、momentum、IV水準、オプション流動性などでは説明されない。

### 5.2 経済的な大きさも大きい

low-SKEW quintileを買い、high-SKEW quintileを売ると、Fama–French 3ファクターalphaは週21bp、年率10.90%（t=2.93）。未調整の年率リターン差も9.19%である。論文要旨の「最も急なsmirkの銘柄は最も緩い銘柄を年率10.9%下回る」という結論に対応する。

ただし、これは取引費用、short borrow、オプションデータのリアルタイム取得費用を控除する前のポートフォリオ結果であり、そのまま実行可能収益とは限らない。

### 5.3 予測力は数か月続く

予測係数は先へ行くほど小さくなるが、約24週先まで負で有意である。ポートフォリオを8–28週保有する設計でも、low-minus-highのリスク調整後収益は年率およそ6–7%残る。`SKEW` 自体は持続的で、AR(1)係数は0.660だが、8週ラグでは約0.20まで低下する。

この持続性は、情報が一週間だけのノイズではないことを示す一方、同じ情報を毎週繰り返し観測している可能性にも注意が必要である。

### 5.4 将来の悪い決算ニュースを予測する

high-SKEW企業は、その後4–24週にわたりlow-SKEW企業より悪いearnings surpriseを示す。これはsmirkが単なる平均的な下方保険料ではなく、企業固有の悪材料を含むという情報取引の説明と整合的である。

## 6. Volatility smirkとrisk-neutral skewnessの違い

両者は似ているが同一ではない。

- **Volatility smirk**: 特定moneyness帯のOTMプットIVとATMコールIVの差。局所的で、取引可能な価格差に近い。
- **Risk-neutral skewness**: 複数ストライクのオプション価格から復元したリスク中立分布の第3モーメント。分布全体を集約する。

標本内の相関は−29%にすぎず、完全な代替指標ではない。本論文の小さめの利用可能標本ではrisk-neutral skewnessに有意なリターン予測力がなく、`SKEW` の予測力は残った。

## 7. なぜオプション市場が現物市場に先行しうるのか

1. **レバレッジ**: プットは少額のプレミアムで大きな下落エクスポージャーを持てる。
2. **空売り制約の回避**: 株券調達やuptick ruleなど現物空売りの摩擦を避けられる。
3. **下方見通しの精密な表現**: OTMプットを選べば、予想する下落幅やtail eventへ集中できる。
4. **注文フローの価格反映**: マーケットメーカーは情報取引リスクや在庫リスクをIVへ転嫁する。
5. **市場間の情報伝達の遅れ**: 現物参加者がオプション注文フローを十分観察・解釈しないと、株価への反映が遅れる。

## 8. 実務的な使い方

### 株式選択シグナル

`SKEW` を横断面で標準化し、極端なhigh-SKEW銘柄をnegative-information flagとして使う。単独で売買するより、短期reversal、momentum、earnings revision、short interest、borrow feeなどと組み合わせ、同業種・同サイズで比較する方が実務的である。

### 決算前のイベント監視

決算前にOTMプットIVだけが急上昇した場合、単なる全市場volatility shockではなく企業固有の悪材料を疑う手掛かりになる。ただし、既知の訴訟、FDA判断、M&A、配当、borrow stressもsmirkを動かすため、イベント・カレンダーとの照合が必要である。

### オプション需給の分解

smirk変化を、プット出来高、open interest、dealer gamma/vega、bid-ask spread、short-sale constraintと結び付ければ、情報需要と保険需要をより識別しやすくなる。

## 9. 解釈上の注意と限界

- **SKEWは純粋な確率予測ではない**: 負のジャンプ確率、下落幅、リスク回避、需給プレミアム、流動性が混在する。
- **情報取引の直接観測ではない**: 悪いearnings surpriseとの関連は整合的証拠だが、誰がどの注文を出したかは識別していない。
- **no-arbitrageだけでは予測力を保証しない**: スキューを生成する価格モデルでも、現物とオプションの情報集合が同じなら将来超過収益は必ずしも生じない。
- **取引費用と空売り費用**: high-SKEW銘柄は小型・不透明・借株困難である可能性があり、long-short alphaの実現性を下げる。
- **データ期間**: 1996–2005年で、週次・月次オプション、電子取引、0DTEが普及した現在とは市場構造が異なる。
- **ルックアヘッド管理**: OptionMetricsサーフェス、企業情報、earnings dataの公表時刻を再現しないバックテストは将来情報を混入させやすい。
- **多重検定**: moneyness、満期、形成日、保有期間を変える場合、仕様探索による見かけの有意性を管理する必要がある。

## 10. 再現・拡張の設計

1. 毎週同一曜日の終値で、10–60日満期のOTMプットとATMコールを抽出する。
2. ゼロbid、広すぎるspread、裁定違反、低open interestを除く。
3. forward moneynessを用いる版とspot moneynessを用いる原論文版を比較する。
4. 満期を一定日数へ補間し、銘柄別 `SKEW` を計算する。
5. 業種・時価総額内でrankし、翌週から28週までのリターンを測る。
6. size、value、momentum、reversal、IV、liquidity、short interest、earnings revisionを統制する。
7. bid-ask、market impact、borrow fee、delisting returnを含む実行可能P&Lを作る。
8. earnings、ニュース、注文主体データで情報取引仮説を検証する。

現代的な拡張では、0DTE/週次オプションを別標本にし、retail flowとinstitutional flow、put buyingとput writing、trade directionを識別することが重要である。

## 11. 批判的評価

本論文の強みは、IVサーフェス全体を複雑に推定せず、OTMプットとATMコールのIV差という単純で直観的な指標を、将来リターンと決算ニュースの両方へ結び付けた点にある。結果の符号、期間、情報内容が一貫しており、「オプション市場に先に現れる企業固有情報」という研究分野の基礎的証拠になった。

一方、smirkは価格予測とリスク価格を分離しない。OTMプットの高さは「下落が起きそう」だけでなく、「下落保険が高価」「供給者のバランスシートが逼迫」「借株が難しい」ことでも生じる。したがって、実務では `SKEW` を真の下落確率として読むのではなく、negative-information demand、tail insurance premium、market frictionの合成シグナルとして扱うのが妥当である。

## 12. 次に検討すべき問い

- 2006年以降、特に金融危機、COVID-19、0DTE時代でも予測力は残るか。
- put buyer/seller initiated flowを使うと、価格水準だけの場合より情報性は高まるか。
- borrow feeとshort interestを統制すると、smirkの係数はどこまで残るか。
- 個別株smirkと指数smirk、implied correlationを組み合わせると予測が改善するか。
- earnings、M&A、訴訟、FDAなどイベント別に情報内容は異なるか。
- 機械学習でIV surface全体を使っても、単純な `SKEW` をout-of-sampleで上回れるか。

## BibTeX

```bibtex
@article{XingZhangZhao2010,
  author  = {Xing, Yuhang and Zhang, Xiaoyan and Zhao, Rui},
  title   = {What Does the Individual Option Volatility Smirk Tell Us About Future Equity Returns?},
  journal = {Journal of Financial and Quantitative Analysis},
  volume  = {45},
  number  = {3},
  pages   = {641--662},
  year    = {2010},
  month   = {June},
  doi     = {10.1017/S0022109010000220},
  url     = {https://www.jstor.org/stable/40930471}
}
```
