# JETSON NANO SETUP INSTALL
After installing jetpack, you can see that opencv and tensorflow version 1.14 are installed.
Some installation steps are required to run the example jetson-inference provided by NVIDIA.

## Installing system packages and prerequisites
Install the system packages needed to start jetson nano

    $ sudo apt-get install git cmake
    $ sudo apt-get install libatlas-base-dev gfortran
    $ sudo apt-get install libhdf5-serial-dev hdf5-tools
    $ sudo apt-get install python3-dev

## python package manager pip install

    $ wget https://bootstrap.pypa.io/get-pip.py
    $ sudo python3 get-pip.py
    $ rm get-pip.py

## virtualenv, virtualenvwrapper install

Install virtualenv and virtualenvwrapper to manage Python virtual environment

    $ sudo pip install virtualenv virtualenvwrapper

After installing virtualenv and virtualenvwrapper you need to update your ~ / .bashrc file.

    $ vi ~ / .bashrc

Update the ~ / .bashrc by entering the following characters at the end and saving them.

    # virtualenv and virtualenvwrapper
    export WORKON_HOME = $ HOME / .virtualenvs
    export VIRTUALENVWRAPPER_PYTHON = / usr / bin / python3
    source /usr/local/bin/virtualenvwrapper.sh

Load the ~ / .bashrc file with the source command.
    
    $ source ~ / .bashrc

Create virtual environment (It is better to create according to API or area of ​​use.)

    $ mkvirtualenv deep_learning -p python3

The above command creates a virtual environment called deep_learning in python3.

## Installing TensorFlow and Keras on the NVIDIA Jetson Nano

Before installation, use the following command to install in a virtual environment called deep_learning.
   
    $ workon deep_learning (same function as linux source activate deep laarning)

numpy install

    $ pip install numpy

It takes about 15 minutes to install, but it seems to take more time depending on the internet. (We recommend using a LAN cable for all installations.)

Tensorflow gpu install

    $ pip install --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v42 tensorflow-gpu == 1.13.1 + nv19.3

It is installed, but if it is different like opencv version, it may have difficulty in operation.

Finally, SciPy and Keras

    $ pip install scipy
    $ pip install keras

It took about 35 minutes, but it seems to take 50 minutes.

## jetson-inference

    $ git clone https://github.com/dusty-nv/jetson-inference
    $ cd jetson-inference
    $ git submodule update --init
    $ mkdir build
    $ cd build
    $ cmake ..
    $ make
    $ sudo make install

The above command is ready to use jetson-inference.

I will upload the jetson-inference example implementation later.
Send feedback
History
Saved
Community
