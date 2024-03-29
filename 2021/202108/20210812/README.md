## 📆 2021-08-12(목) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 집 알아보기
- [x] 전 회사에 전화
- [x] 함께 자라기 끝까지 읽기
  - [PR](https://github.com/saseungmin/reading_books_record_repository/pull/103)
- [x] reading_books_record_repository 사이트에 정리한 책 추가하기
  - [함께 자라기 적용 PR](https://github.com/saseungmin/reading_books_record_repository/pull/104)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 스터디 참여 및 오브젝트 4장까지 읽기
- [x] reading_books_record_repository 사이트에 정리한 책 추가하기
- [ ] ConStu 내 정보 페이지
- ~~함께 자라기 책 읽기 마무리~~
- [x] 입사 관련 서류 준비 및 500만원 한도 장비 구입
- [x] 집 알아보기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 함께 자라기 chapter 3: 애자일
- [정리 링크](https://github.com/saseungmin/reading_books_record_repository/tree/master/summarize_books_in_markdown/%ED%95%A8%EA%BB%98%20%EC%9E%90%EB%9D%BC%EA%B8%B0/Chapter%203)
- 애자일은 불확실성이 높은 프로젝트 적합하다.
- 애자일이 불확실성을 다루는 방식은 좀 더 짧은 주기로 더 일찍부터 피드백을 받고, 더 다양한 사람으로부터 더 자주 그리고 더 일찍 피드백을 받는 것으로 정리할 수 있다.
- 조직에서 성공 기여도를 높이려면 짧은 반복 개발 주기, 고객 참여, 코드 공유에 관심을 기울여야 한다.

#### 🎈 ReScript
- https://rescript-lang.org/docs/manual/latest/introduction
- 리스크립트는 자바스크립트의 기능 중 특별히 선별된 기능만 다룬다.
- 리스크립트의 타입시스템
  - 간단한 서브셋만 선정해서 대부분의 사람이 사용하기 더 쉽다.
  - 타입 함정이 없다. 리스크립트 코드에선 `null` / `undefined` 에러가 없다.
  - 타입은 모두에게 동일하다. 억지로 타입을 맞추기 위한 타입 서커스, 그리고 불필요한 타입정의는 필요 없다.
  - 라스크립트는 자바스크립트 개발을 의한 가장 빠른 컴파일러 및 빌드 시스템 중 하나다.
  - 타입 어노테이션이 필요없다. 리스크립트에 의해 타입은 올바르게 추론되고 정확성이 보장된다.
- ReScript의 장점
  - ReScript는 자바스크립트보다 빠르다.
  - 사용하지 않는 코드를 훌륭하게 제거한다.
    - 자바스크립트 생태계는 패키지 의존성에 매우 민감하다. 실제로 사용하지 않는 엄청난 양의 코드가 최종 프로덕트 코드 번들에 들어가는 경우가 있다. 이렇게 사용하지 않는 코드는 로딩, 구문 분석, 인터프리터 속도에 영향을 끼친다. 리스크립트는 사용하지 않는 코드를 제거하는 기능을 아주 강력하게 제공한다.
  - 용량이 작은 자바스크립트 결과물
    - `Hello world` 리스크립트 프로그램은 20 바이트 자바스크립트 코드를 생성.
  - 개발시 빠른 반복 주기
    - 리스크립트 빌드 시간은 자바스크립트 생태계의 다른 정적 타이핑 환경보다 1 ~ 2배 빠름.
  - 가독성을 고려한 결과물 & 훌륭한 상호운용
    - 리스크립트의 자바스크립트 결과물은 굉장히 읽기 편하다. 이것은 코드가 어떻게 컴파일되는지 이해하고 버그를 줄이기 쉽게 만들어준다.
  - 코드 구조 보존
    - 리스크립트는 하나의 소스파일에 하나의 자바스크립트 결과물 파일을 매핑한다. 이는 번들러와 테스트 러너같은 기존 도구와의 통합을 쉽게 만든다. 빌드 설정을 크게 변경하지 않고 단일 파일로 리스크립트를 시작할 수 있다. 각 파일의 코드 구조도 모두 보존됨.

### ⚡ 아쉬운 점 및 회고
리스크립트는 꼭 공부하고 싶었다. 이번 기회에 공식문서를 훑어봐야겠다. 오늘은 자바스크립트가 아닌 리스크립트를 "왜" 사용해야하는지를 설명할 수 있게되었다! 리스크립트는 페이스북에서 만든 언어이다. 그렇기 때문에 리액트와도 호환이 잘 된다고한다. 그래서 요즘 뜨고있는 것이라 생각한다. 한번쯤은 공부해볼만하다. 그리고 리스크립트 소개에서 얘기하는 내용이 너무 멋있었다.

> 리스크립트는 자바스크립트에 비판적인 거리를 두고 있지만 자바스크립트의 중요성을 인정하는 사람들을 위한 언어.   
> 리스크립트 팀은 타입스크립트를 존중한다. 또한 타입스크립트는 자바스크립트 생태계에 긍정적인 영향을 끼친다고 생각한다.

결국, 기초가 되는 자바스크립트를 존중하고, 자바스크립트 슈퍼셋인 타입스크립트를 존중하는 자세로 리스크립트를 만들었다는 것.   

함께 자라기 책을 마무리지었다. 너무 좋은 책이었다. *아 그게 뭐였었지?* 라고 생각날 때마다 앞으로 계속 참고해볼만한 책이다. 두 피겨스케이팅 그룹에 대한 연구 결과부터 시작해서 얘기할만한 좋은 내용들이 예시로 담겨있다. 애자일이라는 방법론도 중요하지만 그것보다 중요한건 누가 프로젝트에 참여했는가가 더 중요한 문제. 결국 사람이 제일 중요한 문제이다.   

> 소프트웨어 개발은 예측하기 어렵고 복잡한 도메인이다. 새 프로젝트를 진행할 때에 우리가 어떤 방법론을 쓰느냐는 문제보다도 누가 참여하는가가 훨씬 더 압도적으로 중요한 문제가 아닐까?

오늘도 약속도 있었고, 입사 준비로 많은 양의 공부는 못했다. 내일도 마찬가지일듯하다. 내일은 무조건 500만원 한도 장비 목록 제출!

### 🚀 내일 할 일
- 보험관련 문제 해결
- 부동산 전화하기
- ConStu 내 정보 페이지
- 500만원 한도 장비 목록 제출
- ReScript 공식문서 훑어보기

### 🎯 이번주 목표
- 스터디 참여 및 오브젝트 4장까지 읽기
- reading_books_record_repository 사이트에 정리한 책 추가하기
- ConStu 내 정보 페이지
- 함께 자라기 책 읽기 마무리
- 입사 관련 서류 준비 및 500만원 한도 장비 구입
- ReScript 공식문서 훑어보기
- 집 알아보기
