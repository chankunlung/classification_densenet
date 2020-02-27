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

