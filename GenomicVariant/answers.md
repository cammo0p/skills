Q1: How many positions are found in this region in the VCF file?
A: There are 69 positions in the region. I used this command to find the answer:  'bcftools view -r 1:1105411-44137860 CEU.exon.2010_03.genotypes.vcf.gz | bcftools query -f '%POS\n' | wc -l'. It first filters the genomic region and then extract variants from that specific region, and then perform counting.

Q2:How many samples are included in the VCF file?
A: There are 90 samples in the VCF file. I used this command to find the answer: 'bcftools query -l CEU.exon.2010_03.genotypes.vcf.gz | wc -l'. It lists the samples out and performed counting.

Q3: How many positions are there total in the VCF file?
A: There are 3489 positions in total. I used this command to find the answer: 'bcftools query -f '%POS\n' CEU.exon.2010_03.genotypes.vcf.gz | wc -l'. It extracts the position field from the VCF and perform counting.

Q4: How many positions are there with AC=1? Note that you cannot simply count lines since the output of bcftools filter includes the VCF header lines. You will need to use bcftools query to get this number.
There are 1075 positions.  I used this command to find the answer: 'bcftools query -i 'AC==1' -f '%CHROM:%POS\n' CEU.exon.2010_03.genotypes.vcf.gz | wc -l'. It filters variants where the allele count equals 1. It then outputs the chromosome and position of each variant, and then performed the counting.

Q5: What is the ratio of transitions to transversions (ts/tv) in this file?
The ratio is 3.47. Information provided by performing 'bcftools stats', report directly answers the question about the ratio of ts/tv.

Q6: What is the median number of variants per sample in this data set?
The median is 28. I found a table under the MAF called variants.per.sample, and I performed variant_counts <- lgg@variants.per.sample[["Variants"]]  and median(variant_counts) to get the median.



