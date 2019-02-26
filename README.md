# *iLearn*: an integrated platform and meta-learner for feature engineering and machine learning analysis and modeling of DNA, RNA and protein sequence data

*iLearn* is a comprehensive Python-based toolkit, integrating feature extraction/calculation, feature analysis (clustering, feature selection, normalization and dimension reduction), predictor construction, best descriptor/model selection, ensemble learning and performance evaluation for DNA, RNA and protein sequences. *iLearn* is capable of calculating and extracting a wide spectrum of 18 major sequence encoding schemes that encompass 53 different types of feature descriptors for protein sequences, and also can be used to extract 6 major encoding schemes which encompass 26 and 18 different types of feature descriptors for DNA and RNA sequences. Developed from *iFeature*, *iLearn* also integrates five kinds of frequently-used feature clustering algorithms, five feature selection algorithms, and three dimensionality reduction algorithms. Four output feature formats are supported by iLearn, which can be directly used and processed in other tools. Furthermore, five commonly used machine learning algorithms are provided, including SVM (Support Vector Machine), RF (Random Forest), ANN (Artificial Neutral Network), KNN (K-Nearest Neighbours) and LR (Logistic Regression). In order to facilitate users’ interpretability of outcomes, the clustering and dimensionality reduction results generated by iLearn can be further visualized in form of scatter diagrams, while the cross-validation result can be visualized in the form of ROC and PRC curves. This makes iLearn a unique and powerful tool that greatly facilitates feature generation, analysis, training and benchmarking of machine-learning models and predictions.
# Installation

  - Download *iLearn* by 
  ```sh
  git clone https://github.com/Superzchen/iLearn
  ```
  *iLearn* is an open-source Python-based toolkit, which operates depending on the Python environment (Python Version 3.0 or above) and can be run on multi-OS systems (such as Windows, Mac and Linux operating systems). Before running *iLearn*, user should make sure all the following packages are installed in their Python environment: sys, os, shutil, scipy, argparse, collections, platform, math, re, numpy (1.13.1), sklearn (0.19.1), matplotlib (2.1.0), and pandas (0.20.1). For convenience, we strongly recommended users to install the Anaconda Python 3.0 version (or above) in your local computer. The software can be freely downloaded from https://www.anaconda.com/download/.
# For users who want to use *iLearn* package :
cd to the iLearn folder. All the functions regarding feature extraction, feature or sample clustering and feature selection analysis, normalization, dimension reduction and predictor construction can be executed through sixteen main programs. 
The sixteen main programs include:
* `iLearn-protein-basic.py` Extracting 37 different types of feature descriptors for protein sequences.
* `iLearn-protein-PseKRAAC.py` Extracting the 16 types of pseudo K-tuple reduced amino acid composition (PseKRAAC) feature for protein sequence.
* `iLearn-nucleotide-basic.py` Extracting 14 different types of feature descriptors for nucleotide sequences.
* `iLearn-nucleotide-acc.py` Extracting 6 different types of autocorrelation descriptors for nucleotide sequences.
* `iLearn-nucleotide-Pse.py` Extracting 6 different types of pseudo-k-tuple composition descriptors for nucleotide sequences.
* `iLearn-clustering.py` Running the feature or sample clustering algorithms.
* `iLearn-feature-normalization.py` Running the feature normalization algorithms.
* `iLearn-feature-selectior.py` Running the feature selection algorithms.
* `iLearn-dimension-reduction.py` Running the dimension reduction algorithms.
* `iLearn-ML-SVM.py` Running the SVM algorithm.
* `iLearn-ML-RF.py` Running the RF algorithm.
* `iLearn-ML-MLP.py` Running the ANN algorithm.
* `iLearn-ML-LR.py` Running the LR algorithm.
* `iLearn-ML-KNN.py` Running the KNN algorithm.
* `iLearn-descriptor-estimater.py` Estimating the prediction ability for the specified descriptors.
* `iLearn-auto-pipline.py` Running the iLearn pipeline.

Furthermore, the *iLearn* package contains other Python scripts to generate the position-specific scoring matrix (PSSM) profiles, predicted protein secondary structure and predicted protein disorder, which have also been often used to improve the prediction performance of machine learning-based classifiers in conjunction with sequence-derived information included in the `scripts` directory.
# Examples to run the scripts in *iLearn*. 
All files in the example commands can be found in the `examples` directory. 
### Input and output of *iLearn*
The input for *iLearn* is a set of DNA, RNA or protein sequences in a special FASTA format. The FASTA header consists of three parts: part 1, part 2 and part 3, which are separated by the symbol ‘|’. Part 1 is the sequence name. Part 2 is the sample category information, which can be filled with any integer. For instance, users may use 1 to indicate the positive samples and -1 or 0 to represent the negative samples for a binary classification task, or use 0, 1, 2, … to represent the different class in multiclass classification tasks. Part 3 indicates the role of the sample, where e.g. “training” would indicate that the corresponding sequence would be used as the training set for K-fold validation test, and “testing” that the sequence would be used as the independent set for independent testing.  

### Example 1, Extracting Descriptors for DNA Sequences
Running the following command to obtain the `Kmer` descriptor:
```sh
python iLearn-nucleotide-basic.py --file examples/DNA_training.txt --method Kmer --format svm
```
Generally, users can get the parameters by specifying the parameter '--help'

### Example 2, Feature Analysis Using *iLearn*
K-Means clustering (kmeans)
```sh
python iLearn-clustering.py --file examples/code_for_cluster.txt --method kmeans --sof sample --nclusters 2
```
Feature normalization
```sh
python iLearn- feature-normalization.py --file examples/ DNA_code_training.txt --method ZScore --format svm
``` 
Feature selection
```sh
python iLearn-feature-selectior.py --file examples/DNA_code_testing.txt --method CHI2 --format svm
``` 
Dimension reduction
```sh
python iLearn-dimension-reduction.py --file examples/DNA_code_testing.txt --method pca --format svm
```

### Example 3, Predictor Construction Using *iLearn*
Support Vector Machine (SVM) algorithm
```sh
python iLearn-ML-SVM.py --train examples/DNA_code_training.txt --indep examples/DNA_code_testing.txt --auto --format svm --batch 0.5 --out SVM
```

### Example 4, Descriptor and Manchine Learning algorithm Performance Evaluation
For a prediction task, the iLearn package can select out the descriptor with the best performance by using the ‘iLearn-descriptor-estimater.py’.
```sh
python iLearn-descriptor-estimater.py --config
```

### Example 5, *iLearn* pipeline
All the individual functionalities in iLearn can be implemented as a pipeline by using the ‘iLearn-auto-pipeline.py’ script.
```sh
python iLearn-auto-pipline.py --config
```

For more examples and advanced usage of *iLearn*, please refer the iLearnManual.pdf for more help.

# Citation：
If you find *iLearn* useful, please kindly cite the following paper:

Chen Z, Zhao P, Li F, Leier A, Marquez-Lago TT, Leier A, Webb GI, Revote J, Powell DR, Akutsu T, Webb GI, Smith AI, Daly RJ* , Chou KC* , Song J* . *iLearn*: an integrated platform and meta-learner for feature engineering and machine learning analysis and modeling of DNA, RNA and protein sequence data. 2019, submitted for publication.
