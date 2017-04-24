 split_libraries.py -m Fasting_Map.txt -f Fasting_Example.fna –q Fasting_Example.qual -o split_library_output
 pick_de_novo_otus.py -i split_library_output/seqs.fna -o otus
 biom summarize-table –i otus/out_table.biom –o table_summary.txt
 summarize_taxa_through_plots.py -i otus/otu_table.biom –o wf_taxa_summary -m Fasting_Map.txt
 multiple_rarefactions.py -i otus/otu_table.biom -m 20 -x 100 -s 20 -n 10 -o rarefied_20-100
 alpha_diversity.py -i rarefied_20-100 -o alpha_diversity_results –t otus/rep_set.tre
 collate_alpha.py -i alpha_diversity_results -o alpha_div_collated
 make_rarefaction_plots.py -i alpha_div_collated -m Fasting_Map.txt -o rarefaction_plots
 jackknifed_beta_diversity.py -i otus/otu_table.biom –o jackknifed_beta_diversity -e 90 -m Fasting_Map.txt -t otus/rep_set.tre
