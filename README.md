# YOLOv5-Lite：Customized for telecmmunication towers detection for drones  

![论文插图](https://user-images.githubusercontent.com/82716366/167448925-a431d3a4-ad5d-491d-be95-c90701122a54.png)

Perform a series of ablation experiments on yolov5 to make it lighter (smaller Flops, lower memory, and fewer parameters) and faster (add shuffle channel, yolov5 head for channel reduce. It can infer at least 10+ FPS On the Raspberry Pi 4B when input the frame with 320×320) and is easier to deploy (removing the Focus layer and four slice operations, reducing the model quantization accuracy to an acceptable range).</br>

In this project, this model is specifically designed to make it easier to detect the tip of a telecommunications tower so that the drone can maintain its path using its detection and centering.</br>
![image](https://github.com/MhmdRdbri/YOLOv5-Lite-Telecommunication-Detection/blob/main/test1.jpg)

## Example of images that model can detect

![image](https://github.com/MhmdRdbri/YOLOv5-Lite-Telecommunication-Detection/blob/main/test6.png)
![image](https://github.com/MhmdRdbri/YOLOv5-Lite-Telecommunication-Detection/blob/main/test4.jpg)
![image](https://github.com/MhmdRdbri/YOLOv5-Lite-Telecommunication-Detection/blob/main/test3.jpg)
![image](https://github.com/MhmdRdbri/YOLOv5-Lite-Telecommunication-Detection/blob/main/test2.jpg)


## Comparison of ablation experiment results

  ID|Model | Input_size|Flops| Params | Size（M） |Map@0.5|Map@.5:0.95
 :-----:|:-----:|:-----:|:----------:|:----:|:----:|:----:|:----:|
001| yolo-fastest| 320×320|0.25G|0.35M|1.4| 24.4| -
002| YOLOv5-Lite<sub>e</sub><sup>ours</sup>|320×320|0.73G|0.78M|1.7| 35.1|-|
003| NanoDet-m| 320×320| 0.72G|0.95M|1.8|- |20.6
004| yolo-fastest-xl| 320×320|0.72G|0.92M|3.5| 34.3| -
005| YOLOX<sub>Nano</sub>|416×416|1.08G|0.91M|7.3(fp32)| -|25.8|
006| yolov3-tiny| 416×416| 6.96G|6.06M|23.0| 33.1|16.6
007| yolov4-tiny| 416×416| 5.62G|8.86M| 33.7|40.2|21.7
008| YOLOv5-Lite<sub>s</sub><sup>ours</sup>| 416×416|1.66G |1.64M|3.4| 42.0|25.2
009| YOLOv5-Lite<sub>c</sub><sup>ours</sup>| 512×512|5.92G |4.57M|9.2| 50.9|32.5| 
010| NanoDet-EfficientLite2| 512×512| 7.12G|4.71M|18.3|- |32.6
011| YOLOv5s(6.0)| 640×640| 16.5G|7.23M|14.0| 56.0|37.2
012| YOLOv5-Lite<sub>g</sub><sup>ours</sup>| 640×640|15.6G |5.39M|10.9| 57.6|39.1| 


## Comparison on different platforms

Equipment|Computing backend|System|Input|Framework|v5lite-e|v5lite-s|v5lite-c|v5lite-g|YOLOv5s
:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:
Inter|@i5-10210U|window(x86)|640×640|openvino|-|-|46ms|-|131ms
Nvidia|@RTX 2080Ti|Linux(x86)|640×640|torch|-|-|-|15ms|14ms
Redmi K30|@Snapdragon 730G|Android(armv8)|320×320|ncnn|27ms|38ms|-|-|163ms
Xiaomi 10|@Snapdragon 865|Android(armv8)|320×320|ncnn|10ms|14ms|-|-|163ms
Raspberrypi 4B|@ARM Cortex-A72|Linux(arm64)|320×320|ncnn|-|84ms|-|-|371ms
Raspberrypi 4B|@ARM Cortex-A72|Linux(arm64)|320×320|mnn|-|71ms|-|-|356ms
AXera-Pi|Cortex A7@CPU<br />3.6TOPs @NPU|Linux(arm64)|640×640|axpi|-|-|-|22ms|22ms

#### Download Link：

> - [ ] `v5lite-e.pt`:   | [Baidu Drive](https://pan.baidu.com/s/1bjXo7KIFkOnB3pxixHeMPQ)  | [Google Drive](https://drive.google.com/file/d/1_DvT_qjznuE-ev_pDdGKwRV3MjZ3Zos8/view?usp=sharing) |<br> 
>> |──────`ncnn-fp16`:   | [Baidu Drive](https://pan.baidu.com/s/1_QvWvkhHB7kdcRZ6k4at1g)  | [Google Drive](https://drive.google.com/drive/folders/1w4mThJmqjhT1deIXMQAQ5xjWI3JNyzUl?usp=sharing) |<br> 
>> |──────`ncnn-int8`: | [Baidu Drive](https://pan.baidu.com/s/1JO8qbbVx6zJ-6aq5EgM6PA) | [Google Drive](https://drive.google.com/drive/folders/1YNtNVWlRqN8Dwc_9AtRkN0LFkDeJ92gN?usp=sharing) |<br> 
>> └──────`onnx-fp32`: | [Baidu Drive](https://pan.baidu.com/s/1gwLqiPLTDjlSqWJ7AnEB1A) | [Google Drive](https://drive.google.com/file/d/15_z6VlbWuonsHak-7bdtw-QOcvOaMddB/view?usp=sharing) |<br> 
> - [ ] `v5lite-s.pt`:   | [Baidu Drive](https://pan.baidu.com/s/1j0n0K1kqfv1Ouwa2QSnzCQ)  | [Google Drive](https://drive.google.com/file/d/1ccLTmGB5AkKPjDOyxF3tW7JxGWemph9f/view?usp=sharing) |<br> 
>> |──────`ncnn-fp16`:   | [Baidu Drive](https://pan.baidu.com/s/1kWtwx1C0OTTxbwqJyIyXWg)  | [Google Drive](https://drive.google.com/drive/folders/1w4mThJmqjhT1deIXMQAQ5xjWI3JNyzUl?usp=sharing) |<br> 
>> |──────`ncnn-int8`: | [Baidu Drive](https://pan.baidu.com/s/1QX6-oNynrW-f3i0P0Hqe4w) | [Google Drive](https://drive.google.com/drive/folders/1YNtNVWlRqN8Dwc_9AtRkN0LFkDeJ92gN?usp=sharing) |<br> 
>> |──────`mnn-fp16`: | [Baidu Drive](https://pan.baidu.com/s/12lOtPTl4xujWm5BbFJh3zA) | [Google Drive](https://drive.google.com/drive/folders/1PpFoZ4b8mVs1GmMxgf0WUtXUWaGK_JZe?usp=sharing) |<br> 
>> |──────`mnn-int4`: | [Baidu Drive](https://pan.baidu.com/s/11fbjFi18xkq4ltAKUKDOCA) | [Google Drive](https://drive.google.com/drive/folders/1mSU8g94c77KKsHC-07p5V3tJOZYPQ-g6?usp=sharing) |<br> 
>> |──────`onnx-fp32`: | [Baidu Drive](https://pan.baidu.com/s/1gwLqiPLTDjlSqWJ7AnEB1A) | [Google Drive](https://drive.google.com/file/d/123feVchyuqCRZV038I1Gn1gpJEVK4GFh/view?usp=sharing) |<br> 
>> └──────`tengine-fp32`: | [Baidu Drive](https://pan.baidu.com/s/123r630O8Fco7X59wFU1crA) | [Google Drive](https://drive.google.com/drive/folders/1VWmI2BC9MjH7BsrOz4VlSDVnZMXaxGOE?usp=sharing) |<br>                
> - [ ] `v5lite-c.pt`: [Baidu Drive](https://pan.baidu.com/s/1obs6uRB79m8e3uASVR6P1A) | [Google Drive](https://drive.google.com/file/d/1lHYRQKjqKCRXghUjwWkUB0HQ8ccKH6qa/view?usp=sharing) |<br> 
>> |──────`onnx-fp32`: | [Baidu Drive](https://pan.baidu.com/s/1gwLqiPLTDjlSqWJ7AnEB1A) | [Google Drive](https://drive.google.com/file/d/1VJBfZPikTce5vUatC2ZsAWQlmMdcArs2/view?usp=sharing) |<br> 
>> └──────`openvino-fp16`: | [Baidu Drive](https://pan.baidu.com/s/18p8HAyGJdmo2hham250b4A) | [Google Drive](https://drive.google.com/drive/folders/1s4KPSC4B0shG0INmQ6kZuPLnlUKAATyv?usp=sharing) |<br> 
> - [ ] `v5lite-g.pt`: | [Baidu Drive](https://pan.baidu.com/s/14zdTiTMI_9yTBgKGbv9pQw) | [Google Drive](https://drive.google.com/file/d/1oftzqOREGqDCerf7DtD5BZp9YWELlkMe/view?usp=sharing) |<br> 
>> |──────`onnx-fp32`: | [Baidu Drive](https://pan.baidu.com/s/1gwLqiPLTDjlSqWJ7AnEB1A) | [Google Drive](https://drive.google.com/file/d/1bJByk9eoS6pv8Z3N4bcLRCV3i7uk24aU/view?usp=sharing) |<br> 
>> └──────`axpi-int8`: [Google Drive](https://github.com/AXERA-TECH/ax-models/blob/main/ax620/v5Lite-g-sim-640.joint) |<br> 



Baidu Drive Password: `pogg`



## <div>How to use</div>

<details open>
<summary>Install</summary>

[**Python>=3.6.0**](https://www.python.org/) is required with all
[requirements.txt](https://github.com/MhmdRdbri/YOLOv5-Lite-Telecommunication-Detection/blob/main/requirements.txt) installed including
[**PyTorch>=1.7**](https://pytorch.org/get-started/locally/):
<!-- $ sudo apt update && apt install -y libgl1-mesa-glx libsm6 libxext6 libxrender-dev -->

```bash
$ git clone https://github.com/MhmdRdbri/YOLOv5-Lite-Telecommunication-Detection
$ pip install -r requirements.txt
```

</details>

<details>
<summary>Inference with detect.py</summary>

`detect.py` runs inference on a variety of sources, downloading models automatically from
the latest YOLOv5-Lite release and saving results to `runs/detect`.

```bash
$ python detect.py --source 0  # webcam
                            file.jpg  # image 
                            file.mp4  # video
                            path/  # directory
                            path/*.jpg  # glob
                            'https://youtu.be/NUsoVlDFqZg'  # YouTube
                            'rtsp://example.com/media.mp4'  # RTSP, RTMP, HTTP stream
```

</details>

<details open>
<summary>Training</summary>

```bash
$ python train.py --data coco.yaml --cfg v5lite-e.yaml --weights v5lite-e.pt --batch-size 128
                                         v5lite-s.yaml           v5lite-s.pt              128
                                         v5lite-c.yaml           v5lite-c.pt               96
                                         v5lite-g.yaml           v5lite-g.pt               64
```

 If you use multi-gpu. It's faster several times:
  
 ```bash
$ python -m torch.distributed.launch --nproc_per_node 2 train.py
```
  
</details>  

</details>

<details open>
<summary>DataSet</summary>

Training set and test set distribution （the path with xx.jpg）
  
 ```bash
train: ../data/antenna/images/train/
val: ../data/antenna/images/val/
```
```bash
├── images            # xx.jpg example
│   ├── train        
│   │   ├── 000001.jpg
│   │   ├── 000002.jpg
│   │   └── 000003.jpg
│   └── val         
│       ├── 100001.jpg
│       ├── 100002.jpg
│       └── 100003.jpg
└── labels             # xx.txt example      
    ├── train       
    │   ├── 000001.txt
    │   ├── 000002.txt
    │   └── 000003.txt
    └── val         
        ├── 100001.txt
        ├── 100002.txt
        └── 100003.txt
```
  
</details> 

## Reference

https://github.com/ultralytics/yolov5

https://github.com/megvii-model/ShuffleNet-Series

https://github.com/Tencent/ncnn
