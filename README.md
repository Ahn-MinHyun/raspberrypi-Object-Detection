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

### 2. TensorFlow 설치

```
pip3 install tensorflow
```
```
sudo apt-get install libatlas-base-dev
```

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

picamera를 연결해준다.





