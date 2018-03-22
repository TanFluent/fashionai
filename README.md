# TensorFlow Models

This repository contains a number of different models implemented in [TensorFlow](https://www.tensorflow.org):

The [official models](official) are a collection of example models that use TensorFlow's high-level APIs. They are intended to be well-maintained, tested, and kept up to date with the latest stable TensorFlow API. They should also be reasonably optimized for fast performance while still being easy to read. We especially recommend newer TensorFlow users to start here.

The [research models](https://github.com/tensorflow/models/tree/master/research) are a large collection of models implemented in TensorFlow by researchers. They are not officially supported or available in release branches; it is up to the individual researchers to maintain the models and/or provide support on issues and pull requests.

The [samples folder](samples) contains code snippets and smaller models that demonstrate features of TensorFlow, including code presented in various blog posts.

The [tutorials folder](tutorials) is a collection of models described in the [TensorFlow tutorials](https://www.tensorflow.org/tutorials/).


# Edit by TANFULUN

1）代码基于 models/research/inception 的项目开发。使用 InceptionV3（googlenet-22）对fashionai数据进行分类；

2）有两组代码：
    1.对warmingup数据（skirt_length_labes）这一大类别进行6分类
    
3）代码位置：
   /models/research/inception/
   所有代码用 jupyter notebook 编辑运行
   
4）运行代码须知

  （1）imagenet-pretrain模型位置（需要自行下载）：
    /inception/inception-v3-model/
    下载方法：
    # download the Inception v3 model
    curl -O http://download.tensorflow.org/models/image/imagenet/inception-v3-2016-03-01.tar.gz
    tar xzf inception-v3-2016-03-01.tar.gz
  （2）代码是在原项目中 flowers_train.py flowers_val.py flowers_data.py 基础上运行。目的是避免难搞的bazel编译，没功夫弄清楚这个。
      当处理新的数据集时，只需要修改flowers_data.py 中：
  类别个数以及数据集样本个数就行了
  def num_classes(self):
    """Returns the number of classes in the data set."""
    return 46

  def num_examples_per_epoch(self):
    """Returns the number of examples in the data subset."""
    if self.subset == 'train':
      return 71762
    if self.subset == 'validation':
      return 7969
