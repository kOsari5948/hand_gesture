<h1 align="center">GestureControl</h1>

<br/>

## 💡 개요

- 손 모양을 촬영하여 컴퓨터 기능을 수행하는 원격 리모컨

<img src="./img/main.png" width="500px;">

## 👨‍👦 참가자

<table>
 <tr>
    <td align="center"><a href="https://github.com/kOsari5948"><img src="https://avatars.githubusercontent.com/u/86839047?v=4" width="130px;" alt=""></a></td>
    <td align="center"><a href="https://github.com/leafeafeaf"><img src="https://avatars.githubusercontent.com/u/70201753?s=400&v=4" width="130px;" alt=""></a></td>
    <td align="center"><a href="https://github.com/xlloew"><img src="https://avatars.githubusercontent.com/u/77535275?v=4" width="130px;" alt=""></a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/kOsari5948"><b>김민철</b></a></td>
    <td align="center"><a href="https://github.com/leafeafeaf"><b>김성민</b></a></td>
    <td align="center"><a href="https://github.com/xlloew"><b>이정찬</b></a></td>
  </tr>
</table>

| 김민철                            | 김성민                   | 이정찬                 |
| --------------------------------- | ------------------------ | ---------------------- |
| 팀장, 모델 설계 및 학습, 자료조사 | 데이터셋 구축, 모델 설계 | 사용자 UI 제작, 테스트 |

## 🛠️ 기술 스택

- Python
- tensorflow
- cv2
- tkinter

## ⚙️ 개발 과정 및 적용 기법

1. 데이터셋 구축
<hr>

- O, V, paper, rock, side 클래스에 각각 805, 624, 805, 621,
  805개로, 총 3660개의 사진 데이터를 사용
- 가공된 사진을 ImageDataGenerator으로 이미지 증식하여 데이터 양과 변칙성을 추가
- (학습 집합 2058), (검증 집합 687), (테스트 집합 915)로 분류하여 각각을 이미지 증식

2. 이미지 분류 모델 생성 및 학습
<hr>

- 3가지 모델을 생성하여 각각 신경망 성능을 비교
- 이미지 관련 코드를 사용하기 위해, PIL 라이브러리사용
- CNN 모델을 사용하기 위해, tensorflow 라이브러리 사용
- 파이썬에서 영상을 처리하기 위해, cv2 라이브러리 사용
- 이미지 증식을 위한 ImageDataGenerator 라이브러리 사용
- 모델을 생성하기 위한 keras.layers의 Conv2D, MaxPooling2D 등의 라이브러리 사용

- VGG-16 신경망 구조를 활용하여 신경망 구성
- 활성화 함수로 Relu 적용
- 소프트맥스 적용

- 모델 최종 성능
  <br/>
![](img/test.png)

## 📖 사진

<h3>1️⃣분류 제츠쳐 종류</h3>

![](./img/function.png)

<h3>2️⃣이미지 전처리 및 이미지 증강</h3>

![](img/datagenerator.png)

🖼️ 모델 성능 비교
![](img/modelDiff.png)
![](img/lossGraph.png)

## 💥 Trouble Shooting

### 트러블 상황

1. 특정한 손 동작이 제대로 인식되지 않는 상황 발생

2. 모델 학습 시간과 컴퓨터 자원

3. 적중률이 높지 않은 종합 테스트 결과

### 원인

1.  명확히 분리되지 않은 손 동작, 주변 배경

2.  학습 데이터 용량이 매우 큼

3.  기존 손 이미지로만 학습을 진행하여 과대적합 문제 발생

### 문제 해결

1. 손 동작 재설계, 주변 환경과 대비시키기 위해 이미지 흑백 처리

2. 학습 조기종료 기법 적용, 이미지를 64\*64로 변환하여 학습 진행

3. 과대적합

- 다양한 배경에서의 사진을 추가하여 데이터 양과 품질 개선
- 이미지 제너레이터를 적용하여 데이터 양과 다양성 추가
- VGG 신경망 구조 활용 및 dropout 기법을 적용하여 과대적합 개선
