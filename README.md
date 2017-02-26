# tensorflow_docker

IN PROCESS OF EDITING ... this will be removed when it is ready to use

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

As you can see there are a couple of notebooks already in my jupyter session. Ignore those since they will not show up in your session. Click on the "New" button in the upper right hand corner and select Python2 from the dropdown. You will then be presented with a blank notebook page like this:

![Alt text](/jupyterNotebookBlank.jpg?raw=true "Jupyter Notebook")

Now we are ready to write (or cut and paste) some Python code into the notebook.

Copy and paste this code into the box "In [ ]:"

    import tensorflow as tf
    import matplotlib.pyplot as mp
    import numpy as np

    sn = 200

    x = np.linspace(0, 2*np.pi, sn, dtype=np.float32)
    mp.plot (x, np.sin(x**2))
    mp.title ("A simple chirp - " + str(sn))

    sess = tf.Session()
    init = tf.global_variables_initializer()

    sess.run(init)

    mp.show()
    
Then run the code by clicking the run cell button in the toolbar. Your screen should now look like this:

![Alt text](/jupyterRunGraph.jpg?raw=true "Jupyter Run Graph")

