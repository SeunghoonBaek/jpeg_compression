---
description: 이미지 처리(Image Processing)를 시작하기 전 기본적인 개념을 정리
---

# 이미지 처리의 기초

## 이미지 표현하는 방법

영상을 화면에 표시하기 위해 픽셀\(pixel\) 이라는 단위를 사용함. 이 픽셀은 사각형으로 표현하고 한 개의 색상을 표현하고 있음. 일반적으로 PC 디스플레이의 해상도를 이야기할 때 1280x720\(921,600 pixels\), 1920x1080\(2,073,600 pixels\) 등으로 이야기 하는데 이것은 디스플레이 장치에서 사용할 수 있는 픽셀의 크기라고 볼 수 있음.

## 백터\(Vector\) vs 비트맵\(Bitmap\) Graphics

디스플레이 장치\(=모니터\) 에서 이미지를 출력하기 위한 방법으로 Vector 방식과 Bitmap 방식이 있다. 

* Vector 방식: 선과 면을 그리는 Command 들을 저장한 방식. 복잡한 이미지를 표현해야 하는 경우 많은 Drawing command 들을 Re-producing 해야하기 때문에 Loading 시간이 길어기는 문제가 있음.
* Bitmap 방식: 파일안에 이미지가 픽셀로 저장된 형태. 각 픽셀마다 색상정보를 포함하고 있으므로 Loading 시간은 해상도에 비례함. Web 상에 공유되는 대부분의 이미지 파일은 Bitmap 방식임. 

## Color Models

픽셀에서 색상을 표현하기 위한 방법으로 여러가지 모델이 존재함 

* RGB: Red-Green-Blue 색상을 의미함. 세 가지 색상을 혼합하면 원하는 컬러를 얻을 수 있음. 색상 표현범위에 따라 한 픽셀의 데이터 사이즈는 8bit 또는 10bit 등이 가능함. \(8bit =&gt; 256 colors, 0~255 range\)
* Grayscale: 흑백 색상을 의미하며, RGB 모델에서 흑백을 표현할 경우 R=G=B 형태로 표현 가능.
* YCbCr\(=YUV\): Luminance\(=밝기 정보\), Chrominance\(=색상 정보\)를 사용하여 색상을 표현하는 것으로 Y는 Intense \(밝기\), Cb \(Blue 계열의 색상\), Cr\(Red 계열의 색상\) 의 조합으로 색 표현이 가능함.
  * RGB &lt;-&gt; YCbCr 간 색상모델 변경은 간단한 수식을 통해 변경 가능 \(아래 수식 외에 다양한 방법 존재\)
  * YCbCr\(=YUV\) 의 경우 JPEG 이나 Image FileFormat 에서 Chroma sampling 을 통한 Compression 을 위해 주로 사용되는 색상 모델임.
  * Chroma Sampling 에 따라 YUV420, YUV444 등 여러 서브 형태가 존재함.

```bash
[RGB -> YUV]
Y = 0.2999R + 0.587G + 0.114B
Cb = -0.1687R - 0.3313G + 0.5B + 2^(sample precision/2)    
     (Note: Sample precision can be 8 or 10, commonly 8.)
Cr = 0.5R - 0.4187G - 0.0813B + 2^(sample precision/2)

[YUV -> RGB]
R = Y + 1.402 * Cr
G = Y - 0.34414 * (Cb - 2^(sample precision/2)) - 0.71414 * (Cr - 2^(sample precision/2))
B = Y + 1.722 * (Cb - 2^(sample precision/2))
```

* CMYK: 주로 프린터의 색상 모델로 사용되고 있고, 각각은 Cyan\(= Blue\), Magenta\(= Red\), Yellow, Black 색상을 표현함.

## True color vs Palette

TBU

