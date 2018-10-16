# Tools and Dependencies

# use bbmerge for tileseq
#  this will merge tileseq reads, only for perfect overlapped reads 
```
export fqt_out=/nfs/kitzman2/jacob/proj/shared_run_splitting/miseqm_20180928/fqt_out/
export pfx=${fqt_out}tileseq
export miseq=20180928_miseq

is=(${pfx}*.read1.fq.gz)
js=(${pfx}*.read3.fq.gz)


export OUT=/nfs/kitzman2/isaac/miseq/$miseq/tileseq_merge/

for ((i = 0; i < 60; i++)); \
do /nfs/kitzman2/isaac/softwares/bbmap/bbmerge.sh \
in1=${is[i]} \
in2=${js[i]} \
out=$OUT/${is[i]#$fqt_out}.merged.fq.gz \
outu1=$OUT/${is[i]#$fqt_out}.unmerged.fq.gz \
outu2=$OUT/${js[i]#$fqt_out}.unmerged.fq.gz \
pfilter=1 \ ;
done

cd $OUT
for i in *.merged.fq.gz; do mv $i ${i/read1.fq.gz./}; done
```

# This is specific for tile14, need to adjust for other tiles


export suffix=.merged.fq.gz
for i in *Tile1_*.merged.fq.gz; do cutadapt -a CCTGGAGAATTGGCTAGCCGCCGCC...CACGGCGAGGACGCGCTG --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile2_*.merged.fq.gz; do cutadapt -a GGGGCGACTTCTATACGGCG...GATCTTCTTCTGGTTCGTCAGT --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile3_*.merged.fq.gz; do cutadapt -a TGAATTTTGAATCTTTTGTAAAA...AAAATGTCCGCAGTTGATGGC --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile4_*.merged.fq.gz; do cutadapt -a TCCATTGGTGTTGTGGGTGTT...CTCATCCAGATTGGACCAAAGGA --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile5_*.merged.fq.gz; do cutadapt -a AGTTCTCCAATCTTGAGGCTCTC...GACATTTATCAGGACCTCAACCGGTTG --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile6_*.merged.fq.gz; do cutadapt -a AAGCTGACTTTTCCACAAAA...TCAGATGATTCCAACTTTGGACA --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile7_*.merged.fq.gz; do cutadapt -a TCACTGTCTGCGGTAATCAAGTTTTTAGAACTCTTA...CTGGCTGCCTTGCTGAATAAG --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile8_*.merged.fq.gz; do cutadapt -a AGATACCACTGGCTCTCAGTCT...GAATTGAGGCAGACTTTACAAGAAGA --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile9_*.merged.fq.gz; do cutadapt -a GTGGAAGCTTTTGTAGAAGATGCA...AATGTTATACAGGCTCTGGAAAAACATGA --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile10_*.merged.fq.gz; do cutadapt -a TGTTACCGACTCTATCAGGGTATAAATCAACTACCT...GATCAGGTGGAAAACCATGAATTCC --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile11_*.merged.fq.gz; do cutadapt -a TCAGGAAATGATAGAAACAACTTTAGATATG...GACCCTGGCAAACAGATTAAACTGG --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile12_*.merged.fq.gz; do cutadapt -a GCAGCCAGAGATCTTGGCTTG...TTTACCAACAGCAAATTGACTTCT --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile13_*.merged.fq.gz; do cutadapt -a TCCAGAAGAATGGTGTTAAA...CTCAATGATGTGTTAGCTCAGCT --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile14_*.merged.fq.gz; do cutadapt -a GGCTATGTAGAACCAATGCAGACA...GCTTGTGTTGAAGTTCAAGATGA --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile15_*.merged.fq.gz; do cutadapt -a TATTAAAAGCATCCAGGCAT...ATAGTACTCATGGCCCAAATTGGGT --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile16_*.merged.fq.gz; do cutadapt -a ATATTCGACAAACTGGGGTG...TTGGAAACTGCTTCTATCCTCAGG --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile17_*.merged.fq.gz; do cutadapt -a GTCTCCACGTTCATGGCTGAAATG...GGTGCTTTTTGCATGTTTGCA --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile18_*.merged.fq.gz; do cutadapt -a TCAGAATACATTGCAACAAAGATT...GGTGTCTGTGATCAAAGTTTTGGG --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile19_*.merged.fq.gz; do cutadapt -a TGCTTTATCAGGTGAAGAAA...ATCATGGAACCAGCAGCAAAGA --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile20_*.merged.fq.gz; do cutadapt -a TGGAGAATCGCAAGGATATGAT...CCCTTTACTGAAATGTCAGAAGA --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done 
for i in *Tile21_*.merged.fq.gz; do cutadapt -a GGAGTTCCTGTCCAAGGTGAAACAAATG...GGATCCGGCGCAACAAACTTC --minimum-length 20 -q 10 -O 12 -e 0.1 -o ${i%$suffix}.merged.clip.fq.gz $i ; done


# generate tile_cluster.txt fiels

for i in *.merged.clip.fq.gz; do gunzip $i; done
export suffix=.merged.clip.fq
for i in *.merged.clip.fq; do /nfs/kitzman2/isaac/softwares/starcode/starcode -i $i -d 0 -o ${i%$suffix}.tile_cluster.txt; done
mkdir tileseq_cluster
mv *.tile_cluster.txt tileseq_cluster



rsync -avzP xiaoyanj@hk.hg.med.umich.edu:/nfs/kitzman2/isaac/miseq/20180928_miseq/tileseq_merge/tileseq_cluster/* /Users/Isaac/box/Kitzman_lab/data/20180928_tileseq_cluster/

for i in *.txt; do echo $i; WC $i; done


