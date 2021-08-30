# SeverSteel binary segmentation task.
## For defect detection on the SeverSteel dataset was trained segmentation model and created visualisation tools.

* Visualisation notebook contain dataframe preprocessing and mask display. Dataset splits to balanced sample of 1000 images, which includes 500 images with no defects and at least 125 images with defect of each class (due to multiple class images presence). Second, test, sample imcludes other images and was used for model evaluation.

![image](https://user-images.githubusercontent.com/64214190/130695465-6c5abd04-04f0-44ad-a971-2fa0a53de3fa.png)

* PLUnet_model notebook contains model definition, training and output visualisation. Model uses pretrained Unet/imagenet segmentation model for pytorch with resnet18 encoder. 
(https://github.com/qubvel/segmentation_models.pytorch).

Plots for the first training iteration:

![image](https://user-images.githubusercontent.com/64214190/130696828-b4e8082f-1ba5-4500-8a43-696bedf9a963.png)

![image](https://user-images.githubusercontent.com/64214190/130696789-df54b3dc-1cd9-4ee6-94d2-faeb0cdb2e75.png)


Best Dice coefficient for the test set was obtained for twice trained with different conditions model and equals to 0.59.
Therefore, in the first iteration, model is not perfectly trained and can be improved. Green lines correspond to predicted masks, red to ground truth.
![image](https://user-images.githubusercontent.com/64214190/130696907-d246b6f9-1bfe-493b-8118-36efcd22a266.png)

For further result improvement on the same data sample image augmentations are used from albumentations library. However, it caused overfitting, as well as larger encoders such as resnet34. Potential improvement can be reached with implementation of combined Dice and Cross-Entropy loss.


Updated:

As it was mentioned higher, was tried to estimate total loss as geometric mean of Dice and CE losses. It improved results to 0.64 for the best model. Moreover, was made an attempt to rebalance starting sample with 200+ images from each starting class and to work with it. Finally, all the gained results had about 0.6-0.65 Dice scores and the model wasn't able to train more. Validation plateau is below.

![image](https://user-images.githubusercontent.com/64214190/131269499-538b71c4-0304-4b38-9e9f-c682abc73753.png)

### Summary: 
The task was to train model on the balanced sample of 1000 images for binary segmentation. As metrics was suggested to use Dice coefficient, which estimates positive predictions corresponding to ground truth labels. However, it's better to use similar Jaccard coefficient here. Problem of binary segmentation is that default dataset contains images of 4 different classes represented in a significant number with their own different features, what causes problems for the training.

![image](https://user-images.githubusercontent.com/64214190/131270175-954c7f7e-d500-4ddd-9ea0-8c7eef1ae3c6.png)

(Therefore, for better score on presented dataset, it was easier to create sample with weights for different classes, but it's a bit wrong approach at all). 

Also 1000 images is not very big dataset and even with some augmentations the model tries to overfit it, while validation scores doesn't improve. Overall, Dice score about 0.64 was gained. 
