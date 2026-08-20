# Order Flow and Expected Option Returns — Muravyev (2016)

## 書誌情報

- **論文名**: *Order Flow and Expected Option Returns*
- **著者**: Dmitriy Muravyev
- **掲載誌**: Journal of Finance, 71(2), 673-708
- **公刊年**: 2016
- **DOI**: https://doi.org/10.1111/jofi.12380
- **原資料**: JSTOR/Wiley
- **リポジトリ内PDF**: 未保存。指定JSTOR PDF URLはClient Challenge HTMLを返し、PDF本文として検証できなかった。
- **キーワード**: option order flow, expected option returns, inventory risk, asymmetric information, market makers

## 一言でいうと

オプション注文フローは、将来のオプション収益を強く予測する。Muravyevは、取引の価格インパクトをマーケットメーカーの在庫リスク成分と非対称情報成分に分け、オプション市場では在庫リスク成分が特に大きいことを示す。過去の注文不均衡は、一般的なオプション収益予測変数より強い予測力を持つ。

## 1. 問題意識

オプション価格は原資産、ボラティリティ、金利だけで決まるように見えるが、実際のマーケットメーカーは在庫とヘッジコストを抱える。注文フローが一方向へ偏ると、価格は一時的に需給プレミアムを含み、その後のオプション収益に予測可能性が生じる。

## 2. 中核アイデア

取引による価格変化は、大きく2つに分けられる。

- **asymmetric information**: 取引相手が情報を持つため、価格が恒久的に動く部分
- **inventory risk**: マーケットメーカーが一時的に在庫を持つため、補償として価格を動かす部分

オプションでは、原資産デルタだけでなくgamma、vega、skewリスクも抱えるため、在庫リスク成分が大きくなりやすい。

## 3. データと実証設計

- オプション取引・気配データとopen/close区分を用いる。
- 日次のオプション注文不均衡を構成する。
- 価格インパクトを一時的成分と恒久的成分へ分解する。
- オプションの横断的な将来リターンを、過去注文不均衡で予測する。

## 4. 主要結果

- オプション取引の価格インパクトは大きく、在庫リスク成分が非対称情報成分より大きい。
- 在庫リスクに由来する注文不均衡の価格インパクトは、従来想定よりかなり大きい。
- 過去の注文不均衡は、将来のオプション収益を強く予測する。
- この予測力は、単なる原資産リターンや既存の代表的予測変数では説明しきれない。

## 5. 解釈

この論文は、オプションの期待収益をボラティリティ・リスクプレミアムだけでなく、マーケットメーカーの在庫補償として読む道を開く。注文フローが偏った系列は、価格が需給で押し上げられ、その後リターンが低くなる可能性がある。

Bollen and Whaley (2004) がIV形状に対して行った需給分析を、より直接的にオプション期待収益へ接続する研究と位置づけられる。

## 6. 限界

- 指定JSTOR URLからPDFを取得できなかったため、ノートは書誌情報と公開要旨に基づく。
- 取引データと注文方向分類の品質に依存する。
- 現代のマルチレッグ、PFOF、内部化、0DTE市場では在庫移転の経路が変わっている可能性がある。
- 予測可能性があっても、bid-ask、手数料、証拠金、在庫制約後に投資可能とは限らない。

## 7. 次に検討すべき問い

- 0DTEオプションでは在庫リスク成分と情報成分の比率はどう変わるか。
- gamma・vega・vanna別に注文不均衡を作ると、どのリスクが将来収益を予測するか。
- market maker inventory proxyと公開order imbalanceを組み合わせると、IV反転を予測できるか。
- Muravyev型のorder-flow signalは、Bollen-Whaley型NBPやHu (2014) の情報取引指標とどこが重なるか。

## BibTeX

```bibtex
@article{Muravyev2016,
  author  = {Muravyev, Dmitriy},
  title   = {Order Flow and Expected Option Returns},
  journal = {Journal of Finance},
  volume  = {71},
  number  = {2},
  pages   = {673--708},
  year    = {2016},
  doi     = {10.1111/jofi.12380}
}
```
