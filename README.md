<!--
 * @Description: In User Settings Edit
 * @Author: zerollzeng
 * @Date: 2019-08-23 09:16:35
 * @LastEditTime: 2020-03-06 17:12:14
 * @LastEditors: zerollzeng
 -->

![image](https://user-images.githubusercontent.com/38289304/71065174-aafc3100-21ab-11ea-9bcb-665d38181e74.png)

# tiny-tensorrt
A simple, efficient, easy-to-use nvidia TensorRT wrapper for cnn with c++ and python api,support caffe, uff and onnx format models. you will be able to deploy your model with tiny-tensorrt in few lines of code!

```c++
Trt* net = Trt();
net->CreateEngine(onnxModel, engineFile,maxBatchSize, int mode);
net->CopyFromHostToDevice(input, inputBindIndex);
net->Forward();
net->CopyFromDeviceToHost(output, outputBindIndex)
```

# News

Add support for dynamic shapes, **currently dynamic shape can not work with int8** - 2021-8-18

Upgrade to TensorRT 8.0 API, **checkout 7.x branch for use under TensorRT 7** - 2021-7-9

Better int8 calibrator api, refer to [User Guide](https://github.com/zerollzeng/tiny-tensorrt/blob/master/docs/UserGuide.md) - 2021-5-24

Remove caffe and uff support, convert to onnx with tf2onnx or keras.onnx. - 2021-4-23

Want to implement your own onnx plugin and don't know where to start? - 2021-1-29

[onnx plugin template](https://github.com/zerollzeng/tiny-tensorrt/blob/master/plugin/CuteSamplePlugin)

# Features
- [x] Add dynamic shapes support
- [x] Add DLA support
- [x] Custom plugin tutorial and well_commented sample
- [x] Custom onnx model output node
- [x] Engine serialization and deserialization
- [x] INT8 support
- [x] Python api support
- [x] Set device

# System Requirements
cuda 11.0+(recommended)

TensorRT 8

For python api, python 3.x and numpy in needed

# Installation
Make sure you had install dependencies list above, if you are familiar with docker, you can use [official docker](https://ngc.nvidia.com/catalog/containers/nvidia:tensorrt)
```bash
# clone project and submodule
git clone --recurse-submodules -j8 https://github.com/zerollzeng/tiny-tensorrt.git

cd tiny-tensorrt

mkdir build && cd build && cmake .. && make
```
Then you can intergrate it into your own project with libtinytrt.so and Trt.h, for python module, you get pytrt.so

# Docs

[User Guide](https://github.com/zerollzeng/tiny-tensorrt/blob/master/docs/UserGuide.md)

[Custom Plugin Tutorial](https://github.com/zerollzeng/tiny-tensorrt/blob/master/docs/CustomPlugin.md) (En-Ch)

# About License

For the 3rd-party module and TensorRT, you need to follow their license

For the part I wrote, you can do anything you want

