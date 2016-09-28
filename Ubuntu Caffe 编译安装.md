#Ubuntu 16.04下Caffe的编译安装
--

##待配置环境

	Caffe
	Nvidia-367.44 + CUDA 8.0 RC With Patch 1 + cuDNN 5.1
	OpenCV 3.1
	Anaconda 2
	MATLAB 2016b

##步骤

Ubuntu16.04配置

- 修改Ubuntu的软件更新源，添加清华大学源：

>https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/  

- 修改系统语言为汉语；修改系统的输入法框架；添加拼音输入法
- 采用软件更新器更新系统。

Nvidia显卡驱动安装

- 添加Nvidia驱动的ppa源

>		sudo add-apt-repository ppa:graphics-drivers/ppa
>		sudo apt-get update && sudo apt-get install nvidia-367

- 在软件更新器中更新驱动
- 重启

CUDA 配置

- 下载CUDA8.0 RC和 CUDA Patch两个文件
- 安装CUDA8.0 RC 和 CUDA Patch

>   	sudo dpkg -i cuda-repo-ubuntu1604-8-0-rc_8.0.27-1_amd.deb
>   	sudo apt-get update
>   	sudo apt-get install cuda
>  		重启
>   	用软件管理器安装CUDA Patch
>   	重启

cuDNN 5.1 配置

- 配置头文件
>   		sudo cp cudnn.h /usr/local/cuda/include/
- 配置动态链接库

>   	sudo cp lib* /usr/local/cuda/lib64
>   	cd /usr/local/cuda/lib64
>   	sudo rm -rf libcudnn.so libcudnn.so.5    #删除原有动态文件
>   	sudo ln -s libcudnn.so.5.0.5 libcudnn.so.5
>   	sudo ln -s libcudnn.so.5 libcudnn.so
>   	sudo gedit /etc/profile
>   	export PATH=$PATH:/usr/local/cuda/bin
>   	export LD_LIBRARY_PATH=$LD_LIBRARY_PATH :/usr/local/cuda/lib64
>   	sudo ldconfig

- 测试CUDA用例

>   	nvidia-smi #查看CUDA是否安装成功
>   	cp /usr/local/cuda/samples
>   	sudo make all –j8

To be continue

