## 📆 2021-05-25(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] Do it TS 책 11장까지 읽고 스터디 참여
  - [PR Link](https://github.com/saseungmin/typescript_programming_study/pull/12)
- [x] Lean UX Chapter 7장 읽기
  - [Link](https://github.com/saseungmin/reading_books_record_repository/tree/master/LEAN-UX/Part%202/Chapter%207)
- [x] 바닐라 자바스크립트 스터디 퀴즈 풀기

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] Do it TS 책 11장까지 읽고 스터디 참여
- [x] 린 UX 책 8장까지 읽고 스터디 참여
- [ ] 프로그래머스 코테 문제들 풀기
- [ ] 코어 자바스크립트 마무리 짓기
- [x] 바닐라 자바스크립트 스터디 참여하기
- [ ] 페캠 네카라쿠배 지원

### 🤔 공부하면서 배운것이 있다면?
#### 🎈 Do it TS에서 인상 깊었던 부분: Validation 모나드를 사용한 비밀번호 검증 기능 구현

- 비밀번호 검증에 `password`라는 속성이 있어야 하고, 이 속성에 `string` 타입의 값이 들어 있어야 한다.

```ts
import { Failure } from '../classes/Failure';
import { Success } from '../classes/Success';

export const checkNull = <S, F>(o: { password?: string }) => {
  const { password } = o;

  return (password === undefined || typeof password !== 'string') ?
    new Failure(['Password can not be null']) : new Success(o);
};
```

- 문자열 길이가 최소 6자 이상이어야 한다는 등 검증은 다음 `checkLength` 함수로 구현한다.

```ts
import { Failure } from '../classes/Failure';
import { Success } from '../classes/Success';

export const checkLength = (o: { password?: string }, minLength: number = 6) => {
  const { password } = o;

  return (!password || password.length < minLength) ?
    new Failure(['Password must have more than 6 characters']) : new Success(o);
};
```

- 다음 코드에서 `checkPassword` 함수는 이러한 내용을 구현한 예이다.

```ts
import { Validation } from './classes/Validation';
import { checkNull } from './utils/checkNull';
import { checkLength } from './utils/checkLength';

export const checkPassword = (o): [object, string[]] => {
  const result = Validation.of(a => b => o)
    .ap(checkNull(o))
    .ap(checkLength(o));

  return result.isSuccess ? [result.value, undefined] : [undefined, result.value];
};
```

- 다음은 `checkPassword` 함수를 테스트하는 코드이다.

```ts
import { checkPassword } from '../checkPassword';

[
  { password: '123456' },
  { password: '1234' },
  {},
  { pa: '123456' },
]
  .forEach((target, index) => {
    const [ value, failureReason ] = checkPassword(target);

    if (failureReason) {
      console.log(index, 'validation fail.', JSON.stringify(failureReason));
    } else {
      console.log(index, 'validation ok.', JSON.stringify(value));
    }
  });

// 0 validation ok. {"password":"123456"}
// 1 validation fail. ["Password must have more than 6 characters"]
// 2 validation fail. ["Password can not be null","Password must have more than 6 characters"]
// 3 validation fail. ["Password can not be null","Password must have more than 6 characters"]
```


### ⚡ 아쉬운 점 및 회고
- 반성할 점
  - 시간 관리 실패
  - 생각이 많음
  - 우선순위를 정하지 못함
  - 정신 못차림
- 바닐라 자바스크립트 스터디 퀴즈를 풀었다. 오랜만에 다시 생각해보니 다 까먹은거 같은 느낌..?
- 내일은 코테 문제좀 많이 풀어봐야겠다.
- 네카라쿠배 지원이 이번주가 마감인데 얼른 써야겠다.
- 시간관리좀 잘좀하자. 내가 남들보다 배우는 속도가 느려서 좀 관리를 잘 해야할 거 같다.
- 그리고 내일 스터디 두개가 시간이 겹쳐보이는데 어떻게 해야할지 고민좀 해봐야곗다. 어떤 방식으로 되는지도 의문이다.

### 🚀 내일 할 일
- 프로그래머스 코테 문제 풀기
- 린 UX 책 8장까지 읽고 스터디 참여
- 바닐라 자바스크립트 스터디 참여하기

### 🎯 이번주 목표
- Do it TS 책 11장까지 읽고 스터디 참여
- 린 UX 책 8장까지 읽고 스터디 참여
- 프로그래머스 코테 문제들 풀기
- 코어 자바스크립트 마무리 짓기
- 바닐라 자바스크립트 스터디 참여하기
- 페캠 네카라쿠배 지원
