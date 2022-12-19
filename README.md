# codeSnippets
Useful code snippets for data analysis

1. How to extract mouse data from 10x ATAC fragments file by species:<br />
- Extract mouse reads: ```zcat fragments.tsv.gz | awk '{if($1~/mm10/) {x=$0; gsub("mm10_","",$x); print $x}}' > mm10_fragments.tsv``` <br/>
- gzip file: ```mload samtools; bgzip mm10_fragments.tsv``` <br/>
- Creare tabix: ```mload tabix; tabix -f -p bed -0 mm10_fragments.tsv.gz``` <br/>
