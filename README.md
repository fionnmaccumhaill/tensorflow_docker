# tensorflow_docker
Example code for setting up and running TensorFlow from Docker instance. This was created on a MAC so there are small modifications that need to be made to make it work on Windows.

I am assuming you already have Docker installed. If not, go here and install it:

https://www.docker.com/products/overview

Once Docker is installed running a Docker instance with TensorFlow is as simple as typing:

sudo docker run --name tf1 -it -p 8888:8888 tensorflow/tensorflow

This will create a Docker instance and start TensorFlow.

Near the bottom of the terminal window you will find something that looks like this:

    The Jupyter Notebook is running at: http://[all ip addresses on your system]:8888/?token=635efbdc6c206fac2c5f03982410e6efd9b0c9a75620b0a3
    [I 02:03:22.344 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
    [C 02:03:22.344 NotebookApp] 

        Copy/paste this URL into your browser when you connect for the first time,
        to login with a token:
            http://localhost:8888/?token=635efbdc6c206fac2c5f03982410e6efd9b0c9a75620b0a3
            
Cut and paste the URL into your favorite browser and you are ready to start writing code.

The URL will put you in a jupyter session like this:

![Alt text](/jupyterBlank.jpg?raw=true "Jupyter Screenshot")