# metabarcoding of GOA Bottom Trawl 2023 eDNA samples

amplicon sequencing of (1) 12S MiFish and (2) dloop rockfish

-all sample replicates for both amplicons were sequenced on the 20250125 MiSeq run
-demultiplexed reads were processed using Dadasnake (config.mifish.yaml and config.rkfish.yaml)

1_mifish_taxonomic_assignment_blastn.Rmd
- performed taxonomic assignment of ASVs using NCBI nt database (query parameters: 96% seq identity and 98% query coverage)
- filtered taxonomic hits to retain only fish found in the NE Pacific (according to FishBase)
- based taxonomic assignment of ASVs on the top 0.5% of hits if the best match was >= 98% or on the top 1% of matches if the best match was < 98%

taxonomic assignment of the rockfish dloop sequences 
blastn -query /home/kimberly.ledger/goa-bt23-mb/data/dadasnake_rkfish/filtered.seqs.fasta -db /home/kimberly.ledger/rockfish_mb/custom_db/rockfish_db_534_20250117 -out rkfish_bt23_blastn.txt -perc_identity 92 -qcov_hsp_perc 98 -num_threads 10 -outfmt '6 qseqid sseqid pident length mismatch gapopen qstart qend sstart send evalue bitscore sscinames staxids'

then 2_rockfish_taxonomic_assignment.Rmd

