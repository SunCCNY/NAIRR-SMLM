# NAIRR-SMLM
This site provides datasets and benchmark for AI training and validation in single molecule localization microscopy (SMLM). Other types of spatiotemporal localization algorithms can also be benchmarked. 

# Introduction 
The SMLM technique, including PALM [1], FPALM [2], STORM [3] and dSTORM [4], was first invented in 2006 and won the 2014 Nobel Prize in Chemistry. The SMLM technique circumvents the longstanding light diffraction, provides superresolution imaging of biological samples at the nanoscale, and has been significantly impacting on biomedical research. 

## SMLM 

Fig. 1 shows a diagram of an SMLM system. Ultrastructure of a biological sample is labeled with fluorescent molecules (emitters). The emitters are excited by lasers and randomly emits fluorescence that passes through an optical system. A camera acquires a data movie consisting of a large number of data frames. Each data frame records the spots of light diffraction from the activated emitters plus the background fluorescence noise and circuitry thermal noise. A localization algorithm estimates the emitter locations, representing a superresolution image of the ultrastructure of the biological sample. 

## Localization algorithm
The localization algorithm plays an important role in reconstructing the superresolution image from the 


# Datasets
Each dataset consists of two part: (1) a data movie consisting of a sequence of data frames, and (2) a set of coordinates of emitter locations that are used in generation of the data movie. 

# Training of AI
AI can be trained using a dataset: (1) the data movie is the input of AI, and (2) the set of emitter locations is the output of AI. 

# 

# References
[1] E. Betzig, G. H. Patterson, R. Sougrat, O. W. Lindwasser, S. Olenych, J. S. Bonifacino, M. W. Davidson, J. Lippincott-Schwartz, and H. F. Hess, “Imaging intracellular fluorescent proteins at nanometer resolution,” Science, 313(5793), 1642–1645(2006). 

[2] S. T. Hess, T. P. Girirajan, and M. D. Mason, “Ultra-high resolution imaging by fluorescence photoactivation localization microscopy,” Biophys. J., 91(11), 4258–4272(2006). 

[3] M. J. Rust, M. Bates, and X. Zhuang, “Sub-diffraction-limit imaging by stochastic optical reconstruction microscopy (STORM),” Nat. Methods, 3(10), 793-796(2006). 

[4] M. Heilemann, S. v. Linde , M. Schüttpelz, R. Kasper, B. Seefeldt, A. Mukherjee, P. Tinnefeld, and M. Sauer, “Subdiffraction‐resolution fluorescence imaging with conventional fluorescent probes,” Angew. Chem. Int. Ed., 47(33), 6172–6176(2008). 

