# Is Trend Still Your Friend?: A Microstructural Account of the Demise of Short-Term Trend-Following — Kurth et al. (2026)

## 書誌情報

- **論文**: Jutta G. Kurth, Zoltan Eisler, Adam Rej, and Jean-Philippe Bouchaud, “Is Trend Still Your Friend?: A Microstructural Account of the Demise of Short-Term Trend-Following”
- **種別**: arXiv preprint, q-fin.TR / q-fin.PM
- **公開日**: 2026年7月2日（v1、PDF表紙の日付は2026年7月3日）
- **arXiv**: [2607.01550](https://arxiv.org/abs/2607.01550)
- **原論文PDF**: [arXiv PDF](https://arxiv.org/pdf/2607.01550)
- **DOI**: [10.48550/arXiv.2607.01550](https://doi.org/10.48550/arXiv.2607.01550)
- **リポジトリ内PDF**: [2026_Kurth_DemiseShortTermTrendFollowing.pdf](../../../papers/03_Finance/03_Systematic_Trading/2026_Kurth_DemiseShortTermTrendFollowing.pdf)
- **ページ数**: 本文20ページ、付録11ページ、21図
- **キーワード**: trend following、CTA、market microstructure、tick size、HFT、limit order book、price impact

## 1. 一言でいうと

短期トレンドフォローの収益は2008–2009年頃から一様に消えたのではない。約100の流動的な先物を調べると、崩壊したのは主に「1 tickが日次ボラティリティに比べて小さい」small-tick銘柄であり、large-tick銘柄では短期を含むトレンド収益がほぼ残っている。

著者らは、トレンドを単なる過去リターンの予測可能性ではなく、次の自己実現的なフィードバックとして捉える。

```text
trend signal → directional trade → price impact → reinforced trend signal
```

2008年以降、HFT中心のマーケットメイクへ移行すると、予測可能な方向フローの前で流動性が引き上げられるようになった。板が疎なsmall-tick銘柄では残存depthが足りず、CTAが攻撃的執行から撤退し、価格インパクトによる自己強化まで失われた。一方、板が密なlarge-tick銘柄ではdepthが残り、この循環が続いたというのが論文の中心仮説である。

## 2. 問題意識

トレンドフォローは長期には頑健なアノマリーとされるが、SG CTA Indexと著者らの戦略proxyでは、2009年頃から短期シグナルの成績が急に低下した。説明すべきstylized factsは次の四つである。

1. 劣化は緩やかなalpha decayではなく、2008–2009年頃の構造変化に見える。
2. 数日から数週間の速いシグナルほど悪化し、遅いシグナルは一部残る。
3. 株価指数と為替は大きく悪化する一方、金利・国債と多くの商品は比較的安定している。
4. 2018年以降に先物流動性が増え、CTA参加率が下がっても収益は回復していない。

論文は、capacity制約、電子取引化、CTAと注文フローの関係変化、市場マイクロストラクチャーという四つの説明を、タイミング・規模・クロスセクションの三面から比較する。

## 3. データと実証設計

- 約100の流動的な先物契約
- 主要標本期間: 1995–2025年
- 資産クラス: 商品（CMD）、株価指数（IDX）、為替（FXR）、政府債・金利（YLD）
- 日次settlementでトレンドシグナルとPnLを構築
- 最速戦略の長期累積PnLは1950–2025年でも検証
- BarclayHedgeのCTA業界AUMと年率リスク約12%を使い、業界規模のCTA proxyを構築
- 板と取引フローにはvolume-weighted 5分足を使用
- SG CTA Index、CME Globexの電子取引比率、先物の出来高・板・aggressor別取引量を補助データとして使用

CTA proxyの契約別参加率は、業界全体の推定売買量をimplied tradeを除いた出来高で割って求める。クロスセクション中央値は約0.9%で、CTA業界は先物出来高の1%未満という外部推定と整合する。

## 4. トレンドシグナルとポートフォリオ

契約 $i$、日 $t$、速い時間尺度 $\tau$ に対し、価格のfast EWMAとslow EWMAの差を作る。

```math
\widetilde{s}_i^\tau(t)
=
\langle p_i(t-1)\rangle_\tau
-
\langle p_i(t-1)\rangle_{4\tau}.
```

これを自身の遅い推定標準偏差で正規化し、$\pm2$でclipする。

```math
s_i^\tau(t)
=
\frac{\widetilde{s}_i^\tau(t)}
{\langle\!\langle\widetilde{s}_i^\tau(t)\rangle\!\rangle_{16\tau}}.
```

主要なsignal horizonは $\tau\in\{5,10,20,50\}$ 日で、EWM-5-20、EWM-10-40、EWM-20-80、EWM-50-200と呼ぶ。

equal-riskポートフォリオのポジションは

```math
\pi_i^\tau(t)=\frac{s_i^\tau(t)}{\sigma_i(t)}
```

である。頑健性確認では、契約の流動性 $l_i(t)$ と全体流動性 $L(t)$ を用いる

```math
\pi_i^\tau(t)
=
\frac{s_i^\tau(t)l_i(t)}{\sigma_i(t)L(t)}
```

というliquidity-weightedポートフォリオも使う。主要なtick-size結果は両方の構築法で維持される。

## 5. 短期トレンド収益の崩壊

EWM-5-20の累積PnLは2009年以降ほぼ横ばいで、5年rolling Sharpeは歴史的な1–2.5程度から、2010年以降はゼロと統計的に区別しにくい水準へ低下する。

1995–2009年と2009–2025年を比較すると、シグナルが速いほど悪化が大きい。

| $\tau$ | Sharpe 1995–2009 | Sharpe 2009–2025 |
|---:|---:|---:|
| 5 | $0.84\pm0.27$ | $0.12\pm0.24$ |
| 10 | $0.83\pm0.27$ | $0.22\pm0.24$ |
| 20 | $0.79\pm0.27$ | $0.27\pm0.26$ |
| 50 | $0.70\pm0.27$ | $0.40\pm0.26$ |

資産別では、IDXとFXRのfast trendがほぼ消える一方、YLDとCMDには明確な劣化が見られない。ただし著者らは、資産クラスそのものではなく、各クラスに含まれる契約のtick-to-volatility構成がこの差を生むと主張する。

## 6. 代替仮説をなぜ退けるか

### Capacity制約

- CTA AUMは2000年代を通じて増え、2012年頃にplateau、2022年にpeakとなる。PnLのbreakより遅く、因果の時間順序が合わない。
- 2018年以降、先物流動性の増加で参加率が下がってもPnLは回復しない。
- square-root impact law、参加率1%、日次turnover約9%から得るSharpe dragは年率約0.1である。無視できないが、Sharpe約0.7からゼロへの崩壊を単独で説明するには小さい。
- シグナルを同日closeで約定させるzero-lag計算でも2008年以降のPnLは平坦である。単に翌日執行のcostがalphaを食べたのではなく、signal自体が弱くなったことを示唆する。

### 電子取引化

電子取引化は漸進的だったがPnL breakは急である。株価指数はbreakの5年以上前に電子化し、金利先物も早く電子化したのにトレンド収益は残ったため、時期と資産別順位が一致しない。電子板は後述のHFT機構の前提ではあるが、電子化それ自体を原因とはできない。

### CTAと注文フローの関係変化

日次book imbalanceとCTA proxyの売買の相関は2010年頃に符号が変わり、trade imbalanceとの相関も2015年頃に変化する。しかし資産クラス別に分けると、同じ相関変化でもCMDはPnLが残り、FXRは消えるなど、単調な対応がない。診断変数としては有用だが、資産クラス単位では原因を識別できない。

## 7. 中心結果：volatility-normalised tick size

契約 $i$ の月 $m$ におけるtick-to-volatility ratioを

```math
\overline{\rho}_{i,m}
=
\frac{1}{D_m}
\sum_{t=1}^{D_m}
\frac{\Psi_i(t)}{\sigma_i(t)}
```

と定義する。$\Psi_i$ はtick size、$\sigma_i$ は日次ボラティリティ、$D_m$ は月内取引日数である。毎月、$\overline{\rho}_{i,m}$ が小さい下位50%をsmall tick、大きい上位50%をlarge tickとする。分類は当月までの情報で毎月更新される。

結果は明瞭である。

- break前のequal-risk Sharpeはsmall tickで約0.8、large tickで約1.4。
- break後、small tickは全signal horizonでほぼゼロとなり、最速signalではわずかに負になる。
- large tickはbreak後も約1.0–1.2を維持し、相対的な劣化は0–30%程度にとどまる。
- small tickの相対劣化は約100%。
- 資産クラス内で改めて50/50に分けても同方向の結果が得られ、単一の閾値より連続的な関係を示唆する。

流動性とnormalised tick sizeには負の相関（log-log Pearson $-0.35\pm0.08$）があるが、流動性の高低で分けてもsignal horizonをまたぐ整然とした差は出ない。したがって、liquidityは副次的要因ではあっても、最も強い識別変数ではない。

同一契約内の分解も重要である。低ボラティリティ局面では $\Psi/\sigma$ が大きくなるため、通常small-tickの契約でもlarge-tickに近い挙動となり、break後もPnLが残る。また、1標準偏差未満の日のPnLはbreak前後でほぼ不変であり、消えたのはsmall-tick契約の大きな方向変化から得る収益である。

## 8. 提案されるマイクロストラクチャー機構

### HFT中心の流動性供給

著者らは、2008年後の市場が、数時間から数日の在庫を許容する銀行・自己勘定系マーケットメーカーから、日中に在庫をflatへ戻すHFT型マーケットメーカーへ移行したと解釈する。予測可能で持続的なCTAフローの前では、後者は在庫を吸収せずdepthを引き上げやすい。

### Sparse bookとdense bookの非対称性

- **small tick**: 価格優先を得るには改善quoteが必要で、spread captureに対するadverse selection costが重い。掲示depthが薄く、価格level間のgapも生じやすい。
- **large tick**: spreadにqueueing rentがあり、best quoteと深いlevelに厚い注文が蓄積しやすい。

流動性の引き上げが両tierで起きても、denseなlarge-tick bookには執行可能なdepthが残る。sparseなsmall-tick bookでは残存depthが消え、CTAは板を歩いて高いslippageを払うか、短期signalから撤退する必要がある。

### Signal自体が弱くなる理由

トレンドフォロワーのaggressive flowは価格をsignal方向へ動かし、次のsignalを強める。small-tick契約からaggressive flowが消えると、収益機会を刈り取れないだけでなく、弱い初期trendを増幅するimpact channel自体が弱くなる。zero-lagでもsignalが崩壊していることは、この「loopの入力側が切れた」という説明に整合する。

5分returnとbook imbalanceの関係では、2011年以前のsmall-tick銘柄に明確な負の傾きがあり、流動性供給者がdirectional flowにrun overされるadverse selection costを負担していた。2011年以降、この関係はほぼflatになる。著者らは、run overされるdepthが事前に撤去され、costがマーケットメーカー在庫損からtrend followerのslippageへ移った痕跡と解釈する。一方、returnとaggressive trade imbalanceの正の関係は残り、tradeがpriceを押すimpact channel自体は観測される。

### Limit orderへ切り替えても解決しない

passive buy orderは、予測どおり価格が上がる良い状態では約定せず、価格が下がる悪い状態で約定しやすい。visible slippageをmissed-opportunity costへ置き換えるだけである。さらにpassive orderはbuyer-initiated flowを生まず、signalを自己強化するimpact loopにも参加できない。

## 9. 実務への含意

- CTAのcapacityは資産クラスや全体参加率だけでなく、$\Psi/\sigma$ tier別に評価する。
- 「低流動性だからtrendが残る」と単純化せず、spread、tick、depth、price-levelの密度を分けて測る。
- fast trendのバックテストでは、取引cost控除だけでなく、戦略参加がsignal生成へ与える内生的impactを考える。
- market orderからlimit orderへの置換は、slippage、fill率、opportunity cost、signalへのimpactを同じ基準で比較する。
- small-tick契約で大きなdirectional moveを取る戦略は、平均的な日より、stress時のdepth withdrawalを重点的に検証する。
- 遅いtrendが一部残ることは、impact loop以外の情報拡散・underreaction経路が完全には消えていない可能性と整合する。

## 10. 限界と批判点

1. **arXiv v1**: 査読前であり、結果・仕様・記述は改訂され得る。
2. **因果識別**: HFT在庫やCTA個別注文を直接観測した自然実験ではない。tick tier、imbalance、PnLの同時変化は機構と整合するが、HFTへの移行が原因だと確定するものではない。
3. **CTA proxy**: aggregate AUM、年率リスク12%、共通signal、liquidity weightingから業界取引を近似する。実際のCTAは市場、速度、risk cap、execution algorithmが異なる。
4. **自己実現仮説の反射問題**: signalがtradeを生み、tradeがsignalを強めるため、原因と結果を分離しにくい。外生的news、投資家のunderreaction、slow information diffusionも同じtrendを作り得る。
5. **HFTの一括り**: HFT市場参加者にもinventory horizon、maker obligation、venue、risk limitの差がある。論文自身も「参加者の交代」か「既存業者のrisk preference変化」かを識別しない。
6. **50/50分類**: monthly median splitは比較を明確にするが、経済的な絶対閾値ではない。資産クラス内分類は単調性を補強するものの、運用ルールには連続的なcapacity modelが必要である。
7. **zero-lagの理想化**: 同日closeでの執行はsignal decayと翌日costを切り分ける診断だが、現実にその価格で業界規模の売買ができるわけではない。
8. **gross signalと実装収益**: 主要なtier比較はequal-riskの理論PnLを中心とし、実際の手数料、queue position、latency、market impact、contract rollを完全には再現しない。
9. **外部妥当性**: 対象は主に流動的な先物であり、現物株、暗号資産、OTC、異なるtick制度・マーケットメーカー義務を持つ市場へ直ちに一般化できない。
10. **著者所属とデータ再現性**: 一部著者は運用会社所属で、bar dataや業界indexなど第三者が完全再現しにくいデータも含む。独立標本での追試が必要である。

## 11. 次に検討したい問い

1. tick size変更を外生ショックとして、同一契約のfast-trend PnLとdepthがどう変わるか。
2. HFT inventory、order cancellation、CTA rebalancing時刻を使い、depth withdrawalを直接識別できるか。
3. $\Psi/\sigma$、spread、top-of-book depth、price impact、queue lengthから連続的なcapacity frontierを作れるか。
4. venue別のmaker obligationやfee/rebate制度が同一原資産のtrend persistenceへ与える差を利用できるか。
5. 2010年以降に残ったslow trendを、情報拡散成分とimpact-loop成分へ定量分解できるか。
6. small-tick契約でtrendと逆方向に流動性を供給するmean-reversion戦略が、同期間に補完的な収益改善を得たか。
7. 暗号先物、個別株、国債現物など別の板構造でもnormalised tick sizeが同じ識別力を持つか。
8. market-maker義務やminimum tickの変更により、方向takerとliquidity providerの厚生をどう配分すべきか。

## 12. 総合評価

本論文の最大の貢献は、「短期trendが消えた」という時系列の事実を、資産クラスや単純な流動性ではなく、volatility-normalised tick sizeという市場構造変数で鋭く分割した点にある。small tickではbreak後のSharpeがほぼゼロ、large tickでは約1.0–1.2という差、資産クラス内tiering、同一契約内のvolatility・return magnitude分解、zero-lag診断が一つの説明へ収束するのは説得的である。

一方、HFTへの移行、depth withdrawal、CTA撤退、signal decayという因果鎖は、直接の在庫・注文データではなく複数の整合的な証拠から推論されている。したがって現段階では、完成した因果証明というより、有力で反証可能なマイクロストラクチャー仮説として読むべきである。

実務上の核心は、トレンド収益を「予測signal − transaction cost」だけで考えないことにある。戦略のaggressive flowが価格形成へ参加し、その参加可能性がtick、volatility、板の密度、流動性供給者の在庫許容度に依存するなら、alpha、capacity、executionは互いに分離できない。
