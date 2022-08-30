# CNN-for-image-classification-on-CIFAR10-dataset
Problem 1: CNN for Image Classification

Preparing dataset and preprocessing:

The CIFAR10 dataset is loaded into training and test datasets and we normalize it into 0.5 mean and
0.5	variance. Then 20% of our training data is randomly sampled and stored as our final training data
- traindata_loader. We further split the original testing data equally into new validation and test data sets called valdata_loader and test_loader.
Design steps and result discussion:

We have selected our loss function to be the Cross Entropy Loss as we are solving a classification problem. Our output layer across all three networks is activated by the softmax function. The softmax function however, is a part of nn.CrossEntropyLoss in PyTorch and hence we haven’t had the need to specify it as such in our forward function.
Next we define 4 different MLP networks, varying the nodes and layers to find out which setting achieves the highest accuracy for our model. Firstly we have the MLP with 2 layers of 512 nodes [512,512], then an MLP with 2 layers of 1024 nodes [1024,1024], an MLP with 2 layers of 512 and
1024 nodes [512,1024] and finally a MLP with 3 layers of 1024, 512 and 512 nodes [1024,512,512]. The training and validation accuracies for the above were plotted and are shown below –

![image](https://user-images.githubusercontent.com/62597096/187311249-40bcbd44-4515-4423-b436-cdedd4528799.png)

![image](https://user-images.githubusercontent.com/62597096/187311313-f13b805b-cb4b-45cc-9bbb-84ec1c6a865c.png)



We observe from the above graphs that an increase in the layers of our MLP network does not contribute to an improvement in the accuracy of our model as the MLP with three layers [1024,512,512] has the poorest performance out of all our MLP networks. However, an increase in
 
the number of nodes shows a slight improvement in the performance of our MLP network as the MLP with 2 layers and 1024 nodes [1024,1024] has the best performance out of all our networks.
Next, we implement our two CNN models and we compare the training and test accuracies of the 2 CNN models and our best performing MLP model, i.e., the one with 2 layers of 1024 nodes. The train and test accuracies/loss of our 3 models is given below-

![image](https://user-images.githubusercontent.com/62597096/187312631-2dd44d03-709d-466d-9e57-8d1e089a9532.png)


We observe from the above that both our CNN models perform significantly better than our MLP model. Further, we compare the training and validation curves of our two CNN models to observe the difference in the performance of the two.

![image](https://user-images.githubusercontent.com/62597096/187311336-932d6468-9c5d-41c6-a801-83460c0ca152.png)

![image](https://user-images.githubusercontent.com/62597096/187311346-db20188b-1937-47dc-a405-dcb07a134ed5.png)


From the tabulation given above and the graphical outputs, we can conclude that the CNN1 performs far better than our CNN2 model. The pooling layer of the CNN2 model reduces the output dimension as compared to that of our CNN1 model, this reduces the training time of our CNN2 model and can be a reason for its comparatively poor performance. However, increasing the training time for both the CNNs and running them for a greater number of epochs should achieve a similar performance between the two and would guarantee a significantly better performance than any of our MLP models.
