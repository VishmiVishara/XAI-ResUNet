# XAI-ResUNet: Analysing the Impact of Pre-training in ResUNet Architectures for Multiple Sclerosis Lesion Segmentation using EigenGradCAM

## Overview
This project is an implementation of the paper "XAI-ResUNet: Analysing the Impact of Pre-training in ResUNet Architectures for Multiple Sclerosis Lesion Segmentation using EigenGradCAM," which has been accepted for the 26th Irish Machine Vision and Image Processing Conference at the University of Limerick, Ireland, from Wednesday, August 21st, 2024, to Friday, August 23rd, 2024.

## Dataset
The dataset used for this paper, MSSEG-2016, can be downloaded from https://shanoir.irisa.fr/shanoir-ng/welcome.

## Proposed Architecture
![architecture](https://github.com/user-attachments/assets/ea78317a-b17d-4930-93ed-3e2dcd60c082)

## Results
Qualitative results so far: <br>
1. Rows 1 & 2 are ImageNet XAI-ResUNet trained using ImageNet-trained ResNet-50 weights for the encoder (EX1) (red) <br>
2. Rows 3 & 4 are RadImageNet XAI-Res-UNet trained using RadImageNet-trained ResNet-50 weights for the encoder (EX2) (green) <br>
3. Rows 5 & 6 are Vanilla XAI-ResUNet trained using no pre-trained weights for the encoder (EX3) (blue). <br>

![qualitative_2](https://github.com/user-attachments/assets/085a1dac-b627-44f7-924e-50c5b8515534)

Sample qualitative results including EigenGradCAM localization heatmaps overlaid on the original images where red indicates higher pixel importance and ground truth lesion contours are shown in black. 

## Setup

```
conda create -n “xai-resunet-env” python=3.10.12
pip install torchvision==0.15.0+cu117 -f https://download.pytorch.org/whl/torch_stable.html
pip install -r requirements.txt
```
Download RadImageNet pretrained ResNet-50 model from here: https://github.com/BMEII-AI/RadImageNet?tab=readme-ov-file <br>
Torch version: 2.0.0+cu117 <br>
TorchVision version: 0.15.0+cu117

## Preprocess the dataset

- **XAI-ResUnet/**: Root directory of the project
  - **data/**: Contains all the data related to the project
    - **original_data/**: Folder for the original dataset
      - **Training/**: Extract the MSSEG-2016 Training.zip here
      - **Testing/**: Extract the MSSEG-2016 Testing.zip here    

``` 
python preprocess.py
``` 

## Run XAIResUnet Experiments
```
python main.py --model "XAIResUnet_Imagenet" --epoch "100"
python main.py --model "XAIResUnet_Radimagenet" --epoch "100" 
python main.py --model "XAIResUnet_Vanilla" --epoch "100"
``` 

## Contact
Please feel free to raise an issue or contact me at vayangi.ganepola2@mail.dcu.ie with any queries or for discussions.

## Acknowledgement

```
@inproceedings{ganepola2024xai,
  title={XAI-ResUNet: analysing the impact of pre-training in ResUNet architectures for multiple sclerosis lesion segmentation using EigenGradCAM},
  author={Ganepola, Vayangi and Mathur, Prateek and Adegboro, Oluwabukola and Dietlmeier, Julia and Lawlor, Aonghus and O’Connor, Noel E and Mazo, Claudia},
  booktitle={IET Conference Proceedings CP887},
  volume={2024},
  number={10},
  pages={299--302},
  year={2024},
  organization={IET}
}
```
