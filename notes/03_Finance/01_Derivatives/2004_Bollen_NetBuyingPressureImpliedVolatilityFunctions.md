# Does Net Buying Pressure Affect the Shape of Implied Volatility Functions? — Bollen and Whaley (2004)

## 書誌情報

- **論文名**: *Does Net Buying Pressure Affect the Shape of Implied Volatility Functions?*
- **著者**: Nicolas P. B. Bollen, Robert E. Whaley
- **掲載誌**: Journal of Finance, 59(2), 711-753
- **公刊年**: 2004
- **DOI**: https://doi.org/10.1111/j.1540-6261.2004.00647.x
- **手元PDF版**: SSRN稿、Latest draft September 2002
- **リポジトリ内PDF**: [2004_Bollen_NetBuyingPressureImpliedVolatilityFunctions_SSRN319261.pdf](../../../papers/03_Finance/01_Derivatives/2004_Bollen_NetBuyingPressureImpliedVolatilityFunctions_SSRN319261.pdf)
- **キーワード**: net buying pressure, implied volatility function, limits to arbitrage, order flow, volatility smile

## 一言でいうと

オプションのIV smile/smirkは、原資産の確率分布だけでなく、特定系列への公開注文フローの買い圧力にも反応する。S&P 500指数オプションではput買い圧力がIVを強く押し上げ、個別株オプションではcall需要の影響が大きい。需給が完全裁定されないため、IVFの形状は投資家需要とマーケットメーカーの在庫制約を反映する。

## 1. 問題意識

標準的な無裁定モデルでは、オプション価格は原資産分布と金利などから決まる。しかし現実には、OTM putの保険需要や個別株callの投機需要が偏る。マーケットメーカーが無限のリスク許容度を持たないなら、系列ごとの注文不均衡は価格、つまりIVへ反映される。

## 2. 中核アイデア

net buying pressureを、あるオプション系列で顧客が買い手主導となった契約数から売り手主導となった契約数を差し引いた量として測る。

```math
NBP_{i,t}=BuyInitiatedContracts_{i,t}-SellInitiatedContracts_{i,t}
```

IV変化は、原資産リターン、出来高、自己ラグ、ATMやOTM系列のNBPで説明される。

```math
\Delta \sigma_{i,t}
=
\alpha
+ \beta_1 R_{S,t}
+ \beta_2 V_{S,t}
+ \gamma NBP_{i,t}
+ \rho \Delta \sigma_{i,t-1}
+ \varepsilon_{i,t}
```

limits-to-arbitrage仮説では、需要が一時的にIVを押し上げ、その後ある程度反転することが予想される。

## 3. データと実証設計

- S&P 500指数オプションと20銘柄の個別株オプションを比較する。
- オプション系列をmoneyness別に分類する。
- 公開注文フローから系列別のnet buying pressureを構成する。
- IV変化回帰と、デルタヘッジ済みオプション売り戦略の異常収益を検証する。

## 4. 主要結果

- S&P 500指数オプションでは、ATM putやOTM putの買い圧力がIV上昇と強く結びつく。
- 個別株オプションでは、call側の買い圧力がIV変化をより強く説明する。
- ラグ付きIV変化はしばしば負で、需給ショックの一部反転を示す。
- デルタヘッジした指数オプション売りは紙面上大きな異常収益を持つが、vega hedgingを入れると収益は消えるか負になる。

## 5. 解釈

この論文は、IV smileを「市場がリスク中立分布を正しく読んだ結果」とだけ見ない。OTM index putの保険需要、個別株callの投機需要、マーケットメーカーの在庫・ヘッジ制約が、IVFの形を動かすと見る。

0DTEやリテール・オプション市場を読むときも、同じ発想が重要になる。ただし、公開フローだけから最終投資家の意図やディーラー在庫を断定することはできない。

## 6. 限界

- NBPの分類は取引データに依存し、現代の複雑なマルチレッグ取引や内部化市場では測定が難しい。
- 需要効果と情報効果を完全には分離できない。
- デルタ/vegaヘッジの実現可能性は、実際のbid-ask、資金制約、執行リスクに依存する。
- 手元PDFは2002年SSRN稿であり、公刊版の細部と一致しない可能性がある。

## 7. 次に検討すべき問い

- SPXW 0DTEでは、同じNBPがIV levelよりskewやwingへどの程度集中するか。
- retail、institutional、market makerを分けると、Bollen-Whaley型の需要効果はどう変わるか。
- NBPの反転は、在庫解消なのか、情報の現物価格反映なのか。
- option return anomalyのalphaは、需給リスク、volatility risk premium、取引コストでどこまで分解できるか。

## BibTeX

```bibtex
@article{BollenWhaley2004,
  author  = {Bollen, Nicolas P. B. and Whaley, Robert E.},
  title   = {Does Net Buying Pressure Affect the Shape of Implied Volatility Functions?},
  journal = {Journal of Finance},
  volume  = {59},
  number  = {2},
  pages   = {711--753},
  year    = {2004},
  doi     = {10.1111/j.1540-6261.2004.00647.x}
}
```
