# Automated Market Making and Loss-Versus-Rebalancing — Milionis, Moallemi, Roughgarden, and Zhang (2024)

## 書誌情報

- **論文**: Jason Milionis, Ciamac C. Moallemi, Tim Roughgarden, Anthony Lee Zhang, “Automated Market Making and Loss-Versus-Rebalancing”
- **版**: arXiv:2208.06046v5, May 27, 2024
- **初版**: July 31, 2022
- **arXiv**: [2208.06046](https://arxiv.org/abs/2208.06046)
- **PDF**: [arXiv PDF](https://arxiv.org/pdf/2208.06046)
- **分類**: q-fin.MF
- **キーワード**: automated market makers, AMM, CFMM, Uniswap, liquidity provision, loss-versus-rebalancing, LVR, decentralized exchange, market microstructure

## 1. 一言でいうと

AMMの流動性提供者 (LP) が負う主要な逆選択コストを、単なるimpermanent lossではなく、同じ在庫変化を中央集権取引所の市場価格でリバランスした戦略との差分として測る論文である。この差分をloss-versus-rebalancing (LVR) と呼び、AMM版のBlack-Scholes公式に相当する閉形式を導く。LVRは価格ボラティリティとAMM曲線の限界流動性で決まり、LP収益、手数料設計、AMM設計を評価する基礎指標になる。

## 2. 問題意識

Uniswap型のconstant function market maker (CFMM) は、ブロックチェーン上で低コストに取引を成立させる仕組みである。一方で、LPは価格が動いたときに古い価格で裁定取引者に取られる。実務ではこの損失をimpermanent lossで測ることが多いが、impermanent lossは初期ポートフォリオをそのまま持つ戦略との比較であり、LPポジションに内在する市場リスクと逆選択コストを混ぜてしまう。

本稿の狙いは、LPの損益を市場リスクから切り離し、AMM固有の「 stale quote を裁定されるコスト」を測ることである。オプション価格理論でデルタヘッジが方向リスクを除くように、AMM LPでもrebalancing strategyを使って方向リスクを除き、残る損失をLVRとして定義する。

## 3. モデルの基本構造

対象は、リスク資産とニュメレール資産を取引するAMMである。リスク資産価格は、Black-Scholes型に幾何ブラウン運動で動くと仮定する。

- **AMM/DEX**: CFMMなどの自動マーケットメーカー
- **CEX**: 無限に深く、価格インパクトなしで市場価格取引できる中央集権取引所
- **Noise traders**: AMMで取引し、LPに手数料を支払う
- **Arbitrageurs**: CEXとAMMの価格差を裁定し、AMM価格をCEX価格へ戻す

AMMは価格変化に対して能動的にquoteを更新しない。価格がCEX側で動くと、AMMの価格は古くなり、裁定取引者がAMMと取引して価格を更新する。このときLPは、市場価格より不利な価格で在庫を調整させられる。

## 4. Rebalancing strategy と LVR

rebalancing strategyは、AMM LPと同じリスク資産保有量を常に持つが、AMM価格ではなくCEX市場価格で在庫を調整する自己金融戦略である。直感的には、LPポジションをデルタヘッジするためのベンチマークである。

AMM LPの価値を $V_t$、rebalancing strategyの価値を $R_t$ とすると、手数料を無視したLVRは

```math
\mathrm{LVR}_t = R_t - V_t
```

で定義される。LPは、同じ在庫変化を市場価格で実行できるrebalancing strategyよりも、AMM価格で裁定される分だけ劣後する。したがって、LVRはAMM LPがstale priceをpick offされることで負う累積損失である。

## 5. 中核結果

### 5.1 LVRは非負で予測可能なプロセス

Theorem 1では、局所的に滑らかなAMMについて、LVRが非負・非減少・予測可能なプロセスとして表される。これは、手数料を無視すれば、AMM LPはrebalancing strategyに対して体系的に劣後することを意味する。

### 5.2 瞬時LVRはボラティリティと限界流動性で決まる

LVRの瞬時的な大きさは、主に二つの要素で決まる。

- リスク資産価格の瞬時分散
- AMM需要曲線の傾き、すなわち限界流動性

価格が大きく動くほど、AMMのquoteは古くなりやすく、裁定による損失が増える。また、AMMが価格変化に対して大きく在庫を動かす曲線であるほど、同じ価格変化でもLVRは大きくなる。

### 5.3 LVRは裁定取引者の利益に対応する

AMMがCEX価格からずれるたびに、裁定取引者はAMMの古い価格を取る。モデル上、この裁定利益の累積はLVRに等しい。したがって、LVRはLP側の損失であると同時に、AMM-CEX間裁定者が得るsniping profitでもある。

### 5.4 Hedged LPでLP収益をきれいに測れる

LPポジションをそのまま見ると、収益変動の多くは基礎資産価格への方向エクスポージャーで決まる。rebalancing strategyをショートしてhedged LPにすると、方向リスクを大きく除去でき、手数料やインセンティブがLVRを上回るかどうかを直接評価できる。

著者らはUniswap v2 WETH-USDCペアで実証し、モデルで予測されるLVRがdelta-hedged LP収益とかなり近いことを示す。

### 5.5 Impermanent lossよりLVRの方がベンチマークとして明確

impermanent lossは初期保有ポートフォリオとの比較であり、市場リスクの違いによるノイズを含む。リスク中立期待ではLVRとimpermanent lossの期待値は一致し得るが、LVRは市場リスクを取り除く唯一の自然なベンチマークである。LP収益の経済的ドライバーを測るには、impermanent lossよりLVRを見る方が明確である。

## 6. AMM設計への含意

競争的なLP市場では、LPの超過収益はゼロに近づき、手数料収入はLVRを補償する水準になるはずである。このため、LVRは手数料設計の基準になる。

主な設計含意は以下である。

1. **手数料はボラティリティに応じて変えるべき**
   LVRは価格分散に比例するため、固定手数料では高ボラ局面でLP補償が不足し、低ボラ局面で過剰になる可能性がある。

2. **過去のLVRと手数料収入を比較してfeeを調整できる**
   プロトコルは過去ウィンドウでLVRが手数料を上回ればfeeを上げ、手数料がLVRを上回ればfeeを下げるような設計が考えられる。

3. **価格オラクルでstale quoteを減らせる**
   高頻度で信頼できる価格オラクルを使えれば、AMMは市場価格に近いquoteを出せるため、LVRを削減または理論的には除去できる。

4. **裁定権の販売やMEV再分配も設計余地**
   AMMが裁定機会をそのまま外部裁定者に渡すのではなく、期待LVRをプロトコルやLPへ還元する設計が考えられる。

## 7. この論文の貢献

1. AMM LPの逆選択コストをLVRとして定義し、impermanent lossと区別した。
2. Black-Scholesのデルタヘッジに対応するrebalancing strategyを導入した。
3. 一般的なAMMに適用できるLVRの閉形式を導出した。
4. LVRが価格ボラティリティと限界流動性に依存することを示した。
5. Uniswap v2 WETH-USDCで、モデル予測LVRとhedged LP収益の対応を実証した。
6. AMM手数料設計、オラクル利用、MEV/裁定利益の再配分に直接使える設計指針を提示した。

## 8. 限界と批判点

1. **摩擦の単純化**: 基本モデルではgas fee、ブロック時間、CEX/DEX手数料、裁定遅延などを単純化している。
2. **CEXが無限に深い仮定**: 実際にはCEXにも流動性制約と価格インパクトがある。
3. **裁定者が常に価格を一致させる仮定**: ブロックチェーンの混雑、MEVオークション、gas raceにより裁定は遅れることがある。
4. **LPの戦略性**: LPが流動性を出し入れする内生的な行動は、基本モデルでは十分に扱わない。
5. **Uniswap v3以降の集中流動性**: LVR概念は一般化できるが、実装上は価格レンジ、再配置、ポジション管理が重要になる。

## 9. 実務への含意

- AMM LPの損益評価では、単純なAPRやimpermanent lossだけでなく、fees minus LVRを見るべきである。
- ボラティリティが高いペアほど、同じ流動性曲線でもLVRが大きくなるため、必要手数料は高くなる。
- LPバックテストでは、AMM在庫をCEX価格でリバランスするhedged LPを作ると、市場方向リスクを除いた収益評価ができる。
- AMM設計では、固定feeではなく、ボラティリティ・LVR・在庫曲率に応じた動的feeが自然である。
- DeFiのMEV研究では、AMM-CEX裁定利益をLPからのLVR移転として測る視点が有用である。

## 10. 次に検討すべき問い

- Uniswap v3の集中流動性レンジ別にLVRをどう分解するか。
- LVRベースの動的feeは、取引量、LP供給、裁定効率をどう変えるか。
- CEX価格を基準にしたrebalancing strategyは、オラクル遅延やCEX流動性が薄いペアでも有効か。
- MEV auctionやprivate order flowを入れると、LVRは裁定者、validator、LPの間でどう分配されるか。
- LVRを暗号資産以外の電子マーケットメイク、ETF裁定、オプションマーケットメイクの逆選択コストと比較できるか。

## 11. 総合評価

この論文は、AMM LPの収益評価における基礎文献である。impermanent lossという実務用語では混ざりがちな市場リスクと逆選択コストを、rebalancing strategyとの比較によって切り分け、LVRという測定可能な概念に落とし込んだ点が重要である。市場マイクロストラクチャー、DeFi、ボラティリティ取引、MEVを接続する文献としてライブラリに置く価値が高い。
