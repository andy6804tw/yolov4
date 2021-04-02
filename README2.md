# YOLOv4

## 下載repo

```
git clone 
```

## Step 1: 編譯 darknet
我們透過 darknet 網路訓練一個 Yolo v4 物件偵測。darknet 是一個較為輕型的開源深度學習框架，其主要特點是基於 C 與 CUDA 並且容易安裝執行。執行 `build_darknet.ipynb` ，並遵循以下步驟後即可得到編譯好的 darknet。

- clone darknet
- 修改 Makefile
- 編譯 darknet

### 1-1 clone darknet
首先要先 git clone Darknet github:

```
git clone https://github.com/AlexeyAB/darknet
```

### 1-2 修改 Makefile
透過 `sed -i` 指令修改剛 clone 下來的 darknet 裡去修改 Makefile，將 GPU, CUDNN, CUDNN_HALF, OPENCV 修改為1。(預設值為0)

```
!sed -i "s/GPU=0/GPU=1/g" darknet/Makefile
!sed -i "s/CUDNN=0/CUDNN=1/g" darknet/Makefile
!sed -i "s/CUDNN_HALF=0/CUDNN_HALF=1/g" darknet/Makefile
!sed -i "s/OPENCV=0/OPENCV=1/g" darknet/Makefile
```

修改後可以看到 `darknet/Makefile` 中的 GPU, CUDNN, CUDNN_HALF, OPENCV 皆變為 1。

```
GPU=1
CUDNN=1
CUDNN_HALF=1
OPENCV=1
```

### 1-3 編譯 darknet
上述參數修改後，就可以開始編譯 darknet 網路。

```
!cd darknet; make
```

## Step 2: 訓練 car

- 轉換 voc 格式到 txt 格式
- 設定 cfg
- 修改預設 anchors 值