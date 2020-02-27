# classification_densenet
Prior to starting, GPU provided by colab was used based on tensorflow library API. Code for ResNet and is not a function provided by Tensorflow. Finally, I could see the feature map, grad cam.

#### - As a dataset, we used the Cats-vs-Dogs data provided by Kaggle and divided them from 25,000 to 17,000 train_data, validation_data 4000 and test_data 4000.

### DenseNet(Densely Connected Convolutional Networks)
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

