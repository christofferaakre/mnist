# mnist <!-- omit in toc -->
[mnist](http://yann.lecun.com/exdb/mnist/) 
is a database of images of handwritten digits, in particular, a set of 60,000 training examples and 10,000 test examples.

## goal of this project
Write a neural network that can recognise the handwritten digits from the `mnist` dataset.

## results 
The neural network was trained on `60 000` training examples, and then tested on `10 000` more examples. I trained for 100 epochs using SGD with a batch size of `100`, which took approximately 5-10 minutes using the free GPU acceleration in Google Colab. The results were:
```
Correct: 9873 Incorrect: 127
Accuracy: 0.9872999787330627
```
These are very good results in my opinion, and were achieved with very little effort. I got these results the first time I trained the network, I didn't even have to tweak anything.
## input data
`28x28` images representing handwritten digits from `0-9`, represented as a `1x28x28` tensor since the images are greyscale images.
the images were accessed using `torchvision.datasets.MNIST`
## output
A `10D vector` with probabilities for the given digit being each of the 10 digits for `0-9`. For example, if a particular input digit is `3`, we would want a perfect neural network to return 
```
[0, 0, 0, 1, 0, 0, 0, 0, 0, 0],
``` 
and then it would have zero error.

## model
1. `1x28x28` input --> `3x3` conv (`1` in, `6` out) --> `26x26`
2. `relu`
3. `26x26` --> `3x3` conv (`6` in, `16` out) --> `24x24`
4. `relu`
5. `Linear` (`16 * 24 * 24` in, `120` out)
6. `relu`
7. `Linear` (`120` in, `84` out)
8. `relu`
9. `Linear` (`84` in, `10` out)
10. `MSELoss`
