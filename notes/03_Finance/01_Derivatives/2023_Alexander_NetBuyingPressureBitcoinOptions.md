# Net Buying Pressure and the Information in Bitcoin Option Trades — Alexander et al. (2023)

## 書誌情報

- **著者**: Carol Alexander, Jun Deng, Jianfen Feng, Huning Wan
- **掲載誌**: *Journal of Financial Markets*, 63, 100764
- **公刊年**: 2023（オンライン公刊は2022年）
- **DOI**: [10.1016/j.finmar.2022.100764](https://doi.org/10.1016/j.finmar.2022.100764)
- **出版社ページ**: [ScienceDirect（PII: S1386418122000544）](https://www.sciencedirect.com/science/article/pii/S1386418122000544)
- **保存版**: arXiv:2109.02776v2（2022年3月28日版、35ページ）
- **リポジトリ内PDF**: [2023_Alexander_NetBuyingPressureBitcoinOptions_ArXiv2109.02776.pdf](../../../papers/03_Finance/01_Derivatives/2023_Alexander_NetBuyingPressureBitcoinOptions_ArXiv2109.02776.pdf)
- **キーワード**: Bitcoin options、Deribit、net buying pressure、informed trading、market maker inventory、implied volatility

## 1. 研究質問と結論

Bitcoinオプションのインプライド・ボラティリティ（IV）は、マーケットメーカーの在庫制約と、情報を持つ投資家の需要のどちらによって動くのか。情報需要は将来ボラティリティに関するものか、Bitcoin価格の方向に関するものか。

本論文の結論は次のように整理できる。

- IV変化の負の自己相関は全moneynessで強く、マーケットメーカーが不完全ヘッジと在庫リスクを価格へ転嫁する **limits-to-arbitrage仮説** を支持する。
- ATMオプションは主にボラティリティ情報を持つ取引に反応する。
- OTM・deep OTM（DOTM）では、ボラティリティ情報と方向情報の両方が価格に入る。
- 情報取引は2019年以降に明確になり、出来高増加とともにDeribitの情報集約機能が改善する。
- 満期別では短期・中期に情報取引が多い。時間帯別では、方向性需要はアジア時間、ボラティリティ需要の量は欧州時間に強いが、情報内容を持つ需要はアジア・米国時間でより明瞭である。

ただし、net buying pressure（NBP）の係数は「私的情報だけ」を識別するものではない。在庫コスト、流動性、同時的なニュース反応も含み得る。

## 2. データと市場

- **取引所**: Deribit
- **対象**: BitcoinのEuropean call・put
- **期間**: 2017年1月1日–2021年7月28日
- **原データ**: 数百万件のtick-by-tick約定
- **実証頻度**: tickを1時間単位に集約
- **主分析期間**: 流動性が低かった2017–2018年を主要表から外し、2019年、2020年、2021年1–7月を年別に推定
- **現物市場コントロール**: Deribit Bitcoin indexの構成市場のうちBitstamp、Coinbase、GeminiのUSD出来高

標本終了後は短期満期のデータしか揃わないため、2021年7月28日で切っている。Deribitの出来高は2017年の2.6億ドルから2021年1–7月の1,029.6億ドルへ急増した。したがって、年別係数の変化には市場参加者の成熟だけでなく、流動性・契約構成・Bitcoin価格局面の変化も混在する。

## 3. Net buying pressureの構成

約定 (i) のドル建て取引量を (V_i)、オプション・デルタを \(\Delta_i\) とする。買い手主導取引を正、売り手主導取引を負として、moneyness区分 (k) のdelta-weighted NBPを概念的に

```math
A_t^k
= \sum_{i \in \text{buyer},k} V_i |\Delta_i|
- \sum_{i \in \text{seller},k} V_i |\Delta_i|
```

と測る。正なら顧客の純買い、負なら純売りである。callとputのNBPをそれぞれ \(A_{C,t}^k\)、\(A_{P,t}^k\) とすれば、Chen and Wang (2017)に従う方向性需要とボラティリティ需要は

```math
D_{C,t}^k = \frac{A_{C,t}^k-A_{P,t}^k}{2},
\qquad
D_{P,t}^k = -D_{C,t}^k,
```

```math
V_t^k = \frac{A_{C,t}^k+A_{P,t}^k}{2}
```

である。call買い・put売りの組合せは上昇方向の情報需要、callとputの同方向の買いはボラティリティ上昇を予想する需要として解釈される。

この分解は有用だが、単一取引が複数レッグ戦略の一部かどうかは識別しない。例えばstraddleはvolatility demandと整合する一方、別時点で約定したspreadの脚は方向性需要に誤分類され得る。

## 4. 識別する3つの仮説

### Limits to arbitrage

マーケットメーカーが完全ヘッジできなければ、顧客の純買いで在庫リスクが増え、供給曲線が右上がりになる。過大な注文不均衡が解消されればIVの変化は反転するため、IV変化に負の自己相関が現れる。

### Volatility learning

投資家が将来の変動幅を知っている場合、callとputを同方向に取引する。vegaの大きいATM需要が最も情報を持ち、ATMの価格変化がIV smile全体へ波及すると予測する。

### Directional learning

投資家が将来リターンの符号を知っている場合、callとputを逆方向に取引する。安価でレバレッジの高いOTM・DOTMに効果が強く現れ得る。

## 5. 回帰設計

callまたはputのmoneyness区分 (k) の1時間IV変化を、Bitcoin現物リターン (r_t)、現物出来高 (v_t)、call/putのNBP、ラグIV変化へ回帰する。

```math
\Delta \sigma_{j,t}^{k}
= \alpha_0^k + \alpha_1^k r_t + \alpha_2^k v_t
+ \alpha_3^k A_{j,t}^{k} + \alpha_4^k A_{i,t}^{ATM}
+ \alpha_5^k \Delta \sigma_{j,t-1}^{k} + \varepsilon_t^k.
```

- \(\alpha_5<0\): 在庫ショック後のIV反転であり、limits-to-arbitrageと整合する。
- call・putのNBPが同方向に効く: volatility learningと整合する。
- call・putが逆方向に効く: directional learningと整合する。

さらにNBPを (D_t^k\) と (V_t^k\) に直接分解した回帰で、方向情報とボラティリティ情報の併存を検定する。著者らは4時間・8時間集計でも概ね同様の結果を得るが、日次集計では短命な情報と在庫調整が平均化されるため結果が弱くなる。

## 6. 主要結果

### 在庫制約は一貫して重要

2019–2021年のATM、OTM、DOTMでラグIV変化の係数は負で強く有意である。ATM callでは \(\alpha_5\) が2019年の−0.458から2021年の−0.395へ縮小した。著者らは、S&P 500やTAIEXで報告された絶対値より大きいことを、当時のBitcoinオプションで在庫管理がより難しかった証拠と解釈する。

絶対値の縮小は市場成熟と整合するが、それだけで因果的に「マーケットメーカー能力が向上した」とは言えない。流動性、参加者、満期構成、価格水準が同時に変化している。

### ATMはボラティリティ情報、OTMは二種類の情報

ATMではvolatility-motivated demandが中心である。OTM・DOTMではvolatility demandに加えてdirectional demandも有意となり、とくに2021年のBitcoin価格上昇と急落の局面で方向性効果が強い。

ATM需要がsmile全体を機械的に引っ張る証拠は弱く、各moneyness固有の需要が重要である。この点は、ATM需要が曲線全体を動かす単純なvolatility-learning像と異なる。

### 満期別

満期を短期 \([1,7]\) 日、中期 \([8,21]\) 日、長期 \(\ge 22\) 日へ分けると、情報取引は短期・中期に集中する。2020年の長期ATMは主にlimits-to-arbitrageを支持し、長期OTM callは方向情報、長期DOTM putはボラティリティ情報の影響が比較的強い。2021年には長期でも方向取引が増えるが、全体として長期の情報取引は少ない。

### 時間帯別

UTC 00:00–08:00（アジア）、08:00–16:00（欧州）、16:00–24:00（米国）に分けると、2020–2021年に明瞭な日中パターンが現れる。

- 方向性NBPの量はアジア時間に大きい。
- ボラティリティNBPの量は欧州時間に大きい。
- ただし回帰上の情報性はアジア・米国時間の需要でより強く、欧州時間の大きな需要量がそのまま私的情報の多さを意味しない。

この区分は主要金融センターの営業時間を粗く対応させたもので、投資家所在地を直接観測していない。

## 7. 限界と批判点

1. **取引方向の推定**: buyer/seller initiationの分類誤差がNBPへ入る。
2. **複数レッグの識別不足**: 個別約定からstraddle、risk reversal、spreadを完全には再構成できない。
3. **同時性**: informed demandがIVを動かすだけでなく、ニュース・現物価格・IV変化が注文を誘発する逆方向もある。
4. **単一取引所**: 当時最大手でも、CMEや他の暗号資産市場へそのまま一般化できない。
5. **制度・市場の急変**: 2017–2021年は出来高、参加者、Bitcoin価格、取引所構造が急変しており、年別比較は純粋な成熟効果ではない。
6. **時間帯ラベル**: UTC区分は投資家国籍や情報源を識別しない。
7. **版の差**: リポジトリ保存PDFは2022年3月のarXiv v2であり、2023年公刊版の組版・最終校正と細部が異なる可能性がある。

## 8. 実務的含意

- call買い・put売りのフローだけから強気情報を断定せず、複数レッグ、現物・先物ヘッジ、同時ニュースを確認する。
- IVの注文フロー反応には情報だけでなく、マーケットメーカーの在庫・資本・ヘッジコストが含まれる。
- 取引シグナルとして使うなら、moneyness、残存日数、時間帯、現物出来高を条件付けし、日次集計で情報を潰さない。
- 2021年の方向性効果を通常局面へ外挿せず、バブル・急落レジームとの交互作用を検証する。

## 9. 次に検討したい問い

1. 2022年以降のDeribit、CME、現物ETFオプションでもIV反転係数は縮小しているか。
2. 口座またはメッセージデータで複数レッグと顧客・マーケットメーカーを直接識別できるか。
3. NBPの価格インパクトは一時的在庫プレミアムと恒久的情報成分へどこまで分解できるか。
4. Asian/European/USの時間帯効果は、地域ではなく主要マクロ発表やBitcoinの流動性周期で説明できないか。
5. OTMのdirectional demandは将来現物リターンをout-of-sampleで予測し、取引コスト後にも残るか。

## 参考文献上の位置づけ

- Bollen and Whaley (2004): option demand、IV、limits-to-arbitrageを結ぶ基礎。
- Kang and Park (2008): directional learningを導入。
- Chen and Wang (2017): NBPをdirectional demandとvolatility demandへ分解。
- Alexander and Imeraj (2021): DeribitからBitcoin VIXとvariance risk premiumを構築。
- Guo et al. (2022): LedgerXの非流動性・注文不均衡とdelta-hedged returnを分析。
