# 3DAS_HD

## Leaderboard in benchmarking and evaluating
The leaderboard will be updated after a submission. The dataset in Benchmark is used in the benchmarking and evaluating. 

| Algorithm |Algorithm Type|Localization Type|RMSMD (nm)|
|----------:|-------------:|----------------:|---------:|
|UGIA-M     |Theoretical   |Joint frames      |2.21      |
|ThunderSTORM |Conventional |Frame by frame|73.55 |
|DECODE |AI |Frame by frame|139.40|
|3D-DAOSTORM|Conventional|Frame by frame|149.02 |
|UGIA-F     |Theoretical   |Frame by frame   |510.84     |
|QC-STORM   |Conventional|Frame by frame|830.20 |

## 1. Introduction 

### Purposes
To provide 

* AI training datasets
  
* AI validating datasets 

* AI testing datasets

* Evaluating and benchmarking AI performance by the UGIA-F and UGIA-M estimators that achieve the Fisher information of single frames and entire data movie, respectively.
  
* Evaluating and benchmarking performance of conventional spatiotemporal localization algorithms by the UGIA-F and UGIA-M estimators.

### Imaging system
3D imaging, astigmatic (AS) point spread function (PSF), and high density (HD) of emitters. 

### AI input and output
AI can be trained, validated, tested, and benchmarked by a pair of input and output datasets. 

**Input:** A data frame consisting of PSFs for activated emitters through light diffraction. The data frames are generated by using the universal model of data frames in [1] [2]. The emitter activation processes in testing and benchmarking are modeled by the Markov chain in [3]-[4]. All paramters are defined in [1]-[7]. 

An example of data frame is shown below. 

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/3DAS_HD/Docs/Fig3DAS_HD_Train_Frame_10.png)

**Output**: A set of 3D coordinates, each being an emitter's location, used in generating  the data frame in the input. An example of emitter locations is shown below by the red dots over the corresponding data frame above. 

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/3DAS_HD/Docs/Fig3DAS_HD_Train_Frame_10_Emitters.png)

## 2. Training datasets
Training datasets are in the folder: **Train** 

The training dataset consists of a data movie and the list of activated emitters in each frame. 

### Frame by frame datasets
Datasets are stored as individual frames. 

**3DAS_HD_Train_Frame.zip:** The data movie of N frames used as input in training of AI. 

The 10th frame with the activated emitters are shown above. 

**3DAS_HD_Train_xy.zip:** N txt files each containing the list of activated emitter locations of 3D coordinates (x,y,z) in nm in the row-by-row format, e.g.

2.6071158e+03   3.1212930e+02  -2.7390953e+02

2.8985342e+03   8.9119430e+02   3.7647423e+02

... ...

The input data frame "3DAS_HD_Train_Frame_n.tif" and the corresponding output emitter-location file "3DAS_HD_Train_xyz_n.txt" have the same frame index n. 

### Movie datatsets
Datasets are also concisely stored as an entire data movie of all frames as below.  

**3DAS_HD_Train_Frame.tif:** N data frames. 

**3DAS_HD_Train_xy.csv:** All activated emitter locations. 

### Data movie

The main parameters of data movie are as follows. 
 
|Parameter |Variable and value| Unit| 
|:-----|:-----|:-----| 
|Number of frames |N = 1000 |frames | 
|Field of view (FOV) |[0, Lx] x [0, Ly] x [-Lz, Lz] = [0, 3200] x [0, 3200] x [-400, 400]|nm^3| 
|Pixel size |Dx = 100, Dy = 100 | nm | 
|Frame size |Kx = 32, Ky = 32 |pixels | 

### Emitters

The emitter locations are shown below. 

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/3DAS_HD/Docs/Fig3DAS_HD_Train_xy.png)

The emitters are independently and identically activated frame by frame according to a Markov chain with the following parameters [4]. 

