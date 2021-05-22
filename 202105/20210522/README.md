## 📆 2021-05-22(토) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 프로그래머스 코테 문제 풀기
  - [프렌즈 4 블록](https://github.com/saseungmin/daily_coding_dojo/tree/master/programmers/Level%202/%5B1%EC%B0%A8%5D%20%ED%94%84%EB%A0%8C%EC%A6%884%EB%B8%94%EB%A1%9D)
- [ ] 알고리즘 공부
- [x] Do it TS 책 10장 읽기
  - [PR Link](https://github.com/saseungmin/typescript_programming_study/pull/11)
- [ ] 린 UX 책 5장 읽기
- [x] Recoil Todo: 취약점 제거를 위한 npm dependencies를 업데이트 했다.

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] Do it TS 책 9장까지 읽고 스터디 참여
- ~~린 UX 책 4장까지 읽고 스터디 참여~~
- ~~인프런 알고리즘 Section 10 풀기~~
- [x] 프로그래머스 코테 문제들 풀기
- [ ] 코드숨 프로젝트 Dark 모드 적용
- [ ] 코어 자바스크립트 마무리 짓기
- ~~우아한 테크러닝 4기 신청하기~~

### 🤔 공부하면서 배운것이 있다면?
- [프렌즈 4 블록](https://github.com/saseungmin/daily_coding_dojo/tree/master/programmers/Level%202/%5B1%EC%B0%A8%5D%20%ED%94%84%EB%A0%8C%EC%A6%884%EB%B8%94%EB%A1%9D)
- 카카오 코테를 풀면서 이번에 행렬을 다루는 걸 좀 자세히 알게되었다?
- 이리저리 해보면서 행렬을 사용한 완전탐색을 해봤다.

#### 🎈 인덱스 타입 제약
- 객체의 일정 속성들만 추려서 좀 더 단순한 객체를 만들어야 할 때가 있다.

```ts
const obj = {
  name: 'Jane',
  age: 22,
  city: 'Seoul',
  country: 'Korea',
}
const pick = (obj, keys) => keys.map(key => ({ [key]: obj[key] }))
  .reduce((result, value) => ({ ...result, ...value }, {}))
// obj 객체에서 name과 age 두 속성만 추출
pick(obj, ['name', 'age']); // { name: 'Jane', age: 22 }
pick(obj, ['nam', 'agge']); // { name: undefined, age: undefined }
```

- 위 예제처럼 오타가 발생하면 엉뚱한 결과가 나온다. 타입스크립트는 이러한 상황을 방지할 목적으로 다음처럼 `keyof T` 형태로 타입 제약을 설정할 수 있게 지원한다. 이것을 **인덱스 타입 제약**이라고 한다.

```ts
<T, K extends keyof T>
```

- `keyof T` 구문으로 타입 `K`가 타입 `T`의 속성 이름이라고 타입 제약을 설정한다.

```ts
const pick = <T, K extends keyof T>(obj: T, keys: K[]) => 
  keys.map(key => ({ [key]: obj[key] }))
    .reduce((result, value) => ({ ...result, ...value }, {}))
```

- 이렇게 하면 컴파일을 해보지도 않고 앞에서 예로 든 `nam`, `agge`와 같은 입력 오류를 코드 작성 시점에 탐지할 수 있다.

### ⚡ 아쉬운 점 및 회고
- 어구 오늘은 일찍 쉬어야겠다.
- TIL을 작성하는 이유에 대해서 자꾸 까먹고 작성하는 거 같다. TIL을 작성하는 건 하루의 잘못된 점과 배운점, 회고를 하기 위해서 작성하는 것이고, 또 오늘 계획을 잘 지켰졌나를 확인하기 위해서 작성하는 것이다.
- TIL를 작성할 때 조금은 다른 방식으로 작성해봐야겠다. 지금 현재 하루를 마무리하는 의미로 TIL를 작성하고 있는데 하루의 마무리가 아닌 배운 것들이나 한 것들을 주기적으로 업데이트하는 식으로 바꿔봐야겠다.
- 그리고 공부하는데 속도가 안난다. 남들보다 오래걸릴 뿐더러 남들보다 이해하는 즉, 지식을 습득하는 양도 부족하다고 느낀다. 이럴 때 나를 자꾸 탓하게 되는데 또한, 자존감도 낮아지게 된다.
- 그리고 남들과 비교하지 말아야하는데 그게 참 쉽지않다. 이젠 남들을 보며 진짜 열심히한다라고 생각하지만, 이젠 동기부여를 얻기보다 자존감만 낮아지는 느낌이다.
- 아쉬움이 많고 생각이 많은 하루다.

### 🚀 내일 할 일
- 프로그래머스 코테 문제 풀기
- Do it TS 책 10장 읽기
- 린 UX 책 5장 읽기

### 🎯 이번주 목표
- Do it TS 책 11장까지 읽고 스터디 참여
- 린 UX 책 4장까지 읽고 스터디 참여
- ~~인프런 알고리즘 Section 10 풀기~~
- 프로그래머스 코테 문제들 풀기
- 코드숨 프로젝트 Dark 모드 적용
- 코어 자바스크립트 마무리 짓기
- 우아한 테크러닝 4기 신청하기
