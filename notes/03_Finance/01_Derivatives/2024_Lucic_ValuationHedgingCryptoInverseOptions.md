# Valuation and Hedging of Cryptocurrency Inverse Options — Lucic and Sepp (2024)

## 書誌情報

- **論文名**: *Valuation and Hedging of Cryptocurrency Inverse Options*
- **著者**: Vladimir Lucic, Artur Sepp
- **掲載誌**: *Quantitative Finance*, Vol. 24, No. 7, pp. 851-869
- **発行年**: 2024年
- **SSRN投稿日**: 2023年11月18日
- **SSRN最終改訂**: 2026年2月5日
- **執筆日**: 2024年6月3日
- **出版社DOI**: [10.1080/14697688.2024.2364804](https://doi.org/10.1080/14697688.2024.2364804)
- **SSRN**: [Abstract 4606748](https://ssrn.com/abstract=4606748)
- **SSRN DOI**: [10.2139/ssrn.4606748](https://doi.org/10.2139/ssrn.4606748)
- **出版社ページ**: [Taylor & Francis Online](https://www.tandfonline.com/doi/abs/10.1080/14697688.2024.2364804)
- **リポジトリ内PDF**: 未保存。ユーザー指定のSSRNページからのDelivery PDF、および出版社PDFはいずれも403で取得できなかった。
- **キーワード**: inverse options, Deribit, cryptocurrency options, perpetual futures, change of numeraire, delta hedging, volatility risk premium

## 一言でいうと

Deribitなどの暗号資産取引所で一般的な「inverse options」を、通常のvanilla optionsを原資産フォワードをニュメレールにした測度で見たものとして整理し、評価・デルタヘッジ・P&L計測を定式化する論文。実証ではDeribitの暗号資産オプションデータを使ってデルタヘッジ戦略をバックテストし、USD会計とCoin会計の対応、ならびにDeribitオプションに観察される負のボラティリティ・リスクプレミアムを示す。

## 1. 問題意識

暗号資産オプションでは、契約がUSDではなくBTCやETHなど原資産コイン建てで取引・決済される「inverse contract」が広く使われる。これは、取引所やトレーダーが法定通貨口座を維持せずにデリバティブ取引を行えるためである。

ただし、inverse optionは通常のUSD建てオプションとP&L、デルタ、ヘッジ会計の見え方が異なる。実務ではBlack-Scholes型のモデルを使っても、測度・ニュメレール・会計単位を明確にしないと、ヘッジ量や戦略パフォーマンスを誤って読む可能性がある。

## 2. 理論的な整理

論文の中心的な理論結果は、inverse optionは特殊な新商品ではなく、原資産フォワードをニュメレールにしたmartingale measureの下で見た通常のvanilla optionとして扱えるという点である。

この測度変更により、オプション価格式とヘッジ量に調整が入る。特にデルタは、単純なUSD建てBlack-Scholes deltaとは異なり、コイン建て決済とニュメレール変更を反映した値になる。

実務的には、次の3点が重要である。

1. inverse contractのペイオフはコイン建てで表される。
2. USD建て評価とCoin建て評価は、パフォーマンス測定単位を合わせると整合する。
3. ヘッジにはperpetual futuresなど、暗号資産市場で実際に流動性の高いヘッジ手段を使う。

## 3. USD会計とCoin会計

暗号資産オプション戦略では、P&LをUSDで見るか、コイン数量で見るかによって戦略評価が変わって見える。

本論文は、USD accountingとCoin accountingを明示的に導入し、適切な単位で測れば両者が対応することを示す。これは、暗号資産ボラティリティ戦略を評価する際に重要である。USD建てで利益が出ているように見えても、BTC建てでは別のリスクを取っている可能性があるためである。

## 4. 実証：Deribitオプションのデルタヘッジ戦略

実証部分では、Deribitの暗号資産オプションデータを使い、デルタヘッジされたオプション戦略をバックテストする。

SSRN版の要旨では過去4年、出版社版の要旨では過去5年のDeribitデータを用いたと説明されている。これは改訂版・公刊版の差による表現差と見られる。

主な結果は、Deribitオプションには負で有意なリスクプレミアムが観察され、長期的にはボラティリティ売り戦略が正のリスク調整後パフォーマンスを期待できる、というものである。

## 5. 実務的な読み方

### Inverse optionのデルタはそのまま移植できない

伝統的なUSD建てオプションのデルタを、そのままBTC/ETH建てinverse optionへ適用すると、会計単位とニュメレールの違いを見落とす。inverse contractでは、コイン建てペイオフとUSD建て原資産価格が絡むため、測度変更後のデルタを使う必要がある。

### Deribitのvolatility risk premium

Deribitオプションに負のボラティリティ・リスクプレミアムがあるという結果は、伝統的市場の分散リスク・プレミアム研究と接続できる。ただし、暗号資産ではジャンプ、週末取引、清算、証拠金、perpetual funding、取引所固有リスクが強く、伝統市場よりも実装リスクが大きい。

### Coin建てリターンの管理

暗号資産投資家にとって、USD建て収益とCoin建て収益のどちらが目的関数かは重要である。BTCを増やしたい投資家とUSDを増やしたい投資家では、同じオプション戦略でもリスク評価が異なる。

## 6. 注意点と限界

- **PDF未保存**: SSRN Delivery PDFおよび出版社PDFはいずれも403で取得できなかったため、ノートは公開メタデータと要旨に基づく。
- **改訂差**: SSRN版は2026年2月5日改訂、公刊版は2024年版であり、データ期間や表現に差がある可能性がある。
- **単一取引所依存**: Deribitは暗号資産オプションの中心的取引所だが、取引所固有の証拠金、清算、流動性、参加者構成が結果に影響する。
- **ヘッジコスト**: perpetual futuresを使うヘッジでは、funding、スリッページ、清算リスク、取引所リスクが重要になる。
- **ボラティリティ売りのテールリスク**: 負のボラティリティ・リスクプレミアムは平均的な収益機会を示すが、暗号資産ではジャンプと流動性枯渇による損失が大きくなり得る。

## 7. ライブラリー内での位置づけ

- Alexander and Imeraj (2021) は、Deribit BTCオプションからBitcoin VIXと分散リスク・プレミアムを構築する。
- Lucic and Sepp (2024) は、暗号資産inverse option固有の評価・ヘッジ・会計単位を整理する。
- Liu, Packham, and Sepp (2025) は、暗号資産ジャンプリスクプレミアムを群発ジャンプの枠組みで分析する。
- Milionis et al. (2024) のLVR研究とは、暗号資産市場におけるボラティリティ、ヘッジ、流動性供給コストという点で接続する。

この論文は、暗号資産オプションを伝統的なオプション理論へ接続しつつ、inverse contractという市場固有仕様を正面から扱う実務・理論の橋渡し文献である。

## BibTeX

```bibtex
@article{LucicSepp2024,
  author  = {Lucic, Vladimir and Sepp, Artur},
  title   = {Valuation and Hedging of Cryptocurrency Inverse Options},
  journal = {Quantitative Finance},
  volume  = {24},
  number  = {7},
  pages   = {851--869},
  year    = {2024},
  doi     = {10.1080/14697688.2024.2364804},
  url     = {https://www.tandfonline.com/doi/abs/10.1080/14697688.2024.2364804}
}

@techreport{LucicSepp2023SSRN,
  author = {Lucic, Vladimir and Sepp, Artur},
  title  = {Valuation and Hedging of Cryptocurrency Inverse Options},
  year   = {2023},
  doi    = {10.2139/ssrn.4606748},
  url    = {https://ssrn.com/abstract=4606748}
}
```
