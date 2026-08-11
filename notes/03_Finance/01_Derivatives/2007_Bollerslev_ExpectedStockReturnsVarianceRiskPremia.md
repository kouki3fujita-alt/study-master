# Expected Stock Returns and Variance Risk Premia — Bollerslev and Zhou (2007)

## 書誌情報

- **論文**: Tim Bollerslev, Hao Zhou, “Expected Stock Returns and Variance Risk Premia”
- **種別**: Finance and Economics Discussion Series, Federal Reserve Board, 2007-11
- **原論文PDF**: [Federal Reserve PDF](https://www.federalreserve.gov/pubs/feds/2007/200711/200711pap.pdf)
- **初稿**: 2006年9月
- **手元PDF版**: 2006年12月版、33ページ
- **公刊版**: Tim Bollerslev, George Tauchen, Hao Zhou, *The Review of Financial Studies*, Vol. 22, No. 11, pp. 4463-4492, 2009
- **DOI（公刊版）**: [10.1093/rfs/hhp008](https://doi.org/10.1093/rfs/hhp008)
- **キーワード**: return predictability, implied variance, realized variance, equity risk premium, variance risk premium, time-varying risk aversion

## 1. 一言でいうと

S&P 500のmodel-free implied varianceと高頻度データから作ったrealized varianceの差、すなわちvariance risk premiumは、1990-2005年の四半期市場超過リターンを強く予測する。VRP単独で四半期リターン変動の15.14%を説明し、P/Eと組み合わせると26.37%、さらにterm spreadとrelative short rateを加えると27.67%まで上がる。高いVRPは高い将来株式リターンを予測し、著者らはこれを市場全体のリスク回避度のmodel-free proxyと解釈する。

## 2. 問題意識

株式市場リターンは予測できるのか、という古典的な問いに対し、従来はP/E、配当利回り、term spread、default spread、CAYなどが使われてきた。しかし、多くの変数は長期ホライズンで効きやすく、1990年代後半以降は予測力が弱まったとも言われる。

本論文は、オプション市場から得られる将来分散のリスク中立期待と、高頻度データから観測される実現分散の差に注目する。この差は、投資家が分散上昇リスクをどれだけ嫌い、どれだけ保険料を払っているかを表すため、期待株式リターンと結び付くはずだ、という発想である。

## 3. 中核概念：Variance Risk Premium

著者らは、model-free implied varianceを $IV_t$、realized varianceを $RV_t$ とし、variance risk premiumを単純に

```math
VRP_t = IV_t - RV_t
```

として扱う。

ここで $IV_t$ は、幅広いストライクのS&P 500オプションから、特定のBlack-Scholes型モデルに依存せず抽出するリスク中立期待分散である。一方 $RV_t$ は、S&P 500の高頻度日中リターン二乗和から作る実現分散である。

この定義では、$VRP_t$ が高いほど、オプション市場が将来分散を現実に観測された分散より高く価格付けしていることを意味する。分散上昇は悪い状態で起きやすいため、分散ロングは保険になり、その保険料がVRPに表れる。

## 4. データ

- 対象: S&P 500 composite index
- 標本: 1990Q1から2005Q1
- implied variance: CBOEのVIX、新VIXと同じmodel-free approachに基づくS&P 500オプション由来の月次データ
- realized variance: S&P 500の高頻度日中価格から構築
- 予測対象: 四半期S&P 500超過リターン
- 比較変数: P/E、P/D、default spread、term spread、relative short rate、CAY
- 推論: Newey-West robust t-statistics、4ラグ

ほかの説明変数が月次・四半期頻度であるため、主分析は四半期データで行う。重複標本と欠損の問題を避けるため、各四半期の最後の月を四半期観測として使う。

## 5. 主要結果

### 5.1 VRP単独で四半期リターンの15.14%を説明

四半期S&P 500超過リターンを1期ラグの予測変数で回帰すると、$IV_t-RV_t$ の係数は0.86、Newey-West t値は3.94、調整済み $R^2$ は15.14%である。

比較すると、伝統的な変数の説明力はかなり低い。

| 予測変数 | 調整済み $R^2$ |
|---|---:|
| $IV_t-RV_t$ | 15.14% |
| $IV_t$ | 6.32% |
| $RV_t$ | -1.05% |
| $\log(P/E)$ | 6.22% |
| $\log(P/D)$ | 2.76% |
| default spread | 0.27% |
| term spread | -1.63% |
| relative short rate | -0.66% |
| CAY | 4.83% |

つまり、implied varianceやrealized variance単体ではなく、その差であるVRPが強い。

### 5.2 P/Eと組み合わせると説明力がさらに上がる

VRPとP/Eを同時に入れると、調整済み $R^2$ は26.37%に上がる。VRPとCAYでは20.86%、P/EとCAYだけでは5.54%にとどまる。さらにVRP、P/E、term spread、relative short rateを入れると27.67%となる。

著者らは、P/Eがリスク量や長期的な割引率成分を拾い、VRPがリスク回避度を拾うため、両者の組み合わせが効くと解釈する。

### 5.3 model-freeかつ高頻度RVであることが重要

Black-Scholes implied varianceや日次リターンから作るrealized varianceで同じことをすると、予測力は落ちる。たとえば、Black-Scholes implied varianceと高頻度RVの差では単独 $R^2$ が8.08%、model-free IVと日次RVの差では12.36%、Black-Scholes IVと日次RVの差では4.28%に低下する。

これは、VRPを使うときに「どのIV」と「どのRV」を使うかが本質的であることを示している。

### 5.4 ボラティリティ差でも効くが、分散差の方が複合回帰では強い

分散ではなく標準偏差に変換したvolatility risk premium、すなわち $\sqrt{IV_t}-\sqrt{RV_t}$ も単独では強く、調整済み $R^2$ は18.50%となる。ただし、P/EやCAY、term structure変数と組み合わせた複合回帰では、分散差ベースのVRPの方が全体としてよい。

### 5.5 APT型の通常リスク因子ではない

25個のFama-French size/book-to-marketポートフォリオを使ったクロスセクション検証では、VRPを通常の線形APTリスク因子として価格付けする証拠は弱い。したがって、VRPは横断的なリスク・ベータというより、時系列で変動する市場全体のリスク回避度や経済的不安の代理変数として見る方が自然である。

## 6. 経済的解釈

投資家のリスク回避度が高い局面では、分散上昇に対する保険需要が強まり、オプションから見たリスク中立期待分散が現実分散より大きくなる。したがってVRPは高くなる。

同時に、投資家がリスク資産を嫌うため、株価には大きなディスカウントが入り、将来の期待超過リターンは高くなる。これが「高いVRPが高い将来株式リターンを予測する」という関係である。

GDP成長との関係もこの解釈と整合的である。VRPは将来GDP成長と弱い負の相関を持ち、経済が悪化しそうな局面でリスク回避度が高まりやすいことを示唆する。

## 7. この論文の貢献

1. model-free implied varianceと高頻度realized varianceの差を、株式リターン予測変数として明確に使った。
2. 1990-2005年の比較的短いサンプルでも、四半期ホライズンで非常に高い予測力を示した。
3. P/E、P/D、default spread、term spread、CAYなどの伝統的変数と比較し、VRPが優位であることを示した。
4. Black-Scholes IVや日次RVでは結果が弱まることを示し、測定方法の重要性を明確にした。
5. VRPを線形リスク因子ではなく、市場全体のtime-varying risk aversionの代理変数として解釈した。

## 8. 限界と批判点

1. **標本期間が短い**: VIX系列の制約により1990-2005年に限られ、長期ホライズンや複数危機を含む検証には限界がある。
2. **予測回帰の過大評価リスク**: 変数選択、頑健性検証、有限標本の影響により、調整済み $R^2$ は将来標本で低下し得る。
3. **VRPの符号・定義**: 文献によって $IV-RV$ と $RV-IV$ が混在するため、比較時には符号を確認する必要がある。
4. **リアルタイム実装**: 論文のRVは事後的な高頻度データで構築される。実運用ではリアルタイムで使えるデータ、改訂、取引コスト、タイミングを確認する必要がある。
5. **因果ではない**: VRPがリターンを「動かす」証明ではなく、リスク回避度、流動性、裁定資本、マクロ不安が同時に反映されている可能性がある。
6. **公刊版との違い**: 指定PDFはBollerslev and ZhouのFEDS版であり、公刊版はBollerslev, Tauchen, and Zhou (2009)として発表されている。

## 9. 実務への含意

- 株式インデックスのタイミング指標として、VIX水準そのものより、implied varianceとrealized varianceの差を見る方が有用である。
- VRPを作る際は、model-free IVと高頻度RVを使うことが重要であり、簡単なBlack-Scholes IVや日次RVでは情報がかなり落ちる。
- VRPは「恐怖が高いと将来リターンも高い」という直感を、オプション市場と実現分散の差として定量化する。
- P/Eのようなバリュエーション指標とVRPを組み合わせると、リスク量とリスク回避度を分けて見られる。

## 10. 次に検討すべき問い

- 2005年以降、GFC、COVID、0DTE拡大期を含めても四半期予測力は残るか。
- VRPを日次・週次で更新した場合、シグナルのノイズと取引コストをどう扱うべきか。
- VRP、left jump tail variation、VIX futures term structure、variance swap term structureを組み合わせると予測力は改善するか。
- S&P 500以外の日経225、Euro Stoxx 50、BTCなどでも同じ関係が成り立つか。
- VRPの変化を、リスク回避度、流動性制約、ディーラー在庫、マクロ不確実性へどう分解できるか。

## 11. 総合評価

この論文は、Carr and Wu (2009)型の分散リスク・プレミアム研究と、株式リターン予測研究を結び付ける重要な橋である。ポイントは、ボラティリティが高いか低いかではなく、オプション市場が価格付けする将来分散と、実際に観測された分散の差が大きいかどうかにある。VRPは市場の不安やリスク回避度をかなり直接的に映すため、単なるバリュエーション指標より短中期の期待リターンに近い情報を持つ。
