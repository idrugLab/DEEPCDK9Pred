# **Environment**

The most important python packages are:
- python == 3.6.7
- pytorch == 1.2.0
- torch == 0.4.1
- tensorboard == 1.13.1
- rdkit == 2019.09.3
- scikit-learn == 0.22.2.post1
- hyperopt == 0.2.5
- numpy == 1.18.2

For using our model more conveniently, we provide the environment file *<environment.txt>* to install environment directly.


---
# **CDK9 Pred**
### 1. Data
Data file is ***data/CDK9.csv***

### 2. Model
The best trained model is ***model_save/model.pt***

### 3. Prediction with trained models
For example, to predict new molecules (in *test.csv*) with trained CDK9 model, use the command:

`python predict.py  --predict_path test.csv  --model_path model_save/model.pt  --result_path result_CDK9.csv`

The result file contains the prediction of CDK9. 

E.g.

Smiles|labels
:-:|:-:
BrC=1C=Cc2n(C=1)c(cn2)\C=N\N(S(=O)(=O)c1cc([N+](=O)[O-])ccc1C)C|0.731
Brc1c(c2nc(n3CCCc(c23)c1Br)N1CCNCC1)C|0.174
Brc1c2[nH]c3c(c2ccc1)c(nc1c3cccc1)C(O)=O|0.593


---
# **Commands of FP-GNN**

### **1. Train**
Use train.py

Args:
  - data_path : The path of input CSV file. *E.g. input.csv*
  - dataset_type : The type of dataset. *E.g. classification  or  regression*
  - save_path : The path to save output model. *E.g. model_save*
  - log_path : The path to record and save the result of training. *E.g. log*

E.g.

`python train.py  --data_path data/test.csv  --dataset_type classification  --save_path model_save  --log_path log`

### **2. Predict**
Use predict.py

Args:
  - predict_path : The path of input CSV file to predict. *E.g. input.csv*
  - result_path : The path of output CSV file. *E.g. output.csv*
  - model_path : The path of trained model. *E.g. model_save/model.pt*

E.g.

`python predict.py  --predict_path data/test.csv  --model_path model_save/test.pt  --result_path result.csv`

### **3. Hyperparameters Optimization**
Use hyper_opti.py

Args:
  - data_path : The path of input CSV file. *E.g. input.csv*
  - dataset_type : The type of dataset. *E.g. classification  or  regression*
  - save_path : The path to save output model. *E.g. model_save*
  - log_path : The path to record and save the result of hyperparameters optimization. *E.g. log*

E.g.

`python hyper_opti.py  --data_path data/test.csv  --dataset_type classification  --save_path model_save  --log_path log`

### **4. Interpretation of Fingerprints**
Use interpretation_fp.py

Args:
  - predict_path : The path of input CSV file. *E.g. input.csv*
  - model_path : The path of trained model. *E.g. model_save/model.pt*
  - result_path : The path of result. *E.g. result.txt*

E.g.

`python interpretation_fp.py  --predict_path test.csv  --model_path model_save/test.pt  --result_path result.txt`

### **5. Interpretation of Graph**
Use interpretation_graph.py

Args:
  - predict_path : The path of input CSV file. *E.g. input.csv*
  - model_path : The path of trained model. *E.g. model_save/model.pt*
  - figure_path : The path to save figures of graph interpretation. *E.g. figure*

E.g.

`python interpretation_graph.py  --predict_path test.csv  --model_path model_save/test.pt  --figure_path figure`


---
# **Data Standard of FP-GNN**

We provide the three public benchmark datasets used in our study: *<Data.rar>*

Or you can use your own dataset:
### 1. For training
The dataset file should be a **CSV** file with a header line and label columns. E.g.
```
SMILES,CYP_1a2
O(C(=O)C(=O)NCC(OC)=O)C,0
FC1=CNC(=O)NC1=O,0
...
```
### 2. For predicting
The dataset file should be a **CSV** file with a header line and without label columns. E.g.
```
SMILES
O(C(=O)C(=O)NCC(OC)=O)C
FC1=CNC(=O)NC1=O
...
```
### 3. For interpreting fingerprints
The dataset file should be a **CSV** file with a header line and label columns. E.g.
```
SMILES,CYP_1a2
O(C(=O)C(=O)NCC(OC)=O)C,0
FC1=CNC(=O)NC1=O,0
...
```
### 4. For interpreting molecular graphs
The dataset file should be a **CSV** file with a header line and without label columns. E.g.
```
SMILES
O(C(=O)C(=O)NCC(OC)=O)C
FC1=CNC(=O)NC1=O
...
```