|Parameter |Variable and value| Unit| 
|:-----|:-----|:-----| 
|Number of emitters |M = 640 |Ground-truth emitters | 
|Emitter density on camera plane |D = 6.25|emitters/um^2| 
|Emitter distribution| Random and uniform in FOV| | 
|Emitter activation| Markov chain frame by frame | |
|Mean deactivation time |t0 = 0.50 | sec |
|Mean activation time |t1 = 0.04 | sec |
|Mean photoactivatable time| t = 10.0 | sec |

## 3. Validating datasets

Validating datasets are in the folder: **Validate** 

The validating datasets, consisting of N = 500 pairs of input and output files, are generated using the same parameters as those of the training datasets. 

## 4. Testing datasets

Testing datasets are in the folder: **Test**  

Now AI is supposed to have been trained and to be tested. 

The testing datasets are a data movie where emitters are located on a 3D helix. The parameters of each frame are listed below.  

|Parameter |Variable and value| Unit|
|:-----|:-----|:-----|
|Number of frames |N = 1000 |frames |
|Number of emitters |M = 400 |emitters in specimen |
|Field of view (FOV) |[0, Lx] x [0, Ly] x [-Lz, Lz] = [0, 6400] x [0, 6400] x [-400, 400]|nm^3| 
|Pixel size |Dx = 100, Dy = 100 | nm |
|Frame size |Kx = 64, Ky = 64 |pixels |
|Emitter distribution| Helix| |
|Emitter distance |eD = 45|nm |

The ground-truth emitter locations are shown below. 

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/3DAS_HD/Docs/Fig3DAS_HD_Test_xyz.png)

The 10th frame is shown below.

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/3DAS_HD/Docs/Fig3DAS_HD_Test_Frame_10.png)

The emitter locations of white dots on the helix and the activated emitters of red dots over the 10th frame is shown below. 

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/3DAS_HD/Docs/Fig3DAS_HD_Test_Frame_10_Emitters.png)

**Input:** The N frames are input to AI. 

**Output:** AI is supposed to output a list of estimated emitter locations, representing a superresolution SMLM image of the helix. 

## 5. Benchmarking and evaluating 
Benchmarking datasets are in the folder: **Benchmark** 

For the purpose of benchmarking and evaluating, the dataset of ground-truth emitter locations is not provided. 

### Procedure of evaluating
A participant shall run a participating localization algorithm over the data movie in Benchmark to estimate a list of emitter locations. After the participant submits the list of estimated location, we will calculate its RMSMD in comparison of the ground-truth locations. The result will be posted in the leaderboard. 

### Dataset
The emitters with the same adjacent distance are located on a circle. The data movie for benchmarking is generated using the same parameters of Testing with the following parameters.  

|Parameter |Variable and value| Unit|
|:-----|:-----|:-----|
|Number of frames |N = 1000 |frames |
|Number of emitters |M = 150 |emitters in specimen |
|Emitter distribution| Circle | |
|**Emitter distance**|**eD = 45**|**nm** |

The ground-truth emitter locations are shown below. 

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/3DAS_HD/Docs/Fig3DAS_HD_Benchmark_xyz.png)

The 10th frame is shown below.

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/3DAS_HD/Docs/Fig3DAS_HD_Benchmark_Frame_10.png)

The emitter locations of white dots on the helix and the activated emitters of red dots over the 10th frame is shown below. 

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/3DAS_HD/Docs/Fig3DAS_HD_Benchmark_Frame_10_Emitters.png)

### Benchmarking and evaluating
The quality of the reconstructed SMLM is **benchmarked** by the UGIA-F [1-3] and UGIA-M [6] estimators that achieve the Fisher information of data movie and single frames, respectively. Both UGIA-F and UGIA-M estimators are theoretical estimators. 

The quality metrics of the root mean square minimum distance (RMSMD) [3], RMSMD-P, and RMSE-P [5] are used to **evaluate** the accuracy of reconstructed SMLM image in comparison with the ground truth emitter locations.

### Performance of UGIA-F and UGIA-M estimators

