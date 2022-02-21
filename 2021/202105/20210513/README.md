## 📆 2021-05-13(목) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] TS 책 8장 읽기
  - Chapter 8 장을 읽고 정리했다
  - [Link](https://github.com/saseungmin/typescript_programming_study/tree/master/Chapter%208)
- [x] 프로그래머스 코테 문제들 풀기
  - BFS 한 문제를 풀었다.
  - [Link](https://github.com/saseungmin/daily_coding_dojo/tree/master/programmers/Level%203/%EA%B0%80%EC%9E%A5%20%EB%A8%BC%20%EB%85%B8%EB%93%9C)
- [x] leetCode 문제 풀기
  - 한 문제 풀었다
- [x] 프로그래머스 월간 코드 챌린지에 참여했다.
  - 4문제 중 2문제를 풀었다.
- [ ] 인프런 알고리즘 Section 10 풀기

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] Do it TS 책 9장까지 읽고 스터디 참여
- ~~테스트 주도 개발로 배우는 객체 지향 설계와 실천 25장까지 읽고 스터디 참여~~
- [ ] 인프런 알고리즘 Section 10 풀기
- [x] 프로그래머스 코테 문제들 풀기
- [ ] 코드숨 프로젝트 Dark 모드 적용

### 🤔 공부하면서 배운것이 있다면?

- TS Chapter 8장을 공부하면서 함수 조합인 부분 함수 적용 부분이 있었는데 꽤나 인상깊었다.
- `compose` 함수와 `pipe` 함수를 사용하는 법을 익혔다. 이 둘은 함수 조합을 해주는 함수이다.
- 함수 조합은 작은 기능을 구현한 함수를 여러 번 조합해 더 의미 있는 함수를 만들어 내는 프로그램 설계 기법이다.
- 다음은 파이프 함수이다.

```ts
const f = <T>(x: T): string => `f(${x})`;
const g = <T>(x: T): string => `g(${x})`;
const h = <T>(x: T): string => `h(${x})`;

const pipe = <T, R>(...functions: readonly Function[]): Function => (x: T): (T) => R => {
  return functions.reduce((value, func) => func(value), x);
}

const piped = pipe(f, g, h);
console.log(piped('x')); // h(g(f))
```

- 이 `pipe` 함수를 응용해서 다음과 같이 사용할 수 있었다.

```ts
const map = f => a => a.map(f);

const square = value => value * value;
const squareMap = map(square);

const fourSquare = pipe(
  squareMap,
  squareMap,
);

console.log(fourSquare([3, 4])); // [81, 256]
```

### ⚡ 아쉬운 점 및 회고
- TS의 함수형 프로그래밍 부분이 나오는데 너무 재밌다..! 함수형을 점점 알아가는 기분인데 뭔가 변태같은데 계속 함수로 감싸고 빼고 해서 코드가 간단해지는 걸 보면 참 기분이 좋다. 함수형은 어렵지만, 사용해볼려고 노력해야겠다. 오늘 `pipe` 함수를 만들어서 저렇게 사용하는 것을 보고 경의롭다..? 신기했다. 써먹어볼때가 있으면 써먹어보고 싶다.
- 오늘 시간대비 아니, 그냥 공부를 얼마 안했다. 그냥.. 뭔가 하기 싫은 날이였다. 그리고 확실하게 느끼고 있는 건 얼른 취업해야겠다. 남들은 계속 성장하는데 나는 제자리인거 같은 기분..? 얼른 취업해서 더 빨리 성장해야곘다.
- 시간 활용을 너무 못한다. 의미 없는 시간이 너무 많은 거 같다. 좀 더 나은 내일이 되었으면 좋겠다. 진짜로.. 근데 내일은 좀 나가서 놀고 싶다. 지긋지긋해진다. 매일 똑같은 하루.. 솔직히 퇴사하고도 매일 같이 10시간씩 공부하고 주말까지도 똑같은 하루라.. 쉰날이 다섯손가락에 든다.. 사실 이 쉰 날도 하루를 통째로 쉰적은 전혀 없다. 적어도 6시간은 공부했던거 같다.
- 지치면 안되는데 지칠려한다. 물론 코딩은 즐겁다. 똑같은 일상에 지치는거 뿐이지. 끝!

### 🚀 내일 할 일
- 코어 자바스크립트 6장 읽기
- 프로그래머스 코테 문제들 풀기
- leetCode 문제 풀기
- 인프런 알고리즘 Section 10 풀기

### 🎯 이번주 목표
- Do it TS 책 9장까지 읽고 스터디 참여
- 테스트 주도 개발로 배우는 객체 지향 설계와 실천 25장까지 읽고 스터디 참여
- 인프런 알고리즘 Section 10 풀기
- 프로그래머스 코테 문제들 풀기
- 코드숨 프로젝트 Dark 모드 적용
