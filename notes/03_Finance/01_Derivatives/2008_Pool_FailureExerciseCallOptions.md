# Failure to Exercise Call Options: An Anomaly and a Trading Game — Pool, Stoll & Whaley (2008)

## 書誌情報

- **論文**: *Failure to Exercise Call Options: An Anomaly and a Trading Game*
- **著者**: Veronika Krepely Pool, Hans R. Stoll, Robert E. Whaley
- **掲載誌**: *Journal of Financial Markets*, 11(1), 1-35
- **年**: 2008
- **DOI**: [10.1016/j.finmar.2007.09.001](https://doi.org/10.1016/j.finmar.2007.09.001)
- **原資料**: [Moonlight共有ページ](https://www.themoonlight.io/paper/bdefb0f5-c28b-466b-96e7-92049f229976)
- **リポジトリ内PDF**: [2008_Pool_FailureExerciseCallOptions.pdf](../../../papers/03_Finance/01_Derivatives/2008_Pool_FailureExerciseCallOptions.pdf)
- **キーワード**: American call, ex-dividend, early exercise, open interest, dividend spread arbitrage

## 一言でいうと

配当落ち直前に行使すべきdeep ITM American callの半分超が行使されず、1996-2006年の標本で保有者が累計4.91億ドル超を取り逃したと推定する。専門業者はOCCの割当て規則を利用したdividend-spread取引で、その取り逃しの大半を回収する。

## 1. 行使判断

米国上場株式のcallは通常、現金配当でstrikeが調整されない。ex-dividend日前に行使すれば株式と配当を受け取れるため、残存time valueより配当便益が大きければ行使が合理的となる。概念的には、cum-dividend株価 \(S\)、strike \(X\)、配当落ち後の株価 \(S_x\)、call価格 \(C\) で

```math
S-X > C(S_x,X,T)
```

なら即時行使が有利である。配当が大きい、株価が高い、strikeが低い、満期が近い、volが低いほど行使確率は上がる。

## 2. 実証設計

- 1996年1月から2006年4月まで、四半期配当が1セント以上の米国個別株callを対象とする。
- ex-dividend前日のopen interestを用いて、本来ゼロになるべき残存long positionを未行使として測る。
- price/modelに基づく行使条件、OI変化、取引量を組み合わせ、単なる当日新規建てと未行使を区別する。

未行使比率の基本形は、行使対象seriesについて \(OI_{t-1}/OI_{t-2}\) と置く。前日に本来すべての既存longが行使されれば、前日終値時のOIはゼロに近いはずである。

## 3. 主要結果

- 行使が最適なoutstanding longの過半が未行使で残る。
- この失敗によるcall保有者の逸失利益は10年間で4.91億ドル超と推定される。
- 未行使は取引コスト・監視コスト・無知/不注意のいずれでも説明し得るが、データだけで各要因を完全には分離しない。
- market maker等は、cum-dividend call/stockの組合せを使うdividend spreadで行使割当てを受ける余地があり、逸失配当の大部分を回収できる。

## 4. 実務への含意

callを「満期まで持つ権利」とだけ見ると、配当落ちでtime valueと配当の比較を取り落とす。deep ITM short callの割当てリスクは、特にex-date前日に急上昇する。covered call、short-call spread、stock replacementでは、銘柄の配当予定、borrow、bid-ask、早期割当て後の資金・税務を同時に確認すべきである。

## 5. 限界と注意

- 4.91億ドルは対象標本と仮定に依存し、全市場・現在のOCC運用へそのまま外挿できない。
- 個人の未行使を観測しても、個別口座の制約、税務、資金不足、株式受渡し回避の意図は識別できない。
- 行使判断は理論価値だけではなく、bid-ask、手数料、borrow、残存イベントriskを含むnet valueで行う必要がある。
- European option、指数cash-settled option、配当保護付き契約には同じ規則を当てはめない。

## 6. 次に検討すべき問い

- ゼロコミッション化・自動行使通知の普及後にも未行使は残るか。
- 早期割当てを考慮したcovered-call premiumは、非考慮のbacktestとどれほど違うか。
- dividend spreadの収益はOCC allocation、borrow cost、execution cost後にどの程度残るか。

## BibTeX

```bibtex
@article{PoolStollWhaley2008,
  author  = {Pool, Veronika Krepely and Stoll, Hans R. and Whaley, Robert E.},
  title   = {Failure to Exercise Call Options: An Anomaly and a Trading Game},
  journal = {Journal of Financial Markets},
  volume  = {11}, number = {1}, pages = {1--35}, year = {2008},
  doi     = {10.1016/j.finmar.2007.09.001}
}
```
