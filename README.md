# Extract Telomere Related Genes from FPF (MM samples)

#These genes are:
#> TERT gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=TERT<br>
#chr5:1,253,262-1,295,184(GRCh37/hg19)<br>
#Orientation:Minus strand<br>
#Size:41,923 bases<br>
<br>
#> TERC gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=TERC<br>
#chr3:169,482,308-169,482,848(GRCh37/hg19)<br>
#Orientation:Minus strand<br>
#Size:541 bases<br>
<br>
#> DKC1 gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=DKC1<br>
#chrX:153,991,031-154,005,964(GRCh37/hg19)<br>
#Orientation:Plus strand<br>
#Size:14,934 bases<br>
<br>
#> PARN gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=PARN<br>
#chr16:14,529,558-14,726,585(GRCh37/hg19)<br>
#Orientation:Minus strand<br>
#Size:197,028 bases<br>
<br>
#> RTEL1 gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=RTEL1<br>
#chr20:62,289,163-62,328,416(GRCh37/hg19)<br>
#Orientation:Plus strand<br>
#Size:39,254 bases<br>
<br>
#> TINF2 gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=TINF2
#chr14:24,708,849-24,711,880(GRCh37/hg19)
#Orientation:Minus strand
#Size:3,032 bases

#> TERF1 gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=TERF1
#chr8:73,921,097-73,960,357(GRCh37/hg19)
#Orientation:Plus strand
#Size:39,261 bases

#BED file: save as "TRG_genes.bed"
```Bash
chr3	169482308	169482848
chr5	1253262	1295184
chr8	73921097	73960357
chr14	24708849	24711880
chr16	14529558	14726585
chr20	62289163	62328416
chrX	153991031	154005964
```

```
module load vcftools/0.1.14
basedir=/lustre/jlorsal/hiseq4000/run40/soloIPF
for i in {1..9}
do
sample=IPFBCN0${i}
indir=${basedir}/${sample}
outdir=${indir}
trg=${basedir}/TRG_genes
infile=${sample}.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19
outfile=${sample}.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG
vcftools --vcf ${basedir}/${sample}/${infile}.vcf --bed ${trg} --recode --out ${outdir}/${outfile}.vcf
mv ${outdir}/${outfile}.vcf.recode.vcf ${outdir}/${outfile}.vcf 
done
```

```
for i in {10..12}
do
sample=IPFBCN${i}
indir=${basedir}/${sample}
outdir=${indir}
trg=${basedir}/TRG_genes
infile=${sample}.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19
outfile=${sample}.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG
vcftools --vcf ${basedir}/${sample}/${infile}.vcf --bed ${trg} --recode --out ${outdir}/${outfile}.vcf
mv ${outdir}/${outfile}.vcf.recode.vcf ${outdir}/${outfile}.vcf 
done
```
#End of Script
