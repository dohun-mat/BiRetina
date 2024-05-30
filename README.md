데이터

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
ps: wider_val.txt only include val file names but not label information.

##### Data1
We also provide the organized dataset we used as in the above directory structure.

Link: from [google cloud](https://drive.google.com/open?id=11UGV3nbVv1x9IC--_tK3Uxf7hA6rlbsS) or [baidu cloud](https://pan.baidu.com/s/1jIp9t30oYivrAvrgUgIoLQ) Password: ruck
