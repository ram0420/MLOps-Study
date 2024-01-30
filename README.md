

# MLOps-Study
![image](https://github.com/SK-AI-FLY-MLOps-Study/MLOps-Study/assets/108683454/2cf27f2c-cd2a-4728-8ccb-1e8da69a6cf0)
~~다들 웃고있는거 맞죠?^^~~
<br/>
**sk ai fly에서 만난 이들의 mlops study!** <br/>
AI와 빅데이터의 시대인만큼 현업에서 AI를 효과적으로 운영하고 적용하는 데 필수적인 MLops의 중요성이 커짐에 따라 mlops에 대해 알고자하는 이들끼리 스터디 결성

### 🚀MLops란?

ML 시스템 개발(Dev)과 ML 시스템 운영(Ops)을 통합하여 데이터 레이블링의 일관성을 유지, 자동 운영하는것<br/>  
즉, 계속해서 AI/ML을 개발, 배포, 운영하는 Workflow 자체를 MLops라 함


### 📚스터디 내용

• 궁극적인 목표:각자 강의를 보고 쿠버네티스 기반 MLOps 만들어보기<br/>  
• 실제 프로젝트에서의 MLops 적용 사례 및 경험 공유<br/>  
• ELICE INSIGHT CONF: MLops 시청(VOD 보유)<br/>  
• Kaggle or Dacon code review<br/>  


### 0주차 - Orientation(2023.12.29)

MLops study 동기 및 목표에 대해 이야기하였고
앞으로 어떻게 스터디를 운영할지 결정하였습니다.
스터디 운영 방향성 
강의를 보며 쿠버네티스 기반 MLOps를 만드는 것을 궁극적인 목표로 하며
그에 도움되는 컨퍼런스, 논문, kaggle code review, 현업적용 사례 같은 부가적인 레퍼런스 대해 지속적으로 소통하며 
부족한 부분을 채우고 MLOps를 이해하고 구현
- [과제] 내가 생각하는 MLOps 생각해오기(~2024.01.03) 

### 1주차 - 내가 생각하는 MLops란?& 강의 선정
각자가 생각하는 MLops를 말하였습니다.<br/>
그리고 mlops 강좌들을 살펴보며 강좌를 골랐습니다<br/>
[선정 강좌]머신러닝 엔지니어 실무 - chris song<br/>
https://www.inflearn.com/course/%EB%A8%B8%EC%8B%A0%EB%9F%AC%EB%8B%9D-%EC%97%94%EC%A7%80%EB%8B%88%EC%96%B4-%EC%8B%A4%EB%AC%B4#curriculum<br/>
- [과제] Session 1까지 듣기<br/>
  

### 2주차 - Session 1 후기 및 mlops
**들은 강의**
Session0. 머신러닝 파이프라인 소개
Session1.  머신러닝 프로젝트 실험관리
<br/>
**오늘의 Insight**<br/>
원디비의 존재를 알다. <br/>
쉬운 머신러닝과 어려운 머신러닝의 차이<br/>
달파는 모든 서비스가 2주안에 끝남<br/>
데이터의 변환이 빨리 일어나면 모델 학습을 자동화하니까 모델학습을 자동화 시켜줌<br/>
웨이트 인 바이어스로 결과를 도출하는 방식이 상당히 전문적이고 실제 발표에서 써볼만<br/>
**elice MLOps conference 세션 2개 맛보기**
  - DATABRICKS를 활용한 MLOps
  - MLOps를 시작하는 5단계 기초부터
  **[과제] 각자 MLops tool 한개씩 공부해오기**<br/><br/>

### 3주차 - Session 2 후기 및 mlops tool  
Session 2. 코드 품질, 데이터 검증, 모델 분석
**오늘의 Insight**<br/>
민우 - mlflow
가경 - amazone sagemaker
예람 - tensorflow extended  
민수 - jenkins
다은 - github action  
각자 조사해온 툴을 발표하였고 발표하면서 데이터 수집부터 배포 부분을 맡거나 실험 검증 부분을 맡거나 전과정을 맡거나 
다양한 툴을 보면서 어떨 때 어떠어떠한 툴을 써야하는지 알게되었다.  
그리고 이러한 툴을 사용해서 자동화를 하여 전체적인 업무 효율이 올라갈 수 있고  
전체적인 품질 향상에 기여하고 researcher와 시너지도 날 것이다.

[과제] MLOps 활용 사례 하나씩 조사해오기
### 4주차 - Session 3 후기 및 MLOps 활용 사례 공유  
Session 3. 도커&쿠버네티스 기초  
MLOps 엔지니어가 왜 도커와 쿠버네티스를 사용하는지 현업에서 협업을 할 때 도커와 쿠버네티스가 어떤 역할을 맡는지 알게되었고
node, pod, container, docker, kubernetes 같은 기본 개념을 알게되었다.  
MLOps 활용 사례는
기업들의 MLOps 파이프 라인 구축(SK, 네이버, 카카오)
추천시스템, 자율 주행 기술에 쓰이는 파이프라인 
품질 관리, 실험  
그러한 현업 사례들을 살펴보며 왜 MLOps가 필요하고 데이터를 잘관리할 수 있어야하는지  
보다 직관적으로 알게 되었다.  
[과제] MLOps 활용한 Code Review 하나씩 해오기
### 5주
