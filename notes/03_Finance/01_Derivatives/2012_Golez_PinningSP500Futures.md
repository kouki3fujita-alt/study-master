# Pinning in the S&P 500 Futures — Golez and Jackwerth (2012)

## 書誌情報

- **著者**: Benjamin Golez, Jens Carsten Jackwerth
- **提供版**: December 6, 2011, SSRN Working Paper No. 1664261
- **公刊版**: *Journal of Financial Economics*, 106(3), 566–585, 2012
- **DOI**: [10.1016/j.jfineco.2012.06.010](https://doi.org/10.1016/j.jfineco.2012.06.010)
- **SSRN**: [1664261](https://ssrn.com/abstract=1664261)
- **リポジトリ内PDF（2011年稿）**: [2011_Golez_PinningSP500Futures_SSRN1664261.pdf](../../../papers/03_Finance/01_Derivatives/2011_Golez_PinningSP500Futures_SSRN1664261.pdf)
- **JEL**: G12, G13
- **キーワード**: pinning、anti-pinning、S&P 500 futures、option expiration、delta hedge、charm

> **版の注意**: 保存PDFは75ページの2011年SSRN稿で、公刊版は20ページである。推定表・ページ番号は版を混在させない。

## 1. 研究質問と結論

オプション満期日にS&P 500先物価格は権利行使価格へ引き寄せられるのか。それとも離されるのか。個別株で知られるpinningが、非常に流動性の高い指数先物でもヘッジ売買によって生じるかを検証する。

主要結果は二つである。

- S&P 500先物オプションのserial expiration日には、第一限月先物がATM strikeへ近づく **pinning** が起きる。
- SPX指数オプション満期の直前には、cost-of-carry調整後の対応strikeから先物が離れる **anti-cross-pinning** が起きる。

著者らは、時間経過に伴うデルタ変化への再ヘッジと、個人投資家によるITMオプションの売り戻し・早期行使が組み合わさって符号の異なる効果を生むと説明する。推定される先物notionalの移動は満期日当たり少なくとも1.15億ドルである。

## 2. Pinningと単なるclusteringの違い

- **Clustering**: 価格が常に丸い数値へ集まりやすい。
- **Pinning**: オプション満期日に限り、原資産価格が近いstrikeへ通常以上に集まる。

pinningを示すには、通常日や非満期日にも存在するprice gridへの選好を統制し、満期日固有のstrike proximityを検出する必要がある。

## 3. ヘッジ再調整の仕組み

オプション・ポートフォリオのデルタを \(\Delta(S,t)\) とすると、短時間の変化は

```math
d\Delta
\approx
\Gamma\,dS + \Theta_\Delta\,dt,
```

で近似できる。ここで \(\Theta_\Delta=\partial\Delta/\partial t\) は現在の実務用語ではcharmに相当する時間デルタ変化である。

ヘッジャーが原資産先物を \(-\Delta\) 保有するなら、価格変化・時間経過・ポジション解消に応じて先物を売買する。この注文がstrikeの上下で異なる方向へ働くと、価格をstrikeへ引くpinning、またはstrikeから押し出すanti-pinningを生む。

## 4. 市場構造を利用した識別

S&P 500には相互に関係する三市場がある。

1. S&P 500指数
2. S&P 500先物
3. 先物オプション（SP options）と指数オプション（SPX）

先物オプションは月次、先物は四半期に満期を迎える。serial monthではオプションだけが満期になり、第一限月先物はその後も取引されるため、先物価格のpinningを観測しやすい。四半期満期では先物自身が指数basketへ収束するため、同じ機構は弱いはずである。

またSPXオプションのヘッジは、取引しにくい500銘柄basketより流動性の高い先物で行われやすい。この市場間構造を使って、どのオプション満期がどの先物価格へ影響するかを比較する。

## 5. データ

- **主要期間**: 1992年11月–2009年11月
- **市場**: S&P 500先物、先物オプション、SPX指数オプション
- **比較**: serial expiration、quarterly expiration、通常日、近接strike
- **補助情報**: open interest、取引量、個人投資家の売り戻し・早期行使を示すデータ

典型的満期日の先物open interestは約900億ドル、約15%が当日取引される巨大市場であり、単純な価格操作だけで結果を説明しにくい点が重要である。

## 6. 主要結果

### Serial futures-option expirationでpinning

第一限月S&P 500先物は、serial SP option満期日に最寄りstrike近辺へ通常以上に集まる。効果は1998年以降に強く、オプション市場の成長と整合する。

最低推定でも満期日当たり約1.15億ドル、後半標本では約2.4億ドルのnotional price shiftに相当する。

### 単純なショート・オプションのcharmだけでは符号が合わない

マーケットメーカーが先物オプションをネット・ショートなら、時間減衰によるヘッジ再調整だけではanti-pinningが予想される。それでも実際にはpinningが観測される。

著者らは、個人投資家がITMオプションを満期前に売り戻す、または早期行使するため、マーケットメーカー在庫とヘッジ需要が変化し、時間減衰効果を上回るpinning方向のフローが生じると説明する。

### SPX expiration前のanti-cross-pinning

SPXオプション満期に対応するcost-of-carry adjusted strikeの近くでは、S&P 500先物がstrikeから離れる傾向がある。指数オプションのヘッジが先物へ流れる一方、契約仕様・在庫符号・決済構造が先物オプションの場合と異なるため、反対方向の効果が現れる。

### 操作説への証拠は弱い

指数先物は極めて流動的で、関連市場・四半期満期・指数basketには同じ集積が見られない。結果は広範な価格操作より、契約ごとのヘッジ・行使メカニズムと整合する。

## 7. 限界と批判点

1. **在庫符号は完全観測ではない**: マーケットメーカーの全ポジション、OTC、クロスヘッジは見えない。
2. **機構の複合性**: charm、gamma、売り戻し、早期行使が同時に動き、各寄与の分離はモデル依存である。
3. **notional換算**: 推定価格移動を市場価値へ換算した下限であり、実際の取引損益や因果的資金移動とは同じでない。
4. **制度の古さ**: 1987–2009年にはpit trading、契約仕様、取引時間、E-mini普及過程が含まれる。
5. **現在への一般化**: 0DTE、電子マーケットメイク、より細かいstrike grid、週次満期により現在のpinning構造は異なり得る。
6. **満期日選択**: イベント・ロール・四半期需給など満期固有の要因を完全には除けない。

## 8. 実務的含意

- strike近接だけから「ディーラーが価格をpinしている」と断定しない。
- option type、settlement、exercise、serial/quarterly、dealer inventory signを分ける。
- gammaだけでなくcharm、ポジション解消、早期行使、ロールを満期モデルへ入れる。
- pinningは方向予測ではなく、strike付近の条件付き価格密度・引けフローとして評価する。
- 満期直前は小さな価格変化でデルタと行使確率が大きく変わるため、離散ヘッジと流動性を重視する。

## 9. 次に検討したい問い

1. 現在のES・SPX・SPXW 0DTEで同じpinning／anti-pinningは存在するか。
2. 取引所capacityデータでOMM在庫と実際の先物ヘッジを直接復元できるか。
3. charm、gamma、speed、vannaのどれが満期日フローを最も説明するか。
4. AM/PM settlementやcash/physical settlementの差は効果の符号をどう変えるか。
5. strike grid変更や週次満期導入を自然実験として利用できるか。
