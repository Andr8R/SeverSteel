# SeverSteel binary segmentation task.
## For defect detection on the SeverSteel dataset was trained segmentation model and created visualisation tools.

* Visualisation notebook contain dataframe preprocessing and mask display. Dataset splits to balanced sample of 1000 images, which includes 500 images with no defects and at least 125 images with defect of each class (due to multiple class images presence). Second, test, sample imcludes other images and was used for model evaluation.

![image](https://user-images.githubusercontent.com/64214190/130695465-6c5abd04-04f0-44ad-a971-2fa0a53de3fa.png)

* PLUnet_model notebook contains model definition, training and output visualisation. Model uses pretrained Unet/imagenet segmentation model for pytorch with resnet18 encoder. 
(https://github.com/qubvel/segmentation_models.pytorch).

Plots for the first training iteration:
![image](https://user-images.githubusercontent.com/64214190/130696828-b4e8082f-1ba5-4500-8a43-696bedf9a963.png)
![image](https://user-images.githubusercontent.com/64214190/130696789-df54b3dc-1cd9-4ee6-94d2-faeb0cdb2e75.png)


Best Dice coefficient for the test set was obtained for twice trained with different conditions model and equals to 0.6.
Therefore, in the first iteration, model is not perfectly trained and can be improved. Green lines correspond to predicted masks, red to ground truth.
![image](https://user-images.githubusercontent.com/64214190/130696907-d246b6f9-1bfe-493b-8118-36efcd22a266.png)

