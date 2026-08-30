# Cross-Sectional Variation of Option-Implied Volatility Skew — Tian and Wu (2024)

## 書誌情報

- **論文**: Meng Tian and Liuren Wu, “Cross-Sectional Variation of Option-Implied Volatility Skew”
- **掲載誌**: *Management Science*, Vol. 70, No. 6, pp. 3566-3580, 2024
- **DOI**: [10.1287/mnsc.2023.4872](https://doi.org/10.1287/mnsc.2023.4872)
- **SSRN**: [Abstract 3707006](https://ssrn.com/abstract=3707006)（初稿: 2020年10月7日、最終改訂: 2022年7月25日）
- **キーワード**: individual-stock options、implied-volatility skew、risk-neutral skewness、cyclicality、default risk、information flow
- **PDF保存状況**: ユーザー指定のSSRN署名URLは取得時に404で失効していたため、本文PDFは保存していない。書誌と結論はSSRNおよび出版社の恒久ページで照合した。

## 1. 一言でいうと

個別株オプションのIV skewは、企業の景気感応度とデフォルト・リスクという**構造的リスク**だけでなく、短期的な情報フローも混ざった価格である。本論文は半構造的な横断オプション価格モデルで両者を分け、構造的リスクがskew横断分散の最大44%を説明し、残差部分には将来株式リターンを予測する情報が残ると報告する。

## 2. 問題意識

低いstrikeほどIVが高い個別株のdownside skewは、将来の悪材料に備える保険需要、レバレッジ、ジャンプ、倒産リスク、情報取引など複数の要因を混ぜている。したがって、急なskewをそのまま「悪材料情報」と読むと、景気循環や信用リスクという恒常的な露出を情報と取り違える。

論文の狙いは、risk-neutral return skewnessとして観測されるskewを、企業の長期的な構造特性と短期情報へ分解することにある。

## 3. 枠組み

概念的には銘柄 $i$ のskewを

```math
\operatorname{Skew}_{i,t}
=g(\operatorname{Cyclicality}_{i,t},\operatorname{DefaultRisk}_{i,t})
+\operatorname{Info}_{i,t}
+\varepsilon_{i,t}
```

と書く。$g(\cdot)$ が構造的部分、残差の $\operatorname{Info}_{i,t}$ が短期の価格変動に関する情報フローを表す。ここで重要なのは、残差を無条件にmispricingと呼ばないことである。構造モデルの指定誤差、流動性、需給、測定誤差も残差に入り得る。

論文は企業のbusiness cyclicalityとdefault riskを二つの構造的risk sourceとして同定し、景気後退中・後にこの分解の説明力が特に高いとする。

## 4. 主な結果

1. 構造的リスク部分はIV skewの銘柄間変動を最大44%説明する。
2. この説明力は景気後退中・その直後で特に大きい。
3. 構造的部分を除いたskew残差は、hidden structural risk exposureを小さくした株式ポートフォリオの予測シグナルとして利用できると報告する。
4. したがって、skew水準だけで横断ソートするより、景気感応度・信用リスクを控除した成分を使う方が「情報」への解釈に近づく。

## 5. 実務への含意

- 個別株のput skewを見たら、まず企業の信用状態と景気betaを統制する。危機時ほどこの手順が重要になる。
- earnings、アナリスト改訂、オプション注文フローを検証する際には、構造的skewと残差skewを分けて回帰しないと係数の因果解釈が曖昧になる。
- 残差skewを株式ロング・ショートに使う場合でも、bid-ask、売買回転、shortability、イベント日を含むコスト後検証が必要である。

## 6. 限界と検証上の注意

1. 残差は情報だけでなく、モデル誤指定・流動性・一時的な需給を含み得る。
2. 「最大44%」はモデルと標本に条件付く説明力であり、全期間・全銘柄で一定ではない。
3. 本ノート作成時点で指定SSRN PDFが失効しているため、変数定義、標本フィルター、表ごとの係数は公刊本文を入手してから再照合する必要がある。
4. 予測力は公刊時点までのhistorical resultであり、現在の個別株オプション市場における投資可能なalphaを保証しない。

## 7. 関連資料

- Liuren Wu and Yaofei Xu, [Cross-Sectional Variation of Risk-targeting Option Portfolios](2026_Wu_CrossSectionalRiskTargetingOptionPortfolios.md): IV surface全体をrisk-targeting portfoliosへ圧縮する後続研究。
- Yuhang Xing, Xiaoyan Zhang, Rui Zhao, [What Does the Individual Option Volatility Smirk Tell Us About Future Equity Returns?](2010_Xing_OptionVolatilitySmirkEquityReturns.md): individual-stock smirkと将来リターンの代表的検証。
