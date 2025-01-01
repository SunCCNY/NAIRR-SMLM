# 2DGauss_FFL_LD

## Purposes
(1) Provide datasets for AI training, validating, and testing.

(2) Benchmark AI performance by the information-theoretical UGIA-F and UGIA-M detectors.

(3) Evaluate and benchmark performance of conventional spatiotempoal localization algorithms. 

## Type of localization and imaging system
**Localization:** Frame-by-frame localization (FFL) by AI or conventional localization algorithms. 

**System:** 2D imaging, Gaussian point spread functions (PSF), and low density (LD) of emitters. 

## AI input and output
AI can be trained, validated, and tested by a pair of input and output datasets. 

**Input**: A data frame consisting of PSFs for activated emitters through light diffraction. An example of data frame is shown below. 

[Show a figure of a data frame]

![Alt text](https://github.com/SunCCNY/NAIRR-SMLM/blob/main/2DGauss_FFL_LD/Codes/FigFrame.svg)


**Output**: A set of 2D coordinates, each being an emitter's location, producing the data frame in the input. An example of emitter locations is shown below. 

[Show a figure of a set of emitter locations]

## Training datasets
Training datasets are in the folder: **Training**. 

(1) **2DGauss_FFL_LD_Frame.zip**: N data frames used as input in training. The main parameters are given below.
 
|Parameter |Variable and value| Unit|
|:-----|:-----|:-----|
|Number of frames |N = 500 |frames |
|Number of emitters |M = 5 |emitters/frame |
|Emitter density |D = 0.5|emitters/um^2|
|Field of view (FOV) |[0, Lx] x [0, Ly] = [0, 3200] x [0, 3200]|nm| 
|Pixel size |Dx = 100, Dy = 100|nm|
|Frame size |Kx = 32, Ky = 32 |pixels |
|Emitter distribution| Random and uniform in FOV| |

(2) **2DGauss_FFL_LD_xy.zip**: N txt files each containing M emitter locations. The 2D emitter locations (x,y) in nm in each file are given row by row, e.g.

4.4184628e+02   5.0638849e+03

... ...

4.1254239e+02   6.8510823e+03

(3) The input data frame "2DGauss_FFL_LD_Frame_i.tif" and the corresponding output data file "2DGauss_FFL_LD_xy_i.txt" have the same index i. 

## Validating datasets

The validating datasets, consisting of 50 pairs of input and output files, are generated in the same way as the training datasets. The emitter locations are random and independent.



## Testing datasets

The testing datasets, consisting of two pairs of input and output files, are generated in the same way as the training datasets. 

(1) 2DGauss_FFL_LD_Frame_Circle.tif







## Other parameters
The  data frames are synthesized by using the following parameters. 

### Emitter distribution and intensity 
|Parameter |Variable and value| Unit|
|:-----|:-----|:-----|
|Emitter intensity |I = 300000|photons/sec/emitter|
|Analog digital unit |ADU = 1|photons/unit|

### Data frame 
|Parameter |Variable and value| Unit|
|:-----|:-----|:-----|
|Frame time |Dt = 0.01|sec|
|Correspondingly | |
|Frame rate|1/Dt = 100|frames/sec|
|Photon count |Dt\*I = 3000|photons/frame/emitter|

The corresponding 2D coordinate in a data frame is shown below. 

![Alt text](https://github.com/SolnBenchmark/Benchmark/blob/master/2DGauss_SESF/Doc/FrameCoordinates.png)

### Optical system
|Parameter |Variable and value|Unit | |
|:-----|:-----|:-----|:-----|
|Numerical aperture |na = 1.40| | |
|Fluorescence wavelength |lambda = 723|nm|Dye Alexa 700 |
|Correspondingly| | | |
|Standard deviation |sigma = 108.81|nm| |
|Full-width half-maximum |FWHM = 256.22|nm| |

PSF is 2D Gaussian and its standard deviation is estimated from an Airy PSF by sigma = 1.3238/a where a = 2\*pi\*na/lambda [1]. 

### Noise 
|Parameter |Variable and value| Unit|
|:-----|:-----|:-----|
|Mean of Poisson noise |b = 5|photons/sec/nm<sup>2</sup>|
|Variance of Gaussian noise |G = 3|photons/sec/nm<sup>2</sup>| 
|Mean of Gaussian noise |mu = 5|photons/sec/nm<sup>2</sup>|

**Corresponding signal to noise ratios and camera offset**

|Parameter |Variable and value| Unit|
|:-----|:-----|:-----|
|Signal to Poisson noise ratio |rp = 60000|nm<sup>2</sup>/emitter|
|                             |SPNR = -3.97|dB|
|Signal to Gaussian noise ratio |rg = 100000|nm<sup>2</sup>/emitter|
|                             |SGNR = -1.75|dB|
|Total signal to noise ratio |r = 37500|nm<sup>2</sup>/emitter|
|                           |SNR = -6.01|dB|
|Effective camera offset |Coff = 500 |photons/pixel|

The mean of Gaussian noise mu includes the effect of camera offset. When mu is solely contributed by the camera offset, i.e. the Gaussian noise has a zero mean, the effective camera offset is Coff = Dt\*Dx\*Dy\*mu. 

SPNR, SGNR, and SNR are defined in [4]. 
