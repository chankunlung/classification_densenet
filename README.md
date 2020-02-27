# classification_densenet
Prior to starting, GPU provided by colab was used based on tensorflow library API. Code for ResNet and is not a function provided by Tensorflow. Finally, I could see the feature map, grad cam.

#### - As a dataset, we used the Cats-vs-Dogs data provided by Kaggle and divided them from 25,000 to 17,000 train_data, validation_data 4000 and test_data 4000.

### DenseNet(Densely Connected Convolutional Networks)
DenseNet overall background is layer-our network has a direct L(L+1) connection, one between each layer and the subsequent layers. For each layer, the feature map of all leading layers is used as an input.
This configuration destroys decimation phase problems, strengthens character propagation, encourages feature reuse, and significantly reduces the number of parameters.
