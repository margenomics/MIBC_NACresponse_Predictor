# MIBC NAC Response Predictor

This repository contains the executable for the trained random forest machine learning models (RF-RW, RF-R and RF-WNT) presented in "Predicting response to cisplatin-based neoadjuvant chemotherapy for muscle-invasive bladder cancer: transcriptomic features outrank genomic biomarkers" by Acedo-Terrades et al. ([unpublished](https://www.medrxiv.org/content/10.1101/2024.06.28.24309634v1)). The ML models were created using the ML pipeline found in the following repository: https://github.com/EvolutionaryGenomics-GRIB/ML_Pipeline.

## Usage

Random forest trained models (RF-RW, RF-R and RF-WNT) are available in this repository in .joblib format. They can be utilized to predict response to cisplatin-based neoadjuvant chemotherapy (NAC) for muscle-invasive bladder cancer (MIBC) patients. The model were trained using formalin-fixed paraffin-embedded (FFPE) pre-treatment samples obtained after transurethral removal of bladder tumor (TURB) from our cohort of MIBC patients. RF-RW model was trained using RNA-Seq and WES data, while RF-R and RF-WNT was trained using only RNA-Seq data. 

**RF-RW**:
- WNT score
- Top10up score
- Top10dn score
- GROWTH FACTOR score
- CELL CYCLE REG score
- DNAH alterations
- KDM6A deletions

**RF-R**:
- WNT score
- Top10up score
- Top10dn score
- GROWTH FACTOR score
- CELL CYCLE REG score

**RF-WNT**:
- WNT score

In order to be able to run the model with new data a pandas dataframe containing all the features used during model training must be provided as an input. A detailed description of the variables required for each ML model can be found in the sheet "Supplementary Table 9" in the [Supplementary Table 9]. Please note that if any variable is missing, the model will not function properly. 

## Training results

After training, we evaluated it using different strategies. The first one was the classical train/test approach, where 30% of the data was reserved for testing purposes. However, due to the limited amount of data, we repeated this process 1000 times to ensure that the results were not influenced by chance. Furthermore, we employed bootstrap .632+ as an internal validation technique.

**RF-RW**
| Evaluation Type | AUC Score |
| --------------- | --------- |
| Train/test      | 0.82      |
| Bootstrap .632+ | 0.86      |

**RF-R**
| Evaluation Type | AUC Score |
| --------------- | --------- |
| Train/test      | 0.82      |
| Bootstrap .632+ | 0.85      |

**RF-WNT**
| Evaluation Type | AUC Score |
| --------------- | --------- |
| Train/test      | 0.76      |
| Bootstrap .632+ | 0.76      |

## New unseen data:
An example to test the AUC and other metrics of the models with new unseen data can be found here: https://github.com/EvolutionaryGenomics-GRIB/BLCA_ICI_Response_Predictor/blob/main/how_to_load_trained_model.ipynb 

## Contact:
- Sergio Vázquez Montes de Oca (svazquez1@researchmar.net)
- Ariadna Acedo-Terrades (aacedo@researchmar.net)
