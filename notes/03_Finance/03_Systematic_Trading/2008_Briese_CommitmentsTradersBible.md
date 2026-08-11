# The Commitments of Traders Bible — Briese (2008)

## 書誌情報

- **書籍**: Stephen Briese, “The Commitments of Traders Bible: How to Profit from Insider Market Intelligence”
- **出版社**: John Wiley & Sons, Inc.
- **シリーズ**: Wiley Trading
- **出版年**: 2008
- **ISBN**: 978-0-470-17842-3
- **手元PDF上の注意**: ユーザー指定のローカルPDFを保存した。これは査読論文ではなく、COTレポートを使った先物・商品トレーディングの実務書である。

## 1. 一言でいうと

CFTCのCommitments of Traders (COT) レポートを、合法的に公開される「大口参加者の実ポジション情報」として読み、commercial hedgers、large speculators、small traders、commodity index tradersの動きから市場転換を探すための実務フレームを整理した本である。中心は、commercial net positionを履歴レンジで標準化するCOT Indexと、急なポジション変化を見るMovement Indexである。

## 2. 問題意識

多くのテクニカル指標やセンチメント指標は価格やアンケートから作られるが、COTは実際の先物ポジションを報告する。Brieseの主張は、価格だけを見るよりも、誰が買い、誰が売っているかを見た方が、市場の行き過ぎや転換点を発見しやすいというものだ。

特に重視されるのはcommercial hedgersである。商業参加者は生産、在庫、輸入、輸出、加工など現物ビジネスと結び付いており、需給の実態に近い情報を持つとされる。本書では、commercialが極端に買っている局面は強気、極端に売っている局面は弱気の手がかりとして扱われる。

## 3. COTレポートの基本構造

COTは、CFTCが週次で公表する先物市場の建玉レポートである。本書では主に以下の分類を扱う。

- **Commercial hedgers**: 現物ビジネスのリスクをヘッジする参加者
- **Large speculators**: 報告基準を超える大口投機家
- **Small traders**: 報告基準未満の非報告参加者
- **Commodity index traders**: 商品指数連動の投資家・運用主体

また、futures-onlyとfutures-and-options combined、long formとshort form、supplemental reportの違いも実務上の注意点として整理される。

## 4. 中核となる指標

### 4.1 COT Index

COT Indexは、ある参加者の現在のネットポジションが、過去一定期間のレンジのどこにあるかを0-100で表す指標である。

```math
\mathrm{COT\ Index}_t
=
100
\times
\frac{\mathrm{Net}_t-\min(\mathrm{Net}_{t-L:t})}
{\max(\mathrm{Net}_{t-L:t})-\min(\mathrm{Net}_{t-L:t})}
```

commercialのCOT Indexが100に近い場合は、過去レンジの中でcommercialが非常に買っている状態を意味する。0に近い場合は、非常に売っている状態を意味する。Brieseは、この極端値を市場転換の重要な候補として扱う。

### 4.2 Movement Index

Movement Indexは、COT Indexの水準だけではなく、急激な変化を見る。たとえばcommercialのポジションが短期間で大きく買い方向へ動いた場合、価格トレンドがまだ反転していなくても、内部の需給バランスが変わり始めた可能性がある。

### 4.3 価格トリガーとの併用

本書は、COTの極端値だけで機械的に売買するのではなく、価格のブレイク、トレンドライン、チャートパターンなどと組み合わせる姿勢を取る。COTは方向の準備状態を示し、エントリーや損切りは価格で確認する、という分担である。

## 5. 構成と対象市場

本書は、理論編と実践編に分かれる。

- **Part I: COT Theory**: COTの歴史、レポート形式、参加者分類、commercialの読み方、COT Index、Movement Index、パターン認識
- **Part II: COT in Practice**: 通貨、株価指数、金属、石油、米国債、穀物、畜産、食品・繊維などの市場別分析

このため、研究論文というより、COTデータを使った特徴量設計・裁量判断・システム検証の材料集に近い。

## 6. 主要な考え方

### 6.1 Commercialを逆張り情報として読む

