# Panther
Panther Package

This package suport PANTHER (Protein ANalysis THrough Evolutionary Relationships) Classification System.

More information in http://pantherdb.org



## **Data mapping**

Given a list of genes and a species, this service return the gene ontology annotations, PANTHER protein class annotations and Reactome annotations.

**Parameters:** 

**genes:**  Genes identifier. Maximum of 1000 Identifiers can be any of the following: Ensemble gene identifier, Ensemble protein identifier, Ensemble transcript identifier, Entrez gene id, gene symbol, NCBI GI, HGNC Id, International protein index id, NCBI UniGene id, UniProt accession and UniProt id. \
**organism:** Taxon id. Ex.: 9606

```
data <- panther_map(genes = c("BRCA1", "VDR", "HBB"), organism = "9696")
```

**Return:**

**name:** Pathways' name \
**id:** Gene Ontology ID \
**panther_id:** Annotation id from PANTHER \
**panther_label:** Annotation label from PANTHER \
**gene_acession:** Id of the gene from HGNC and UniProtKB \


## **Overrepresentation test**

Overrepresentation function compares a gene list to a reference gene list, and determines whether a particular class (e.g. molecular function, biological process, cellular component, PANTHER protein class, the PANTHER pathway or Reactome pathway) of genes is overrepresented or underrepresented.

**Parameters:** 

**genes:**  Genes identifier. Maximum of 1000 Identifiers can be any of the following: Ensemble gene identifier, Ensemble protein identifier, Ensemble transcript identifier, Entrez gene id, gene symbol, NCBI GI, HGNC Id, International protein index id, NCBI UniGene id, UniProt accession andUniProt id \
**organism:** One taxon id required. Ex.: 9606 \
**ref_list:** If not specified, the system will use all the genes for the specified organism. Each identifier to be delimited by comma i.e. ','. Maximum of 100000 Identifiers can be any of the following: Ensemble gene identifier, Ensemble protein identifier, Ensemble transcript identifier, Entrez gene id, gene symbol, NCBI GI, HGNC Id, International protein index id, NCBI UniGene id, UniProt accession andUniProt id \
**refOrganism:** This parameter is only required, if parameter 'refInputList' has been specified. Only one taxon id can be specified. Retrieve the list of supported genomes and corresponding taxon ids from the 'supportedgenomes' service. \
**annotDataSet:** One of the supported PANTHER annotation data types. Use the 'supportedannotdatasets' service to retrieve list of supported annotation data types. Ex: GO:0003674 \
**testtype:** Fisher's Exact test will be used by default. Options - "FISHER" and "BINOMIAL" \
**correction:** correction of enrichment. Options - "FDR", "BONFERRONI" and "NONE" \


```
data <- panther_over(genes = c("BRCA1", "VDR", "HBB"), annotDataSet = "GO:0003674")
```

**Return:** 

**number_in_list** \
**fold_enrichment:** proportion of term genes found in the input list compared to the. proportion of total term genes found in the background \
**fdr correction** \
**expected** \
**number_in_reference** \
**pValue** \
**term.id:** Gene Ontology ID \
**term.label** \
**plus_minus**


## **Supported genomes**

Retrieve the list of supported organisms


```
sup <- support_annot()
```

**Return:** 

**Returns information about annotation data sets supported by PANTHER** \
**release_date** \
**description** \
**id** \
**label** \
**version**

