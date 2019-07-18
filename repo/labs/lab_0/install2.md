## Install and Start Docker Desktop

    https://www.docker.com/get-started


## Spin up a Docker Tensorflow Container with Python 3


    docker pull tensorflow/tensorflow:latest-py3-jupyter
    
    docker run -it --rm -p 8888:8888 tensorflow/tensorflow:latest-py3-jupyter

### Copy and Paste The TF Link and token into browser


for example .... "127.0.0.1:8888/?token=4f65e58c2790574db951ed4ee98903f96998a8d50250e0ce"

###  Create a python 3 notebook 


Click the new button in the top right hand corner

Run the following code that should output TF version

    import tensorflow as tf
    import numpy
    import matplotlib
    print(tf.__version__)

    
Your finished!



## Troubleshooting

docker container ps
docker container kill <container-id>
    
    