# GPS Project, HM Lee

## HiC Run Progress

Command for Split Run, 8 nodes \[11-17,20] in GDLWulf

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

* Set1, 10 samples, w/ early stop, SRR10359958 \~ SRR10359967
  * Start at 240528-1100
* Set2, 10samples, w/ early stop, SRR10359968 \~ SRR10359977
  * Start at 240530-2054

## 240525, Hi-C Error

* Error occured at `dupmerge` in `dedup` process of JUICER.

```bash
/var/spool/slurm/d/job214779/slurm_script: line 12: /usr/bin/cat: Argument list too long
```

* Error log in `dup-merge.err`
  * hitting `MAX_ARG` limit of bash
* (Solution?) FASTQ files are split and analyzed up to the deduplication step, then merged using the `mega.sh` script.
  * Issues in JUICER Github: [https://github.com/aidenlab/juicer/issues/110](https://github.com/aidenlab/juicer/issues/110)
