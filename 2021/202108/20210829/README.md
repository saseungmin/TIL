## 📆 2021-08-29(일) TIL

### 📈 오늘 한 일
- [x] NEXT-IT 스터디?
- [x] 오브젝트 7장
- [x] 개인 프로젝트 한 피처
  - [MyInfo의 user detail을 가져오는 로직을 리팩터링하라](https://github.com/CodeSoom/ConStu/pull/232)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 회사 문화에 적응하기
- [x] 자취에 필요한 물품들 구매하기
- [x] 스터디 참여 및 오브젝트 8장까지 읽기
- [ ] ReScript 공식문서 훑어보기
- ~~거주시에 처리하지 못한 일들 처리하기~~
- [ ] NEXT-IT Repos 관리하기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 오브젝트 7장
- 하향식 기능 분해의 문제점
  1. 하나의 메인 함수라는 비현실적인 아이디어
  2. 메인 함수의 빈번한 재설계
  3. 비즈니스 로직과 사용자 인터페이스의 결합
  4. 성급하게 결정된 실행 순서 (무엇을 해야 하는지가 아니라 어떻게 동작해야 하는지에 집중)
  5. 데이터 변경으로 인한 파급효과
- 하향식 분해가 유용한 경우는 이미 해결된 알고리즘을 문서화하고 서술하는 데는 훌륭한 기법 그러나 실제로 동작하는 커타란 소프트웨어를 설계하는 데 적합한 방법은 아니다.
- 정보 은닉은 시스템을 모듈 단위로 분해하기 위한 기본 원리로 시스템에서 자주 변경되는 부분을 상대적으로 덜 변경되는 안정적인 인터페이스 뒤로 감춰야 한다는 것이 핵심이다.
- 모듈의 장점
  - 모듈 내부의 변수가 변경되더라도 모듈 내부에만 영향을 미친다.
  - 비즈니스 로직과 사용자 인터페이스에 대한 관심사를 분리한다.
  - 전역 변수와 전역 함수를 제거함으로써 네이스페이스 오염을 방지한다.

### ⚡ 아쉬운 점 및 회고
쉬고싶었지만, 생각보다 쉬지 못했다. 그래도 할건 해야한다는 마음에 결국 공부를 했고, 마음 편하게 주말같이 쉬지 못했다. 이번주도 잘 버텨보자. 일단, 이번주는 주어진 task에 대해서 어떻게 작업은 분활할지와 어떻게 구현할지 생각을 좀 해봐야겠다. 일단, 먼저 코드를 작성하지말고, 도메인은 분석하고 문맥에서 생각해보자. 기본적으로는 먼저 기존 코드를 분석. api를 분석.

이번주는 좀 더 뭐든지 적극적으로 해봐야겠다. 좀 소극적이기보단 더 적극적인 자세로...   

### 🚀 내일 할 일
- 오브젝트 8장 읽기 및 스터디 참여

### 🎯 이번주 목표
- 회사 문화에 적응하기
- 스터디 참여 및 오브젝트 10장까지 읽기
- 스터디를 위한 자바스크립트 코딩의 기술 훑어보기
- ReScript 공식 문서 훑어보기