## All-in-one Docker image for Deep Learning
This is a Dockerfile to get you up and running with a fully functional deep learning machine. It contains all the popular deep learning frameworks with GPU support (CUDA and cuDNN included). This has been tested and works on Linux machines. 

Note that this Dockerfile and the instructions below are for a GPU-based setup only. I might make a CPU version soon. Consequently, this will not work in Windows and Mac OS X environments, because Docker runs inside a Virtual Box VM, which does not have access to the GPU on the host.

## Specs
This is what you get out of the box when you create a container with the provided image/Dockerfile:
* Ubuntu 14.04
* [CUDA 7.5](https://developer.nvidia.com/cuda-toolkit)
* [cuDNN v4](https://developer.nvidia.com/cudnn)
* [Tensorflow](https://www.tensorflow.org/)
* [Caffe](http://caffe.berkeleyvision.org/)
* [Theano](http://deeplearning.net/software/theano/)
* [Keras](http://keras.io/)
* [Lasagne](http://lasagne.readthedocs.io/en/latest/)
* [Torch](http://torch.ch/) (includes nn, cutorch, cunn and cuDNN bindings)
* [iPython/Jupyter Notebook](http://jupyter.org/) (including iTorch Torch kernel)
* [Numpy](http://www.numpy.org/), [SciPy](https://www.scipy.org/), [Pandas](http://pandas.pydata.org/), [Scikit Learn](http://scikit-learn.org/), [Matplotlib](http://matplotlib.org/)
* A few common libraries used for deep learning

## Setup
1. Install Docker following the installation guide for your platform: [https://docs.docker.com/engine/installation/](https://docs.docker.com/engine/installation/)
2. Install Nvidia drivers on your machine either from [Nvidia](http://www.nvidia.com/Download/index.aspx?lang=en-us) directly or follow the instructions [here](https://github.com/saiprashanths/dl-setup#nvidia-drivers). Note that you [b]don't[/b] have to install CUDA and cuDNN on your host machine. These are included in the Docker container.
3. Install nvidia-docker. Follow the instructions here: [https://github.com/NVIDIA/nvidia-docker](https://github.com/NVIDIA/nvidia-docker). This will install a replacement for the docker client. It takes care of setting up the Nvidia host driver environment inside the Docker containers and a few other things.

## Why do I need a Docker?
Installing all the deep learning frameworks correctly is an exercise in dependency hell. Unfortunately, given the current state of DL development and research, it is almost impossible to rely on just one framework. This Docker is intended to provide a solution for this use case.

If you would rather install all the frameworks yourself manually, take a look at this guide: [Setting up a deep learning machine from scratch](https://github.com/saiprashanths/dl-setup)

### Do I need an all-in-one container?
No. The provided all-in-one solution is useful if you have dependencies on multiple frameworks (say, load a pre-trained Caffe model, finetune it, convert it to Tensorflow and continue developing there) or if you just want to play around with the various frameworks.

The Docker philosophy is to build a container for each logical task/framework. If we followed this, we should have one container for each of the deep learning frameworks. This minimizes clashes between frameworks and is easier to maintain as things evolve. In fact, if you only intend to use one of the frameworks, or at least only one framework at a time, follow this approach. You can find Dockerfiles for individual frameworks here:
* [Tensorflow Docker](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/tools/docker)
* [Caffe Docker](https://github.com/BVLC/caffe/tree/master/docker)
* [Theano Docker](https://github.com/Kaixhin/dockerfiles/tree/master/cuda-theano)
* [Keras Docker](https://github.com/Kaixhin/dockerfiles/tree/master/cuda-keras/cuda_v7.5)
* [Lasagne Docker](https://github.com/Kaixhin/dockerfiles/tree/master/cuda-lasagne/cuda_v7.5)
* [Torch Docker](https://github.com/Kaixhin/dockerfiles/tree/master/cuda-torch-plus)