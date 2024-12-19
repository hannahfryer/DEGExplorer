## DEGExplorer: : Visualising and Annotating Top Genes

This repository contains scripts for analyzing differential gene expression (DEG) data, identifying significant genes, and annotating genes using external databases such as NCBI and KEGG. The scripts are designed to streamline the analysis and provide interactive visualization options, ranked gene lists, and functional annotations

## Repository Overview
Scripts:
1. interactive_volcano_plot.py:
Processes DESeq2 results to identify significant genes based on adjusted p-values and log2 fold-change thresholds.
Saves significant genes to a CSV file and creates an interactive volcano plot for visualization.

2. significant_gene_details.py:
Processes DESeq2 results to rank genes by log2 fold change. Extracts the top 100 significant genes and queries the NCBI Gene database for Pisum sativum (pea) to retrieve gene details such as description, protein information, and functional annotations. Saves results to a new CSV file.

3. KEGG_retriever.py:
Queries the KEGG database to check if gene IDs have KEGG Orthology (KO) assignments.
Reads gene IDs from a CSV file, retrieves KO information, and saves the results to a new CSV file.

## Requirements
- Python version 3.8 or higher

#### 1. Clone the Repository
```bash
git clone https://github.com/hannahfryer/DEGExplorer.git
cd DEGExplorer
```

#### 2. Install Dependencies
Use `requirements.txt` for a streamlined setup:
```bash
pip install -r requirements.txt
```

Alternatively, manually install the required libraries:
```bash
pip install pandas plotly numpy biopython beautifulsoup4 requests
```

### Input

If you are not using the sample data provided in this repository, ensure your input CSV file (`DEG_results.csv`) is correctly formatted with the following columns:

- **`gene`**: Gene identifiers (e.g., gene names or locus tags).  
- **`log2FoldChange`**: Log2-transformed fold-change values indicating the magnitude and direction of differential expression.  
- **`pvalue`**: Raw p-values representing the statistical significance of the differential expression.  
- **`padj`**: Adjusted p-values  



Here's an updated version of the "Running the Script" and "Output" section for each script in the repository, tailored to their specific functionalities:

---

### **1. DEG Analysis and Interactive Volcano Plot**

#### Running the Script
Run the script with your DEG results file (`DEG_results.csv`) as input:
```bash
python volcano_plot.py --input DEG_results.csv
```

#### Output
The following file will be generated:
- **`volcano_plot.html`**: An interactive volcano plot visualizing the differential expression results.
- **`significant_genes.csv`**: A list of significant genes filtered based on the specified thresholds.

---

### **2. DEG Analysis and Gene Information Retrieval**

#### Running the Script
Run the script with the significant genes file (`significant_genes.csv`) as input:
```bash
python gene_info_retrieval.py --input significant_genes.csv
```

#### Output
The following files will be generated:
- **`top_100_genes.csv`**: A ranked list of the top 100 genes by log2 fold change.
- **`top_100_gene_details.csv`**: Detailed metadata for the top 100 genes retrieved from the NCBI Gene database.

---

### **3. KEGG KO Assignment Checker**

#### Running the Script
Run the script with the gene details file (`top_100_gene_details.csv`) as input:
```bash
python kegg_ko_checker.py --input top_100_gene_details.csv
```

#### Output
The following file will be generated:
- **`gene_ko_results.csv`**: A file containing KEGG Orthology (KO) information for each gene.

---

### Notes
- Replace `--input <file>` with the appropriate file path if your data files are located elsewhere.
- Ensure your input files are correctly formatted and match the expected structure for each script.  
- Adjust thresholds and parameters in the scripts to fit your analysis needs.

## Limitations
- The KEGG search may not return KO terms for all genes.
- Accuracy of gene ID retrieval depends on input data quality.
- Assumes properly formatted DEG input file.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.
