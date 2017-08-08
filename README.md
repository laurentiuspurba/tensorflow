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
4. To make easier to download all required files, make sure to install this chrome extension, `Fatkun Batch Download Image`
5. Now, let's download all required images to be saved in those directories above (darth_vader, darth_maul)
You can use the following links to download darth vader and darth maul:
    * [Darth Vader](https://www.google.com/search?q=darth+vader&source=lnms&tbm=isch&sa=X&ved=0ahUKEwi9g8GVqcbVAhUK8GMKHUc9DlwQ_AUICigB&biw=1276&bih=703)
        * Once you open the above link opened, click `Fatkun Batch Download Image` icon
        * A modal window will be opened, click on `This Tab`
        * Click on `More Options` and make sure to select `Rename based on pic_{NO001}.{EXT}` option
        * Once you have it downloaded, make sure to move these files to `~/tensorflow/tf_files`
    * [Darth Maul](https://www.google.com/search?biw=1276&bih=703&tbm=isch&sa=1&q=darth+maul&oq=darth+maul&gs_l=psy-ab.3..0l4.159357.159830.0.160359.4.4.0.0.0.0.166.351.2j1.3.0....0...1.1.64.psy-ab..1.3.351.816QVobFZ9w)
        * Do the same steps as the [Dart Vader] above
6. Now, let's install tensoflow image on the docker that you open through **'Docker Quickstart Terminal'**. 
7. In **'Docker Quickstart Terminal'**, type the following:
    * docker run -it -v /Users/lrpurba/latih/python/tensorflow/tf_files/:/star_wars/  gcr.io/tensorflow/tensorflow:latest-devel
