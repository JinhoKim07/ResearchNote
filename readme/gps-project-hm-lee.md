# GPS Project, HM Lee

## 240729, HiC Merging Script

* To Do List, Test for 10 or more samples (cat issue, 240525, Hi-C Error in document).
* Step 1. Merge `merged_dedup.bam` from each single run

```bash
cThreads="$(getconf _NPROCESSORS_ONLN)"
cThreadString="-@ $cThreads"
samtools merge -c -t cb "$cThreadString" -o "${outputDir}"/mega_merged_dedup.bam ${bams_to_merge}
```

* Step 2. Split by quality score 1 and 30
  * Error: the chromosome combination 7\_7 appears in multiple blocks \[[link](https://groups.google.com/g/3d-genomics/c/2w1OGHo5XdM)]
  * in sort `-m` options have to remove
    * This option merges already sorted files.

```bash
# mapq = 1 and mapq = 30
samtools view "$cThreadString" -F 1024 -O sam "${outputDir}"/mega_merged_dedup.bam | awk -v mapq=1 -f "${juiceDir}"/scripts/common/sam_to_pre.awk > "${outputDir}"/merged1.txt
# for the first read end chromosome to be less than the second read end chromosome
awk '{if ($2 > $6){ print $5, $6, $7, $8, $1, $2, $3, $4 }else {print}}' "${outputDir}"/merged1.txt > "${outputDir}"/merged1.tmp.txt
# for the reads to be sorted by chromosome block.
sort --parallel=${cThreads} -S8G -T ${tmpdir} -k2,2d -k6,6d ${outputDir}/merged1.tmp.txt > ${outputDir}/merged1.sort.txt
```

* Step 3. Create the statistic files

```bash
site_file="../../juicer/restriction_sites/GRCm38p6_MboI.txt"
outputDir="./"
genomeID_file="../../juicer/references/GRCm38p6_Chromsize.txt"
# or genomeID_files="none" also available option
../../juicer/scripts/common/juicer_tools statistics "$site_file" "$outputDir"/inter.txt "$outputDir"/merged1.sort.txt "$genomeID_file"
```

* Step 4. make HIC

```bash
resstr="-r 2500000,1000000,500000,250000,100000,50000,25000,10000,5000,2000,1000,500,200,100"
site_file="../../juicer/restriction_sites/GRCm38p6_MboI.txt"
outputDir="./"
genomeID_file="../../juicer/references/GRCm38p6_Chromsize.txt"
fragstr="-f $site_file"
../../juicer/scripts/common/juicer_tools pre -n -s $outputDir/inter.txt -g $outputDir/inter_hists.m -q 1 $resstr $fragstr $outputDir/merged1.sort.txt $outputDir/inter.hic $genomeID_file
```

* Step 4-1?. HiC Normalization

```bash
outputDir="./"
../../juicer/scripts/common/juicer_tools addNorm ${outputDir}/inter.hic 
```



## 240724, Lab Meeting

* present, HiC-GNN paper&#x20;
  * [HiC-GNN: A generalizable model for 3D chromosome reconstruction using graph convolutional neural networks](https://www.sciencedirect.com/science/article/pii/S2001037022006122)
  * Computational and Structural Biotechnology Journal, 21, 812-836 (2023)

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

## ~~Issue: Pointer Null Exception~~

* ~~Multicore process in juice\_tools pre -> single run~~

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

## ~~240525, Hi-C Error (Solved)~~

* ~~Error occured at `dupmerge` in `dedup` process of JUICER.~~

```bash
/var/spool/slurm/d/job214779/slurm_script: line 12: /usr/bin/cat: Argument list too long
```

* ~~Error log in `dup-merge.err`~~
  * ~~hitting `MAX_ARG` limit of bash~~
* ~~(Solution?) FASTQ files are split and analyzed up to the deduplication step, then merged using the `mega.sh` script.~~
  * ~~Issues in JUICER Github:~~ [~~https://github.com/aidenlab/juicer/issues/110~~](https://github.com/aidenlab/juicer/issues/110)
