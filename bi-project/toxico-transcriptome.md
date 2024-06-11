# Toxico Transcriptome

## 240607, Sample Selection in gene level

* Code : "Step1\_SampleProfiling.ipynb"
* Low correlation (< 0.95) was observed between replications of TPM in multiple samples.
  * ex. BPS-HepG2 \~ 0.2459, BPA-H1299 \~ 0.9031
  * In most case, the correlation of TPM b/w technical reps. was observed to be above 0.95.
* Thus, in this study, samples with correlation b/w technical reps. below 0.95 and also lower than the correlation with other sample groups were excluded.
  * H1299 BPA : 0.9032, $$\max(\rho_{i\neq j} )$$=0,9968 (H1299 Hg S2, TPM Hg S1)
  * H1299 Tol : 0.9092,  $$\max(\rho_{i\neq j} )$$=0.9985 (H1299 Fu S1, H1299 NAP S2)
  * HepG2 BPA : 0.9463, $$\max(\rho_{i\neq j} )$$=0.9932 (HepG2 Hg S2, HepG2 MP S1)
  * HepG2 BPS : 0.2459,  $$\max(\rho_{i\neq j} )$$=0.9966 (HepG2 HCB S1, HepG2 Pb S2)
  * HepG2 Cdcl2: 0.9339,  $$\max(\rho_{i\neq j} )$$=0.9933 (HepG2 Triclosan S1, HepG2 MEOHP S2)
  * HepG2 Hg: 0.8103,  $$\max(\rho_{i\neq j} )$$= 0.9852 (HepG2 EP S1, HepG2 BPA S2)
  * HepG2 MEOHP: 0.8852,  $$\max(\rho_{i\neq j} )$$=0.9933 (HepG2 Cdcl2 S2, HepG2 AC S1)
  * HepG2 MP: 0.9040,  $$\max(\rho_{i\neq j} )$$= 0.9932 (HepG2 BPA S2, HepG2 BPA S1)

## 240529, Short Discussion w/ PI

* 누가 환경변화의 subtle change를 sensing하는가?
* Chemical sensing mecahnism -> splicing
  * or Speckle?

## 240525, Short Discussion w/ GS Shin

### Paper Structure

#### Concepts

> Gene Level -> No difference, Transcript level -> little difference, balance disrupted

> RI -> **It is the most sensitive marker and a critical factor that manifests even at low exposure levels.**

**The main figure shows logFC and PValue, with expressions provided in the supplementary materials.**

* Fig 1. All group analysis, gene-level&#x20;
  * There is no changes in DEG
* Fig 2-4. Expand to Transcript-level
  * Fig 2. Concept of Alternative Splicing, Expression varied
  * Fig 2 or 3. GO all
  * Fig 3 or 4. Up and Down transcript analysis, select major transcript in CTL
* Fig 5. RI Analysis, Up-reg in treatment group
* Fig 6. RI Downstream Analysis
* Fig 7. Conclusion?

### Chemical Grouping

* Phenol Group
  * BPA, BPF, BPS, NP, Triclosan
* VOC (Volatile Organic Compounds),
  * Benzene, Fu, HCB, NAP, Xylene, Toluene, TE
  * HCB : Weak corerlation
  * **Due to its high volatility, the effectiveness may be reduced.**
* Pthalate
  * DEHP, MCXX, MEXXX, MbZP, MnBP
  * DEHP: Pthalate Di- group
  * Others, Mono group -> detoxified in cell
* Similar Chemical Structure, Differing Only in Physical Properties
  * Paraben, EP, PP, MP
* Pesticide
  * Mirex, NAP, HCB
* Multi-Benezne Ring&#x20;
  * BAP, NAP
* Heavy Metal Group
  * AC, CdCl2, CH, Hg, Pb
* Others
  * Cotinine, Mirex
  * Cotinine, detoxified Nicotine
  * Mirex, Structurally independent



## 240523, Short Discussion

* Change the concepts Transcript -> RI to Gene -> Transcript (Alternative Splicing) -> RI
* Chemical Grouping