**UGIA-F estimator:** The UGIA-F estimator outputs an SMLM image as shown below. Its quality in terms of RMSMD is given in the table below. 

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/3DAS_HD/Docs/Fig3DAS_HD_Benchmark_xyz_UGIA-F.png)

**UGIA-M estimator:** The UGIA-M estimator outputs an SMLM image as shown below. Its quality in terms of RMSMD is given in the table below. 

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/3DAS_HD/Docs/Fig3DAS_HD_Benchmark_xyz_UGIA-M.png)

## 6. Participation in benchmarking and evaluating
A participant algorithm shall run over the data movie in fold **Benchmark**, produce a list of 3D coordinates (x,y,z) in nm for the estimated emitter locations, and saved them row by row in a .txt file: e.g.

4.4184628e+02 5.0638849e+03 -4.2658749e+03

4.2119986e+02 5.8867272e+03  4.5179889e+02 

... ...

The filenames in submission shall be in the format:

**3DAS_HD_xyz_algorithmName.txt** 

The RMSMD of the submitted list will be posted in the Leaderboard. 

## 7. Other parameters
**Independent parameters**

|Parameter |Variable and value| Unit|
|:-----|:-----|:-----|
|Emitter intensity |I = 240000|photons/sec/emitter|
|Analog digital unit |ADU = 1|photons/unit|
|Frame time |Dt = 0.01|sec|
|Astigmatic PSF |c=205, d=290	| nm |
| |sigmax0=140	| nm |
| |Ax=0.05, Bx=0.03	|  |
| |sigmay0=135	| nm |
| |Ay=-0.01, By=0.02|  |	
|Mean of Poisson noise |b = 0.3|photons/sec/nm^2|
|Variance of Gaussian noise |G = 0.2|photons/sec/nm^2| 
|Mean of Gaussian noise |mu = 5|photons/sec/nm^2|

**Corresponding composite parameters**

|Parameter |Variable and value| Unit|
|:-----|:-----|:-----|
|Frame rate|1/Dt = 100|frames/sec|
|Photon count |Dt\*I = 2400|photons/frame/emitter|
|Signal to noise ratio [8] |SNR = 1.22|dB|
|Effective camera offset |Coff = 500 |photons/pixel|

The corresponding 2D coordinate in a data frame is shown below. 

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/Docs/FrameCoordinates.png)

## 8. Codes
All the codes that generate the datasets are in the folder: **Codes**  

A researcher can modify the parameters to generate desired datasets with acknowledging of the codes in a publication. 

# References
[1] Y. Sun, "Localization precision of stochastic optical localization nanoscopy using single frames," J. Biomed. Optics, 18(11), 111418-14(2013). 

[2] Y. Sun, and Y. Guan, "Effect of unknown emitter intensities on localization accuracy in stochastic optical localization nanoscopy using single frames," JOSA A, 38(12), 1830-1840(2021). 

[3] Y. Sun, "Root mean square minimum distance as a quality metric for stochastic optical localization nanoscopy images," Sci. Reports, 8(1), 17211(2018). 

[4] Y. Sun, "Markov chain models of emitter activations in single molecule localization microscopy," Optics Express, 32(19), 33779-33794(2024).

[5] Y. Sun, "Partition of estimated locations: an approach to accurate quality metrics for stochastic optical localization nanoscopy," JOSA A, 39(12), 2307-2315(2022).

[6] Y. Sun, "Spatiotemporal resolution as an information theoretical property of stochastic optical localization nanoscopy," 2020 Quantitative BioImaging Conf. (QBI2020), Oxford, UK, Jan. 6-9, 2020. 

[7] Y. Sun, "Information sufficient segmentation and signal-to-noise ratio in stochastic optical localization nanoscopy," Optics Letters, 45(21), 6102-6105(2020). 

[8] M. Sun and Y. Sun, "Information sufficient segmentation and signal-to-noise ratio for 3D astigmatism stochastic optical localization nanoscopy," Electr. Letters, 58(2), 58-60(2021).
