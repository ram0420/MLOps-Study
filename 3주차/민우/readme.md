오늘 새로 알게된 툴 및 라이브러리
1. black
2. lint
3. code c
# 리서치 코드 품질 관리 자동화
리서처분들과 일할 때 CI(Continuous Integration) 필요
리서처분들의 코드가 부족할 경우
품질 자동화를 써서 끌어올릴 수 있
lint 나 unitest 지동적 통합 세팅
목차
1. 리서치 코드 품질 문제 이해
2. 린트와 유닛테스트 이해
3. 지속적 통합 이해
   ![image](https://github.com/barabonda/MLOps-Study/assets/108683454/daff1a26-b0fa-4aa5-b9b9-f0d6a9ee33c8)
이걸 챙겨야 파이프라인이 의미가 있
![image](https://github.com/barabonda/MLOps-Study/assets/108683454/1de785a8-bb13-4d90-8d5f-4211c80e0c06)
라이브러리를 만들면 좋다! 기술부채를 줄일 수 있음
전역변수는 편하지만 side effect를 가져온다.
import를 엡솔루트 import 구조로!
지속적 통합-> 코드 통합으로부터
type hint: 함수의 변수를 분명하게 명
`def fn(a: int) -> bool`
mypy이용하면 타입힌트에 오류가 있는지 자동으로 확인할 수 있음

## CI(지속적 통합)
 ![image](https://github.com/barabonda/MLOps-Study/assets/108683454/d4d6b965-49d5-4944-b155-c7c92fc27ebd)
 소프트웨어의 질적향상  
 CI tool: circle CI, jenkins, 오늘 해볼것 github action!
 ## black 과 lint
black을 쓰면 코드를 수정하고 이를 lint와 연동하여 깃허브에 풀리퀘스트를 해보면 코드적으로 오류가 있을때 풀리퀘스트가 안되도록함
## CODE CLIMATE
코드관리 유료 툴
- 정적 분석하기에 좋
코드가 어떤지 평가를 해

CI 에다가 2가지 테스트 추가한것을 커밋
![image](https://github.com/barabonda/MLOps-Study/assets/108683454/0b458f34-81ba-4efa-bb87-e3581641a272)
코드 검증을 받아야 리퀘스트를 할 수 있는

작업에 대해서 초반에는 일관성을 유지하도록 강제하고 그 이후부터는 코드가 예쁘게 알려주고
CLIMATE 덕분에 코멘트도 다남겨줌  
시니어들이 코드리뷰하는 시간이 줄어들음
그리고 마크다운으로 리드미에 업뎃할 수도 있음
테스트 --> 린트 -->
이과정을 통해 코드의 품질이 떨어지지않도록 계속 봐줌  
![image](https://github.com/barabonda/MLOps-Study/assets/108683454/30b924ba-23ac-4eca-ab66-ca895d027bc2)
리서치 코드 뿐만 아니라 api서버에서도 사용가능  
![image](https://github.com/barabonda/MLOps-Study/assets/108683454/b812d5e6-2dc2-422f-aa07-3289207a48bd)
자동
# 데이터 검증 tfdv
1. 데이터 검증 필요성
2. 스키마 추론 & 스키마 환경
3. 데이터 드리프트 & 스
# tfx
TFDV

아파치 빔을 이용하여 통계 계산 및 시각화

스키마 추론과 스키마 환경  

스키마 추론

평가데이터의 오류확인
![image](https://github.com/barabonda/MLOps-Study/assets/108683454/5c6fb86d-ffac-4b9d-8a0d-29bb0e80e72b)
![image](https://github.com/barabonda/MLOps-Study/assets/108683454/3b068e93-bd2d-4e09-a323-59fb4a6f3ddc)

data validation이라는 것을 프로그래미틱하게 구현해보앗다.
![image](https://github.com/barabonda/MLOps-Study/assets/108683454/1fc4f978-1bf3-4b8d-b48a-93922413a34c)

데이터 드리프트 및 스큐

데이터 드리프트

모델을 배포하고나면 모델의 성능이 떨어지는 것이 다반사

serving time의 정답을 수집하여 하는 방법도 있겠지만

자체적인 데이터가 바뀌면 이것을 어떻게 인지할까? ex) 성비가 바뀌었다던가
Skew의 3가지 종류
schema Skew
학습 및 서빙데이터가 동일한 스키마가 아닐때
Feature Skew 
모델이 학습하는 특성값이 서빙시에 표시되는 특성 값과 다를 때 
Distiribution Skew
분포 스큐는 학습 데이터 세트의 분포가 제공 데이터세트의 분포와 크게 다를

# 머신러닝 모델 분석 What if tool  
TFMA  
**전통적인 소프트웨어 개발**  
개발자는 명시적으로 컴퓨터에게 해야 할 일을 알려줘야함  

**머신러닝 소프트웨어 개발**  
개발자는 데이터를 통해서 특정 작업을 수행하도록 알고리즘 학습  
품질과 양에 의존
what-if-tool은 시각화 도구  
워크스페이스가 있
https://pair-code.github.io/what-if-tool/  
![image](https://github.com/barabonda/MLOps-Study/assets/108683454/b77b70f0-348a-43c3-a90f-2c906db753e3)
marital로 다양한 데이터 분석을 모델안에서 할 수 있는 것이 장  
![image](https://github.com/barabonda/MLOps-Study/assets/108683454/f254b117-88e0-4617-9172-82bde5509f91)
얼굴 디텍
이미지도 된다...미쳤다  
