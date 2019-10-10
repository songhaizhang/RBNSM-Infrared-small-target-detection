#获取谷歌账户授权
!apt-get install -y -qq software-properties-common python-software-properties module-init-tools
!add-apt-repository -y ppa:alessandro-strada/ppa 2>&1 > /dev/null
!apt-get update -qq 2>&1 > /dev/null
!apt-get -y install -qq google-drive-ocamlfuse fuse
from google.colab import auth
auth.authenticate_user()
from oauth2client.client import GoogleCredentials
creds = GoogleCredentials.get_application_default()
import getpass
!google-drive-ocamlfuse -headless -id={creds.client_id} -secret={creds.client_secret} < /dev/null 2>&1 | grep URL
vcode = getpass.getpass()
!echo {vcode} | google-drive-ocamlfuse -headless -id={creds.client_id} -secret={creds.client_secret}


#绑定谷歌云盘
!mkdir -p drive
!google-drive-ocamlfuse drive  -o nonempty

#安装深度学习的库
!pip install keras pandas numpy scipy

#opencv安装
!apt-get -qq install -y libsm6 libxext6 && pip install -q -U opencv-python

#显示当前的工作文件夹下的文件
!ls

#修改工作文件夹
import os
os.chdir("drive/cloud")


#py文件运行方式
!python3 drive/app/xxx.py

#网速测试
!pip install speedtest-cli

!speedtest-cli


#重启Google colab
!kill -9 -1

#运行脚本文件需要安装的文件
!pip install requests
!pip install requests_html

#CPU信息查看
!cat /proc/cpuinfo

#RAM信息查看
!cat /proc/meminfo

#查看在使用哪个GPU
from tensorflow.python.client import device_lib
device_lib.list_local_devices()

#查看是否使用GPU
import tensorflow as tf
tf.test.gpu_device_name()

#安装PyTorch： 
!pip install -q http://download.pytorch.org/whl/cu75/torch-0.2.0.post3-cp27-cp27mu-manylinux1_x86_64.whl torchvision 
import torch

#查看显存情况 
!/opt/bin/nvidia-smi

#安装XGBoost： 
!pip install -q xgboost 
import xgboost

#安装图形库GraphViz 
!apt-get -qq install -y graphviz && pip install -q pydot 
import pydot

#安装解压工具7zip Reader 
!apt-get -qq install -y libarchive-dev && pip install -q -U libarchive 
import libarchive

#安装其他的工具包使用下面的命令： 
!pip install or !apt-get install 想要安装的包

#卸载安装的某个库
!pip uninstall -y keras  注意这儿用-y是因为，google笔记本只会显示结果不能输入，因此避免安装过程中需要你输入yes什么的