# Dynamics of Implied Volatility Surfaces — Cont and da Fonseca (2002)

## 書誌情報

- **論文名**: *Dynamics of Implied Volatility Surfaces*
- **著者**: Rama Cont, Jose da Fonseca
- **掲載誌**: Quantitative Finance, 2(1), 45-60
- **公刊年**: 2002
- **DOI**: https://doi.org/10.1088/1469-7688/2/1/304
- **原資料**: 手元PDF
- **リポジトリ内PDF**: [2002_Cont_DynamicsImpliedVolatilitySurfaces.pdf](../../../papers/03_Finance/01_Derivatives/2002_Cont_DynamicsImpliedVolatilitySurfaces.pdf)
- **キーワード**: implied volatility surface, Karhunen-Loeve decomposition, PCA, vega risk, sticky moneyness

## 一言でいうと

インプライド・ボラティリティ・サーフェスの変化は、単なる水準変化ではなく、少数の直交因子でかなり説明できる。SPXとFTSEの指数オプションを用い、日次IVサーフェス変化をKarhunen-Loeve分解すると、level、slope、curvatureに相当する因子が現れ、古典的なsticky delta/sticky moneynessより豊かなサーフェス変動モデルが必要だと示す。

## 1. 問題意識

Black-Scholesではボラティリティは定数だが、実務では行使価格と満期ごとにIVが異なる。さらに、そのサーフェス自体が日々変形するため、単一のボラティリティ・パラメータや単一のvegaだけでは、オプション・ポートフォリオのリスクを捉えにくい。

著者らの焦点は、原資産価格の確率過程からIVを導くのではなく、市場で観測されるIVサーフェスそのものを確率的な曲面として扱う点にある。

## 2. 中核アイデア

日次のIVサーフェスを、moneynessと満期の関数として表す。

```math
\sigma_t(K,T)
```

その変化を平均サーフェスからの偏差として取り出し、共分散作用素を推定する。Karhunen-Loeve分解では、サーフェス変動は次のように近似される。

```math
U_t(x) \approx \sum_{k=1}^{N} x_k(t) f_k(x)
```

ここで、`x` はmoneynessと満期の座標、`f_k` は固有サーフェス、`x_k(t)` は各因子への日次射影である。通常のPCAを、曲面データへ拡張したものと考えればよい。

## 3. データと実証設計

- SPX指数オプションとFTSE指数オプションの終値データを用いる。
- ノイズの大きい個別オプション価格をそのまま使わず、moneynessと満期方向に平滑化してIVサーフェスを構成する。
- 日次サーフェスの変化に対して共分散を推定し、固有モードを抽出する。

この設計の利点は、個別ストライクの欠損やノイズに引きずられず、サーフェス全体の「動き方」を直接見る点にある。

## 4. 主要結果

- SPXでは最初の3因子が日次IV変化の分散の大半を説明し、本文では約98%と報告される。
- 第1因子はサーフェス全体の水準変化、つまりlevel factorに近い。
- 第2因子は短期/長期、またはmoneyness方向の傾き変化を捉える。
- 第3因子はbutterfly/curvatureに近く、smileの曲率変化を表す。
- 第1因子は原資産リターンと強い負の関係を持つが、全因子が原資産だけで完全に説明されるわけではない。

## 5. 解釈

この論文は、IVサーフェスのリスク管理を「ATM IVが何ポイント動くか」から、「水準、傾き、曲率のどのリスクに曝露しているか」へ拡張する。分散スワップやVIXだけでは拾えない、skewやwingの変動リスクを扱う出発点になる。

また、1因子の確率ボラティリティ・モデルや単純なsticky ruleでは、観測されるIVサーフェス変形を十分に再現できないという批判にもなっている。

## 6. 限界

- サンプルは指数オプション中心で、個別株や0DTEのような短期・需給主導市場にそのまま外挿できない。
- 平滑化手法が結果に影響しうる。
- PCA因子は統計的に直交するが、必ずしも経済的に独立したリスク源ではない。
- 取引可能性、bid-ask、裁定制約を直接モデル化しているわけではない。

## 7. 次に検討すべき問い

- 0DTE導入後のSPXサーフェスでも、level/slope/curvatureの3因子で十分か。
- PCA因子のショックはディーラー在庫、顧客注文フロー、マクロイベントとどう対応するか。
- VIX、VVIX、SKEW、variance swapを組み合わせると、どの因子がヘッジ可能か。
- 機械学習的な低次元表現は、この古典的なPCA表現をどれだけ改善するか。

## BibTeX

```bibtex
@article{ContDaFonseca2002,
  author  = {Cont, Rama and da Fonseca, Jose},
  title   = {Dynamics of Implied Volatility Surfaces},
  journal = {Quantitative Finance},
  volume  = {2},
  number  = {1},
  pages   = {45--60},
  year    = {2002},
  doi     = {10.1088/1469-7688/2/1/304}
}
```
