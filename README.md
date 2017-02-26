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

So now you want to save notebook which you spent seconds copying and pasting. How do you do that? From the File dropdown of course:

![Alt text](/jpuyterFile.jpg?raw=true "Jupyter File Dropdown")

If you click "Save and Checkpoint" here you will save something with the name "Untitled" which is probably something you don't want. Instead click "Rename" and give it some meaningful name like RunGraph and then click File-->Save and Checkpoint and your nifty little program will be saved.

Click back to the tab for your Jupyter Home tab and refresh. Now you will see your notebook:

![Alt text](/jupyterHome2.jpg?raw=true "Jupyter Home Page")

You are probably thinking this is great except for the part where my code is now saved inside my Docker container. I would much prefer it to be saved on my local hard drive if you don't mind. The simplist way to do that is to use the Jupyter:

File --> Download as --> Notebook (.ipynb)

![Alt text](/jupyterDownloadNotebook.jpg?raw=true "Jupyter Download Notebook")

Then you can save it to anywhere on your hard drive you want. You are probably thinking that is good but what I really want is to click "Save and Checkpoint" in the File dropdown and have it automagically saved to my hard drive. Can I do that? 

Yes. The Docker -v option allows you to save the notebooks to your local drive by mapping  the /notebooks directory in the container to wherever on your local drive you want to save the files. Use this command to start the Docker container and you are all set:

sudo docker run -v /Users/{user}/Desktop/notebooks:/notebooks --name tf3 -it -p 8888:8888 tensorflow/tensorflow

You should replace the {user} with the name of the user on MAC OS.
