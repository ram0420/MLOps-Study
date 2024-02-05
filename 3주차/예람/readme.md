notion_link : https://www.notion.so/3-c65c4dc1c861420a97d03c2b3135763b?pvs=4

### TFX 활용사례

[우수사례 및 언급  |  TensorFlow](https://www.tensorflow.org/about/case-studies?hl=ko)

### 1. **에어비앤비 숙소 사진 분류하기**

[Categorizing Listing Photos at Airbnb](https://medium.com/airbnb-engineering/categorizing-listing-photos-at-airbnb-f9483f3ab7e3)

**이미지 분류**

특정 목록 사진의 **객실 유형을 올바르게 분류**하는 기능은 사용자 경험을 최적화하는 데 매우 유용합니다. 게스트 측에서는 객실 유형에 따라 사진의 순위를 다시 매기고 레이아웃을 다시 지정하여 **사람들이 가장 관심을 보이는 사진이 먼저 표시되도록** 합니다. 호스트 측에서는 목록이 자동으로 검토되어 시장의 높은 기준을 준수하는지 확인하는 데 도움이 됩니다. 정확한 사진 분류는 이러한 핵심 기능의 중추입니다.

1) 출력 차원이 우리의 것과 일치하도록 DNN의 마지막(상위) 몇 개의 레이어를 수정하고 2) DNN을 어느 정도 재교육하여 만족스러운 성능을 달성해야 합니다. 이 모델에 대한 몇 가지 실험 후에 우리는 모델 성능과 계산 시간 간의 균형이 잘 잡혀 **[ResNet50을 강력한 솔루션으로 선택](https://arxiv.org/abs/1512.03385)**했습니다. 우리 사용 사례와 호환되도록 하기 위해 **두 개의 완전히 연결된 레이어를 추가하고 마지막에 Softmax 활성화를 추가**했습니다

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/95be1cab-599e-4623-bf15-98ca74be2020/792d938e-0de8-4bc9-8cbd-8171c82a97dc/Untitled.png)

**감독되지 않은 장면 분류**

사전 훈련된 ResNet50 모델을 사용하여 방 유형 분류를 처음 시도했을 때 표지 사진을 나열하기 위한 이미지 임베딩(2048x1 벡터)을 생성했습니다. 이러한 임베딩이 의미하는 바를 해석하기 위해 PCA 기술을 사용하여 이러한 긴 벡터를 2D 평면에 투영했습니다. 놀랍게도 투영된 데이터는 자연스럽게 두 그룹으로 클러스터됩니다. 이 두 클러스터를 살펴보면 왼쪽 그룹은 거의 실내 장면이고 오른쪽 그룹은 거의 실외 장면이라는 것을 알 수 있습니다. 이는 재교육 없이 이미지 임베딩의 첫 번째 주요 구성 요소에 절단선을 설정하는 것만으로 실내 및 실외 장면을 결정할 수 있음을 의미합니다. 이 발견은 전이 학습(임베딩)이 비지도 학습을 만나는 매우 흥미로운 영역의 문을 열었습니다.

**객체 감지**

우리가 추구하려고 시도한 또 다른 영역은 객체 감지였습니다. [Open Images Dataset](https://github.com/openimages/dataset) 에서 사전 훈련된 [Faster R-CNN](https://arxiv.org/abs/1506.01497) 모델은 이미 놀라운 결과를 제공했습니다. 아래 예시에서 볼 수 있듯이 모델은 창문, 문, 식탁 및 그 위치를 감지할 수 있습니다. [Tensorflow 객체 감지 API를](https://github.com/tensorflow/models/tree/master/research/object_detection) 사용하여 목록 사진에 대한 몇 가지 빠른 평가를 수행했습니다. 기성품 결과를 사용하여 많은 가정용 편의 시설을 감지할 수 있습니다. 앞으로는 Airbnb의 맞춤형 편의 시설 라벨을 사용하여 Faster R-CNN 모델을 재교육할 계획입니다. 이러한 라벨 중 일부는 오픈 소스 데이터에 누락되어 있으므로 우리가 직접 라벨을 만들 가능성이 높습니다. 이러한 알고리즘으로 감지된 편의 시설을 통해 우리는 호스트가 제공하는 숙소의 품질을 검증하고 게스트가 특정 편의 시설이 필요한 숙소를 훨씬 쉽게 찾을 수 있도록 해줍니다. 이는 Airbnb의 사진 지능 분야를 한 단계 더 발전시킬 것입니다.

**결론_몇가지 핵심사항**

1. 고품질 라벨의 중요성
2. 간단하고 빠른 방법으로 시작하기. 작은 데이터 세트를 사용하여 최상위 레이어만 훈련
3. 훈련을 병렬화. 8개의 GPU를 사용하여 약 6배(준선형) 속도 향상

### 2. **ISS 원격 측정 데이터의 이상 징후를 감지**

https://blog.tensorflow.org/2020/04/how-airbus-detects-anomalies-iss-telemetry-data-tfx.html?hl=ko&_gl=1*1eq62km*_ga*OTczNTE4NTM4LjE3MDM3NDM5MjU.*_ga_W0YLR4190T*MTcwNjE0OTY1Ni45LjEuMTcwNjE1MjY2Ni4wLjAuMA..

Airbus : **국제 우주 정거장 (ISS)에서 콜럼버스 모듈** 과 탑재체의 작동을 위한 여러 서비스를 제공
