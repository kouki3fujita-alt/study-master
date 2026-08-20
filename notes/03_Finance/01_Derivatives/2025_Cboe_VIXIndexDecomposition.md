# The VIX Index Decomposition — Cboe (2025)

## 書誌情報

- **資料名**: *The VIX Index Decomposition: A Heuristic Framework to Unravel Unexpected Behaviors in the VIX Index*
- **発行者**: Cboe / Volatility Insights
- **著者**: Edward K. Tom
- **日付**: 2025年8月1日
- **原資料**: https://cdn.cboe.com/resources/vix/VIX-Decomposition-2025-08-01.pdf
- **リポジトリ内PDF**: [2025_Cboe_VIXIndexDecomposition.pdf](../../../papers/03_Finance/01_Derivatives/2025_Cboe_VIXIndexDecomposition.pdf)
- **キーワード**: VIX, decomposition, SPX skew, sticky strike, parallel shift, downside convexity

## 一言でいうと

VIXの変化を「SPXが下がったからVIXが上がった」と単純に見ず、SPX spot移動に伴う期待変化、IVサーフェスの平行シフト、put/call skewの傾き、downside/upside convexity需要へ分解するCboeの実務フレーム。VIXがSPXと同方向に動く、あるいは通常より大きく動く局面を、SPXオプション・サーフェスのどの部分が動いたかから説明する。

## 1. 問題意識

VIXはしばしばfear gaugeとして扱われ、SPXと逆方向に動くと期待される。しかし実際には、SPXとVIXが同方向に動く日もあり、VIXの上昇幅が直感より大きい日もある。Cboeは、VIX算出式が壊れているのではなく、SPXオプション・サーフェスの複数成分が重なっていると整理する。

## 2. 6つの分解要素

資料は、VIX変化を以下の6要素で説明する。

1. expected VIX move per sticky strike
2. parallel shift of the volatility skew
3. change in the slope of the put skew gradient
4. change in the slope of the call skew gradient
5. demand for downside convexity
6. demand for upside convexity

この分解は厳密な構造モデルではなく、VIX算出に使われるSPXオプションの30日補間skewを、実務家が理解しやすいリスク成分へ分けるヒューリスティックである。

## 3. 中核アイデア

まず、spotが動いたとき、前日のskew上で新しいATM付近へ移動しただけならVIXはどれだけ変わるかを測る。これはsticky strike的な期待変化である。

次に、skew全体が上がった/下がった分をparallel shiftとして取り出す。

さらに、put側とcall側のskew勾配の変化、deep OTM wingの曲率変化を分ける。特にdownside convexityは、深いOTM putへのテール保険需要を表す。

## 4. データと実務設計

- VIX算出対象となるSPXオプションの近い満期と次の満期を用いる。
- 30日相当のSPX skewへ補間してから、spot、ATM、30-delta、10-delta近辺などを参照する。
- 2024年8月のyen-carry unwindや2025年の大幅変動局面をケーススタディとして比較する。

## 5. 主要結果・読み方

- 平常時の小さなVIX変化は、spot移動に伴うexpected move per sticky strikeでかなり説明できる。
- 大きなショック時には、parallel shiftやwing convexityがexpected moveを上回ることがある。
- SPX下落でもVIXが下がる、SPX上昇でもVIXが上がるといった同方向変化は、surface shiftやskew/convexity需要で説明できる。
- VIXの上昇がdownside convexity由来なのか、upside convexity由来なのかで、ポジショニング解釈は大きく変わる。

## 6. 解釈

この資料は、VIXを単一の恐怖指数としてではなく、SPXオプション・サーフェス全体の加重集計として読む実務メモである。VIX上昇には、単純な株価下落、全体的なvol regime shift、put skew steepening、deep OTM wing需要など複数の経路がある。

0DTEや短期SPXオプションの分析では、VIX水準だけでなく、どのdelta帯・どのwingが動いたのかを分解する必要がある。

## 7. 限界

- Cboeの実務ヒューリスティックであり、査読済み論文ではない。
- 分解成分は直感的だが、完全に直交する経済因子ではない。
- VIX算出用のmid quote、満期補間、strike選択、気配フィルターの影響は別途残る。
- 公開資料だけでは、実際の投資家別ポジションやディーラー在庫は分からない。

## 8. 次に検討すべき問い

- VIX分解成分を日次系列化すると、VIX futures returnやSPX returnを予測するか。
- downside convexity成分とVVIX、SKEW、put spread需要はどの程度一致するか。
- 0DTE出来高の増加は、VIX spotの短期skew/wing分解へどの程度影響するか。
- Cboeの分解とCont-da Fonseca型のPCA因子を対応づけられるか。

## BibTeX

```bibtex
@techreport{CboeVIXDecomposition2025,
  author      = {Tom, Edward K.},
  title       = {The VIX Index Decomposition: A Heuristic Framework to Unravel Unexpected Behaviors in the VIX Index},
  institution = {Cboe},
  type        = {Volatility Insights},
  year        = {2025},
  month       = {August},
  day         = {1},
  url         = {https://cdn.cboe.com/resources/vix/VIX-Decomposition-2025-08-01.pdf}
}
```
