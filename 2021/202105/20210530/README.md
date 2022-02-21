## 📆 2021-05-30(일) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 프로그래머스 코테 문제 풀기
  - [삼각 달팽이](https://github.com/saseungmin/daily_coding_dojo/tree/master/programmers/Level%202/%EC%82%BC%EA%B0%81%20%EB%8B%AC%ED%8C%BD%EC%9D%B4)
  - [숫자의 표현](https://github.com/saseungmin/daily_coding_dojo/tree/master/programmers/Level%202/%EC%88%AB%EC%9E%90%EC%9D%98%20%ED%91%9C%ED%98%84)
- [x] 바닐라 자바스크립트 스터디 과제 하기
  - Private Repo라 생략
- [x] Do it TS 책 12장 읽기
  - [PR Link](https://github.com/saseungmin/typescript_programming_study/pull/13)
- [ ] 페캠 네카라쿠배 지원서 작성

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] Do it TS 책 12장까지 읽고 스터디 참여
- ~~린 UX 책 8장까지 읽고 스터디 참여~~
- [x] 프로그래머스 코테 문제들 풀기
- [ ] 코어 자바스크립트 마무리 짓기
- [x] 바닐라 자바스크립트 과제 및 스터디 참여
- [ ] 페캠 네카라쿠배 지원

### 🤔 공부하면서 배운것이 있다면?
- Object Null 체크하는 방법을 알았다.
- Object와 Null은 타입이 같기 때문에 null도 체크해주어야 한다.
- [Link](https://levelup.gitconnected.com/how-to-check-for-an-object-in-javascript-object-null-check-3b2632330296)

```js
const isObject = (value) => typeof value === "object" && value !== null;
```

- ESLint 컨벤션에 `no-prototype-builtins`으로 인해 다음과 같이 객체에서 직접 호출할 때 에러를 발생시킨다.

```js
const obj = {
  name: 'seungmin',
};

obj.hasOwnProperty('name'); // error
```

- 그래서 다음과 같이 `Object.prototype`에서 직접호출하여야 한다.

```js
Object.prototype.hasOwnProperty.call(obj, 'name'); // true
```

- 그에 대한 이유는 다음 링크 참고
- [Link](https://stackoverflow.com/questions/12017693/why-use-object-prototype-hasownproperty-callmyobj-prop-instead-of-myobj-hasow)
- [Link](https://yeon-js.tistory.com/8)

### ⚡ 아쉬운 점 및 회고
- 지원서좀 작성하자..
- 솔직히 너무 귀찮아.. 아오..
- TIL을 처음으로 이틀동안 쓰지 않았다. 물론 공부는 계속했다. 새벽에 공부하니까 열심히공부하고 TIL까지 쓰려니 피곤해서 안쓰게 되는거 같다..
- 그리고 TIL작성을 하루의 마지막이아니라 하루를 지나가며 배우고 한 것에 대해서 작성하기로 했는데 그러지 못했다. 한가지를 수행 혹은 완료하면 꼭 작성하고 배운거나 알게된 것들을 꼭 그때그때 작성좀 해야겠다.
- 마지막에 작성하니 뭐였는지 까먹는경우도 많다.
- 그리고 테크러닝 4기 발표가 나와는데 당연히 떨어질줄 알았다. 역시 3기 수강했던 사람들은 아예 배제하고 뽑았던거 같다. 같은 슬랙방을 쓰는거보니..
- 슬랙방이 어쩌다보니 9개가 되었다. 계속 인사이트를 얻을 수 있어서 더 많은 슬랙방에 들어가고 싶다.

### 🚀 내일 할 일
- 페캠 네카라쿠배 지원서 작성
- Do it TS 책 12장까지 읽고 스터디 참여
- 바닐라 자바스크립트 스터디 과제 하기

### 🎯 이번주 목표
- Do it TS 책 12장까지 읽고 스터디 참여
- ~~린 UX 책 8장까지 읽고 스터디 참여~~
- 프로그래머스 코테 문제들 풀기
- 코어 자바스크립트 마무리 짓기
- 바닐라 자바스크립트 스터디 참여하기
- 페캠 네카라쿠배 지원
