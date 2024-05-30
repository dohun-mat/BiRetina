## 설치
#### clone
1. git clone https://github.com/dohun-mat/BiRetina

#### 데이터

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

## 훈련
[google cloud](https://drive.google.com/open?id=1oZRSG0ZegbVkVwUd8wUIQx8W7yfZ_ki1)이 링크에서 MobilenetV1X0.25_pretrain.tar를 다운로드 받습니다.
```Shell
  ./weights/
      mobilenetV1X0.25_pretrain.tar
```
1. 훈련하기 전에 에서 네트워크 구성(예: 배치_크기, 최소 크기 및 단계 등)을 확인할 수 있습니다. ``data/config.py and train.py``.

2. WIDER FACE를 사용하여 모델을 훈련합니다.
  ```Shell
  python train.py --network mobile0.25
  ```


## 평가
1. txt 파일 생성
```Shell
python test_widerface.py --trained_model ./weights/mobilenet0.25_Final.pth --network mobile0.25
```
2. txt 결과를 평가합니다. 데모는 [Here](https://github.com/wondervictor/WiderFace-Evaluation) 에서 제공됩니다. 
```Shell
cd ./widerface_evaluate
python setup.py build_ext --inplace
python evaluation.py -p ./widerface_txt -g ./eval_tools/ground_truth
```
3. You can also use widerface official Matlab evaluate demo in [Here](http://mmlab.ie.cuhk.edu.hk/projects/WIDERFace/WiderFace_Results.html)
