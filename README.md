# Yolov5_Win10_Ncnn_C++_VS2019
最近准备在工控机端利用NCNN部署Yolov5，在自己电脑上部署时需要注意一些细节，在此记录如下

# 环境要求

VS2019（Release x64）

CUDA 11.3

CUDNN 8.6

Opencv452

NCNN

**NCNN编译**

首先需要在windows上编译 ncnn，在此我是按照  https://blog.csdn.net/yohnyang/article/details/128384633 步骤进行编译的，主要是：

（1）编译protobuf

（2）编译NCNN

（3）环境配置

编译后将NCNN和protobuf库放在一起

# 属性表配置

**Opencv**

VC++目录 -> 包含目录：D:\Library\opencv452\build\include;

VC++目录 -> 库目录：D:\Library\opencv452\build\x64\vc15\lib;

链接器 -> 输入 -> 附加依赖项：opencv_world452.lib

**CUDA**

VC++目录 -> 包含目录：C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.3\include;

VC++目录 -> 库目录：C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.3\lib\x64;

链接器 -> 输入 -> 附加依赖项：C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.3\lib\x64\*.lib;

**Ncnn**

VC++目录 -> 包含目录：D:\Library\ncnn\build\include\google;D:\Library\ncnn\build\include\ncnn;D:\Library\ncnn\build\include;

VC++目录 -> 库目录：D:\Library\ncnn\build\lib;

链接器 -> 输入 -> 附加依赖项：ncnn.lib;libprotobuf.lib;

**其他配置**

属性表->配置属性->C/C++->预处理器->预处理器定义：NDEBUG; _CONSOLE; _CRT_SECURE_NO_WARNINGS;NOMINMAX;

# 工程建立

（1）建立工程，加载代码，代码是从 https://github.com/Tencent/ncnn/tree/master/examples 下载的yolov5.cpp

（2）加载模型，模型是从 https://github.com/nihui/ncnn-assets/tree/master/models 下载的[yolov5s_6.0.bin](https://github.com/nihui/ncnn-assets/blob/master/models/yolov5s_6.0.bin)和[yolov5s_6.0.param](https://github.com/nihui/ncnn-assets/blob/master/models/yolov5s_6.0.param)

# 联系

**有问题可以提issues 或者加qq群:722237896 询问**

