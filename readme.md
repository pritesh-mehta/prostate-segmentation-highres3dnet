# Prostate-Segmentation-HighRes3DNet

This repository provides a trained HighRes3DNet<sup>1</sup> for prostate segmentation. Training and inference is facilitated by NiftyNet<sup>2</sup>.

HighRes3DNet was trained using 79 T2-weighted images (T2WI) from the PICTURE study dataset<sup>3</sup> and 47 T2WI from the PROMISE12 dataset<sup>4</sup>. On a small validation set (N=4), HighRes3DNet achieved a mean Dice score of 0.90.

If you use this repository, please cite the following publication: 

[Mehta, P., Antonelli, M., Ahmed, H.U., Emberton, M., Punwani, S., Ourselin, S. Computer-aided diagnosis of prostate cancer using multiparametric MRI and clinical features: A patient-level classification framework. Medical Image Analysis 2021, 73, 102153, doi:10.1016/j.media.2021.102153.](https://www.sciencedirect.com/science/article/pii/S1361841521001997?via%3Dihub)

Note: NiftyNet [is not actively maintained anymore](https://github.com/NifTK/NiftyNet/commit/935bf4334cd00fa9f9d50f6a95ddcbfdde4031e0).

## Installation instructions 

1) Clone/download this repository.

2) Create a Python virtual environment:
    ```
	conda create -n prostate_segmentation_highres3dnet_venv python=3.6.3
    ```
	
3) Activate the virtual environment:
	```
	conda activate prostate_segmentation_highres3dnet_venv
    ```
	
4) Install CUDA Toolkit (required for running TensorFlow GPU):
	```
	conda install -c anaconda cudatoolkit=9.0
    ```
	
5) Download [cuDNN v7.0.5 (Dec 5, 2017), for CUDA 9.0](https://developer.nvidia.com/rdp/cudnn-archive)

5) Locate cudnn64_7.dll and copy+paste into path e.g. in environment bin _<FULL_PATH>_\prostate_segmentation_highres3dnet_venv\Library\bin.
 
6) Install requirements, chiefly NiftyNet==0.3.0 and tensorflow-gpu==1.7:
	```
	pip install -r requirements.txt
    ```
	
## How to use it (command line)

1) Activate the virtual environment if not already activated:
	```
	conda activate prostate_segmentation_highres3dnet_venv
    ```

2) Change directory into repository.

2) Add T2WI for inference to: .\sample_data\sample_t2w

3) Run the following command:
	```
	net_segment inference -c .\configs\config_infer.ini -a niftynet.application.segmentation_application.SegmentationApplication
    ```

## References

<sup>1</sup> Li, W.; Wang, G.; Fidon, L.; Ourselin, S.; Cardoso, M.J.; Vercauteren, T. On the compactness, efficiency, and representation of 3D convolutional networks: Brain parcellation as a pretext task. In Proceedings of the Information Processing in Medical Imaging (IPMI 2017); 2017; Vol. 10265, pp. 348–360.

<sup>2</sup> Gibson, E.; Li, W.; Sudre, C.; Fidon, L.; Shakir, D.I.; Wang, G.; Eaton-Rosen, Z.; Gray, R.; Doel, T.; Hu, Y.; et al. NiftyNet: a deep-learning platform for medical imaging. Comput. Methods Programs Biomed. 2018, 158, 113–122.

<sup>3</sup> Simmons, L.A.M.; Kanthabalan, A.; Arya, M.; Briggs, T.; Barratt, D.; Charman, S.C.; Freeman, A.; Gelister, J.; Hawkes, D.; Hu, Y.; et al. The PICTURE study: Diagnostic accuracy of multiparametric MRI in men requiring a repeat prostate biopsy. Br. J. Cancer 2017, 116, 1159–1165.

<sup>4</sup> Litjens, G.; Toth, R.; van de Ven, W.; Hoeks, C.; Kerkstra, S.; van Ginneken, B.; Vincent, G.; Guillard, G.; Birbeck, N.; Zhang, J.; et al. Evaluation of prostate segmentation algorithms for MRI: the PROMISE12 challenge. Med. Image Anal. 2014, 18, 359–373.