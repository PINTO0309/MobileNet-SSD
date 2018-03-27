# MobileNet-SSD
YoloV2 より超速 MobileNetSSD+Neural Compute Stick(NCS)+Raspberry Piによる爆速・高精度の複数動体検知 https://qiita.com/PINTO/items/b97b3334ed452cb555e2

# 動作イメージ
MobileNet-SSD + Neural Compute Stick + RaspberryPi3 / MultiStick(3本/Hard)

![Riders](https://github.com/PINTO0309/MobileNet-SSD/blob/master/media/Riders.gif)  ![MultiStick](https://github.com/PINTO0309/MobileNet-SSD/blob/master/media/MultiStick.jpeg)
# 環境
・RaspberryPi 3 + Raspbian Stretch

・NCSDK v1.12.00

・Intel Movidius Neural Compute Stick　１本

・OpenCV 3.4.1

・OpenGL

・numpy

・UVC対応のUSB-Webカメラ


# 環境構築
1. パッケージのインストール
```
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install python3-pip python3-numpy git cmake
```
2. NCSDKのインストール
```
$ cd ~
$ git clone https://github.com/movidius/ncsdk.git
$ cd ncsdk
$ make install
```
3. OpenCVのインストール
```
$ wget https://github.com/PINTO0309/OpenCVonARMv7/blob/master/libopencv3_3.4.1-20180304.1_armhf.deb
$ sudo apt install -y ./libopencv3_3.4.1-20180304.1_armhf.deb
$ sudo ldconfig
```
4. OpenGLのインストール
```
$ sudo apt-get install python-opengl
$ sudo -H pip3 install pyopengl
$ sudo -H pip3 install pyopengl_accelerate
$ sudo raspi-config
```
5. 「7.Advanced Options」-「A7 GL Driver」-「G2 GL (Fake KMS)」の順に選択し、Raspberry Pi のOpenGL Driver を有効化
6. 再起動
```
$ sudo reboot
```
7. リソース一式のダウンロード
```
$ cd ~
$ git clone https://github.com/PINTO0309/MobileNet-SSD.git
```
8. USB-WEBカメラ(UVC対応) と Neural Compute Stick をRaspberryPiのUSBポートへ接続
9. RaspberryPiとディスプレイをHDMIケーブルで接続
10. MobileNet-SSDの実行
```
$ cd MobileNet-SSD
$ python3 MultiStickSSD.py
```
