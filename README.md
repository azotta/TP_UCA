# TP_UCA

# TP Atelier genomique – Master BBC


Download the data from: https://unice-my.sharepoint.com/:f:/r/personal/ana-paula_zotta-mota_unice_fr/Documents/TP_Master_BBC_2023?csf=1&web=1&e=9zIjSS

## Basic terminal commands

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
6 - Create a file with some text inside: 
```
echo "putyourtexthere" > file.txt
```
7 - Read your text
To read your text you have several options. 
To simple print everything directly to the terminal 
```
more file.txt
```
To show your file but not print on the terminal 
```
less file.txt
```
To visualize and edit your file
```
vi file.txt

nano file.txt
```

8 - Now, change the name of your file: 
```
mv file.txt test.txt
```

9 - Move your file to another directory
```
mv test.txt /home/user/Documents (change accordling to your computer!)
```

10 - Delete your file 
```
rm test.txt
```
Download the file blast_result.txt

This is a blast result (format 6) 

|1.  qseqid   |   query or source (gene) sequence id |
--------------|---------------------------------------
|2.  sseqid   |   subject or target (reference genome) sequence id |
|3.  pident   |   percentage of identical positions |
|4.  length   |   alignment length (sequence overlap) |
|5.  mismatch |   number of mismatches |
|6.  gapopen  |   number of gap openings |
|7.  qstart   |   start of alignment in query |
|8.  qend     |   end of alignment in query |
|9.  sstart   |   start of alignment in subject | 
|10.  send    |    end of alignment in subject |
|11.  evalue  |    expect value |
|12.  bitscore|    bit score |

11 - How many different contigs we could map our seq Mare_2_3_1 ?
```
 sort -u -k2,2 blast_result.txt |wc
```

12 - How many matchs have more than 90% of identity ?

```
awk '$3 > 90.0 {print $0}' blast_result.txt |wc
```

13 - Print only the query name, query start, query end 
```
Your time to play ;)
```
14 - Change the name of our subject from Mare_2_3_1 to subject_1
```
sed 's/Mare_2_3_1/subject_1/g' blast_result.txt |less
```
You also have the option to change it on the same file directly (Be extra careful), using the option -i



## Fastq and Fasta files

1 - Download the file Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa.gz from the OneDrive link 

2 - Move the file to your new directory
```
mv /path/download/Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa.gz .
```
3 - List the files on your new directory
```
ls -la
```
4 - Use zcat to read a .gz file
```
zcat Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa.gz |less

for mac users:
zcat < Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa.gz |less
```

5 - How many sequences your file have? (Here you have two options: decompress the file or do all the analysis using the command above before the pipe)
```
To decompress you file:
gzip -d Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa.gz
To count the number of sequences
grep '>' Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa |wc
```
6 - How many letters on the sequences? 
```
awk '/^>/{if (l!="") print l; print; l=0; next}{l+=length($0)}END{print l}' Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa
```

7 - Based on the header of the sequences, which kind of sequence is this? 

8 - Download the file SRR4242474_1.fastq.gz 

9 - Move the file to your TP_Genomics directory

10 - Repeat the command to decompress the file

10.1 - Check the size of the file decompressed and the compressed, what is the size in Gb ? 
```
ls -latrh
```
11 - How many lines do you have? Could you guess how many sequences do you have? 

12 - Visualize the file using "more"  or "less"

13 - Are these sequences from a short or long read technology ? 

14 - How would you count the number of sequences in this kind of file? 


## BAM/SAM files


Download the file out_arabi_chr1.sam from the OneDrive

1 - Visualize your file 

2 - What are its characteristics ? 

3 - How many reads were mapped to the reference ? 

```
awk -F"\t" '$3=="1" {print $0}' out_arabi_chr1.sam |wc
```

4 - Change the name of the chromosome 1 (which now is only the number 1, to chr 1)
```
awk '{ if ($3 == 1) $3 = "chr1"; print }' out_arabi_chr1.sam > new_file.sam
```

## VCF files






















