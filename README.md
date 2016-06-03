# blast

Downloaded the bowhead whale genome from http://www.bowhead-whale.org/downloads/ to the cluster

Used blastn to compare the .fasta files agains the bowhead genome, but customised the output using -outfmt. For some reason
For some reason, even though max_target_seqs = 4, 5 are returned??

for i in *.fasta; 
do 
blastn -db ../bowhead/bowhead_scaffold -num_threads 12 -evalue 0.00001 -max_target_seqs 4 -query $i -out $i.txt -outfmt "6 evalue pident qseqid qlen sseqid length sseq"; 
done

For each file, the code returned the top 5 hits for each allele for each sample at each locus.

Therefore, I checked whether the top hit for each allele per sample was the same, which would give high support
for the subject sequence being a match for the query sequences.
