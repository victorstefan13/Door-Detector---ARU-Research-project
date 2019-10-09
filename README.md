# Door Detector - ARU Research project

This project explains how to setup the enviroment in order to run the door detector. 

STEP 1 - Installing tensorflow object detection API (Ubuntu 16.04 or higher):
 
  The tensorflow object detection API requiers the following python 3.6 libraries: 
  Protobuf 3.0.0
  Python-tk
  Pillow 1.0
  lxml
  tf Slim (which is included in the "tensorflow/models/research/" checkout)
  Jupyter notebook
  Matplotlib
  Tensorflow (>=1.12.0)
  Cython
  contextlib2

For detailed steps to install Tensorflow, follow the Tensorflow installation instructions, however a typical user can install Tensorflow using one of the following commands:
 
 ````
#For CPU 
pip3 install tensorflow

#For GPU 
pip3 install tensorflow-gpu
````
The remaining libraries can be installed via apt-get:

````
sudo apt-get install protobuf-compiler python-pil python-lxml python-tk
pip3 install --user Cython
pip3 install --user contextlib2
pip3 install --user jupyter
pip3 install --user matplotlib
````
Using the command 'git clone', clone the following git repository on your local machine;

https://github.com/tensorflow/models.git

The Tensorflow Object Detection API uses Protobufs to configure model and training parameters. Before the framework can be used, the Protobuf libraries must be compiled. This should be done by running the following command from the tensorflow/models/research/ directory:

````
# From tensorflow/models/research/
protoc object_detection/protos/*.proto --python_out=.
````

When running locally, the tensorflow/models/research/ and slim directories should be appended to PYTHONPATH. This can be done by running the following from tensorflow/models/research/:
````
# From tensorflow/models/research/
export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim
````
Note: This command needs to run from every new terminal you start. If you wish to avoid running this manually, you can add it as a new line to the end of your ~/.bashrc file, replacing `pwd` with the absolute path of tensorflow/models/research on your system.

Finally to test your installation run the following command;

python object_detection/builders/model_builder_test.py

The above installation guide can be found at the following links; 

https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md

https://www.youtube.com/watch?v=COlbP62-B-U&list=PLQVvvaa0QuDcNK5GeCQnxYnSSaar2tpku

STEP 2 - Installing Intel OpenVINO SDK on Raspberry Pi:

Requirements:

Hardware

    Raspberry Pi* board with ARM* ARMv7-A CPU architecture. Check that uname -m returns armv7l.

    One of Intel® Movidius™ Visual Processing Units (VPU):
    Intel® Movidius™ Neural Compute Stick
    Intel® Neural Compute Stick 2

Operating Systems

    Raspbian* Buster, 32-bit
    Raspbian* Stretch, 32-bit

Software

    CMake* 3.7.2 or higher
    
First you must download OpenVINO toolkit from the following link - https://download.01.org/opencv/2019/openvinotoolkit/

Open the Terminal* or your preferred console application.
Go to the directory in which you downloaded the OpenVINO toolkit. This document assumes this is your ~/Downloads directory. If not, replace ~/Downloads with the directory where the file is located.

``
cd ~/Downloads
``

By default, the package file is saved as l_openvino_toolkit_raspbi_p_<version>.tgz. Create an installation folder.
 
``
sudo mkdir -p /opt/intel/openvino
``

Unpack the archive:

``
sudo tar -xf l_openvino_toolkit_raspbi_p_<version>.tgz --strip 1 -C /opt/intel/openvino
``

Now the OpenVINO toolkit components are installed. Additional configuration steps are still required. Continue to the next sections to install External Software Dependencies, configure the environment and set up USB rules.

CMake* version 3.7.2 or higher is required for building the Inference Engine sample application. To install, open a Terminal* window and run the following command:

``
sudo apt install cmake
``

You must update several environment variables before you can compile and run OpenVINO toolkit applications. Run the following script to temporarily set the environment variables:

``
source /opt/intel/openvino/bin/setupvars.sh
``

NOTE: OpenVINO environment variables are removed when you close the shell. As an option, you can permanently set the environment variables as follows:
``
echo "source /opt/intel/openvino/bin/setupvars.sh" >> ~/.bashrc
``

To test your change, open a new terminal. You will see the following:

``
[setupvars.sh] OpenVINO environment initialized
``

Add the current Linux user to the users group:

``
sudo usermod -a -G users "$(whoami)"
``

Log out and log in for it to take effect.If you didn't modify .bashrc to permanently set the environment variables, run setupvars.sh again after logging in. To perform inference on the Intel® Movidius™ Neural Compute Stick or Intel® Neural Compute Stick 2, install the USB rules running the install_NCS_udev_rules.sh script:

``
sh /opt/intel/openvino/install_dependencies/install_NCS_udev_rules.sh
``

The installation is now complete. 








