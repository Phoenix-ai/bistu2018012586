# Research on Data Augmentation Method Based on Style Transfer

## Abstraction

Deep learning has been widely used in computer vision tasks such as image classification and object detection. However, in practical application scenarios, due to differences in lighting conditions, filter styles, etc. between the actual image and the image used for training the model, the prediction performance of the model in the actual scenario is often significantly reduced. Based on the style transfer technology, the style of the training set image is transferred to the actual image style, and the label is kept unchanged, and a labeled training set with a style close to the specific actual image set can be generated. Training the model based on this training set will help improve the prediction performance of the model in specific real-world scenarios. This paper studies the data augmentation method based on style transfer, and sees whether its model prediction effect on image classification tasks is improved through experiments. Specifically, the models are trained using five types of data: data before style transfer, data after style transfer, new style data, data before style transfer enhanced during training, and data after style transfer enhanced during training. Based on the five trained models, make predictions on the new style test set respectively and compare their effects. The results show that the data augmentation method based on style transfer can improve the performance of the model better than the traditional data augmentation method, and the effect of using these two data augmentation methods at the same time is better.

## Method

Here, the training set of [Plant Pathology 2020 - FGVC7](https://www.kaggle.com/competitions/plant-pathology-2020-fgvc7) on Kaggle is borrowed, and it is re-divided into training set, validation set and test set, and filters are added to all data to obtain new style data. Use the training set and validation set of the original image data to perform style transfer learning between the test set of the new style image data, and then transfer the style of the training set and validation set of the original image data to obtain the style-transferred training set and validation set. In this way, four sets of data are obtained: training set and validation set of original image data, training set and validation set of image data after style transfer, training set and validation set of new style image data, and test set of new style image data. Select an appropriate deep learning classification model, and use the original data, the style-transferred data, and the training set and validation set corresponding to the new style data for training, to obtain the trained model 1, model 2, and model 3. Use these three models to make classification predictions on the test set of the new style data, and compare the classification effects of the three classification models.

## Code

+ The first step is image preprocessing, including data set division, adding filters to images, building directories, etc.(See [MyStep1](https://www.kaggle.com/code/sssbanana/mystep1))
+ The output of the first step is used to build the dataset.(See [step1tostep2](https://www.kaggle.com/datasets/sssbanana/step1tostep2))
+ The second step is to use the CycleGAN method for style transfer, including loading the dataset, building the generator and discriminator, building the CycleGAN model, training the CycleGAN model, and using the CycleGAN model for prediction.(See [MyStep2](https://www.kaggle.com/code/sssbanana/mystep2))
+ The output of the second step is used to build the dataset.(See [step2tostep3](https://www.kaggle.com/datasets/sssbanana/step2tostep3))
+ The third step is preprocessing before using the classification model.(See [MyStep3](https://www.kaggle.com/code/sssbanana/mystep3))
+ The output of the third step is used to build the dataset.(See [step3tostep4](https://www.kaggle.com/datasets/sssbanana/step3tostep4))
+ The fourth step has one code, but ten versions. Each version is saved on Kaggle, they just have different parameters (Step, BALANCE). For example, MyStep4.1b means that Step is V1 and BALANCE is True. MyStep4.5u means that Step is V5 and BALANCE is False. The version can be changed by changing Step and BALANCE.(Take MyStep4.5b as an example, just to see [MyStep4.5b](https://www.kaggle.com/code/sssbanana/mystep4-5b)))
+ The fifth step is to sort out the experimental results of the above ten versions.(See [MyStep5](https://www.kaggle.com/code/sssbanana/mystep5))

## Details

1. Image preprocessing before style transfer.
<img src="https://github.com/Phoenix-ai/bistu2018012586/blob/f1035d8d0497e59a59df465ac165584a435e6fb2/images/019.PNG" width="40%" heigth="40%" />
2. The construction of the dataset (step1tostep2).
<img src="https://github.com/Phoenix-ai/bistu2018012586/blob/f1035d8d0497e59a59df465ac165584a435e6fb2/images/020.PNG" width="40%" heigth="40%" />
3. Obtaining the variables of the train_step method of the CycleGAN class.(Take monet to photo as an example)
<img src="https://github.com/Phoenix-ai/bistu2018012586/blob/f1035d8d0497e59a59df465ac165584a435e6fb2/images/031.PNG" width="60%" heigth="60%" />
4. Obtaining the losses of the train_step method of the CycleGAN class.(Take monet to photo as an example)
<img src="https://github.com/Phoenix-ai/bistu2018012586/blob/f1035d8d0497e59a59df465ac165584a435e6fb2/images/032.PNG" width="60%" heigth="60%" />
5. Example of image comparison before and after style transfer.
<table align="center">
  <tr align="center">
    <td>
      <img src="https://github.com/Phoenix-ai/bistu2018012586/blob/f1035d8d0497e59a59df465ac165584a435e6fb2/images/1001a.jpg" width="100%" heigth="100%" border=0 />
    </td>
    <td>
      <img src="https://github.com/Phoenix-ai/bistu2018012586/blob/f1035d8d0497e59a59df465ac165584a435e6fb2/images/1001b.jpg" width="100%" heigth="100%" border=0 />
    </td>
    <td>
      <img src="https://github.com/Phoenix-ai/bistu2018012586/blob/f1035d8d0497e59a59df465ac165584a435e6fb2/images/1001c.jpg" width="100%" heigth="100%" border=0 />
    </td>
  </tr>
  <tr align="center">
    <td>
      Before style transfer
    </td>
    <td>
      After style transfer
    </td>
    <td>
      New style
    </td>
  </tr>
</table>
6. The construction of the dataset (step3tostep4).
<img src="https://github.com/Phoenix-ai/bistu2018012586/blob/f1035d8d0497e59a59df465ac165584a435e6fb2/images/022.PNG" width="50%" heigth="50%" />
7. The five versions of the classification model.
<img src="https://github.com/Phoenix-ai/bistu2018012586/blob/f1035d8d0497e59a59df465ac165584a435e6fb2/images/023.PNG" width="40%" heigth="40%" />
8. The result of MyStep5.
<img src="https://github.com/Phoenix-ai/bistu2018012586/blob/f1035d8d0497e59a59df465ac165584a435e6fb2/images/cut.jpg" width="70%" heigth="70%" />
