# genes and the count of published papers in PubMed

## file hgnc_ncbi_ensembl_pmid
which genes are most popular in research? what are the number of publications associated with each gene?  
You can get the answer from this file.

5 columns
* HGNC ID: ID in HGNC
* Approved symbol: gene symbol
* NCBI Gene ID: gene ID in NCBI
* Ensembl gene ID: like ENSG00000183044
* pmid_count: count of published papers with the gene.

The counting is based on "NCBI Gene ID" and use the eutils of NCBI. Check the example python code to see how the file is generated.
