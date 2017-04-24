


#### Return the size of the smallest and largest sequences in a fastQ file
bioawk -cfastx '{ print length($seq) }' ${input} | datamash min 1 max 1

##### The same as above, but returning quantiles 
bioawk -cfastx '{ print length($seq) }' ${input} | datamash min 1 q1 1 median 1 q3 1 max 1

