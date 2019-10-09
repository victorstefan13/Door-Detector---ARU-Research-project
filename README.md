# Door Detector - ARU Research project

This project explains how to setup the enviroment in order to run the door detector. 

Step 1 - Installing tensorflow object detection API (Ubuntu 16.04 or higher);
 
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

