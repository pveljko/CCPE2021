# Repository for Robustness of Deep Learning Methods for Ocular Fundus Segmentation: Evaluation of Blur Sensitivity

This repository contains supplementary material that accompanies the paper titled "Robustness of Deep Learning Methods for Ocular Fundus Segmentation: Evaluation of Blur Sensitivity". 

## The results
The `results.dat` file is a tab-separated file suitable for processing in R. The fields are:
1. *FileUID* unique identifier for the input file being processed. It simplifies picking out how various networks treated one file. 
2. *CaseUID* unique per-case tested identifier that should be a stable rowid. 
3. *Dataset* one of CHASE, DRIVE, and STARE. 
4. *Subset* differentiates between training and test subsets of each dataset. 
5. *N* unique identifier of picture within each dataset. Not unique or commesurate between datasets. 
6. *Mod* the modification being used. See below for mapping between user friendly and simplified mod names. 
7. *Ksize* the kernel size of the blur modification. If the picture being processed has not been blurred this is guaranteed to be 0. 
8. *Angle* the angle of the blur modification. If the picture being procesed has not been motion-blurred this is guaranteed to be 0. 
9. *SD* the standard deviation of the gaussian noise modification. If the picture being processed has not had noise added to it, this is guaranteed to be 0. 
10. *Network* the network used to process the image. See below for the correspondence between user friendly and simplified names of networks. 
11. *Threshold* the threshold to convert a probability map into a segmentation mask. 
12. *CP* Condition positive. 
13. *CN* Condition negative. 
14. *TP* True positives. 
15. *FP* False positives. 
16. *FN* False negatives. 
17. *TN* True negatives. 

### Correspondence between modification names and user-friendly names. 

| Mod label        | User-friendly name                                               | Remarks                                                         |
|------------------|------------------------------------------------------------------|-----------------------------------------------------------------|
| gb               | Gaussian Blur                                                    |                                                                 |
| mbH              | Horizontal motion blur                                           |                                                                 |
| mbV              | Vertical motion blur                                             |                                                                 |
| mbC              | Motion blur, other                                               | The angle field contains the angle of this type of motion blur. |
| gnoise_all_mono  | Gaussian noise, equal  accross all color  channels               |                                                                 |
| gnoise_all_color | Gaussian noise, different across all color channels              |                                                                 |
| gnoise_r         | Gaussian noise, red channel only                                 |                                                                 |
| gnoise_g         | Gaussian noise, green channel only                               |                                                                 |
| gnoise_b         | Gaussian noise, blue channel only                                |                                                                 |
| gnoise_yuv_color | Gaussian noise, UV components of YUV                             |                                                                 |
| gnoise_freq      | Gaussian noise, frequency domain using Discrete Cosine Transform |                                                                 |

### Correspondence between network names and user-friendly names.

| Mod label   | User-friendly name | Remarks                                                                                                                                                                                                     |
|-------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| eswanet     | ESWANet            |                                                                                                                                                                                                             |
| saunet      | SA-UNet            |                                                                                                                                                                                                             |
| iternet     | IterNet            |                                                                                                                                                                                                             |
| iternet-uni | IterNet            | Signifies a case in which the IterNet network was used with a model not trained on the root dataset of the currently active synthetic set but on the author-provided model trained with multiple datasets.  |
| laddernet   | LadderNet          |                                                                                                                                                                                                             |
| unet        | UNet               |                                                                                                                                                                                                             |
| vgan        | RVSGAN             |                                                                                                                                                                                                             |
| vesselunet  | DenseBlockUNet     |                                                                                                                                                                                                             |

## The comparisons

The `comparison.csv` file is a comma separated value file containing the results of comparing networks on their MCC values (details of the procedure available in paper). The group1 and group2 files are the networks being compared, and the crucial values for evaluation are `p.value` and `p.crit` which are the computed p-value and the critical signfiicance value that it needs to be compared with given Holm's correction. 

## Licencing

This repository is licensed under the CC BY 4.0 licence. See the LICENSE file for legal details or [this](https://creativecommons.org/licenses/by/4.0/) for a human-readable summary. 
