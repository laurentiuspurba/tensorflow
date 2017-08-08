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
5. Now, let's download all required images to be saved in those directories above (darth_vader, darth_maul). You can use the following links to download darth vader and darth maul:
    * [Darth Vader](https://www.google.com/search?q=darth+vader&source=lnms&tbm=isch&sa=X&ved=0ahUKEwi9g8GVqcbVAhUK8GMKHUc9DlwQ_AUICigB&biw=1276&bih=703)
        * Once you open the above link opened, click `Fatkun Batch Download Image` icon
        * A modal window will be opened, click on `This Tab`
        * Click on `More Options` and make sure to select `Rename based on pic_{NO001}.{EXT}` option
        * Once you have it downloaded, make sure to move these files to `~/tensorflow/tf_files`
    * [Darth Maul](https://www.google.com/search?biw=1276&bih=703&tbm=isch&sa=1&q=darth+maul&oq=darth+maul&gs_l=psy-ab.3..0l4.159357.159830.0.160359.4.4.0.0.0.0.166.351.2j1.3.0....0...1.1.64.psy-ab..1.3.351.816QVobFZ9w)
        * Do the same steps as the [Dart Vader] above
6. Now, let's install tensoflow image on the docker that you open through **'Docker Quickstart Terminal'**. Type the following in your **'Docker Quickstart Terminal'**
    * `docker run -it -v ~/tensorflow/tf_files/:/star_wars/ gcr.io/tensorflow/tensorflow:latest-devel`
What the above command does is:
    * It maps your host `~/tensorflow/tf_files` directory to `/star_wars/` directory in tensorflow docker container
    * You will be logged in to tensorflow docker container
7. Now, you are in `tensorflow` docker container, do the following:
    * `cd /tensorflow`
    * `git pull`
8. Now, it's time to train the model (darth_vader and darth_maul):
Make sure you are in `tensorflow` docker container, and in `/tensorflow/` directory, and type the following:
```
python tensorflow/examples/image_retraining/retrain.py \
--bottleneck_dir=/tf_files/bottlenecks \
--how_many_training_steps 500 \
--model_dir=/tf_files/inception \
--output_graph=/tf_files/retrained_graph.pb \
--output_labels=/tf_files/retrained_labels.txt \
--image_dir /star_wars
```
If everything is setup properly, you will see similar output as follows:
```
>> Downloading inception-2015-12-05.tgz 100.0%
Successfully downloaded inception-2015-12-05.tgz 88931400 bytes.
Looking for images in 'darth_maul'
Looking for images in 'darth_vader'
Looking for images in 'kitten'
No files found
2017-08-08 00:49:13.566091: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.1 instructions, but these are available on your machine and could speed up CPU computations.
2017-08-08 00:49:13.566173: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use SSE4.2 instructions, but these are available on your machine and could speed up CPU computations.
2017-08-08 00:49:13.566235: W tensorflow/core/platform/cpu_feature_guard.cc:45] The TensorFlow library wasn't compiled to use AVX instructions, but these are available on your machine and could speed up CPU computations.
Creating bottleneck at /tf_files/bottlenecks/darth_maul/pic_003.jpg.txt
2017-08-08 00:49:14.095826: W tensorflow/core/framework/op_def_util.cc:332] Op BatchNormWithGlobalNormalization is deprecated. It will cease to work in GraphDef version 9. Use tf.nn.batch_normalization().
Creating bottleneck at /tf_files/bottlenecks/darth_maul/pic_004.jpg.txt
Creating bottleneck at /tf_files/bottlenecks/darth_maul/pic_006.jpg.txt
...
...
...
2017-08-08 00:51:07.991467: Step 480: Validation accuracy = 100.0% (N=100)
2017-08-08 00:51:08.811397: Step 490: Train accuracy = 100.0%
2017-08-08 00:51:08.811650: Step 490: Cross entropy = 0.020678
2017-08-08 00:51:08.896350: Step 490: Validation accuracy = 100.0% (N=100)
2017-08-08 00:51:09.644563: Step 499: Train accuracy = 100.0%
2017-08-08 00:51:09.644881: Step 499: Cross entropy = 0.019680
2017-08-08 00:51:09.738435: Step 499: Validation accuracy = 100.0% (N=100)
Final test accuracy = 100.0% (N=7)
Converted 2 variables to const ops.
```
9. Now, we want to write a script that uses trained classifier to detect if a given image contains Darth Vader. Open a new terminal windows, and do the following:
    * `cd ~/tensorflow/tf_files`
    * Create a new file. You can name it whatever you want. [Source code](./tf_classify.py)
