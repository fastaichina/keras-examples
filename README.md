## Running Keras on Floyd

[Floyd](https://www.floydhub.com/) has native support for Keras with Tensorflow or Theano backends. This page lists some of the best example projects for Keras.

## Keras Official Examples

The Keras project ([fchollet/keras](https://github.com/fchollet/keras)) itself comes with a great set of [examples](https://github.com/fchollet/keras/tree/master/examples) for Keras. These range from simple CNN to deep dream transformation of your own images.

You can start by cloning the keras repository and initializing a floyd project.

```bash
$ git clone https://github.com/fchollet/keras
$ cd keras/examples
$ floyd init keras-examples
```

If you don't have floyd already installed, you can run:
```bash
pip install -U floyd-cli
floyd login
```

### Deep Dream

To run the `deep_dream.py` example on a GPU instance:
First download the image you want to transform the current directory.
Then run floyd using the Keras environment.

```bash
$ wget URL/sample.jpg
$ floyd run --env keras --gpu python deep_dream.py sample.jpg /output/
$ floyd logs -t <RUN_ID>
$ floyd output <RUN_ID>
```
The output should contain all the deep dream generated images. For example:
![deep_dream](https://dev.floydhub.com/viewer/data/ujRBgsxfGATSftVLKcVdVM/rVLSHv3RheWUQnFKnGJoz7/_at_iteration_4.png)

### CNN on Cifar10

To train a simple deep CNN on the CIFAR10 small images dataset:

```bash
$ floyd run --env keras --gpu python cifar10_cnn.py
$ floyd logs -t <RUN_ID>
```

### ACGAN on MNIST

To train an Auxiliary Classifier Generative Adversarial Network (ACGAN) on the
MNIST dataset:

```bash
$ floyd run --env keras --gpu python mnist_acgan.py
$ floyd logs -t <RUN_ID>
```

There are lots of other example scripts that run on MNIST dataset. They can all be run 
the same way with Floyd.

### Neural Style Transfer

You can transfer the style (artistically) of any image over another base image. For this
you need a base image and a style image (use famoust paintings like [this](https://github.com/floydhub/fast-style-transfer/blob/master/examples/style/the_scream.jpg)).

```bash
$ wget URL/style.jpg
$ floyd run --env keras --gpu python neural_style_transfer.py base.jpg style.jpg /output/result
$ floyd logs -t <RUN_ID>
$ floyd output <RUN_ID>
```
An example output:
![style_transfer](https://www.floydhub.com/viewer/data/fWbbaWgY29aZJtfvDZoSmM/maEBJn9ULHVvCVxhRcKNmM/result_at_iteration_9.png)

### Other examples

Similarly you can run all the other examples easily on Floyd in seconds.

```bash
# Convolutional LSTM network
floyd run --env keras --gpu python conv_lstm.py

# Generate text from Nietzsche's writings
floyd run --env keras --gpu python lstm_text_generation.py

# Simple MLP on the Reuters newswire topic classification task
floyd run --env keras --gpu python reuters_mlp.py
```
