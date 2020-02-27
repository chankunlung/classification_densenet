# classification_densenet
Prior to starting, GPU provided by colab was used based on tensorflow library API. Code for ResNet and is not a function provided by Tensorflow. Finally, I could see the feature map, grad cam.

#### - As a dataset, we used the Cats-vs-Dogs data provided by Kaggle and divided them from 25,000 to 17,000 train_data, validation_data 4000 and test_data 4000.

## DenseNet(Densely Connected Convolutional Networks)
DenseNet overall background is layer-our network has a direct L(L+1) connection, one between each layer and the subsequent layers. For each layer, the feature map of all leading layers is used as an input.
This configuration destroys decimation phase problems, strengthens character propagation, encourages feature reuse, and significantly reduces the number of parameters.

<img width="734" alt="스크린샷 2020-02-28 02 08 50" src="https://user-images.githubusercontent.com/45933225/75467606-44776880-59cf-11ea-987c-26462f352d1a.png">

Similar methods were seen in the previous ResNet.
However, if ResNet is a method that adds feature maps, DenseNet is the biggest difference in order to make each feature map concation.

#### Growth Rate
Since each feature map is connected flexibly, if the number of channels in the feature map is high, then the channel can continue to be connected to channel-wise, which can lead to more channels. So DenseNet uses a very small number of channels for each layer's feature map, which is called the number of channels for each layer's feature map is called a row rate(k).

### Bottleneck Layer
You can also check the bottle neck section on ResNet.

<img width="734" alt="스크린샷 2020-02-28 02 19 29" src="https://user-images.githubusercontent.com/45933225/75468567-c0be7b80-59d0-11ea-93c9-ad5869a5bae8.png">

The number of channels in the input feature map is about to be reduced through 1x1 component before the 3x3 competition. After that, instead of creating as many channels as the input feature map, the difference is to create as many feature map as the row rate, which can reduce the computational cost.
Efficiency can reduce parameters and see the figure for areas that differ from ResNet.

### Transition Layer
The function is to reduce the horizontal and vertical size of the feature map and to reduce the number of

### Composite function

<img width="734" alt="스크린샷 2020-02-28 02 27 08" src="https://user-images.githubusercontent.com/45933225/75469140-d54f4380-59d1-11ea-8317-273f6dcacf39.png">

Use pre-activation structures in the batchNorm-ReLU-Conv sequence

### avg pooling vs max pooling

I will finish the brief explanation on the densenet and continue to compare max and avg pooling based on the experiment.

Pooling plays a very important role on CNN. It can use sub-sampling to reduce the size of feature-map and extract features that have a stronger nature for location or movement. 

First, the Avg-pooling method uses a lot of RELUs as an active function. This results in a large number of zeros, and the impact is reduced by strong stimulation by the average operation.
In addition, taking the average of positive and negative stimuli can cause offsetting situations.
Second, the Max-pooling method would like to be overfitting with learning data.

Avg, Max pooling was tested as follows. The Stochastic pooling part will be later....

Both used 121-layer. And two results were obtained.

When I studied 250epoch, Avg-pooling came out 86.87% acuracy, loss 0.28962, Max-pooling came out acuracy 90.85% and loss 0.22649 and was not obvious about the differences above.

#### - feature map(conv_2d layer)

##### avg pooling
The following figures show a Constructed Layer feature map from input to output layer.

![image](https://user-images.githubusercontent.com/45933225/75474243-f74cc400-59d9-11ea-9d09-43faa465a9af.png)

##### max pooling

![image](https://user-images.githubusercontent.com/45933225/75474318-1f3c2780-59da-11ea-9948-00dcb768fc68.png)


#### - Grad CAM:Generalized version of CAM(cat, dog)
Simply put, the Grid CAM is called a face position tracker.

##### avg pooling

![image](https://user-images.githubusercontent.com/45933225/75474663-bb662e80-59da-11ea-9f76-d6daef32eae7.png)
![image](https://user-images.githubusercontent.com/45933225/75474708-ce78fe80-59da-11ea-98e9-a375dfa123f3.png)

##### max pooling

![image](https://user-images.githubusercontent.com/45933225/75474520-780bc000-59da-11ea-8adf-2ce5c50522d0.png)
![image](https://user-images.githubusercontent.com/45933225/75474573-8d80ea00-59da-11ea-8e49-be0d9e4e152f.png)

Although it is not as good as the previous model, there are some areas that we can see in detail.
