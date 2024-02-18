# DeepScena
DeepScena is a novel deep-learning clustering method for scRNA-seq data analysis that provides accurate results for hierarchically detecting rare cell populations. The method was fully equipped with features such as data imputation, dimensionality reduction, enhanced pairwise cell similarities, and efficient clustering strategies (see the ![workflow](https://github.com/SophiaChen-codes/DeepScena/DeepScena_Workflow.jpeg)). A key feature of DeepScena is the use of a negative binomial-based autoencoder to fit the NB model for data imputation, which enhances accuracy. Additionally, DeepScena uses paired data similarity as a self-supervised means to capture cell relationships and obtain a cluster-friendly space for efficient aggregation of similar cells. The study found that the NB-based autoencoder in DeepScena outperformed a regular autoencoder in terms of clustering scRNA-seq data. DeepScena was tested on eight expansive scRNA-seq datasets and results showed it has superior performance than seven other methods.

## Install packages
The code of DeepScena runs with Python version 3.9 and Pytorch==1.7.1. And you should have CUDA installed.

Please create a Pytorch environment, install Pytorch and some other packages, such as "**numpy**","**pandas**", "**scikit-learn**", "**scanpy**", and "**cudatoolkit**". See the __requirements.txt__ and __intall.txt__ file for an overview of the packages in the environment we used to produce our results.

## Data preprocessing

### Run the following command line to preprocess UMI-count data:
```
python preprocess_data.py -p Data/ -i pbmc4340.txt -o pbmcpre.csv
```
or 
```
python preprocess_data.py --filepath Data/ --filename pbmc4340.txt --resultfile pbmcpre.csv
```
The program accepts "**.txt**", "**.csv**", and **10x_mtx** files as input file name. 

### If the scRNA-seq data is read-count, please add a parameter "-r" or "--reads" as follows
```
python preprocess_data.py -p FILE_PATH/ -i FILE_NAME -o OUTPUT_FILE.csv -r
```
You can type command "**python preprocess_data.py -h**" for usage help. 

## Training and clustering

```
python runDeepScena.py
```
Before running DeepScena, please modify your file path and names (two files: the preprocessed scRNA-seq data file and its cell-type file), rename your dataset name (e.g. *dataset_name = 'pbmc'*), set the number of clusters (e.g. *number_cluster = 8*), and reset some other parameters such as batch size and maximum iterations. 

The latent low-dimensional space will be saved as "dataset_name"+"_uspace.csv" (e.g.  *pbmc_upsace.csv*)， which can be used for visualization.

The clustering result file will be saved as "dataset_name"+"_clusters.csv" (e.g.  *pbmc_clusters.csv*).

## Citation
Please cite our paper if you use the code.

Tianyuan Lei, **Ruoyu Chen,** Shaoqiang Zhang, Yong Chen, Self-supervised deep clustering of single-cell RNA-seq data to hierarchically detect rare cell populations, Briefings in Bioinformatics, Volume 24, Issue 6, November 2023, bbad335, https://doi.org/10.1093/bib/bbad335
