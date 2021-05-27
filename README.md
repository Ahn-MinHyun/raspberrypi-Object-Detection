# raspberrypi-Object-Detection 방법

## 준비물

raspberrypi
raspverry pi camera

## 환경 설정
1. 라즈베리 파이 업데이트 
2. TensorFlow 설치
3. OpenCV 설치 
4. Protobuf 설치 및 컴파일
5. Object Detection에 필요한 파일 다운 및 환경설정
6. Object Detection 실행


### 1. 라즈베리 파이 업데이트

```
sudo apt-get update
sudo apt-get dist-upgrade
```
- 카메라 설정

raspberry pi Configuration 설정으로 들어가 picamera를 연결해준다.

![image](https://user-images.githubusercontent.com/78781222/119777467-287bb300-bf01-11eb-98aa-740f78dfbd64.png)


리부팅을 하면 카메라가 연결되어 있다.
```
sudo reboot
```

### 2. TensorFlow 설치

```
pip3 install tensorflow
```
```
sudo apt-get install libatlas-base-dev
```

종속 라이브러리 설치
```
sudo pip3 install pillow lxml jupyter matplotlib cython
sudo apt-get install python-tk
```


### 3. OpenCV 설치 
```
sudo apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev
sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
sudo apt-get install libxvidcore-dev libx264-dev
sudo apt-get install qt4-dev-tools libatlas-base-dev
```

```
sudo pip3 install opencv-python
```

### 4. Protobuf 설치 및 컴파일
```
sudo apt-get install protobuf-compiler
```
`protoc --version`을 확인해 봤을 때 `libprotoc 3.6.1`나 비슷하게 나올 것이다. 

### 5. Object Detection에 필요한 파일 다운 및 환경설정
```
mkdir tensorflow1
cd tensorflow1
```

```
git clone --depth 1 https://github.com/tensorflow/models.git
```

- bashrc의 파일로 들어가 맨 마지막 줄에  

```
sudo vi ~/.bashrc
```

이 코드를 추가한다.

```
export PYTHONPATH=$PYTHONPATH:/home/pi/tensorflow1/models/research:/home/pi/tensorflow1/models/research/slim

```

- 컴파일
이 명령은 모든 "name".proto 파일을 "name_pb2".py 파일로 변환
```
cd /home/pi/tensorflow1/models/research
protoc object_detection/protos/*.proto --python_out=.
```

- SSDLite-MobileNet 모델을 다운로드
```
cd /home/pi/tensorflow1/models/research/object_detection
```
압축해제 
```
wget http://download.tensorflow.org/models/object_detection/ssdlite_mobilenet_v2_coco_2018_05_09.tar.gz
tar -xzvf ssdlite_mobilenet_v2_coco_2018_05_09.tar.gz
```

### 6. Object Detection 실행

- Object Detection 파일 다운로드 
```
wget https://raw.githubusercontent.com/Ahn-MinHyun/raspberrypi-Object-Detection/main/Object_detection_picamera.py
```

- 실행 

```
python3 Object_detection_picamera.py 
```



