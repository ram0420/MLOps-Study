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
 
