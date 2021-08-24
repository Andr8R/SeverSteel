# SeverSteel binary segmentation task.
## For defect detection on the SeverSteel dataset was trained segmentation model and created visualisation tools.

* Visualisation notebook contain dataframe preprocessing and mask display. Dataset splits to balanced sample of 1000 images, which includes 500 images with no defects and at least 125 images with defect of each class (due to multiple class images presence). Second, test, sample imcludes other images and was used for model evaluation.

![image](https://user-images.githubusercontent.com/64214190/130695465-6c5abd04-04f0-44ad-a971-2fa0a53de3fa.png)

* PLUnet_model notebook contains model definition, training and output visualisation. Model uses pretrained Unet/imagenet segmentation model for pytorch. 
(https://github.com/qubvel/segmentation_models.pytorch)
