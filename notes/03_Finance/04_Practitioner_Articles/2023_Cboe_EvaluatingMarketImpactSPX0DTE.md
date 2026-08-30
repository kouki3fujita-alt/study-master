# Volatility Insights: Much Ado About 0DTEs — Evaluating the Market Impact of SPX 0DTE Options — Cboe (2023)

## 書誌情報

- **記事**: “Volatility Insights: Much Ado About 0DTEs - Evaluating the Market Impact of SPX 0DTE Options”
- **著者**: Mandy Xu
- **発行者**: Cboe Global Markets
- **日付**: 2023年9月8日
- **原文**: [Cboe Insights](https://www.cboe.com/insights/posts/volatility-insights-evaluating-the-market-impact-of-spx-0-dte-options/)
- **種別**: 取引所の実務的市場構造記事（査読論文ではない）
- **保存方針**: Web記事本文は複製せず、URLと分析ノートのみを保存する。

## 1. 一言でいうと

SPX 0DTEの出来高・想定元本は大きいが、それだけで市場への影響は測れない。Cboeは取引役割を含む自社データでcustomer flowとmarket-maker net gammaを集計し、平均的な0DTEデルタヘッジ量はS&P先物の一日想定元本のごく小さい割合で、2023年時点のデータからは0DTEが日中ボラティリティを系統的に増幅した証拠は限定的だと論じる。

## 2. なぜ出来高だけでは不十分か

火曜・木曜満期の導入後、SPX 0DTEは2016年の全SPX出来高の約5%から、2023年8月には平均約50%へ拡大した。2023年の平均日次出来高は約123万契約、想定元本は約5,000億ドルとされる。

しかし、market makerのヘッジは総出来高ではなく、customerの買い・売り、put・call、strike、時点を相殺した**ネット感応度**で決まる。たとえば2023年8月15日の4,440 putでは約10万契約のgross取引があっても、market makerのnet shortは約3千契約（買い52千、売り55千）にとどまったという。

## 3. net gammaでの市場影響評価

記事はCboe取引データからmarket makerの0DTE net gammaを見積もり、平均的なgamma hedge想定元本を約1.7億-6.7億ドルとする。これは日次S&P先物想定元本の約0.04-0.17%である。

15時30分ETの中央値は約1.73億ドル、25-75 percentileは -11億ドルから +24億ドル、観測範囲は -50億ドルから +77億ドルとされる。極端な場合でも先物の日次想定元本に対する比率は約1.3-1.9%であり、記事はこれを「通常時に市場を支配するほどの規模ではない」と解釈する。

## 4. ボラティリティとの照合

- 2023年年初来の1か月close-to-close IVとintraday realized volatilityの差は2.7 vol pointで、過去10年平均と同程度。
- 1分間の2-sigma価格ギャップの頻度に、0DTE成長後の明瞭な上昇は観測されなかったとする。
- 2023年8月15日の約0.4%下落では、15時のmarket maker gammaは約+20億ドル、15時30分でも約-5億ドルにすぎず、機械的な負gammaヘッジだけで下落を説明することは難しいとしている。

## 5. 実務への含意

- 「0DTE出来高が大きい」ではなく、顧客の符号付きflow、net gamma、delta、満期別position、先物の実際のmarket impactを同時に見る。
- public OIだけからdealer inventoryや顧客意図を断定しない。記事の集計はCboe取引役割データを使うため、外部者がOIだけで再現できる指標ではない。
- stress dayには0DTEだけでなく、SPY、非0DTE SPX、先物・現物・OTCを含むヘッジ総量を確認する必要がある。

## 6. 限界と批判点

1. Cboe自身の市場解説であり、独立した査読・再現研究ではない。
2. net gammaの復元仕様、他市場でのoffsetting positions、participant-level inventoryは完全には開示されない。
3. 「平均的に小さい」ことは、特定strike・イベント時・流動性低下時の局所的フィードバックがないことを意味しない。
4. 2023年の結果を、参加者構成や満期制度が変化した現在へそのまま外挿してはならない。

## 7. 関連資料

- Cboe, [0DTEs Decoded: Positioning, Trends, and Market Impact](../01_Derivatives/2025_Cboe_0DTEsDecodedPositioningTrendsMarketImpact.md): 2025年の更新的な取引所レポート。
- Amaya et al., [0DTE Index Options and Market Volatility: How Large is Their Impact?](../01_Derivatives/2025_Amaya_0DTEIndexOptionsMarketVolatility.md): 全取引記録を使う学術的な集計gamma推定。
