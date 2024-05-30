## 설치
##### clone
1. git clone https://github.com/dohun-mat/BiRetina

##### 데이터

1.  [WIDERFACE](http://shuoyang1213.me/WIDERFACE/WiderFace_Results.html) 데이터셋을 다운로드

2. [dropbox](https://www.dropbox.com/s/7j70r3eeepe4r2g/retinaface_gt_v1.1.zip?dl=0) 에서 얼굴 경계 상자 및 5개의 얼굴 랜드마크를 다운로드

3. 데이터셋 디렉토리를 다음과 같이 구성합니다.

```Shell
  ./data/widerface/
    train/
      images/
      label.txt
    val/
      images/
      wider_val.txt
```
ps: wide_val.txt에는 val 파일 이름만 포함되고 레이블 정보는 포함되지 않습니다.

##### Data1
또한 위의 디렉터리 구조와 같이 사용된 정리된 데이터 세트를 제공합니다.

Link: from [google cloud](https://drive.google.com/open?id=11UGV3nbVv1x9IC--_tK3Uxf7hA6rlbsS) or [baidu cloud](https://pan.baidu.com/s/1jIp9t30oYivrAvrgUgIoLQ) Password: ruck

## Training
We provide restnet50 and mobilenet0.25 as backbone network to train model.
We trained Mobilenet0.25 on imagenet dataset and get 46.58%  in top 1. If you do not wish to train the model, we also provide trained model. Pretrain model  and trained model are put in [google cloud](https://drive.google.com/open?id=1oZRSG0ZegbVkVwUd8wUIQx8W7yfZ_ki1) and [baidu cloud](https://pan.baidu.com/s/12h97Fy1RYuqMMIV-RpzdPg) Password: fstq . The model could be put as follows:
```Shell
  ./weights/
      mobilenet0.25_Final.pth
      mobilenetV1X0.25_pretrain.tar
      Resnet50_Final.pth
```
1. Before training, you can check network configuration (e.g. batch_size, min_sizes and steps etc..) in ``data/config.py and train.py``.

2. Train the model using WIDER FACE:
  ```Shell
  CUDA_VISIBLE_DEVICES=0,1,2,3 python train.py --network resnet50 or
  CUDA_VISIBLE_DEVICES=0 python train.py --network mobile0.25
  ```


## Evaluation
### Evaluation widerface val
1. Generate txt file
```Shell
python test_widerface.py --trained_model weight_file --network mobile0.25 or resnet50
```
2. Evaluate txt results. Demo come from [Here](https://github.com/wondervictor/WiderFace-Evaluation)
```Shell
cd ./widerface_evaluate
python setup.py build_ext --inplace
python evaluation.py
```
3. You can also use widerface official Matlab evaluate demo in [Here](http://mmlab.ie.cuhk.edu.hk/projects/WIDERFace/WiderFace_Results.html)
