# Extract Telomere Related Genes from FPF (MM samples)

#Telomere-Related Genes (TRG) are:
<br>
> TERT gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=TERT<br>
chr5:1,253,262-1,295,184(GRCh37/hg19)<br>
Orientation:Minus strand<br>
Size:41,923 bases<br>

> TERC gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=TERC<br>
chr3:169,482,308-169,482,848(GRCh37/hg19)<br>
Orientation:Minus strand<br>
Size:541 bases<br>

> DKC1 gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=DKC1<br>
chrX:153,991,031-154,005,964(GRCh37/hg19)<br>
Orientation:Plus strand<br>
Size:14,934 bases<br>

> PARN gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=PARN<br>
chr16:14,529,558-14,726,585(GRCh37/hg19)<br>
Orientation:Minus strand<br>
Size:197,028 bases<br>

> RTEL1 gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=RTEL1<br>
chr20:62,289,163-62,328,416(GRCh37/hg19)<br>
Orientation:Plus strand<br>
Size:39,254 bases<br>

> TINF2 gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=TINF2<br>
chr14:24,708,849-24,711,880(GRCh37/hg19)<br>
Orientation:Minus strand<br>
Size:3,032 bases<br>

> TERF1 gene: https://www.genecards.org/cgi-bin/carddisp.pl?gene=TERF1<br>
chr8:73,921,097-73,960,357(GRCh37/hg19)<br>
Orientation:Plus strand<br>
Size:39,261 bases<br>

#BED file: save as plain text and name as "TRG_genes.bed"<br>
```[Bash]
chr3	169482308	169482848
chr5	1253262	1295184
chr8	73921097	73960357
chr14	24708849	24711880
chr16	14529558	14726585
chr20	62289163	62328416
chrX	153991031	154005964
```

#Now run this code in the shell
```[Bash]
module load vcftools/0.1.14 htslib/1.3.1
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
#And this code
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
#Copy VCF's of interest to a safe place
```[Bash]
find . -type f -name "*.TRG.vcf" | sort > ./TRG/TRG_list
# Or
find . -type f -name "*.TRG.vcf" -exec basename {} \; | sort
indir=${indir}
cp ${indir}/IPFBCN01/IPFBCN01.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf ${indir}/TRG/
cp ${indir}/IPFBCN02/IPFBCN02.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf ${indir}/TRG/
cp ${indir}/IPFBCN03/IPFBCN03.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf ${indir}/TRG/
cp ${indir}/IPFBCN04/IPFBCN04.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf ${indir}/TRG/

cp ${indir}/IPFBCN05/IPFBCN05.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf ${indir}/TRG/
cp ${indir}/IPFBCN06/IPFBCN06.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf ${indir}/TRG/
cp ${indir}/IPFBCN07/IPFBCN07.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf ${indir}/TRG/
cp ${indir}/IPFBCN08/IPFBCN08.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf ${indir}/TRG/

cp ${indir}/IPFBCN09/IPFBCN09.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf ${indir}/TRG/
cp ${indir}/IPFBCN10/IPFBCN10.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf ${indir}/TRG/
cp ${indir}/IPFBCN11/IPFBCN11.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf ${indir}/TRG/
cp ${indir}/IPFBCN12/IPFBCN12.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf ${indir}/TRG/

# Then bgzip compress and tabix:
cd ${indir}/TRG/
infile=IPFBCN01.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf
outfile=${infile}.gz
bgzip -c ${infile} > ${outfile}
tabix -p vcf ${outfile}

infile=IPFBCN02.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf
outfile=${infile}.gz
bgzip -c ${infile} > ${outfile}
tabix -p vcf ${outfile}

infile=IPFBCN03.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf
outfile=${infile}.gz
bgzip -c ${infile} > ${outfile}
tabix -p vcf ${outfile}

infile=IPFBCN04.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf
outfile=${infile}.gz
bgzip -c ${infile} > ${outfile}
tabix -p vcf ${outfile}

infile=IPFBCN05.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf
outfile=${infile}.gz
bgzip -c ${infile} > ${outfile}
tabix -p vcf ${outfile}

infile=IPFBCN06.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf
outfile=${infile}.gz
bgzip -c ${infile} > ${outfile}
tabix -p vcf ${outfile}

infile=IPFBCN07.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf
outfile=${infile}.gz
bgzip -c ${infile} > ${outfile}
tabix -p vcf ${outfile}

infile=IPFBCN08.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf
outfile=${infile}.gz
bgzip -c ${infile} > ${outfile}
tabix -p vcf ${outfile}

infile=IPFBCN09.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf
outfile=${infile}.gz
bgzip -c ${infile} > ${outfile}
tabix -p vcf ${outfile}

infile=IPFBCN10.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf
outfile=${infile}.gz
bgzip -c ${infile} > ${outfile}
tabix -p vcf ${outfile}

infile=IPFBCN11.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf
outfile=${infile}.gz
bgzip -c ${infile} > ${outfile}
tabix -p vcf ${outfile}

infile=IPFBCN12.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf
outfile=${infile}.gz
bgzip -c ${infile} > ${outfile}
tabix -p vcf ${outfile}

# Merge all VCF's
vcf-merge \
IPFBCN01.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf.gz \
IPFBCN02.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf.gz \
IPFBCN03.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf.gz \
IPFBCN04.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf.gz \
IPFBCN05.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf.gz \
IPFBCN06.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf.gz \
IPFBCN07.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf.gz \
IPFBCN08.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf.gz \
IPFBCN09.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf.gz \
IPFBCN10.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf.gz \
IPFBCN11.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf.gz \
IPFBCN12.SNP_INDEL.recalibrated.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf.gz > IPFBCN.AllIndividuals.ANNOVAR.snpEff.GATK.annotations.hg19.TRG.vcf.gz


#End of Script
