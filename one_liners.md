
## Sequence Processing and Manipulation

#### Calculate genome size statistics (e.g., N50, N90)
```
# scaffold N50:
fastx_length scaffolds.fasta > scaffolds.sizes
size_stats scaffolds.sizes 
# ... without .sizes file:
fastx_lengths scaffolds.fasta | size_stats - 
# ... transpose output for easier CLI viewing
fastx_lengths scaffolds.fasta | size_stats - | datamash transpose 

# contig N50:
# (TODO)
```

#### Read in a file and add a line break every 200 characters
fold -w200 input.fasta

#### Return the size of the smallest and largest sequences in a fastQ file
bioawk -cfastx '{ print length($seq) }' ${input} | datamash min 1 max 1

##### The same as above, but returning quantiles 
bioawk -cfastx '{ print length($seq) }' ${input} | datamash min 1 q1 1 median 1 q3 1 max 1


#### PacBio
##### Get the names of some pacbio subreads, split each name in to discrete parts (delimited by forward slashes), and calculate how many ZMWs are represented. 
fastx_names m160611_100724_42219_c101002732550000001823227509161692_s1_p0.1.subreads.fasta | cut -d/ -f2 | sort | uniq | wc -l


## Sysadmin

#### List all immediate subdirectories of the current working directory
find ./* -maxdepth 0 -type d

#### Clear contents of a file 
`> ${OUT_FILE}  # clear contents`


