
## Sequence Manipulation

#### Read in a file and add a line break every 200 characters
fold -w200 input.fasta


#### Return the size of the smallest and largest sequences in a fastQ file
bioawk -cfastx '{ print length($seq) }' ${input} | datamash min 1 max 1

##### The same as above, but returning quantiles 
bioawk -cfastx '{ print length($seq) }' ${input} | datamash min 1 q1 1 median 1 q3 1 max 1



## Sysadmin

#### List all immediate subdirectories of the current working directory
find ./* -maxdepth 0 -type d


