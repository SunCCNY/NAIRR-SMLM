# NAIRR-SMLM
This site dedicates to AI research, training, and education. 

It provides datasets for AI training, validating and testing as well as information-theoretical benchmarking for trainined AI in single molecule localization microscopy (SMLM). 

It can also evaluate and benchmark other types of spatiotemporal localization algorithms. 

# Introduction 
The SMLM technique, including PALM [1], FPALM [2], STORM [3] and dSTORM [4], was first invented in 2006 and won the 2014 Nobel Prize in Chemistry. The SMLM technique circumvents the longstanding light diffraction, provides superresolution imaging of biological samples at the nanoscale, and has been significantly impacting on biomedical research. 

## SMLM 

The figure below shows a diagram of an SMLM system. Ultrastructure of a biological sample is labeled with fluorescent molecules (emitters). The emitters are excited by lasers and randomly emits fluorescence that passes through an optical system. A camera acquires a data movie consisting of a large number of data frames. Each data frame records the spots of light diffraction from the activated emitters plus the background fluorescence noise and circuitry thermal noise. A localization algorithm estimates the emitter locations, representing a superresolution image of the ultrastructure of the biological sample. 

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/Docs/Fig-SMLM-system-3.jpg)

## Localization algorithm
A localization algorithm plays a critical role in mining the information of emitter locations from a large number of data frames to reconstruct a one-shot superresolution image. Hence, the localization algorithm must be informationally efficient and computationally efficient.  

## AI
Due to its highly informational and computational efficiency, an AI built on neural network and deep learning is particularly suitable to serve as a localization algorithm in SMLM. 

# Datasets
## Type of datasets
In each case, there are three datasets for AI training, validating and testing, respectively.

## Components 
Each dataset consists of two components:

* A set of emitter locations (2D/3D coordinates) representing the original image of biological ultrastrucutre.
*
* A data movie consisting of a sequence of data frames synthesized with the emitter locations according to the model of data movie [5-8]. 

## Model of data movie
The model of data movie consists of two sub-models: 

(1) the model of a data frame [5, 6]; 

(2) the model of emitter photoactivation processes [7, 8]. 

All parameters used to synthesize the data movies are defined in [5-8]. 

# Training and testing of AI
## Training
Given a training dataset, AI can be trained by supervised learning where 

(1) the input is the data movie; 

(2) the desired output is the set of corresponding emitter locations. 

## Testing 
Given a testing dataset, a trained AI can be tested where 

(1) the input is the data movie of the testing dataset

(2) the output is a set of estimated emitter locations, i.e., the reconstructed superresolution image by the AI. 

# Evaluating and Benchmarking
## Evaluating
The performance of a trained AI can be evaluated by the universal quality metrics of root mean square minimum distance (RMSMD) [7], RMSMD with partition (RMSMD-P) [9], and root mean square error (RMSE) with partition (RMSE-P) [9]. Specifically, 

(1) Given the set of emitter locations in the testing dataset and the AI outputted set of emitter locations, their error can be calculated in terms of RMSMD. 

(2) If the number of frames that each emitter is activated in the testing data movie is further given, the RMSMD-P and RMSE-P can be calculated. 

## Benchmarking
The performance of a trained AI can also be benchmarked by the unbiased Gaussian information achieving for a movie (UGIA-M) estimator [10] and the unbiased Gaussian information-achieving for a frame  (UGIA-F) estimator [7]. Both UGIA-M and UGIA-F estimators are theoretical estimators derived from the Fisher information. The UGIA-M estimator achieves the Fisher information of the data movie and the UGIA-F estimator achieves the Fisher information of each data frame. 

Given a testing dataset, the UGIA-M estimator can generate a set of estimated emitter locations, and the RMSMD, RMSMD-P and RMSE-P can be calculated, which can be used to benchmark the performance of AI. 

Similarly, given a testing dataset, the UGIA-F estimator can generate a set of estimated emitter locations, and the RMSMD, RMSMD-P and RMSE-P can be calculated, which can be used to benchmark the performance of AI. 

# Acknowledgments
This work was partly supported by the NSF under Grant Number CCF-2313072 and the Army Research Office under Grant Number W911NF-23-1-0189. The views and conclusions contained in this document are those of the author and should not be interpreted as representing the official policies, either expressed or implied, of the Army Research Office or the U.S. Government. The U.S. Government is authorized to reproduce and distribute reprints for Government purposes notwithstanding any copyright notation.

# References
[1] E. Betzig, G. H. Patterson, R. Sougrat, O. W. Lindwasser, S. Olenych, J. S. Bonifacino, M. W. Davidson, J. Lippincott-Schwartz, and H. F. Hess, "Imaging intracellular fluorescent proteins at nanometer resolution," Science, 313(5793), 1642–1645(2006). 

[2] S. T. Hess, T. P. Girirajan, and M. D. Mason, "Ultra-high resolution imaging by fluorescence photoactivation localization microscopy," Biophys. J., 91(11), 4258–4272(2006). 

[3] M. J. Rust, M. Bates, and X. Zhuang, "Sub-diffraction-limit imaging by stochastic optical reconstruction microscopy (STORM)," Nat. Methods, 3(10), 793-796(2006). 

[4] M. Heilemann, S. v. Linde , M. Schüttpelz, R. Kasper, B. Seefeldt, A. Mukherjee, P. Tinnefeld, and M. Sauer, "Subdiffraction‐resolution fluorescence imaging with conventional fluorescent probes," Angew. Chem. Int. Ed., 47(33), 6172–6176(2008). 

[5] Y. Sun, "Localization precision of stochastic optical localization nanoscopy using single frames," J. Biomed. Optics, 18(11), 111418-14(2013). 

[6] Y. Sun, and Y. Guan, "Effect of unknown emitter intensities on localization accuracy in stochastic optical localization nanoscopy using single frames," JOSA A, 38(12), 1830-1840(2021). 

[7] Y. Sun, "Root mean square minimum distance as a quality metric for stochastic optical localization nanoscopy images," Sci. Reports, 8(1), 17211(2018). 

[8] Y. Sun, "Markov chain models of emitter activations in single molecule localization microscopy," Optics Express, 32(19), 33779-33794(2024).

[9] Y. Sun, "Partition of estimated locations: an approach to accurate quality metrics for stochastic optical localization nanoscopy," JOSA A, 39(12), 2307-2315(2022).

[10] Y. Sun, "Spatiotemporal resolution as an information theoretical property of stochastic optical localization nanoscopy," 2020 Quantitative BioImaging Conf. (QBI2020), Oxford, UK, Jan. 6-9, 2020. 

# Contact
Yi Sun, Electrical Engineering Department, Nanoscopy Laboratory, The City College of City University of New York, New York, NY 10031, USA. E-mail: ysun@ccny.cuny.edu
