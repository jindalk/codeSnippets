# codeSnippets
Useful code snippets for data analysis

## Bash
1. How to extract mouse data from 10x ATAC fragments file by species:<br />
```
zcat fragments.tsv.gz | awk '{if($1~/mm10/) {x=$0; gsub("mm10_","",$x); print $x}}' > mm10_fragments.tsv #Extract mouse reads
mload samtools; bgzip mm10_fragments.tsv #gzip file
mload tabix; tabix -f -p bed -0 mm10_fragments.tsv.gz #Create tabix
```


## Python
1. Save data to pickle file <br/>
```
import pickle
with open('my_file.pkl', 'wb') as f:
    pickle.dump(data, f)
```
