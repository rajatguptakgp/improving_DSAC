# Improving building segmentation through image augmentation

***
## Overview
This work is about improving building instance segmentation through Deep Structured Active Contours [DSAC](https://arxiv.org/abs/1803.06329) on Bing Huts dataset using image augmentation techniques like Denoising and Super Resolution.

## Results

The work highlights how Denoising and Super Resolution can help in removing noise or increasing resolution respectively, thereby improving quality of images, can consequently lead to better segmentation.

The work is specifically done on [Bing Huts dataset](https://github.com/dmarcosg/DSAC) because of its low-resolution images of 64 pixels. The following results highlight the improvement in evaluation metrics with augmented datasets:

| Dataset | IoU |
| :---:   | :-: |
| Bing Huts (64 X 64) | 0.64 |
| Denoised Bing Huts (64 X 64) | 0.66 |
| Bing Huts (128 X 128) | 0.68 |

From the results, we can conclude that our 'enhanced' data has marginally been able to improve building segmentation. Such enhancing techniques can be applied in general to low-quality images in order to feed the model with better input. 

## Code modifications

No modifications were required in the code for Denoised dataset. However, for higher-resolution images, the building footprints were needed to be modified to match building boundaries as shown below:

![high-resolution-image](https://user-images.githubusercontent.com/55928605/84311885-b1c79780-ab81-11ea-9fc7-393572efa828.png)

- Use `make_building_footprints.ipynb` to transform building footprints and store them in a CSV file.

Also, in order to expedite the learning process for higher-resolution images, the initial ACM was initialized with double the original size. This helped in better initialization and made the learning faster.

## Datasets

### Image Denoising
A pretrained GAN-based MSRResNet(https://github.com/cszn/KAIR) was used to obtain denoised images. The average PSNR obtained between original and noisy images was 30.10 dB. The following is an image-pair highlighting the model performance: 

![denoised_output](https://user-images.githubusercontent.com/55928605/84306686-6f9a5800-ab79-11ea-96e0-ad4afc30a6ee.png)

### Super Resolution

A pretrained Residual Dense Network (RDN)(https://github.com/idealo/image-super-resolution) was used to obtain 128 X 128 images.

## Acknowledgement
* Diego Marcos [Original Implementation](https://github.com/dmarcosg/DSAC) 
