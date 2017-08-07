# tensorflow

A quick how-to on tensorflow based on **Siraj Raval** tutorial, **"Build a TensorFlow Image Classifier in 5 Min"**

## Install Docker
1. For Mac user:
    * Download and install this, https://www.docker.com/docker-mac
    * Once you have the above installed, download and instlal the following, https://www.docker.com/products/docker-toolbox
2. Once you have it installed, make sure to run **'Docker Quickstart Terminal'**
3. Let's prepare some other things, before we install tensorflow image
    * Create a 'tensorflow/tf_files' under your home directory; type the following
    * mkdir `~/tensorflow/tf_files`
    * This directory will hold all directories of images that we will be used for training
    * The structure of the directory should be as follows:
    <pre>
    ~/tensorflow/tf_files
      +-- darth_vader
         +-- dv1.jpg
         +-- dv2.jpg
         +-- dv3.jpg
         +-- ...
         +-- dv{n}.jpg
      +-- darth_maul
         +-- dm1.jpg
         +-- dm2.jpg
         +-- dm3.jpg
         +-- ...
         +-- dm{n}.jpg
      +-- kitten
         +-- ...
     </pre>
4. 
5. Now, let's download all required images to be saved in those directories above (darth_vader, darth_maul)
6. Now, let's install tensoflow image on the docker that you open through **'Docker Quickstart Terminal'**. 
7. In **'Docker Quickstart Terminal'**, type the following:
    * docker run -it -v /Users/lrpurba/latih/python/tensorflow/tf_files/:/star_wars/  gcr.io/tensorflow/tensorflow:latest-devel
