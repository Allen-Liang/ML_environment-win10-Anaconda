# ML_environment-win10-Anaconda
## win10_conda_搭建ML环境（windows 10 64bit下安装Tensorflow+（Keras+theano）+opencv++VS2015+CUDA8.0+cudnn 5.1 GPU加速)

[一个教程一首歌](http://music.163.com/#/song?id=4876898 "卖假货的学长推荐，点了不后悔，哈哈！")<br>
![](https://github.com/Allen-Liang/ML_environment-win10-Anaconda/raw/master/1.PNG)<br>
![](https://github.com/Allen-Liang/ML_environment-win10-Anaconda/raw/master/2.PNG)<br>
![](https://github.com/Allen-Liang/ML_environment-win10-Anaconda/raw/master/3.PNG)<br>
![](https://github.com/Allen-Liang/ML_environment-win10-Anaconda/raw/master/4.PNG)<br>

1. conda create -n ml python=3.5  <br>
2. activate ml  <br>
3.（GPU版本）pip install --upgrade https://storage.googleapis.com/tensorflow/windows/gpu/tensorflow_gpu-0.12.0rc0-cp35-cp35m-win_amd64.whl  <br>
4.（如果3报错）则： pip install --upgrade --ignore-installed setuptools   <br>
   继续3步骤安装    <br>
5.由于安装的是GPU版的，我们还需要安装 Cuda Toolkit 8.0 和 cuDNN v5去 https://developer.nvidia.com/cuda-downloads 下载win10版本    <br>
6.默认安装下载下来的 cuda_8.0.44_win10.exe （推荐默认安装）<br>
  接下来我们可以检查 C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin（默认安装目录下，安装路径可以自定义）是否添加到了环境变量 （如果是默认安装，一般不会有问题）<br>

7.测试  <br>
$ nvcc -V  <br>
$ python  <br>
...    <br>
>>> import tensorflow as tf   <br>
>>> hello = tf.constant('Hello, TensorFlow!')   <br>
>>> sess = tf.Session()  <br>
>>> print(sess.run(hello))   <br>
Hello, TensorFlow!  <br>
>>> a = tf.constant(10)  <br>
>>> b = tf.constant(32)  <br>
>>> print(sess.run(a + b))  <br>
42  <br>
>>>  <br>


安装opencv3,基于python3.5  <br>
1. conda install -c https://conda.binstar.org/menpo opencv3  <br>
测试：$ python  <br>
      >>> import cv2  <br>

安装keras   <br>
1.conda install scipy  <br>
2.pip install keras   <br>
测试： $ python  <br>
      >>> import cv2  <br>





安装cuDNN  <br>
1.让速度更快一点，cuDNN可以在前面GPU加速基础上大概再提升1.5倍的速度，它由nVIDIA开发。  <br>
可以到nVIDIA官网上下载（https://developer.nvidia.com/rdp/cudnn-download）。下载之前需要注册，然后问一系列问题，请耐心弄完。  <br>
然后就可以下载了。不要下载错了，下载windows 10系统下64位的，建议下：cudnn-8.0-windows10-x64-v5.1.zip  <br>

2. 下载完成后解压缩。里面有bin、include、lib三个目录，将三个文件夹复制到安装CUDA的地方覆盖对应文件夹，默认文件夹在：  <br>
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0   <br>

3. 如何验证CuDNN是否配置成功呢？  <br>
打开Anaconda Prompt，输入python，再输入import tensorflow，显示的如果是下图这样子，不提示没有安装cudnn，就成功了。  <br>
![](https://github.com/Allen-Liang/ML_environment-win10-Anaconda/raw/master/1.PNG)<br>
