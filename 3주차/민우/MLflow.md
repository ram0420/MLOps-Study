# MLflow란
머신러닝 실험, 배포를 쉽게 관리할 수 있는 오픈소스

관련 오픈소스 중 제일 빠르게 성장 중

집에서 요리만들때, 레시피를 기록해야 어떤 조합이 좋은지 알 수 있음(파라미터, 모델 구조 등) => mlflow
여러 시행착오를 겪으며 요리함(머신러닝 모델링도 많은 실험을 함!) => mlflow
이 레시피에서 제일 맛있었던(성능이 좋았던)레시피를 레스토랑에 사용한다 => mlflow
요리 만드는 과정에서 생기는 부산물 저장!(=모델 Artifact, 이미지 등) => mlflow
타코(모델)은 다양한 종류가 있으므로 언제 만든 타코인지(=모델 생성일), 얼마나 맛있었는지(모델 성능), 유통기한 등(=모델 메타 정보)을 기록해둘 수 있음 => mlflow
언제부터 닭고기 타코, 돼지고기 타코, 부리또를 만들어 판매(=여러 모델 운영) => mlflow

위의 기능들,, 혹시 WandB의 상위호환 버전인가?!
# 핵심기
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
