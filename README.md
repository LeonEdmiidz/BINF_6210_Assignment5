# BINF_6210_Assignment5

Introduction
	Freshwater ecosystems are vital for society globally as they provide clean water and food, support livelihoods, and contribute significantly to the economy (Darwall et al., 2018). These ecosystems are highly stressed due to various factors, one major cause being the harmful impacts of invasive species (Darwall et al., 2018). Research on invasive fish in freshwater ecosystems has found that many species belong to the Carassius genus (Wouters et al., 2012). DNA barcoding has emerged as an essential and effective method for species identification, which is crucial for detecting invasive species and analyzing the harm caused by their presence (Trivedi et al., 2016). DNA barcoding relies on specific marker genes that vary in sequence from species to species. These marker genes cannot be too similar or different across species, therefore, there are only a small number of reliable marker genes. One gene identified as a reliable marker gene for barcoding animals is the mitochondrial COI gene (Trivedi et al., 2016).
	This study aims to compare the COI gene and the Cytochrome b (CYTB) gene to analyze whether COI is genuinely ideal as a DNA barcoding marker gene compared to other mitochondrial genes. Using sequence data of COI and CYTB from Carassius species and unsupervised machine learning to cluster the sequences. I hypothesize that each cluster of COI sequences will represent a particular species of Carassius and that the clusters for the CYTB sequences will not be representative of the species. If true, COI is a better genetic marker for DNA barcoding than CYTB. Dendrograms will be generated to visualize how the sequences clustered, and Silhouette plots will be used to analyze the validity of the consistency within the clusters for both COI and CYTB. As a secondary objective, I will compare Kimura's 2-parameters distance model to the Tamura-Nei model and the single-linkage clustering method to the neighbour-joining clustering method.

Dataset Description
	This analysis will be conducted on data gathered from NCBI's Nucleotide database. This database consists of data from various sources, including submissions from individual researchers, sequencing projects, scientific literature, and other public databases. I used functions from the R package “rentrez” to gather the data on December 7th, 2023. Initially, the COI dataset consisted of 1094 samples, and the CYTB dataset had 2344 samples; however, much of the data was filtered out during the filtering steps, so not all of these entries were used in the analysis. The key variables of interest are the genus, species, process ID, and gene sequences. The genus, species, and process ID had to be extracted from the information within the entries. The gene sequences varied greatly in length and quality, therefore, the filtering steps were necessary for the analysis. Since the goal is to compare the genes, the COI and CYTB data were gathered into different datasets. The CYTB dataset contained many more entries than the COI dataset; therefore, the filtering steps were more stringent to reduce the number of entries closer to that of the COI dataset. The median values for the COI and CYTB sequence lengths were highly different, yet this is not an issue for the analysis since the datasets were not combined.
U.S. National Library of Medicine. (n.d.). Home - nucleotide - NCBI. National Center for Biotechnology Information. https://www.ncbi.nlm.nih.gov/nucleotide/ 
Main Software Tools Description
	The primary software tool used for this analysis was the “Treeline” function from the DECIPHER package. This function was used to cluster the sequences based on the distance matrices. Although I considered using the FactoMineR package to run a PCA as an alternative analysis, I chose this function as it is a very user-friendly tool. One of the tool's strengths is its easy customizability regarding the clustering method and threshold. The dendrogram created from this tool was also easy to customize, allowing for adequate visualization of the clusters. A challenge I encountered with this tool was that the output needed to be reformatted to generate the Dunn and Silhouette indices. Although the output could not be directly used to generate the indices, several alterations allowed the output to be applied to functions to create the indices and the Silhouette plot. The other software tools that greatly contributed to the analysis include the Tidyverse, Biostring, ape, and muscle packages. To build upon the outputs from the “Treeline” tool, I used the “dunn” function from the clValid package and the “silhouette” function from the cluster package. The Dunn index allowed me to test the quality of the clusters and compare the models used for the distance matrices and the clustering methods. 
Growing phylogenetic trees with treeline - bioconductor. (n.d.). https://bioconductor.org/packages/release/bioc/vignettes/DECIPHER/inst/doc/GrowingTrees.pdf

