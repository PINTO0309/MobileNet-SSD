# MobileNet-SSD
YoloV2 より超速 MobileNetSSD+Neural Compute Stick(NCS)+Raspberry Piによる爆速・高精度の複数動体検知 https://qiita.com/PINTO/items/b97b3334ed452cb555e2

# 動作イメージ
MobileNet-SSD MultiStick(3本/Hard)

![Riders](https://github.com/PINTO0309/MobileNet-SSD/blob/master/media/Riders.gif)

# 環境
・RaspberryPi 3 + Raspbian Stretch

・NCSDK v1.12.00

・Intel Movidius Neural Compute Stick　１本

・OpenCV 3.4.1

・OpenGL

・numpy

・Samba

・UVC対応のUSB-Webカメラ


# 環境構築
1. OpenCVのインストール
```
wget https://github.com/PINTO0309/OpenCVonARMv7/blob/master/libopencv3_3.4.1-20180304.1_armhf.deb
sudo apt install -y ./libopencv3_3.4.1-20180304.1_armhf.deb
sudo ldconfig
```
