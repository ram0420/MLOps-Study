### Tensorflow Extended

모델을 프로덕션에서 지속적으로 발전시키면서 운영하기 위해서 지속적으로 변화하는 데이터와 모델을 관리하기 위한 방법론이 MLOps

### Google 에서 제공하는 MLOps 플랫폼

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/95be1cab-599e-4623-bf15-98ca74be2020/f338a1eb-ab38-45db-908c-a468cfc43057/Untitled.png)

**MLOps 파이프라인**의 **각 단계를 위한 (모델 정의, 전처리, 빌드, 모니터링을 통합할 수 있는) 프레임워크 및 라이브러리를 제공**

ML 파이프라인의 각 주요 단계 별로 Library(TensorFlow Data Validation, TensorFlow Transform, TensorFlow Model Analysis 등)가 구현

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/95be1cab-599e-4623-bf15-98ca74be2020/f426ed43-239f-4e14-9d55-d375ce6b578a/Untitled.png)

**TFX ML system**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/95be1cab-599e-4623-bf15-98ca74be2020/4997550a-2a67-4260-94ad-622895007037/Untitled.png)

1. **Data Extract**데이터 소스로부터 학습 데이터를 추출
2. **Data ValidationTFDV**가 예상(원시) 데이터 스키마를 기준으로 데이터를 검사하여 데이터 분포 및 스키마 편향과 관련된 이상치를 감지
3. **Data Transformation**데이터 검사가 완료된 후 **TFT**를 사용해서 data transformatoin 및 featue engineering을 수행하여 ML 작업에 맞게 데이터를 분할하고 준비.output은 일반적으로 TFRecords 형식으로 변환되는 모델 학습 및 평가를 위한 데이터 파일.
4. **Model Training and Tuning**ML 모델을 구현 및 학습시키기 위해서 **tf.estimator** 또는 **tf.Keras API**를 활용. 파라미터 튜닝을 위해서 Keras Tuner 또는 Katib과 같은 서비스를 사용할 수 있음.output은 (1) 평가에 사용될 모델과 (2) 온라인 서비스용 모델 두가지.
5. **Model evaluation and validation**학습 후 모델을 내보낼 때 **TFMA**를 사용하여 모델 품질을 평가. **TFMA**는 전반적으로 모델 품질을 평가하고, 문제가 있는 데이터 모델 부분을 식별. 이러한 기준에는 여러 데이터 하위 집합(예: 인구통계 및 위치)에서의 올바른 성능과 이전 모델 또는 벤치마크 모델에 대비 향상된 성능이 포함output은 (1) performance metric과 (2) 모델 프로덕션 적용 여부.
6. **Model serving for prediction**TensorFlow Serving을 통해 online estimation을 제공하도록 microservice로 배포.이 단계는 model registry에 모델을 저장하고, 별도의 CI/CD 프로세스를 통해 배포하는것으로 대체될 수 있다.output은 ML model의 estimation service.

**TFX 주요 구성 요소**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/95be1cab-599e-4623-bf15-98ca74be2020/832c7117-f78e-4b68-82a8-aede34c28d28/Untitled.png)

**Driver : input을 받기, 작업 실행을 오케스트레이션하고 executor에게 메타데이터를 피드해준다.**

**Executor : 데이터를 처리, 실제로 각 component에 대한 작업이 수행되는 곳**

**Publisher : output을 발행, executor의 결과를 받아 메타데이터 저장소를 업데이트**

Driver와 publisher는 boilerplate code로 개발자가 직접 수정할 일은 없다. 

개발자가 실제로 **코드를 삽입하고 사용자 설정을 하는 부분은 executor**

**Metadata Store : Component의 input과 output을 저장**

[https://jaemunbro.medium.com/mlops-tfx-1-개요-2897b56feec7](https://jaemunbro.medium.com/mlops-tfx-1-%EA%B0%9C%EC%9A%94-2897b56feec7) **2**
