# MLflow란
https://mlflow.org/
머신러닝 실험, 배포를 쉽게 관리할 수 있는 오픈소스

관련 오픈소스 중 제일 빠르게 성장 중

집에서 요리만들때, 레시피를 기록해야 어떤 조합이 좋은지 알 수 있음(파라미터, 모델 구조 등) => mlflow
여러 시행착오를 겪으며 요리함(머신러닝 모델링도 많은 실험을 함!) => mlflow
이 레시피에서 제일 맛있었던(성능이 좋았던)레시피를 레스토랑에 사용한다 => mlflow
요리 만드는 과정에서 생기는 부산물 저장!(=모델 Artifact, 이미지 등) => mlflow
타코(모델)은 다양한 종류가 있으므로 언제 만든 타코인지(=모델 생성일), 얼마나 맛있었는지(모델 성능), 유통기한 등(=모델 메타 정보)을 기록해둘 수 있음 => mlflow
언제부터 닭고기 타코, 돼지고기 타코, 부리또를 만들어 판매(=여러 모델 운영) => mlflow

위의 기능들,, 혹시 WandB의 상위호환 버전인가?!  



**1.1. 장점**
오픈 소스임. 다른 MLOps 플랫폼에 통합이 쉬게 이뤄질 수 있게 되어 있음.<br/>
다양한 머신 러닝 프레임워크와 통합되어 있어, 머신 러닝 모델의 개발과 관리를 보다 쉽게 가능.
모델의 개발, 테스트, 배포, 모니터링 및 관리를 통합된 인터페이스에서 수행할 수 있어 생산성과 효율성이 높아짐.
다양한 실험을 수행하고, 실험 결과를 쉽게 추적하고 비교 가능.
모델의 성능과 안정성을 평가하고, 모델의 버전 관리를 가능.
엔터프라이즈급 시스템에서 사용하기 적합한 보안성과 확장성을 제공.
**1.2. 단점**
모델의 개발환경에 MLflow를 적용하는 것이 어렵거나 불가능한 경우 존재함.
MLflow의 추가 기능이 필요한 경우, 별도의 프로그래밍이 필요함.
MLflow가 제공하는 모델 개발 및 관리 기능이 충분하지 않을 수 있음.  

# 핵심기능
### 1. Experiment Management & Tracking

머신러닝 관련 "실험"들을 관리하고, 각 실험의 내용들을 기록할 수 있음
-- 예를 들어, 여러 사람이 하나의 MLflow 서버위에서 각자 자기 실험을 만들고 공유할 수 있음
실험을 정의하고, 실험을 실행할 수 있음. 이 실행은 머신러닝 훈련 코드를 실행한 기록
-- 각 실행에 사용한 소스 코드, 하이퍼 파라미터, Metric, 부산물(모델 Artifact, Chart Image)등을 저장
### 2. Model Registry

MLflow로 실행한 머신러닝 모델을 Model Registry(모델 저장소)에 등록할 수 있음

모델 저장소에 모델이 저장될 때마다 해당 모델에 버전이 자동으로 올라감(Version 1->2->3..)

Model Registry에 등록된 모델은 다른 사람들에게 쉽게 공유 가능하고, 쉽게 활용할 수 있음

Git과 docker와 유사하다?!
### 3. Model Serving

Model Registry에 등록한 모델을 REST API형태의 서버로 Serving 할 수 있음
Input = Model의 Input
Output = Model의 Output
직접 Docker Image 만들지 않아도 생성할 수 있음
# MLflow Component
### 1. MLflow Tracking

머신러닝 코드 실행, 로깅을 위한 API, UI
MLflow Tracking을 사용해 결과를 Local, Server에 기록해 여러 실행과 비교할 수 있음
팀에선 다른 사용자의 결과와 비교하며 협업할 수 있음
### 2. MLflow Project

머신러닝 프로젝트 코드를 패키징하기 위한 표준
Project
-- 간단하게 소스코드가 저장된 폴더
-- Git Repo
-- 의존성과 어떻게 실행해야 하는지 저장
MLflow Tracking API를 사용하면 MLflow는 프로젝트 버전을 모든 파라미터와 자동으로 로깅
### 3. MLflow Model

모델은 모델파일과 코드로 저장
다양한 플랫폼에 배포할 수 있는 여러 도구 제공
MLflow Tracking API를 사용하면 MLflow는 자동으로 해당 프로젝트에 대한 내용을 사용함
### 4. MLflow Registry

MLflow Model의 전체 Lifecycle에서 사용할 수 있는 중앙 모델 저장소
[출처]https://velog.io/@ifelifelse/MLflow

# MLflow 실제 활용 사례
MLflow Tracking Server는 하나로 통합 운영

Tracking Server를 하나 배포하고, 팀 내 모든 Researcher가 이 Tracking Server에 실험 기록
-- 배포할때는 Docker Image, Kubernetes 등에 진행(회사의 인프라에 따라 다름)

로그나 모델이 한 곳에 저장되므로, 팀 내 모든 실험을 공유할 수 있음
-- Artifact Storage는 GCS나 S3같은 스토리지 이용
-- DB는 CloudSQL이나 AuroraRDS 같은 DB이용
-이 두 저장소는 Tracking Server에 의해 관리  


![image](https://github.com/SK-AI-FLY-MLOps-Study/MLOps-Study/assets/108683454/77314d65-f668-4266-877e-33aab33f4eb0)

