# Hope at a Reasonable Price — Fu, Li, Musto, and Pearson (2025)

## 書誌情報

- **論文**: Lei Fu, Su Li, David K. Musto, Neil D. Pearson, “Hope at a Reasonable Price: Customer Use of Limit Orders in the 0DTE Market”
- **版**: SEC Division of Economic and Risk Analysis (DERA) Working Paper Series
- **日付**: March 16, 2025
- **原論文**: [SEC PDF](https://www.sec.gov/files/dera-hope-reasonable-prc-2503.pdf)
- **JEL**: G12, G13, G23
- **キーワード**: 0DTE options, SPXW, OPRA, non-marketable limit orders, BBO, retail order flow, transaction costs
- **手元PDF上の注意**: DERA Working Paperであり、SECやCommissionの公式見解ではなく、著者の見解として読む必要がある。

## 1. 一言でいうと

0DTEオプションはスプレッドが広く、個人投資家がマーケットメーカーに高いコストを払わされているように見える。本稿は、SPXW 0DTEのlimit-order bookとOPRAデータを分析し、顧客がmarketable orderだけでなくnon-marketable limit order (NMLO)で流動性供給側にも回っていること、そしてその取引コストがかなり低いことを示す。結論は、0DTE市場で顧客が一方的に搾取されているという見方は単純すぎる、というもの。

## 2. 問題意識

0DTEオプション、とくにSPXWの短期・ややOTMオプションは、少額で大きなペイオフを狙えるため「宝くじ型」商品として批判されやすい。 quoted spread が広ければ、顧客がmarketable orderで即時執行すると、半スプレッド分のコストが大きく見える。

しかし、顧客は常にスプレッドを支払う必要はない。自分でBBO内またはBBO上に指値を置き、マーケットメーカーや他の注文と競争して流動性を供給できる。本稿の焦点は、実際に顧客がNMLOを使っているのか、使っているならどれだけ低コストに執行できているのかである。

## 3. データと対象市場

主な対象はCboeのSPXWオプションである。

- **商品**: SPXW 0DTE options
- **データ**: OPRA trades and quotes、MIDAS関連データ
- **期間**: 2020年7月1日から2023年9月28日
- **区分**:
  - Early period: 2020年7月1日から2022年4月22日
  - Late period: 2022年4月25日から2023年9月28日
- **制度イベント**: 2022年に火曜・木曜満期が追加され、0DTE取引日が週全体へ拡大

著者らは、BBO、quote condition code、trade condition codeを使い、顧客のNMLOがBBOに存在する時間、実際に約定したケース、MTOとPOの取引コストを測定する。

## 4. 中核となるデータ処理

### 4.1 OPRAのtrade/quote sequencing問題

本稿の重要な技術的貢献は、OPRAデータの時系列順序問題を特定して補正する点である。SPXWのLOBでは、取引がBBOの板数量を消費すると、その取引後の新しいBBOが記録される。しかしOPRAデータでは、この新BBOのタイムスタンプが取引そのものより前に見えることがある。

このまま取引価格を「直前BBO」と比較すると、実際には取引後のBBOと比較してしまい、執行コストやBBO内約定の判定を誤る。著者らは、連続するBBO変化と取引数量・価格を突き合わせ、取引とBBOを実際の順序へ戻す。

### 4.2 quote condition codeによる顧客NMLOの識別

OPRAのquote condition codeは、BBO上に顧客注文が含まれるかを示す。本稿はこれを使い、顧客がBBOで流動性供給している場面を識別する。

特に分析される顧客NMLOは次の二つである。

- **MTO (market-turning order)**: 既存BBOを改善して、新しいbest bidまたはbest offerを作る顧客指値注文
- **PO (pick-off order)**: BBOの既存価格に並び、先行注文が消えた結果、最後に残って約定する顧客注文

MTOは価格改善によって先頭に立つ能動的な流動性供給、POは同価格の行列で待つ受動的な流動性供給として読める。

## 5. 主要結果

### 5.1 顧客NMLOはBBOに頻繁に存在する

直近データでは、活発に取引されるややOTMオプションで、顧客注文がBBOにいる時間が半分を超える。深いOTMオプションでは、best offer側で顧客注文が存在する比率がさらに高い。

これは、顧客が単にmarketable orderでスプレッドを支払うだけの存在ではなく、limit-order book上で流動性を供給していることを示す。

### 5.2 0DTE取引の相当部分が顧客NMLO由来

0DTE取引の大きな割合が、顧客NMLOと関連している。著者らは、少なくとも約4分の1の0DTE取引が、約定した顧客MTOまたはPOであると推定する。多くは1枚から数枚の小口取引で、リテールサイズの注文フローと整合的である。

### 5.3 MTOの期待コストはmarketable orderより低い

顧客がBBOを改善するMTOを出す場合、約定すればmarketable orderより安い価格で取引できる。一方、約定しなければ、価格が不利に動いた後にmarketable orderへ置き換えるコストがある。

著者らは、MTOが1秒以内に約定しなければmarketable orderで置き換えるという保守的な仮定でも、期待コストはmarketable orderより低いと示す。例として、2ティック幅の低価格call買いでは、MTOのfill rateはearly periodで50%、late periodで62%へ上がり、期待コストはmarketable orderの約半分程度になる。

### 5.4 取引コストは時間とともに低下する

2020年から2023年にかけて、BBO幅は狭まり、顧客MTOのfill rateは上昇する。これは0DTE市場の流動性供給競争が強まり、顧客がより低コストで参加できるようになったことを示す。

### 5.5 RetailはPIAだけでなくLOBにもいる

先行研究では、個人投資家の注文はprice improvement auction (PIA)へ送られることが多いと想定されることがある。本稿は、非成行の顧客指値注文はLOB上で処理されるため、リテールサイズの顧客注文がLOBにも相当量存在する可能性を示す。

## 6. この論文の貢献

1. 0DTE市場における顧客の役割を、marketable orderの需要者ではなく、NMLOによる流動性供給者として再評価した。
2. OPRA trade/quote sequencing問題を補正し、0DTEオプションの執行品質分析で重要なデータ処理上の注意点を示した。
3. quote condition codeを使って顧客NMLOを識別し、BBO上の顧客存在と約定を実証的に測定した。
4. 広いquoted spreadから見える表面的コストと、実際の指値執行コストが大きく異なることを示した。
5. 0DTE市場の「顧客搾取」論に対し、より細かい市場構造ベースの反証を与えた。

## 7. 限界と批判点

1. **対象はSPXW中心**: 単一株オプション、ETFオプション、他指数オプションへ一般化するには注意が必要である。
2. **顧客種別の限界**: customer codeや注文サイズからリテールらしさを推定できるが、リテールと機関投資家を完全には分離できない。
3. **未約定注文の完全観測ではない**: MTOの未約定リスクは保守的に仮定されるが、顧客の実際のキャンセル・再発注戦略までは完全に分からない。
4. **0DTEの厚い銘柄に偏る**: 活発なSPXW市場では指値競争が機能しても、流動性の薄い市場では同じ結論にならない可能性がある。
5. **DERA Working Paper**: preliminary materialであり、最終的な査読済み公刊版ではない。

## 8. 実務への含意

- 0DTEの執行コストを評価するとき、quoted spreadだけでなく、指値注文のfill rate、未約定時コスト、realized spreadを測る必要がある。
- OPRAデータを使う研究では、tradeとquoteのタイムスタンプ順序をそのまま信じると、BBO比較が壊れる可能性がある。
- 顧客注文は常に流動性を消費する側ではなく、BBO改善やBBO上の待機によって流動性供給側にも回る。
- 0DTE市場のリテール論争では、PIAだけでなくLOB上のnon-marketable limit ordersを含めて評価する必要がある。
- 0DTEの市場影響を扱うAmaya et al. (2025)や、日中ヘッジ需要を扱うBaltussen et al. (2021)と併読すると、取引コスト、注文フロー、ガンマヘッジの接点が見える。

## 9. 次に検討すべき問い

- OPRA sequencing補正を実装しない場合、既存研究の執行コスト推定はどの程度バイアスを受けるか。
- 0DTEのNMLO戦略は、満期までの残り時間、moneyness、tick size、VIX水準でどのように変わるか。
- 2023年以降、0DTE取引量の拡大と競争激化により、顧客MTOのfill rateとコストはさらに改善したか。
- 顧客NMLOはマーケットメーカーのgamma hedgingやmarket-on-close flowとどう相互作用するか。
- 日本市場や他指数オプション市場でも、同様に顧客指値注文がスプレッド内競争を作っているか。

## 10. 総合評価

この文献は、0DTEオプションを「高コストな宝くじ的取引」とだけ見る議論に対して、実際の注文種別と板上の競争を持ち込む重要な補正である。とくにOPRAのtrade/quote sequencing問題は、執行品質研究の前処理として実務的価値が高い。0DTE市場のリスクや投機性を否定する論文ではないが、顧客が指値注文でスプレッドを回避し、流動性供給側にも立っているという点は、0DTE市場構造を評価するうえで外せない。
