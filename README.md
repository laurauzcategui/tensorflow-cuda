# tensorflow-cuda

It has been awhile since I wrote my first post and today I decided to write the next one. So here is the story, I was in Google HQ Dublin for GDG DevFest 2017 and one of the codelabs provided was on Tensorflow.

While poking around in the codelab for setting up the environment, one of the options is to use Tensorflow with GPUs, therefore I decided to use take advantage of my Nvidia graphic cards and give a try to the setup.

**Disclaimer** : This post is a collection of guidelines on how to setup NVIDIA drivers if you have a gaming laptop with Linux. You might need to change few steps based on what distribution you are running on.

### How is my setup:
* Distribution: **[Ubuntu 17.04](https://wiki.ubuntu.com/ZestyZapus/ReleaseNotes)**
* Laptop Model: **[Lenovo Y50-70](https://www.cnet.com/products/lenovo-y50-70-laptop-59440640-black-web-special-4th-generation-intel-core-i7-4720hq-2-60ghz-1600mhz-6mb/specs/)**
* Nvidia graphic card: **[GeForce GTX 860](https://www.geforce.com/hardware/notebook-gpus/geforce-gtx-860m/specifications)**

#### Let's get a first overview on why you would love to do this in the first place.


## **What is a GPU?** 

> ### "It is a specialized electronic circuit designed to rapidly manipulate and alter memory to accelerate the creation of images in a frame buffer intended for output to a display device."

![NVIDIA Geforce GTX 860M  ](./images/geforce.png)

## **Architecturally**:

* **CPU** is composed of just **few cores** with lots of cache memory that can handle a **few software threads** at a time.

* **GPU** is composed of **hundreds of cores** that can handle thousands of threads simultaneously.

</br>

![ CPU vs GPU cores  ](./images/gpu_cpu.jpg)

## How GPUs accelerate software applications?

> GPU has a massively parallel architecture consisting of thousands of smaller, more efficient cores designed for handling multiple tasks simultaneously.

</br>

![ GPU Acceleration  ](./images/gpu_acceleration.png)

### What is CUDA 

> CUDA is a parallel computing platform and programming model that enables dramatic increases in computing performance by harnessing the power of the graphics processing unit (GPU).

**************************
# How to setup your gaming laptop with NVIDIA Graphic Cards to use Tensorflow.

## NVIDIA requirements to run TensorFlow with GPU support
1. CUDA® Toolkit 8.0. For details, see NVIDIA's documentation. Ensure that you append the relevant Cuda pathnames to the LD_LIBRARY_PATH environment variable as described in the NVIDIA documentation.


- In order to get the CUDA Toolkit, first verify if you have a CUDA capable GPU


  `lspci | grep -i nvidia`

Note: if this step does not display any output, go and check the following in the BIOS and also lookup your graphic card in the list of cuda drivers provided by NVIDIA.

- Verify you have a supported version of linux

`uname -m && cat /etc/*release`

And crosscheck against the table at the very beggining of the documentation.

- Verify you have your gcc installed.

`gcc --version`

**Note**: If you run into problems when running tensorflow due to gcc checkout: [gcc problems with cuda nvcc ](https://stackoverflow.com/questions/6622454/cuda-incompatible-with-my-gcc-version)

- Verify your system has the correct Kernel and headers installed.

First check the kernel version

`uname -r`

Then, install the headers for the current version of the kernel you are running on:

`sudo apt-get install linux-headers-$(uname -r)`

- Finally install CUDA and CUDA Toolkit.

`sudo apt install cuda-8-0`

** Note** : **Do Not** install latest version cuda-9-0, as October 2017, CUDA 9.0 is not supported by tensorflow yet.

- Install And the NVIDIA drivers compatible with your graphic card.

`sudo apt install nvidia-367`

**Note**: Again try not to install the latest version as it might not be supported by your graphic card.

### Post installation actions ###

* Setup your environment.

  `export PATH=/usr/local/cuda-8.0/bin${PATH:+:${PATH}}`

If you use the runfile method, additionally export the following, depending if you are:
  * Running on 64 bit

  `export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}`

  * Running on 32 bit

2. The NVIDIA drivers associated with CUDA Toolkit 8.0.
cuDNN v6.0. For details, see NVIDIA's documentation. Ensure that you create the CUDA_HOME environment variable as described in the NVIDIA documentation.


3. GPU card with CUDA Compute Capability 3.0 or higher. See NVIDIA documentation for a list of supported GPU cards.

*********



Checkout your graphic card model 
Check secureboot is disabled
Check your graphic card is enabled via Bios

Installation Guide Linux :: CUDA Toolkit Documentation
The installation instructions for the CUDA Toolkit on Linux.docs.nvidia.com
NVIDIA cuDNN
The NVIDIA CUDA® Deep Neural Network library (cuDNN) is a GPU-accelerated library of primitives for deep neural…developer.nvidia.com
