# The Information in Option Volume for Future Stock Prices — Pan and Poteshman (2006)

## 書誌情報

- **著者**: Jun Pan, Allen M. Poteshman
- **掲載誌**: *The Review of Financial Studies*, 19(3), 871–908, 2006
- **DOI**: [10.1093/rfs/hhj024](https://doi.org/10.1093/rfs/hhj024)
- **著者PDF**: [MIT](https://www.mit.edu/~junpan/volume.pdf)
- **リポジトリ内PDF**: [2006_Pan_InformationOptionVolumeFutureStockPrices.pdf](../../../papers/03_Finance/01_Derivatives/2006_Pan_InformationOptionVolumeFutureStockPrices.pdf)
- **関連WP**: NBER Working Paper 10925
- **キーワード**: option volume、put-call ratio、informed trading、opening transactions、stock return predictability

## 1. 一言でいうと

CBOEの特殊な参加者別データから「買い手が新規ポジションを建てたput volume／call volume」を作ると、低いput-call ratioの銘柄が高い銘柄を翌日40bp超、翌週1%超アウトパフォームすることを示した代表的研究である。

重要なのは、一般公開される通常の出来高ではなく、売買方向と新規／手仕舞いを識別した非公開情報が予測力の中心だった点である。著者らは、単純な市場非効率ではなく、私的情報を持つ投資家が高レバレッジのオプションを選び、その情報が徐々に現物株価へ反映される過程と解釈する。

## 2. 中核シグナル

銘柄 \(i\)、日 \(t\) について、顧客の買いで新規建てされたプットとコールの出来高をそれぞれ \(PutOpenBuy_{i,t}\)、\(CallOpenBuy_{i,t}\) とする。基本シグナルは

```math
PC_{i,t}
=
\frac{PutOpenBuy_{i,t}}
{PutOpenBuy_{i,t}+CallOpenBuy_{i,t}}.
```

- 低い \(PC\): 新規コール買いが相対的に多く、正の方向情報
- 高い \(PC\): 新規プット買いが相対的に多く、負の方向情報

単純なput volume／call volumeではなく、**取引開始者、売買方向、新規建て**を識別することが核心である。既存ポジションの手仕舞いは、現在得た情報を自由に表現できるとは限らないため、opening tradeより情報量が弱いと予想される。

## 3. データと設計

- **期間**: 1990–2001年
- **データ**: CBOEの個別株オプション取引記録
- **識別可能な属性**: put/call、顧客区分、買い手／売り手主導、新規建て／手仕舞い
- **評価**: 翌日から数週間の個別株リターン
- **統制**: 市場、size、book-to-market、momentum等のリスク調整

銘柄をput-call signalで横断的に並べ、最も強い正シグナル群を買い、最も強い負シグナル群を売る。予測が徐々に弱まり反転しないか、公開取引データから再構築できるsignalでも同じ結果が出るか、投資家区分・情報非対称性・契約レバレッジで効果が変わるかを調べる。

## 4. 主要結果

### 翌日・翌週リターンを強く予測

最低put-call ratio群は最高群を、リスク調整後で翌日40bp超、翌週1%超アウトパフォームする。効果は数週間かけて弱まるが、方向を反転しない。

この持続性は、一時的な需給圧力より、私的情報が株価へ段階的に織り込まれる説明と整合する。

### 公開signalと非公開signalは違う

公開trade・quoteからLee–Ready型アルゴリズムで推定した買い手主導volumeにも短期予測力はあるが、1–2日程度で弱まり、その後反転する。非公開のopening分類と同時に入れると、公開signalの予測力は消える。

したがって「公表volumeだけで容易に利益を得られる」という結論ではない。主結果を生む情報は、当時リアルタイムに一般投資家が観測できない取引分類に含まれていた。

### 情報トレーダーが多い銘柄ほど強い

PIN（probability of informed trading）が高い銘柄ではsignalの予測力が大きい。単なる小型株効果ではなく、sizeを統制しても関係が残る。

### 高レバレッジ契約ほど情報量が多い

deep OTMなどレバレッジが大きい契約から作るsignalの予測力が最も強く、低レバレッジ契約では弱い。情報投資家が資本効率の高いオプションを選ぶというBlack（1975）型の仮説を支持する。

### 投資家区分で異なる

full-service broker経由の取引はdiscount broker経由より情報量が大きく、firm proprietary traderのsignalにはほとんど予測力がない。投資家を一括して集計すると情報が薄まることを示す。

## 5. 解釈上の注意

1. **put-call ratioは定義依存**: 総出来高、open interest、buyer-open volumeでは経済的意味が異なる。
2. **非公開情報に依存**: 研究の主signalを当時の一般投資家がリアルタイム再現できたわけではない。
3. **OTMは高レバレッジだけではない**: spread、lottery demand、ジャンプリスク、低premiumという特性も同時に変わる。
4. **予測力は因果そのものではない**: オプション取引が株価を動かすのか、情報を持つ投資家が先にオプションを選ぶのかを区別する必要がある。本論文の解釈は主に後者である。
5. **古い市場構造**: 1990–2001年は電子取引、複数取引所、週次・0DTE、手数料無料化以前である。
6. **実行コスト**: signalに基づく株式ロング・ショートでも、空売り、遅延、market impact、データ取得費用がある。

## 6. Hu (2014)・Ni et al. (2008)との関係

- **Pan–Poteshman (2006)**: オプションvolumeは将来の**株価方向**を予測するか。
- **Ni–Pan–Poteshman (2008)**: vega加重需要は将来の**実現ボラティリティ**を予測するか。
- **Hu (2014)**: option-induced stock imbalanceの予測力は**情報**か**デルタヘッジ圧力**か。

同じ「オプション注文フロー」でも、delta方向、vega方向、価格インパクトの識別は別問題である。

## 7. 実務的含意

- 総put-call ratioを、そのまま本論文のsignalと同一視しない。
- 可能ならopening/closing、customer/dealer、buy/sell、delta・vega換算を分ける。
- deep OTM volumeは情報だけでなくlottery demandやイベントヘッジも反映するため、決算・M&A・borrow条件と照合する。
- 予測戦略は、実際に利用可能だった時点のデータだけでout-of-sample検証する。

## 8. 次に検討したい問い

1. OPRA・取引所capacity・CATを使い、現在の市場でopening signalを再構築できるか。
2. 0DTEでは情報の株価反映速度が分・秒単位へ短縮しているか。
3. OTMレバレッジ効果はlottery preferenceとどう分離できるか。
4. delta、vega、gamma別の注文フローを同時に入れると、方向とボラティリティ情報を分けられるか。
5. 手数料・borrow・market impact後にも株式ロング・ショート収益は残るか。
