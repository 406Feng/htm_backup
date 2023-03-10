---
url: https://blog.csdn.net/ZeroChia/article/details/90749937
title:  Pycharm 使用 Anaconda 管理虚拟环境 Python 版本_ZeroChia 的博客 - CSDN 博客_pycharm 用 anaconda 的环境
date: 2022-07-08 15:24:52
tag: 
summary: 
---
最近开发的几个项目由于各种原因，要求使用的 Python 版本都不同，摸索使用 [Anaconda](https://so.csdn.net/so/search?q=Anaconda&spm=1001.2101.3001.7020) 来管理虚拟环境，在 Pycharm 中切换 Python 版本，非常方便。由于 Anaconda 是前一段时间安装的，当时也没记录安装流程，在此只大体整理一下使用方法。

## 1. 安装 Anaconda

在 [Anaconda 官网](https://www.anaconda.com/distribution/)中下载符合系统版本的安装包，我下的是 Python 3.7 version，默认自带 Python 3.7。  
安装过程应该挺顺利的，没留下什么印象，找找别的博客看看吧。  
安装成功后将 Anaconda3 安装路径及下面两个文件夹路径添加到系统环境变量，我的是这样：

```
C:\ProgramData\Anaconda3
C:\ProgramData\Anaconda3\Scripts
C:\ProgramData\Anaconda3\Library\bin 
```

## 2. 创建含有新 Python 版本的[虚拟环境](https://so.csdn.net/so/search?q=%E8%99%9A%E6%8B%9F%E7%8E%AF%E5%A2%83&spm=1001.2101.3001.7020)

打开命令行，使用命令创建一个带有新 Python 版本的虚拟环境，这里以 Python 3.5 为例：

```
conda create --name python35 python=3.5 
```

其中，–name 后的名字是可以自己随便起的。命令执行后会自动创建以 Python35 为名的虚拟环境，并展示以下信息，询问这些包是否一并安装，我选了是，根据自己需求选择吧。

```
## Package Plan ##

  environment location: C:\ProgramData\Anaconda3\envs\python35

  added / updated specs:
    - python=3.5


The following packages will be downloaded:

    package                    |            build
    ---------------------------|-----------------
    wheel-0.31.1               |           py35_0          81 KB
    vs2015_runtime-14.15.26706 |       h3a45250_4         2.4 MB
    pip-10.0.1                 |           py35_0         1.8 MB
    wincertstore-0.2           |   py35hfebbdb8_0          13 KB
    python-3.5.6               |       he025d50_0        18.2 MB
    certifi-2018.8.24          |           py35_1         140 KB
    setuptools-40.2.0          |           py35_0         597 KB
    ------------------------------------------------------------
                                           Total:        23.2 MB

The following NEW packages will be INSTALLED:

    certifi:        2018.8.24-py35_1
    pip:            10.0.1-py35_0
    python:         3.5.6-he025d50_0
    setuptools:     40.2.0-py35_0
    vc:             14.1-h0510ff6_4
    vs2015_runtime: 14.15.26706-h3a45250_4
    wheel:          0.31.1-py35_0
    wincertstore:   0.2-py35hfebbdb8_0

Proceed ([y]/n)? 
```

选择是之后，就是开始安装包，如下所示：

```
Downloading and Extracting Packages
wheel-0.31.1         | 81 KB     | ############################################################################ | 100%
vs2015_runtime-14.15 | 2.4 MB    | ############################################################################ | 100%
pip-10.0.1           | 1.8 MB    | ############################################################################ | 100%
wincertstore-0.2     | 13 KB     | ############################################################################ | 100%
python-3.5.6         | 18.2 MB   | ############################################################################ | 100%
certifi-2018.8.24    | 140 KB    | ############################################################################ | 100%
setuptools-40.2.0    | 597 KB    | ############################################################################ | 100%
Preparing transaction: done
Verifying transaction: done
Executing transaction: done
#
# To activate this environment, use:
# > activate python35
#
# To deactivate an active environment, use:
# > deactivate
#
# * for power-users using bash, you must source
# 
```

## 3. 进入虚拟环境

上边的创建环境也写得很清楚了，进入创建好的虚拟环境只需要命令

```
activate python35 
```

至此，就可以使用命令在此虚拟环境中一键安装项目所需依赖包

```
pip install -r requirement.txt 
```

## 4. 在 Pycharm 中使用新的虚拟环境

在 Pycharm 中打开项目，点击 File–>Settings–>Project:ProjectName–>Project Interpreter  
添加新的 Python 解释器：  

![](media/20190603143215990.png)

  

![](media/20190603143924616.png)

  
按照图中所示选择完成后点击 OK，就为项目应用了该虚拟环境。