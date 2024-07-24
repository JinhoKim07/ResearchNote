# FROM Project, Prof. SH Lee (Dong-A Univ.)

## 240718, Discussion w/ PI

* Data quality Check and draw final Figure
  * PMID: 36452869 Fennell, Lochlan J., et al. "Comparative analysis of Illumina Mouse Methylation BeadChip and reduced-representation bisulfite sequencing for routine DNA methylation analysis." Cell Reports Methods 2.11 (2022).
  * PMID: 30510283 Kim, Hee-Jin, et al. "Whole genome MBD-seq and RRBS analyses reveal that hypermethylation of gastrointestinal hormone receptors is associated with gastric carcinogenesis." Experimental & Molecular Medicine 50.12 (2018): 1-14.
  * PMID: 33461589 El Khoury, Louis Y., et al. "Identification of DNA methylation signatures associated with poor outcome in lower-risk Stage, Size, Grade and Necrosis (SSIGN) score clear cell renal cell cancer." Clinical epigenetics 13 (2021): 1-16.
  * PMID: 30989176 Xu, Zongli, Dale P. Sandler, and Jack A. Taylor. "Blood DNA methylation and breast cancer: a prospective case-cohort analysis in the sister study." JNCI: Journal of the National Cancer Institute 112.1 (2020): 87-94.

## 240703, Short Discussion w/ PI

* find DMR for marker of iAs, sum4As
  * Including Intergenic regions
* Message, 240708&#x20;
  * Apoptotic Gene List -> Table
  * Immune related Term -> GO

## 240610, Short Discussion w/ PI

* For iAsgp, statistical significant difference observed in MCV.
  * RBC development? -> Phenotype?
* or Epigentic marker?

## 240523, LabMeeting&#x20;

* DMR analysis -> Done&#x20;
* DML analysis -> Done
* Locus analysis
  * ML Approach (Prediction) failed
    * Feature Selection -> XGBoost, RF : failed, overfitting issue
    * Patterns are does not exist.
  * (NEXT) Statistical Approach
    * $$R^2$$ Approach, w/ selected features
    * including CpG in Intergenic
  * (NEXT) Summary all results
