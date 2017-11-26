# tensorflow-cuda

### It has been awhile since I wrote my first post and today I decided to write the next one. So here is the story, I was in Google HQ Dublin for GDG DevFest 2017 and one of the codelabs provided was on Tensorflow.

### While poking around in the codelab for setting up the environment, one of the options is to use Tensorflow with GPUs, therefore I decided to use take advantage of my Nvidia graphic cards and give a try to the setup.

 ### This post is a collection of guidelines on how to setup NVIDIA drivers if you have a gaming laptop with Linux.

### Let's get a first overview on why you would love to do this in the first place.


## **What is a GPU?** 

> ### "It is a specialized electronic circuit designed to rapidly manipulate and alter memory to accelerate the creation of images in a frame buffer intended for output to a display device."

![NVIDIA Geforce GTX 860M  ](./images/geforce.png)

## **Architecturally**:

 ### **CPU** is composed of just **few cores** with lots of cache memory that can handle a **few software threads** at a time.

 ###  **GPU** is composed of **hundreds of cores** that can handle thousands of threads simultaneously.

</br>

![ CPU vs GPU cores  ](./images/gpu_cpu.jpg)

## How GPUs accelerate software applications?

> GPU has a massively parallel architecture consisting of thousands of smaller, more efficient cores designed for handling multiple tasks simultaneously.

</br>
![ GPU Acceleration  ](./images/gpu_acceleration.png)

### What is CUDA 

### CUDA is a parallel computing platform and programming model that enables dramatic increases in computing performance by harnessing the power of the graphics processing unit (GPU).

### How to setup your gaming laptop with NVIDIA Graphic Cards to use Tensorflow.

In order to setup


Checkout your graphic card model 
Check secureboot is disabled
Check your graphic card is enabled via Bios

Installation Guide Linux :: CUDA Toolkit Documentation
The installation instructions for the CUDA Toolkit on Linux.docs.nvidia.com
NVIDIA cuDNN
The NVIDIA CUDA® Deep Neural Network library (cuDNN) is a GPU-accelerated library of primitives for deep neural…developer.nvidia.com
