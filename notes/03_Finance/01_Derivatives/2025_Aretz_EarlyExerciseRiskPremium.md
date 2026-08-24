# The Early Exercise Risk Premium — Aretz & Gazi (2025)

## 書誌情報

- **論文**: *The Early Exercise Risk Premium*
- **著者**: Kevin Aretz, Adnan Gazi
- **掲載誌**: *Management Science*, 71(2), 1824-1845
- **年**: 2025（保存PDFは2023年8月draft）
- **DOI**: [10.1287/mnsc.2023.00440](https://doi.org/10.1287/mnsc.2023.00440)
- **原資料**: [Moonlight共有ページ](https://www.themoonlight.io/paper/4dafa540-40af-48e2-b32f-fe6c8bf645d9)
- **リポジトリ内PDF**: [2025_Aretz_EarlyExerciseRiskPremium.pdf](../../../papers/03_Finance/01_Derivatives/2025_Aretz_EarlyExerciseRiskPremium.pdf)
- **キーワード**: American put, European synthetic put, early exercise, option anomalies, delta-hedged return

## 一言でいうと

American putを満期まで機械的に保有した収益と、最適な早期行使を反映した収益は別物である。American putとput-call parityで合成したEuropean putを比較すると、早期行使を入れたraw return差は正、delta-hedged差は負となり、既存のoption anomaly 15本中14本の収益推定が有意に変わる。

## 1. 定義と予測

同一原資産・strike・満期のAmerican/European putの期待収益差を

```math
EEP^{raw}=E[R^{A}]-E[R^{E}],
\qquad
EEP^{\Delta}=E[R^{A,\Delta hedged}]-E[R^{E,\Delta hedged}]
```

と定義する。Longstaff-Schwartz型の最適停止をphysical \(P\) とrisk-neutral \(Q\) の下で比較すると、行使権は価格だけでなく期待payoffも高める。raw EEPは通常正だが、variance/jump risk premiumを取り除くdelta hedge後のEEPは負になると予測する。moneyness、短い残存期間、低い原資産volなど、早期行使確率を高める特徴ほど差は大きい。

## 2. データと実証設計

- 1996年1月-2021年12月のzero-dividend US individual stocksのAmerican optionsをOptionMetricsから取得し、CRSP/Compustat/Markitを補完する。
- zero-dividend stockではAmerican callの早期行使は最適でないため、put-call parityでEuropean putを合成する。
- 月次で最適早期行使payoffを反映したAmerican put returnと、合成European put returnを比較し、portfolio sortsとFama-MacBeth回帰を行う。

## 3. 主要結果

- long American put / short synthetic European putの平均月次raw spreadは2.38%（t=5.58）、delta-hedged spreadは-0.50%（t=-12.20）。
- 最適行使を許さないと同じ差はraw -0.89%、delta-hedged -0.22%となり、結論の符号・大きさが変わる。
- 15本中14本の既報anomalyの平均spread returnが有意に変化し、絶対変化の平均は32%、5本は95%水準で有意でなくなる。
- theoretical simulationでは、標準パラメータのGBMでもraw EEPは月2.45%程度となり、SV/jumpのrisk premiumがdelta-hedged差を負に押す。

## 4. 解釈

早期行使可能性を無視したAmerican option returnは、同じrisk exposureを測っていないEuropean returnとの比較になり得る。これは「早期行使で裁定が取れる」という話ではなく、実現収益の定義に最適停止を入れないと、因子負荷・alpha・anomalyの推定対象が変わるという計測上の警告である。

## 5. 限界

- 保存PDFは2023年draftであり、数値を最終掲載版のものと混同しない。
- 合成European putはput-call parity、株式借入、金利、気配値、実行可能性に依存する。
- zero-dividend stocksに限定した識別は強みだが、配当株・指数・cash-settled optionへ直接外挿できない。
- 実際の投資家が最適停止できるとは限らず、資金、証拠金、税務、運用ルールで実現可能性は変わる。

## 6. 次に検討すべき問い

- 既存option-factorの推定を最適行使込みで再計算すると、どのfactor premiumが残るか。
- early-exercise probabilityを特徴量として入れると、IPCA等のconditional factor modelは改善するか。
- 配当株のAmerican callではPool et al. (2008)の未行使とこの理論的EEPをどう接続するか。

## BibTeX

```bibtex
@article{AretzGazi2025,
  author  = {Aretz, Kevin and Gazi, Adnan},
  title   = {The Early Exercise Risk Premium},
  journal = {Management Science},
  volume  = {71}, number = {2}, pages = {1824--1845}, year = {2025},
  doi     = {10.1287/mnsc.2023.00440}
}
```
