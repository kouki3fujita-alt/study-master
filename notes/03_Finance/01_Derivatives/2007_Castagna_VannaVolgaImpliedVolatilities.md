# The Vanna-Volga Method for Implied Volatilities: Tractability and Robustness — Castagna & Mercurio (2007)

## 書誌情報

- **論文**: *The Vanna-Volga Method for Implied Volatilities: Tractability and Robustness*
- **著者**: Antonio Castagna, Fabio Mercurio
- **掲載誌**: *Risk*, 20, pp. 106-111
- **年**: 2007
- **原資料**: [Moonlight共有ページ](https://www.themoonlight.io/paper/910007ab-30ca-4a5b-85b3-a1dcd8bd1dc2)
- **リポジトリ内PDF**: [2007_Castagna_VannaVolgaImpliedVolatilities.pdf](../../../papers/03_Finance/01_Derivatives/2007_Castagna_VannaVolgaImpliedVolatilities.pdf)
- **キーワード**: FX options, implied-volatility smile, vanna, volga, risk reversal, butterfly

## 一言でいうと

FX市場で通常観測できる25-delta put、ATM、25-delta callの3つのvol quoteだけから、Black-Scholes価格にvanna・volgaリスクを合わせたヘッジ費用を足してsmileを作る実務手法を、複製の形で明示し、strikeの取り方に対する整合性と近似IVを示した論文である。

## 1. 問題意識

FX vanillaの板は全strikeのIVを直接提示せず、ATM、25-delta risk reversal (RR)、25-delta vega-weighted butterfly (VWB)で出ることが多い。任意strikeやbarrierの評価にはsmileが必要だが、単なる多項式補間はヘッジ解釈を失いやすい。VVは、3つの流動的なanchor optionに対して対象optionのvega、vanna、volgaを合わせる、という市場慣行を価格関数として整理する。

## 2. 市場quoteから3点IVへ

同一満期の25-delta put/call IVを \(\sigma_{25P},\sigma_{25C}\)、ATMを \(\sigma_{ATM}\) とすると、慣行上は

```math
RR_{25}=\sigma_{25C}-\sigma_{25P},\qquad
VWB_{25}=\frac{\sigma_{25C}+\sigma_{25P}}{2}-\sigma_{ATM}
```

から3点を復元する。VVは、これら3点を通る「真の分布」を推定したと主張するのではなく、限られたliquid quoteに整合する局所的なrevaluation/hedging ruleである。

## 3. 中核式

ATM flat-vol Black-Scholes価格を \(C^{BS}(K;\sigma_{ATM})\)、市場3点を \((K_i,C_i^{MKT})\) とする。対象strike \(K\) に対し、\(x_i(K)\) を

```math
\sum_{i=1}^{3}x_i\,\mathrm{Vega}(K_i)=\mathrm{Vega}(K),
\quad
\sum_{i=1}^{3}x_i\,\mathrm{Vanna}(K_i)=\mathrm{Vanna}(K),
\quad
\sum_{i=1}^{3}x_i\,\mathrm{Volga}(K_i)=\mathrm{Volga}(K)
```

で決める。VV価格は

```math
C^{VV}(K)=C^{BS}(K;\sigma_{ATM})+
\sum_{i=1}^{3}x_i(K)\left[C_i^{MKT}-C^{BS}(K_i;\sigma_{ATM})\right].
```

つまり、flat BS価格に、market smileを用いた3本のhedge portfolioのコスト差を加える。名称のvanna/volgaは、\(\partial\mathrm{Vega}/\partial S\) と \(\partial\mathrm{Vega}/\partial\sigma\) を合わせることに由来する。

## 4. 論文の理論的結果

- 3本のanchorが異なれば、上の3 Greekを合わせる重みは一意に定まる。
- anchor strike/volの組を整合的に取り替えても、得られる価格関数は同じになるというconsistencyを示す。
- vanillaと同じvanna-volga exposureを持つportfolioのmarket-vs-BS cost差でexoticを調整する形に一般化できる。
- VV価格から1次・2次のimplied-volatility近似を導き、実装を高速化する。

## 5. 実務上の読み方

- RRが大きく負ならput wingのIVが高く、VV smileはdownside側に傾く。
- VWBの変化はcentral 25-delta pairとATMの相対的な曲率を表す。
- VVのrisk adjustmentは「市場が見ているvanna/volga hedge cost」を転写するもので、デルタ・vegaだけのflat-vol hedgeよりFX exoticのsmile riskを反映しやすい。

## 6. 限界

- 3 quoteだけではrisk-neutral density全体、まして動学・path dependenceを識別できない。
- static-arbitrageの一部の整合性は論じるが、全満期横断のcalendar arbitrage free surfaceを自動的に保証しない。
- barrier/DNTではspot-vol correlation、smile dynamics、liquidity/credit valuation adjustmentが重要で、VV単独のmodel riskが大きい。
- delta convention（spot/forward、premium-adjusted）、cut、discount curveを混ぜると、同じRR/VWBでもsurfaceが変わる。

## 7. 次に検討すべき問い

- VV、SABR、SVIを、価格誤差だけでなく実際のvanna/volga hedging P&Lで比較できるか。
- FX 25-delta quoteの流動性が低いストレス局面で、anchor選択はどれだけ不安定化するか。
- equity index skewへ使う場合、OTM put/call quote conventionの違いをどう調整するか。

## BibTeX

```bibtex
@article{CastagnaMercurio2007,
  author  = {Castagna, Antonio and Mercurio, Fabio},
  title   = {The Vanna-Volga Method for Implied Volatilities: Tractability and Robustness},
  journal = {Risk},
  volume  = {20},
  pages   = {106--111},
  year    = {2007}
}
```
