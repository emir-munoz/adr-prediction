# Article supplemental material

- **Title**: Knowledge Graphs and Multi-label Learning Models Facilitate Flexible and Efficient Prediction of Adverse Drug Reactions
- **Authors**: Emir Muñoz, Vít Novácek, Pierre-Yves Vandenbussche
- **Contact**: Emir Muñoz, emir.munoz@insight-centre.org

## Data sets

We make available the data sets used to evaluate our approach.


### Liu's data set

This data set was originally proposed by Liu et at. (2012), and then processed after by Zhang et at. (2015) for machine learning. Liu's dataset contains 832 drugs with 2892 features, and 1385 ADRs.

The results of our approach using this dataset are in _Table 4_ and _Table 5_ of our article.

**Folder:** `liu/`
**Files:**
- `Liu_drug_lists.csv`: list of 832 drugs. The file is in `csv` format: `DrugBank ID, Drug Name, PubChem ID`.
- `Liu_dataset.mat`: a file with the features for each drug. The file uses MatLab `mat` format, and contains a dictionary with features name and values for each of the 832 drugs. The features are:

| Feature type | Specific feature      | Source   | ID                | Dimension | Dictionary key |
|--------------|-----------------------|----------|-------------------|-----------|----------------|
| Chemical     | Substructures         | PubChem  | PubChem IDs       | 881       | `chemical`     |
| Biological   | Targets               | DrugBank | GeneBank Gene IDs | 786       | `target`       |
| Biological   | Transporters          | DrugBank | HGNC IDs          | 72        | `transporter`  |
| Biological   | Enzymes               | DrugBank | GeneBank Gene IDs | 111       | `enzyme`       |
| Biological   | Pathways              | KEGG     | KEGG IDs          | 173       | `pathway`      |
| Phenotypic   | Treatment indications | SIDER    | CUI disease code  | 869       | `treatment`    |
| Label        | Side effects          | SIDER    | CUI disease code  | 1385      | `sideeffect`   |

- `feature_description`: folder that contains the description of each feature mentioned above.
	+ `chemical_feature_index.txt`
	+ `enzyme_feature_index.txt`
	+ `pathway_feature_index.txt`
	+ `target_feature_index.txt`
	+ `transporter_feature_index.txt`
	+ `treatment_feature_index.txt`
	+ `sideeffect_index.txt`


### Bio2RDF v1

We consider the list of drugs from Liu's dataset but not their features. Instead, we extract the features from the Knowledge Graph generated from Bio2RDF v1 DrugBank and SIDER datasets. This generates 30161 features for the 832 drugs, and we consider the same set of 1385 ADRs in Liu's dataset.

The results of our approach using this dataset are in _Table 6_ of our article.

**Folder:** `bio2rdf_v1/`
**Files:**
- `matrices.mat`: contains the design matrix `X` and the target matrix `y` that are passed to the machine learning methods.
- `X_column_labels.json`: enumerates the 30161 features label extracted from Bio2RDF v1 dataset.
- `X_row_labels.json`: list of 832 drugs with the ID in the rows of matrix `X`.
- `y_column_labels.json`: list of 1385 ADRs with the ID in the columns of matrix `y`


### Bio2RDF v2

We consider the list of drugs from Liu's dataset but not their features. Instead, we extract the features from the Knowledge Graph generated from Bio2RDF v2 DrugBank, SIDER and KEGG datasets. This generates 37368 features for the 832 drugs, and we consider the same set of 1385 ADRs in Liu's dataset.

The results of our approach using this dataset are in _Table 7_ of our article.

**Folder:** `bio2rdf_v2/`
**Files:**
- `matrices.mat`: contains the design matrix `X` and the target matrix `y` that are passed to the machine learning methods.
- `X_column_labels.json`: enumerates the 37368 features label extracted from Bio2RDF v2 dataset.
- `X_row_labels.json`: list of 832 drugs with the ID in the rows of matrix `X`.
- `y_column_labels.json`: list of 1385 ADRs with the ID in the columns of matrix `y`


