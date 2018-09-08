# [English] MobileNet-SSD
Ultra-fast MobileNet-SSD(MobileNetSSD) + Neural Compute Stick(NCS) than YoloV2 + Explosion speed by RaspberryPi.<br>
Multiple moving object detection with high accuracy.<br>
Video playback and object detection are executed asynchronously.<br>
In order to realize high speed rendering with multi stick, it is implemented in multithreading/OpenGL.<br>

**【Japanese Article】https://qiita.com/PINTO/items/b97b3334ed452cb555e2**<br><br>
**【USB Camera + MultiProcessing High performance version】 <br>
Below is the performance which is more than three times the performance of this repository program.<br>
I recommend that you refer to the following repository.<br>
https://github.com/PINTO0309/MobileNet-SSD-RealSense.git**

# Change history
[July 19, 2018]　Corresponds to NCSDK v2.05.00.02 / OpenCV 3.4.2 / FPS View<br>
[July 27, 2018]　**[Add an unnecessary version of OpenGL (USBCamera / MultiStick / MultiProcessing / RealSense)](https://github.com/PINTO0309/MobileNet-SSD-RealSense)**<br>

# Image of motion
MobileNet-SSD + Neural Compute Stick + RaspberryPi3 / MultiStick(3 Stick / Hard Motion)

**Youtube: https://youtu.be/sQnFbRSqIA8**

![Riders](https://github.com/PINTO0309/MobileNet-SSD/blob/master/media/Riders.gif)  ![MultiStick](https://github.com/PINTO0309/MobileNet-SSD/blob/master/media/MultiStick.jpeg)<br><br>

MobileNet-SSD + Neural Compute Stick(1 Stick) + RaspberryPi3 + USB Camera(640x480)<br>
**Youtube: https://youtu.be/_Cbt0gI8niQ**<br>
![Goku](https://github.com/PINTO0309/MobileNet-SSD/blob/master/media/Goku.gif)
# Environment
・RaspberryPi 3 + Raspbian Stretch

・NCSDK v2.05.00.02 (It does not work with NCSDK v1　**[v1 version is here](https://github.com/PINTO0309/MobileNet-SSD/tree/v1.0)**)

・Intel Movidius Neural Compute Stick　1 piece

・OpenCV 3.4.2

・OpenGL

・numpy

・(UVC)USB-Web Camera


# Building environment
1. Temporary extension of SWAP area
```
$ sudo nano /etc/dphys-swapfile
CONF_SWAPSIZE=2048

$ sudo /etc/init.d/dphys-swapfile restart swapon -s
```
2. Installing packages
```
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install python3-pip python3-numpy git cmake
```
3. Installing NCSDK
```
$ cd ~
$ git clone -b ncsdk2 https://github.com/movidius/ncsdk.git
$ cd ncsdk
$ make install
```
4. Installation of OpenCV
```
$ cd ~
$ wget https://github.com/PINTO0309/OpenCVonARMv7/raw/master/libopencv3_3.4.2-20180709.1_armhf.deb
$ sudo apt install -y ./libopencv3_3.4.2-20180709.1_armhf.deb
$ sudo ldconfig
```
5. Installing OpenGL
```
$ sudo apt-get install python-opengl
$ sudo -H pip3 install pyopengl
$ sudo -H pip3 install pyopengl_accelerate
$ sudo raspi-config
```
6. 「7.Advanced Options」-「A7 GL Driver」-「G2 GL (Fake KMS)」 and Activate Raspberry Pi's OpenGL Driver

7. Reboot
```
$ sudo reboot
```
8. Download complete set of resources
```
$ cd ~
$ git clone https://github.com/PINTO0309/MobileNet-SSD.git
```
9. Connect USB-WEB camera (UVC compatible) and Neural Compute Stick to RaspberryPi's USB port (self power USB-Hub required due to insufficient voltage when using Neural Compute Stick in multiple)

10. Connect RaspberryPi and display with HDMI cable

11. Running MobileNet-SSD
```
$ cd MobileNet-SSD
$ python3 MultiStickSSD.py
```
12. Reducing the SWAP area
```
$ sudo nano /etc/dphys-swapfile
CONF_SWAPSIZE=100

$ sudo /etc/init.d/dphys-swapfile restart swapon -s
```


# Procedure for generating original learning data
https://github.com/movidius/ncappzoo/tree/master/caffe/SSD_MobileNet<br>
https://github.com/FreeApe/VGG-or-MobileNet-SSD<br>
https://github.com/chuanqi305/MobileNet-SSD<br>
https://github.com/avBuffer/MobilenetSSD_caffe<br>
　
　
 
 
# [Japanese] MobileNet-SSD
YoloV2 より超速 MobileNetSSD(MobileNetSSD)+Neural Compute Stick(NCS)+Raspberry Piによる爆速・高精度の複数動体検知<br>
映像再生と物体検出は非同期実行。<br>
マルチスティックを実現するために、マルチスレッド かつ OpenGL で実装している。<br>
**【Qiita記事】 https://qiita.com/PINTO/items/b97b3334ed452cb555e2**<br>
**【RealSense D435 + MultiProcessing対応版】 https://github.com/PINTO0309/MobileNet-SSD-RealSense.git**

# 変更履歴
[2018/07/19]　NCSDK v2.05.00.02対応 / OpenCV 3.4.2対応 / FPS View対応<br>

# 動作イメージ
MobileNet-SSD + Neural Compute Stick + RaspberryPi3 / MultiStick(3本/Hard)

**Youtube: https://youtu.be/sQnFbRSqIA8**

![Riders](https://github.com/PINTO0309/MobileNet-SSD/blob/master/media/Riders.gif)  ![MultiStick](https://github.com/PINTO0309/MobileNet-SSD/blob/master/media/MultiStick.jpeg)<br><br>

MobileNet-SSD + Neural Compute Stick(1 Stick) + RaspberryPi3 + USB Camera(640x480)<br>
**Youtube: https://youtu.be/_Cbt0gI8niQ**<br>
![Goku](https://github.com/PINTO0309/MobileNet-SSD/blob/master/media/Goku.gif)
# 環境
・RaspberryPi 3 + Raspbian Stretch

・NCSDK v2.05.00.02 (NCSDK v1では動作しません　**[v1バージョンはこちら](https://github.com/PINTO0309/MobileNet-SSD/tree/v1.0)**)

・Intel Movidius Neural Compute Stick　１本

・OpenCV 3.4.2

・OpenGL

・numpy

・UVC対応のUSB-Webカメラ


# 環境構築
1. SWAP領域の一時的な拡張
```
$ sudo nano /etc/dphys-swapfile
CONF_SWAPSIZE=2048

$ sudo /etc/init.d/dphys-swapfile restart swapon -s
```
2. パッケージのインストール
```
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install python3-pip python3-numpy git cmake
```
3. NCSDKのインストール
```
$ cd ~
$ git clone https://github.com/movidius/ncsdk.git
$ cd ncsdk
$ make install
```
4. OpenCVのインストール
```
$ wget https://github.com/PINTO0309/OpenCVonARMv7/raw/master/libopencv3_3.4.2-20180709.1_armhf.deb
$ sudo apt install -y ./libopencv3_3.4.2-20180709.1_armhf.deb
$ sudo ldconfig
```
5. OpenGLのインストール
```
$ sudo apt-get install python-opengl
$ sudo -H pip3 install pyopengl
$ sudo -H pip3 install pyopengl_accelerate
$ sudo raspi-config
```
6. 「7.Advanced Options」-「A7 GL Driver」-「G2 GL (Fake KMS)」の順に選択し、Raspberry Pi のOpenGL Driver を有効化

7. 再起動
```
$ sudo reboot
```
8. リソース一式のダウンロード
```
$ cd ~
$ git clone https://github.com/PINTO0309/MobileNet-SSD.git
```
9. USB-WEBカメラ(UVC対応) と Neural Compute Stick をRaspberryPiのUSBポートへ接続(Neural Compute Stickをマルチで使用する場合は電圧が不足するためセルフパワーUSB-Hub必須)

10. RaspberryPiとディスプレイをHDMIケーブルで接続

11. MobileNet-SSDの実行
```
$ cd MobileNet-SSD
$ python3 MultiStickSSD.py
```
12. SWAP領域の縮小
```
$ sudo nano /etc/dphys-swapfile
CONF_SWAPSIZE=100

$ sudo /etc/init.d/dphys-swapfile restart swapon -s
```

# 独自学習データの生成手順
https://github.com/movidius/ncappzoo/tree/master/caffe/SSD_MobileNet<br>
https://github.com/FreeApe/VGG-or-MobileNet-SSD<br>
https://github.com/chuanqi305/MobileNet-SSD<br>
https://github.com/avBuffer/MobilenetSSD_caffe<br>
　
