# Article supplemental material

- **Title**: Knowledge Graphs and Multi-label Learning Models Facilitate Flexible and Efficient Prediction of Adverse Drug Reactions
- **Authors**: Emir Muñoz, Vít Novácek, Pierre-Yves Vandenbussche
- **Contact**: Emir Muñoz, [emir.munoz@insight-centre.org](mailto:emir.munoz@insight-centre.org)

This page provides a full description of the data sets used in this manuscript and that are made available. These data sets were used to evaluate all approaches reviewed in the manuscript.


## Download

All data sets files are publicly available for download at [https://figshare.com/s/d1a6f7c3dc10111037d5](https://figshare.com/s/d1a6f7c3dc10111037d5).


## Liu's data set

This data set was originally proposed by Liu et at. (2012), and then processed after by Zhang et at. (2015) for machine learning. Liu's data set contains 832 drugs with 2892 features, and 1385 ADRs.

The results obtained using this data set are in _Table 4_ and _Table 5_ of the article.

**Folder:** `liu/`
**Files:**
- `Liu_drug_lists.csv`: list of 832 drugs. The file is in `csv` format: `DrugBank ID, Drug Name, PubChem ID`.
- `Liu_dataset.mat`: a file with the features for each drug. The file uses MatLab `mat` format, and contains a dictionary with features name and values for each of the 832 drugs. Drugs are represented by binary vectors whose elements encode the presence or absence of each feature as 1 or 0, respectively.
- `feature_description/`: folder that contains the description of each feature mentioned above.
	+ `chemical_feature_index.txt` (See `pubchem_fingerprints.txt` for a description.)
	+ `enzyme_feature_index.txt`
	+ `pathway_feature_index.txt`
	+ `target_feature_index.txt`
	+ `transporter_feature_index.txt`
	+ `treatment_feature_index.txt`
	+ `sideeffect_index.txt`

The feature types, sources, and IDs are described as follows:

| Feature type | Specific feature      | Source   | ID                | Dimension | Dictionary key |
|--------------|-----------------------|----------|-------------------|-----------|----------------|
| Chemical     | Substructures         | PubChem  | Substructure Fingerprints* | 881       | `chemical`     |
| Biological   | Targets               | DrugBank | GeneBank Gene IDs | 786       | `Targets`       |
| Biological   | Transporters          | DrugBank | HGNC IDs          | 72        | `Transporters`  |
| Biological   | Enzymes               | DrugBank | GeneBank Gene IDs | 111       | `Enzymes`       |
| Biological   | Pathways              | KEGG     | KEGG IDs          | 173       | `Pathways`      |
| Phenotypic   | Treatment indications | SIDER    | CUI disease code  | 869       | `Treatment`    |
| Label        | Side effects          | SIDER    | CUI disease code  | 1385      | `side_effect`   |

> (*) A full description of PubChem Substructure Fingerprints can be found at [ftp://ftp.ncbi.nlm.nih.gov/pubchem/specifications/pubchem_fingerprints.txt](ftp://ftp.ncbi.nlm.nih.gov/pubchem/specifications/pubchem_fingerprints.txt)


## Bio2RDF v1

We consider the list of drugs from Liu's data set but not their features. Instead, we extract the features from the Knowledge Graph generated from Bio2RDF v1 DrugBank and SIDER data sets. This generates 30161 features for the 832 drugs, and we consider the same set of 1385 ADRs in Liu's data set.

The results obtained using this data set are in _Table 6_ of the article.

**Folder:** `bio2rdf_v1/`
**Files:**
- `matrices.mat`: contains the design matrix `X` and the target matrix `y` that are passed to the machine learning methods.
- `X_column_labels.json`: enumerates the 30161 features label extracted from Bio2RDF v1 data set.
- `X_row_labels.json`: list of 832 drugs with the ID in the rows of matrix `X`.
- `y_column_labels.json`: list of 1385 ADRs with the ID in the columns of matrix `y`.


## Bio2RDF v2

We consider the list of drugs from Liu's data set but not their features. Instead, we extract the features from the Knowledge Graph generated from Bio2RDF v2 DrugBank, SIDER and KEGG data sets. This generates 37368 features for the 832 drugs, and we consider the same set of 1385 ADRs in Liu's data set.

The results obtained using this data set are in _Table 7_ of the article.

**Folder:** `bio2rdf_v2/`
**Files:**
- `matrices.mat`: contains the design matrix `X` and the target matrix `y` that are passed to the machine learning methods.
- `X_column_labels.json`: enumerates the 37368 features label extracted from Bio2RDF v2 data set.
- `X_row_labels.json`: list of 832 drugs with the ID in the rows of matrix `X`.
- `y_column_labels.json`: list of 1385 ADRs with the ID in the columns of matrix `y`.


## Liu + Bio2RDF v2

We also consider the integration of features from both Liu and Bio2RDF v2 data sets for the 832 drugs. This generates 40260 features in total, which are used to train the machine learning models.

The results obtained using this data set are in _Table 8_ of the article.

**Folder:** `liubio2rdf_v2/`
**Files:**
- `matrices.mat`: contains the design matrix `X` and the target matrix `y` that are passed to the machine learning methods.
- `X_column_labels.json`: enumerate the 40260 features label extracted from Bio2RDF v2 data set.
- `X_row_labels.json`: list of 832 drugs with the ID in the rows of matrix `X`.
- `y_column_labels.json`: list of 1385 ADRs with the ID in the columns of matrix `y`.


## SIDER 4 data set

We also performed an independent evaluation using the SIDER 4 data set provided by Zhang et at. (2015), which comprises a subset of the drugs from Liu's data set plus some newly added drugs.

### Download original files

> Zhang, Wen; Liu, Feng; Luo, Longqiang; Zhang, Jingxia (2015): Predicting drug side effects by multi-label learning and ensemble learning. figshare.
http://doi.org/10.6084/m9.figshare.c.3608738
Retrieved: 12 34, May 09, 2017 (GMT)

The results obtained using this data set are in _Table 9_ of the article.

**Folder:** `sider4/`
**Files:**
- `sider_test_dataset.mat`: contains the features for the 309 test set drugs.
- `sider_train_dataset.mat`: contains the features for the 771 training set drugs.
- `sider_test_dataset_drug_list.csv`: enumerates the 309 drugs in the test set.
- `sider_train_dataset_drug_list.csv`: enumerates the 771 drugs in the training set.
- `feature_description/`: folder that contains the description of each feature mentioned above.
	+ `enzyme_feature_index.txt`
	+ `pathway_feature_index.txt`
	+ `target_feature_index.txt`
	+ `transporter_feature_index.txt`
	+ `treatment_feature_index.txt`
	+ `sideeffect_index.txt`

The feature types, sources, and IDs are described as follows:

| Feature type | Specific feature      | Source   | ID                | Dimension | Dictionary key |
|--------------|-----------------------|----------|-------------------|-----------|----------------|
| Chemical     | Substructures         | PubChem  | Substructure Fingerprints* | 881       | `chemical`     |
| Biological   | Targets               | DrugBank | GeneBank Gene IDs | 1046      | `Targets`       |
| Biological   | Transporters          | DrugBank | HGNC IDs          | 96        | `Transporters`  |
| Biological   | Enzymes               | DrugBank | GeneBank Gene IDs | 160       | `Enzymes`       |
| Biological   | Pathways              | KEGG     | KEGG IDs          | 268       | `Pathways`      |
| Phenotypic   | Treatment indications | SIDER    | CUI disease code  | 2537      | `Treatment`    |
| Label        | Side effects          | SIDER    | CUI disease code  | 5579      | `side_effect`   |

> (*) A full description of PubChem Substructure Fingerprints can be found at [ftp://ftp.ncbi.nlm.nih.gov/pubchem/specifications/pubchem_fingerprints.txt](ftp://ftp.ncbi.nlm.nih.gov/pubchem/specifications/pubchem_fingerprints.txt)


## SIDER 4 + Bio2RDF v2 data sets

Similarly to what we did with Liu's data set, we also consider the list of drugs in SIDER 4 data set but not their features. Instead, we extract the features from the Knowledge Graph generated from Bio2RDF v2 DrugBank, SIDER and KEGG data sets. This generates 43843 features for the 1080 drugs (771 for training and 309 for testing), and we consider the same set of 5579 ADRs in SIDER 4 data set.

The results obtained using this data set are in _Table 10_ of the article.

**Folder:** `sider4bio2rdf_v2_sider/`
**Files:**
- `matrices.mat`: contains the design matrices `X_train` and `X_test`, and the target matrices `y_train` and `y_test` that are passed to the machine learning methods.
- `X_train_row_labels.json`: list of 771 drugs in the training set with the ID in the rows of matrix `X_train`.
- `X_test_row_labels.json`: list of 309 drugs in the test set with the ID in the rows of matrix `X_test`.
- `y_column_labels.json`: list of 5579 ADRs with the ID in the columns of matrices `y_train` and `y_test`.


## SIDER 4 + Bio2RDF v2 + Aeolus data sets

Additionally, we evaluate the predictions on newly added ADRs which were discovered (reported) after the generation of SIDER 4 data set. This relationships are published in the Aeolus data set, which is generated from the FAERS reports. The matrices shape is as in SIDER 4, and we update the matrix `y_test` with drug-ADR relations from Aeolus.

The results obtained using this data set are in _Table 11_ of the article.

**Folder:** `sider4bio2rdf_v2_aeolus/`
**Files:**
- `matrices.mat`: contains the design matrices `X_train` and `X_test`, and the target matrices `y_train` and `y_test` that are passed to the machine learning methods.
- `X_train_row_labels.json`: list of 771 drugs in the training set with the ID in the rows of matrix `X_train`.
- `X_test_row_labels.json`: list of 309 drugs in the test set with the ID in the rows of matrix `X_test`.
- `y_column_labels.json`: list of 5579 ADRs with the ID in the columns of matrices `y_train` and `y_test`.


## Changelog

+ Version 0.0.2 (May 9, 2017 1:50 PM)
	- Adding table with detailed description of Liu's and SIDER 4 data sets features
+ Version 0.0.1 (April 6, 2017 1:51 PM)
	- Adding description to all data sets

## References

* Liu M, Wu Y, Chen Y, et al. Large-scale prediction of adverse drug reactions using chemical, biological, and phenotypic properties of drugs. Journal of the American Medical Informatics Association. 2012.
* ZhangW, Liu F, Luo L, et al. Predicting drug side effects bymulti-label learning and ensemble learning. BMC bioinformatics. 2015;16:1.
* Zhang W, Chen Y, Tu S, et al. Drug side effect prediction through linear neighborhoods and multiple data source integration. In: 2016 IEEE International Conference on Bioinformatics and Biomedicine (BIBM); 2016. p. 427–434.
* Muñoz E, Novacek V, Vandenbussche PY. Using drug similarities for discovery of possible adverse reactions. In: AMIA 2016, American Medical Informatics Association Annual Symposium. American Medical Informatics Association; 2016. p. 924–933.