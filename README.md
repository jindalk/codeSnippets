# codeSnippets
Useful code snippets for data analysis

## Bash
1. How to extract mouse data from 10x ATAC fragments file from mixed species expts:<br />
```
zcat fragments.tsv.gz | awk '{if($1~/mm10/) {x=$0; gsub("mm10_","",$x); print $x}}' > mm10_fragments.tsv #Extract mouse reads
mload samtools; bgzip mm10_fragments.tsv #gzip file
mload tabix; tabix -f -p bed -0 mm10_fragments.tsv.gz #Create tabix
```
2. Replace substring with another substring in a string. E.g. Replace Day2 with Day5 in al file names in a folder:
```
for i in $(ls); do echo ${i//Day2/Day5}; done
```
3. List files not matching a regex pattern:
```
ls !(*<pattern>*)
```

## Slurm
1. To unbuffer python job output, run as ```python -u <python_script>```
2. To run a bash command inside a running slurm job ```srun --ntasks-per-node=1 --jobid=<job_id> <command>```

## Python
1. Save data to pickle file <br/>
```
import pickle
with open('my_file.pkl', 'wb') as f:
    pickle.dump(data, f)
```
2. Check if scipy sparse matrix is the right format, this is helpful when jumping around scipy versions ```<mtx_name>.check_format()```
