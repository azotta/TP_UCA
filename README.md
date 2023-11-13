# TP_UCA

# TP Atelier genomique – Master BBC


Download the data from: https://unice-my.sharepoint.com/:f:/r/personal/ana-paula_zotta-mota_unice_fr/Documents/TP_Master_BBC_2023?csf=1&web=1&e=9zIjSS


1-	Open your terminal 

2-	Identify where you are located 
```
pwd
```

3- Create a directory under your Documents 
```
mkdir TP_Genomics
```

4- Navigate to your new directory
```
cd TP_Genomics
```
5 - List the files 
```
ls -la
```
6 - Download the file Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa.gz from the OneDrive link 
7 - Move the file to your new directory
```
mv /path/download/Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa.gz .
```
8 - List the files on your new directory
```
ls -la
```
9 - Use zcat to read a .gz file
```
zcat Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa.gz |less

for mac users:
zcat < Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa.gz |less
```

10 - How many sequences your file have? (Here you have two options: decompress the file or do all the analysis using the command above before the pipe)
```
To decompress you file:
gzip -d Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa.gz
To count the number of sequences
grep '>' Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa |wc
```
11 - How many letters on the sequences? 
```
awk '/^>/{if (l!="") print l; print; l=0; next}{l+=length($0)}END{print l}' Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa
```

12 - Based on the header of the sequences, what is this ? 

13 - 


















