# JetsonNano-ROS2

## ROS2 설치
<details>
<summary> 설치 방법 </summary>
<div markdown="1">

```
$ sh ./install_ros2_jetson_nano.sh
$ sh ./plus.sh
```

### SD 카드 파티션 늘리는 방법

[참고 사이트](https://omorobot.gitbook.io/manual/product/omo-r1mini/r1mini-pro/jetson-nano)
```
$ sudo apt update
$ sudo apt install -y gparted
$ sudo gparted
```
</div>
</details>

-----

## Real-time Detection 

```
# Install system packages required by TensorFlow
$ sudo apt-get update
$ sudo apt-get install libhdf5-serial-dev hdf5-tools libhdf5-dev zlib1g-dev zip libjpeg8-dev liblapack-dev libblas-dev gfortran
```

```
# Install and upgrade pip3
$ sudo apt-get install python3-pip
$ sudo pip3 install -U pip testresources setuptools==65.5.0 
```

```
# Install the Python package dependencies.
$ sudo pip3 install -U numpy==1.21.1 future==0.18.2 mock==3.0.5 keras_preprocessing==1.1.2 keras_applications==1.0.8 gast==0.4.0 protobuf pybind11 cython pkgconfig packaging h5py==3.6.0
```

```
# Install Tensorflow.
$ sudo pip3 uninstall tensorflow
$ sudo pip3 install tensorflow

$ sudo pip uninstall numpy
$ pip install numpy --upgrade
```

여기서부터 하면댐 사실상
```
$ source /opt/ros/foxy/setup.bash
$ colcon build
$ source ./install/local_setup.bash
```

termainal 1
```
$ ros2 run image_tools cam2image
```

terminal 2
```
$ ros2 run live_detection live_detector

# (option)
$ ros2 run live_detection live_detector -P {ckpt_path}
or
$ ros2 run live_detection live_detector -ckpt-path {ckpt_path}
```
