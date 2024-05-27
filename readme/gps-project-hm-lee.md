# GPS Project, HM Lee

## 240525, Hi-C Error

* Error occured at `dupmerge` in `dedup` process of JUICER.

```bash
/var/spool/slurm/d/job214779/slurm_script: line 12: /usr/bin/cat: Argument list too long
```

* Error log in `dup-merge.err`
  * hitting `MAX_ARG` limit of bash
* (Solution?) FASTQ files are split and analyzed up to the deduplication step, then merged using the `mega.sh` script.
  * Issues in JUICER Github: [https://github.com/aidenlab/juicer/issues/110](https://github.com/aidenlab/juicer/issues/110)