Results and Discussion
	Investigating the distinct clustering patterns exhibited by the COI and CYTB genes within the Carassius fish species unveils divergences in evolutionary signals encoded by these genes, assessing their suitability as molecular markers for taxonomic classification and deciphering nuanced evolutionary pressures and serves as an exploration of molecular taxonomy. First, I should specify that I used Kimura's 2-parameters distance model and single-linkage clustering as these parameters fit better than their counterparts. The dendrograms indicate that COI is a better DNA barcoding marker than CYTB. The clusters of COI overall represented the different species of Carassius, meanwhile, the cluster patterns of CYTB were far more random and contained more clusters than there were species. The analysis results were expected, yet a key caveat must be addressed.
	The filter COI dataset consists of five species, yet only three major clusters were identified. The first cluster consists exclusively of Carassius carassius, and the second consists exclusively of Carassius Cuvieri. The caveat lies in the third cluster, consisting mainly of Carassius Auratus and Carassius Gibelio, one of Carassius Langsdorfii and one of Carassius carassius. This could indicate that COI is an insufficient marker for identifying Auratus, Gibelio, and Langsdorfi. However, Gibelio and Langsdorfi are often classified as intraspecies of Carassius auratus (Wouters et al., 2012). This means that the three may, in some cases, be considered as the same species, Carassius auratus. This explains the highly similar sequences of COI among these three intraspecies and reflects why they were also clustered together. Only one sequence of Langsdorfi was included in the analysis due to sample size limitation, and the one Carassius carassius sequence clustered in the third cluster was likely an outlier.
	This research could be expanded to analyze more genes, potentially identifying more genes that could be used as genetic markers for DNA barcoding. The sample size for this analysis was relatively small and only analyzed five different species; therefore, running the same analysis with a larger dataset and more species would be very interesting. Although this analysis showed that CYTB is not a sufficient marker gene for the Carassius genus, it may serve as a sufficient marker gene for species of other genera. This project could also be expanded to study marker genes in other kingdoms, such as plants. The COI gene is considered the DNA barcoding marker gene only for animals. There are several candidates for DNA barcode genes for plants, including MatK, RbcL, TrnH-psbA, and ITS (Li et al., 2014). This project can potentially discover new candidate DNA barcode genes for plants. Overall, I would love to expand on this project to analyze more genera and genes while using a larger dataset and analyze clustering patterns to understand DNA barcoding marker genes better.

References
Darwall, W., Bremerich, V., De Wever, A., Dell, A. I., Freyhof, J., Gessner, M. O., Grossart, H., Harrison, I., Irvine, K., Jähnig, S. C., Jeschke, J. M., Lee, J. J., Lu, C., Lewandowska, A. M., Monaghan, M. T., Nejstgaard, J. C., Patricio, H., Schmidt‐Kloiber, A., Stuart, S. N., … Weyl, O. (2018). The Alliance for Freshwater Life A global call to unite efforts for Freshwater Biodiversity Science and Conservation. Aquatic Conservation: Marine and Freshwater Ecosystems, 28(4), 1015–1022. https://doi.org/10.1002/aqc.2958
Dunn Index. R. (n.d.). https://search.r-project.org/CRAN/refmans/clValid/html/dunn.html#:~:text=The%20Dunn%20Index%20is%20the,details%20see%20the%20package%20vignette. (Accessed on December 7th, 2023).
Growing phylogenetic trees with treeline - bioconductor. (n.d.). https://bioconductor.org/packages/release/bioc/vignettes/DECIPHER/inst/doc/GrowingTrees.pdf (Accessed on December 7th, 2023).
Li, X., Yang, Y., Henry, R. J., Rossetto, M., Wang, Y., & Chen, S. (2014). Plant DNA barcoding: From gene to genome. Biological Reviews, 90(1), 157–166. https://doi.org/10.1111/brv.12104
Silhouette: Compute or extract silhouette information from clustering. RDocumentation. (n.d.). https://www.rdocumentation.org/packages/cluster/versions/2.1.4/topics/silhouette (Accessed on December 7th, 2023).
Trivedi, S., Aloufi, A. A., Ansari, A. A., & Ghosh, S. K. (2016). Role of DNA barcoding in Marine Biodiversity Assessment and Conservation: An Update. Saudi Journal of Biological Sciences, 23(2), 161–171. https://doi.org/10.1016/j.sjbs.2015.01.001
U.S. National Library of Medicine. (n.d.). Home - nucleotide - NCBI. National Center for Biotechnology Information. https://www.ncbi.nlm.nih.gov/nucleotide/ (Accessed on December 7th, 2023).
Wouters, J., Janson, S., Lusková, V., & Olsén, K. H. (2012). Molecular identification of hybrids of the invasive gibel carp Carassius auratus gibelio and crucian carp Carassius carassius in Swedish waters. Journal of Fish Biology, 80(7), 2595–2604. https://doi.org/10.1111/j.1095-8649.2012.03312.x 