### Liu + Bio2RDF v2

We also consider the integration of features from both Liu and Bio2RDF v2 datasets for the 832 drugs. This generates 40260 features in total, which are used to train the machine learning models.

The results of our approach using this dataset are in _Table 8_ of our article.

**Folder:** `liubio2rdf_v2/`
**Files:**
- `matrices.mat`: contains the design matrix `X` and the target matrix `y` that are passed to the machine learning methods.
- `X_column_labels.json`: enumerate the 40260 features label extracted from Bio2RDF v2 dataset.
- `X_row_labels.json`: list of 832 drugs with the ID in the rows of matrix `X`.
- `y_column_labels.json`: list of 1385 ADRs with the ID in the columns of matrix `y`


### SIDER 4 data set

We also performed an independent evaluation using the SIDER 4 dataset provided by Zhang et at. (2015), which comprises a subset of the drugs from Liu's dataset plus some newly added drugs.

The results of our approach using this dataset are in _Table 9_ of our article.

**Folder:** `sider4/`
**Files:**
- `sider_test_dataset.mat`: contains the features for the 309 test set drugs.
- `sider_train_dataset.mat`: contains the features for the 771 training set drugs.
- `sider_test_dataset_drug_list.csv`: enumerates the 309 drugs in the test set.
- `sider_train_dataset_drug_list.csv`: enumerates the 771 drugs in the training set.
- `feature_description`: folder that contains the description of each feature mentioned above.
	+ `enzyme_feature_index.txt`
	+ `pathway_feature_index.txt`
	+ `target_feature_index.txt`
	+ `transporter_feature_index.txt`
	+ `treatment_feature_index.txt`
	+ `sideeffect_index.txt`


### SIDER 4 + Bio2RDF v2 data sets

Similarly to what we did with Liu's dataset, we also consider the list of drugs in SIDER 4 dataset but not their features. Instead, we extract the features from the Knowledge Graph generated from Bio2RDF v2 DrugBank, SIDER and KEGG datasets. This generates 43843 features for the 1080 drugs (771 for training and 309 for testing), and we consider the same set of 5579 ADRs in SIDER 4 dataset.

The results of our approach using this dataset are in _Table 10_ of our article.

**Folder:** `sider4bio2rdf_v2_sider/`
**Files:**
- `matrices.mat`: contains the design matrices `X_train` and `X_test`, and the target matrices `y_train` and `y_test` that are passed to the machine learning methods.
- `X_train_row_labels.json`: list of 771 drugs in the training set with the ID in the rows of matrix `X_train`.
- `X_test_row_labels.json`: list of 309 drugs in the test set with the ID in the rows of matrix `X_test`.
- `y_column_labels.json`: list of 5579 ADRs with the ID in the columns of matrices `y_train` and `y_test`.


### SIDER 4 + Bio2RDF v2 + Aeolus data sets

Additionally, we evaluate the predictions on newly added ADRs which were discovered (reported) after the generation of SIDER 4 dataset. This relationships are published in the Aeolus dataset, which is generated from the FAERS reports. The matrices shape is as in SIDER 4, and we update the matrix `y_test` with drug-ADR relations from Aeolus.

The results of our approach using this dataset are in _Table 11_ of our article.

**Folder:** `sider4bio2rdf_v2_aeolus/`
**Files:**
- `matrices.mat`: contains the design matrices `X_train` and `X_test`, and the target matrices `y_train` and `y_test` that are passed to the machine learning methods.
- `X_train_row_labels.json`: list of 771 drugs in the training set with the ID in the rows of matrix `X_train`.
- `X_test_row_labels.json`: list of 309 drugs in the test set with the ID in the rows of matrix `X_test`.
- `y_column_labels.json`: list of 5579 ADRs with the ID in the columns of matrices `y_train` and `y_test`.

### Changelog

+ Version 0.0.2 (May 5, 2017 4:26 PM)
	- Adding table with detailed description of Liu's data set features
+ Version 0.0.1 (April 6, 2017 1:51 PM)
	- Adding description to all data sets
