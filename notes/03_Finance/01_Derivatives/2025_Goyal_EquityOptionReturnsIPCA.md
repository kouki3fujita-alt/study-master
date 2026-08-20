# Can Equity Option Returns Be Explained by a Factor Model? IPCA Says Yes — Goyal and Saretto (2025)

## 書誌情報

- **論文**: Amit Goyal, Alessio Saretto, “Can Equity Option Returns Be Explained by a Factor Model? IPCA Says Yes”
- **掲載誌**: *The Review of Financial Studies*, Vol. 38, No. 6, pp. 1783-1821, 2025
- **DOI**: [10.1093/rfs/hhae087](https://doi.org/10.1093/rfs/hhae087)
- **SSRN working paper**: [Abstract 4194384](https://ssrn.com/abstract=4194384)、2024年6月29日版
- **保存状況**: 指定された出版社の署名付きPDF URLとSSRN配布PDFは取得時点で利用できなかったため、リポジトリ内PDFは未保存。引用・版管理は公刊版を優先する。
- **キーワード**: individual equity options、delta-hedged returns、IPCA、latent factor、multiple testing、transaction costs

## 1. 研究質問と結論

個別株のデルタヘッジ済みオプションで報告される多数のlong-short異常収益は、真のalphaなのか、それとも条件付きfactor exposureへの補償なのかを問う。

著者らはInstrumented Principal Components Analysis（IPCA）をoption returnへ適用し、特性で時変betaを作る3因子モデルが、既報の46のlong-short戦略の大部分を説明すると示す。取引コスト前には月次80 bp超の平均リターンを持つ戦略群の平均IPCA alphaがほぼゼロとなり、net returnを使うとalphaはむしろ負になる。結論は「全ての既報予測可能性が無意味」ではなく、raw returnをそのままmispricingと呼ぶ前に、条件付きrisk adjustmentと取引コストを通すべき、というものだ。

## 2. IPCAの枠組み

オプション（またはstock-monthに集約したdelta-hedged option position）(i\) の次期リターンを

```math
R_{i,t+1}
= Z_{i,t}'\Gamma_\alpha
+ (Z_{i,t}'\Gamma_\beta)F_{t+1}
+ \varepsilon_{i,t+1}
```

と置く。\(Z_{i,t}\) はRV-IV、IV term、IV volatility、moneyness、liquidity、企業特性などのobservable characteristics、\(F_{t+1}\) はlatent factorsである。\(\Gamma_\beta\) が特性を時変factor loadingへ写すため、同じ因子でもoptionごと・時点ごとにbetaが変わる。

主分析では \(\Gamma_\alpha=0\) を課し、平均リターンがrisk factorで説明できるかを問う。portfolio (p\) のIPCA alphaは

```math
\hat\alpha_p
=\frac{1}{T}\sum_t
\left(R_{p,t+1}-Z_{p,t}'\hat\Gamma_\beta\hat F_{t+1}\right)
```

であり、raw returnが高くても、条件付き期待リターンが高ければalphaは小さくなる。

## 3. データと実証設計

- **オプション**: OptionMetrics、1996年1月-2022年12月。無裁定境界・非標準契約・流動性等のfilterを適用。
- **企業情報**: CRSP/Compustatをsix-month reporting lagで突合し、look-ahead biasを避ける。
- **収益**: 個別株callをdelta hedgeし、expiration-to-expirationで計算。46のcharacteristicsによるdecile long-short portfolioを作る。
- **推定**: 1-5因子を比較し、bootstrap/Wald testと平均factor returnを組み合わせて3因子を選ぶ。後半の2009-2022年でexpanding-windowのout-of-sample検証も行う。
- **費用**: quoted spreadを使って、long・shortの実効執行価格をmidからずらしたnet returnを再計算する。

## 4. 主要結果

1. 46の特性戦略のうち39はraw returnがmultiple-hypothesis-test調整後にも有意であるが、3因子IPCAは大半のalphaをゼロ付近へ縮める。
2. IPCAはmanaged portfolio returnの変動の約80%-90%をin-sampleで説明する。out-of-sampleでも、過度に単純なstatic beta/PCAより良いpricing performanceを示す。
3. RV-IV、Assets、MarketCapが3因子の主なconditional loading sourceとして現れる。例えば高RV-IV optionが高い期待収益を要求するのは、第一因子へのbetaが高いためと解釈される。
4. transaction costs前の戦略群では平均月次raw returnが80 bp超でも、平均IPCA alphaはほぼゼロである。net returnでは有意な戦略が16残る一方、IPCA alphaは全戦略で負となる。

## 5. 解釈上の注意

IPCAはlatent factorを統計的に抽出する。したがって「IPCAがalphaを消す」ことは、因子が必ず消費CAPMのprimitive riskであることを意味しない。sentiment、資金制約、モデルが拾った共通のreturn variationも同じ形で説明力を持ち得る。

また、因子はfull-sample推定を含むため、著者らはexpanding-window検証を行うが、real-timeで同じ精度のfactor loadingを推定できるかは別問題である。異常収益の実務的な収益性は、risk adjustmentとは独立に、bid-ask、borrow、margin、turnover、capacityで決まる。

## 6. 限界と批判点

1. latent factorの経済的な正体は一意に識別されず、「risk」と呼ぶ解釈には追加検証が要る。
2. 特性選択・filter・満期整列方法に依存する。別のoption universeや0DTEには直接適用できない。
3. 執行費用はquoted spreadベースの近似で、market impact、queue priority、注文分割、short-sale constraintsを完全には含まない。
4. alphaを説明できても、投資家がそのfactor exposureへ補償を払う均衡モデルを構築したわけではない。

## 7. 次に検討したい問い

1. 0DTEや週次optionを含めたとき、IPCAの因子数・重要特性は変わるか。
2. dealer inventory、customer type、order flowを特性に加えると、RV-IV factorの解釈は明確になるか。
3. 実際の注文簿で再現したimplementation shortfall後にも、IPCA alphaがゼロ又は負であるか。
