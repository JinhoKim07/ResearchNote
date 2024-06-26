# GPS Project, HM Lee

## 240626, GPS Meeting

* **GC0010:** Code upload to Github (make fit for GPS Project)
* Probability distribution -> diag factor&#x20;

## HiC Merge

* The method for merging `juicer` results using `mega.sh` for Hi-C data that has been processed for each technical replicates
  * Refrencing the 'Creating a "mega" map section of the `juicer` github repository [\[Link\]](https://github.com/aidenlab/juicer/wiki/Usage).
  * make soft link of All directory and run mega script with parameter as below,

```bash
bash ./juicer/scripts/mega.sh \
-g ./juicer/references/GRCm38p6_Chromsize.txt \
-y ./juicer/restriction_sites/GRCm38p6_MboI.txt \
-s MboI \
-T 12
```

## Issue: Pointer Null Exception

* ??

## HiC Run Single

* In the previous process, computations were performed by combining multiple technical replicates, which can eliminate natural duplication.&#x20;
* Therefore, it is necessary to perform computations separately for each technical replicates and subsequently merge them.&#x20;
* For the results of all computations, the merging method needs to be considered separately.

```bash
bash ./juicer/scripts/juicer.sh \
-z ./juicer/references/Mus_musculus.GRCm38.dna.primary_assembly.fa \
-p ./juicer/references/GRCm38p6_Chromsize.txt \
-y ./juicer/restriction_sites/GRCm38p6_MboI.txt \
-s MboI \
-g GRCm38p6 \
-t 12
```

## ~~HiC Run Progress~~

~~Command for Split Run, 8 nodes \[11-17,20] in GDLWulf~~

```bash
bash ./juicer/scripts/juicer.sh \
-z ./juicer/references/Mus_musculus.GRCm38.dna.primary_assembly.fa \
-p ./juicer/references/GRCm38p6_Chromsize.txt \
-y ./juicer/restriction_sites/GRCm38p6_MboI.txt \
-s MboI \
-g GRCm38p6 \
-t 12 \
-e
```

* ~~Set1, 10 samples, w/ early stop, SRR10359958 \~ SRR10359967~~
  * ~~Start at 240528-1100~~
* ~~Set2, 10samples, w/ early stop, SRR10359968 \~ SRR10359977~~
  * ~~Start at 240530-2054~~

## 240525, Hi-C Error

* Error occured at `dupmerge` in `dedup` process of JUICER.

```bash
/var/spool/slurm/d/job214779/slurm_script: line 12: /usr/bin/cat: Argument list too long
```

* Error log in `dup-merge.err`
  * hitting `MAX_ARG` limit of bash
* (Solution?) FASTQ files are split and analyzed up to the deduplication step, then merged using the `mega.sh` script.
  * Issues in JUICER Github: [https://github.com/aidenlab/juicer/issues/110](https://github.com/aidenlab/juicer/issues/110)