commercial hedgersは、価格下落局面で買いヘッジまたはショート削減を行い、価格上昇局面で売りヘッジを増やすことが多い。そのため、commercialの極端な買いは相場底入れ、極端な売りは天井圏の候補として解釈される。

### 6.2 Large speculatorsはトレンド追随的になりやすい

大口投機家は、価格トレンドに乗ってポジションを積み上げる傾向がある。本書では、large speculatorsのポジション極端化を、トレンド成熟や反転リスクのサインとして読む場面が多い。

### 6.3 Small tradersはしばしば逆指標として扱われる

小口トレーダーは、相場の終盤で遅れて参加しやすいとされる。ただし、この見方は市場や時期に依存するため、機械的な「小口と逆に行く」ルールとして扱うのは危険である。

### 6.4 COTはセンチメントではなくポジションである

本書の強いメッセージは、COTが意見調査ではなく実建玉データだという点である。誰かが強気と言ったかではなく、実際にポジションを持っているかを見る。その意味で、価格系列とは別の情報源として利用できる。

## 7. 実務への含意

- COTデータは、先物市場のポジショニング特徴量として体系的に管理する価値がある。
- commercial net、non-commercial net、small trader net、COT Index、Movement Indexを分けて保存すると、検証しやすい。
- COT単独の売買ルールではなく、価格トレンド、ボラティリティ、季節性、ロール利回り、需給ファンダメンタルズと組み合わせるべきである。
- 週次公表のため短期デイトレードよりも、スイングから中期のシグナル設計に向く。
- COT分類は制度変更を受けるため、長期バックテストでは系列の定義変更を明示的に処理する必要がある。

## 8. 限界と批判点

1. **査読論文ではない**: 実務書として有用だが、統計的検定や再現可能な学術実証としては限定的である。
2. **事例依存**: 多くの説明がチャート事例に基づくため、事後的なパターン認識に見えるリスクがある。
3. **データ遅延**: COTは週次で遅れて公表されるため、急変局面ではシグナルが古くなる。
4. **制度変更**: 2009年以降のdisaggregated COTなど、現在の分類体系は本書出版時点から変化している。
5. **極端値の罠**: COT Indexが極端になっても、価格トレンドは長く継続し得る。逆張りのタイミング指標として過信できない。
6. **市場横断の違い**: 農産物、通貨、金利、株価指数では参加者構造が異なるため、同じ閾値を一律に使うべきではない。

## 9. Sanders, Irwin, and Merrin (2008)との接続

BrieseはCOTをトレーディングのシグナルとして読む。一方、Sanders, Irwin, and Merrinは、COTやCITを市場機能と規制論争のために読む。両者を並べると、COTデータには少なくとも二つの使い方があることが分かる。

1. **予測・売買シグナル**: commercialやspeculatorの極端なポジションから価格転換を探す。
2. **市場構造分析**: ヘッジ需要に対して投機流動性が十分か、過剰かを評価する。

ライブラリ上では、前者をsystematic tradingの特徴量設計、後者をcommodity futuresの市場機能・規制分析として扱うのがよい。

## 10. 次に検討すべき問い

- COT Indexのlookback期間は、52週、156週、3年などのどれが市場別に安定するか。
- COT極端値は、単独でリターンを予測するのか、それとも価格モメンタムやbasisと交互作用すると強くなるのか。
- commercialの買い極端は、contango/backwardation、在庫、季節性を入れても情報を持つか。
- disaggregated COTのProducer/Merchant、Swap Dealer、Managed Money分類で、Briese型シグナルをどう更新できるか。
- COTを特徴量にした商品先物モデルは、Moskowitz et al. (2012)のtime series momentumと補完的か。

## 11. 総合評価

本書は、学術的な厳密さよりもCOTをどう読めばよいかに価値がある。商品先物や通貨先物のポジショニングを扱うなら、commercial hedgersとlarge speculatorsの見方、COT Indexの作り方、データ遅延や分類変更の落とし穴を押さえる入口として有用である。一方で、実運用に使うには、必ず現在のCFTC分類で再実装し、取引コスト、ロール、季節性、アウトオブサンプル検証を加える必要がある。
