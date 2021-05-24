## 📆 2021-05-24(월) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] Do it TS 책 11장까지 읽고 스터디 참여
  - [PR Link](https://github.com/saseungmin/typescript_programming_study/pull/12)
- [x] Lean UX Chapter 6장 읽기
  - [Link](https://github.com/saseungmin/reading_books_record_repository/tree/master/LEAN-UX/Part%202/Chapter%206)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] Do it TS 책 11장까지 읽고 스터디 참여
- [x] 린 UX 책 8장까지 읽고 스터디 참여
- [ ] 프로그래머스 코테 문제들 풀기
- [ ] 코어 자바스크립트 마무리 짓기
- [ ] 바닐라 자바스크립트 스터디 참여하기
- [ ] 페캠 네카라쿠배 지원

### 🤔 공부하면서 배운것이 있다면?
#### 🎈 Do it TS에서 인상 깊었던 부분
- 모나드의 Maybe 테스트하는 부분이다.
- 다음 `getJokeAsMaybe` 함수는 정상적인 데이터는 `Maybe.Just`로 처리하고, 오류가 발생하면 `reject` 함수를 호출하지 않고 `Maybe.Nothing`을 반환한다.

```ts
import * as R from 'ramda';

import { JokeType, getRandomJoke } from './getRandomJoke';
import { IMaybe, Maybe } from './classes/Maybe';

const _getJokeAsMaybe = async() => {
  const jockItem: JokeType = await getRandomJoke();
  const jock = R.view(R.lensProp('joke'), jockItem);
  return jock;
}

export const getJokeAsMaybe = () => new Promise<IMaybe<string>>((resolve, reject) => {
  _getJokeAsMaybe()
    .then((jock: string) => resolve(Maybe.Just(jock)))
    .catch(e => resolve(Maybe.Nothing)); // reject가 아닌 resolve
});

export { IMaybe, Maybe };
```

- `getJokeAsMaybe`는 에러가 발생하면 `reject` 호출 대신 `Maybe.Nothing`을 반환하므로 다음 테스트 코드는 `catch`문이 없어 간결하다.

```ts
import { getJokeAsMaybe, IMaybe } from '../getJokeAsMaybe';

(async() => {
  const joke: IMaybe<string> = await getJokeAsMaybe();
  console.log(joke.getOrElse('something wrong'));
})();
```

- `Maybe`는 이처럼 오류일 때와 정상일 떄를 모두 고려하면서도 사용하는 쪽 코드를 매우 간결하게 작성할 수 있게 해준다.


### ⚡ 아쉬운 점 및 회고
- 호잇! 시간이 6시가 다되어간다. TIL를 작성법을 바꾼다고 했는데 그렇게 하지 못했다.
- TDD를 적용할 때도 작업의 단위를 잘게 쪼개듯이 할 일의 단위를 잘게 쪼개서 작성해봐야겠다.
- 즉, 바로바로 한 일들을 TIL을 작성하는 것에 채워나가는 것이다. 그니까 TIL TDD라 할 수 있겠다.
- 오늘도 효율적인 공부는 못했다.
- 그리고 수요일부터 바닐라 JS 스터디가 시작되는데 신청을 잘한건지 모르겠다. 하지만, 해야만 한다는 그런 이끌림이 있었다. 그냥 지금 아니면 다신 못할 거 같다는 생각이 들었고, 지금 중요한 것도 이부분이 부족하다고 느꼈다.
- 잘 해보자..!
- 근데 코드숨 스터디가 9시 시작인데 그 스터디는 8시 시작이다.. 일단 바닐라 스터디를 참여하고 시간이 되면 늦게라도 들어가는 식으로 해야겠다.
- 얼른 잠에 빠지러 갑시다! 좋은 꿈을 꿨으면 좋겠당.

### 🚀 내일 할 일
- 프로그래머스 코테 문제 풀기
- Do it TS 책 11장 마저 읽기
- 린 UX 책 7장 읽기

### 🎯 이번주 목표
- Do it TS 책 11장까지 읽고 스터디 참여
- 린 UX 책 8장까지 읽고 스터디 참여
- 프로그래머스 코테 문제들 풀기
- 코어 자바스크립트 마무리 짓기
- 바닐라 자바스크립트 스터디 참여하기
- 페캠 네카라쿠배 지원
