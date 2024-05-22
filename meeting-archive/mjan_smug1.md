# Smug1 Project, MJ An

## 240522, CpG/non-CpG Methylation Pattern

* Based on profile-plot, we focused on gene start and end point +-300bp
* BioGPS Mouse Cell Type -> get Gene List
  * Standard value over 1.5 and -1.5
  * Down (removed!) -> Not specific gene in given tissue
* For up gene set, calculate mean methylation level and draw heatmap (TSS, TTS, genebody)
  * FPKM over 5 in up-gene applied
* Next, PolII

<figure><img src="../.gitbook/assets/스크린샷 2024-05-22 191555.png" alt=""><figcaption><p>average methylation level of Up-regulated? or Gene Specific Gene, TSS (Gene Start Point +- 300), TTS(Gene End Point +- 300), Gene body = (start, end) point of gene</p></figcaption></figure>

## 240520, CpG/non-CpG Methylation Pattern

### Meeting

* Failed to detect non-CpG patterns among TSS/TES/Top/Bot
  * mlvl of TES Top is similar to others (cumulative plots)
  * TES +- 100bp and TSS +- 100bp versus All PC genes
  * TES +- 300bp and TSS +- 300bp versus All PC genes
  * Top All and Bot All are same as 4 groups
* (Future work) How to filter zero or sparse regions?
* (Future work) Top and Bot gene selection criteria?

### Plan

* CpG and non-CpG methylation in individual tissue : Cumulative and boxplot

> Q. CpG and non-CpG methylation patterns in genomic region?

* TSS, Exon, Intron, TSS : Cumulative and boxplot

> Q. If non-CpG methylation level in TTS is low, What is the role of non-CpG in TSS?

* RNA polymerase II termination events in lowly non-CpG methylation regions
  * RNA PolII termination index calculation
  * Correlation Plots b/w non-CpG methylation on TTS and RNA PolII

## 240514, CpG/non-CpG Methylation Pattern

* WorkSpace

```
/mnt/InfoTrend/Smug1_Project/240513_Figure1_Screening
```

* DML files copied from other directories
* PC Gene, Top/Bot Gene: mC level boxplot and cumulative plot
* Future Works,
  * mC level for Genomic Regions (TSS, TES)
