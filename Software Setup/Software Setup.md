# Initial Software Setup
Before running through any JetRacer modules, follow these steps to download the necessary dependencies on the Jetson Nano

## Flash Jetson Nano Image
Setup the base image for the 2GB Jetson Nano following [these instructions](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-2gb-devkit#intro)
You should use a microSD card of at least 64GB
On the existing Jetson Nanos, the username is *Jetson* and the password is **ee497*.

## Install Necessary Dependencies
Download dependencies by entering the following commands into the terminal:

### Install setup tools
`sudo apt-get update

sudo apt-get install python3-setuptools

sudo apt-get install python3-pip`

`sudo pip3 install packaging
sudo pip3 install traitlets`

### Install pytorch
`sudo apt-get install python3-pip libjpeg-dev libopenblas-dev libopenmpi-dev libomp-dev
sudo -H pip3 install future
sudo pip3 install -U --user wheel mock pillow
sudo -H pip3 install testresources`

### Install JetCam Python package
`cd $HOME
git clone https://github.com/NVIDIA-AI-IOT/jetcam
cd jetcam
sudo python3 setup.py install`

### Install torch2trt Python package
`cd $HOME
git clone https://github.com/NVIDIA-AI-IOT/torch2trt
cd torch2trt
sudo python3 setup.py install`

### Install JetRacer package
`cd $HOME
git clone https://github.com/NVIDIA-AI-IOT/jetracer
cd jetracer
sudo python3 setup.py install`

Put JetsonNano int 5W mode
`sudo nvpmodel -m1`

Now, you can run Nvidia's basic motion example