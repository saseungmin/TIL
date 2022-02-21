## 📆 2021-06-02(수) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 바닐라 자바스크립트 스터디 참여하기 및 Mission 2 필수과제 풀기
- [ ] 프로그래머스 코테 문제들 풀기
- [x] 코드숨 개인 프로젝트
  - [회원가입과 로그인에 대한 e2e 테스트를 작성](https://github.com/CodeSoom/ConStu/pull/195)
- CodeceptJS PR 날리기
  - [CodeceptJS 문서에서 잘못 작성된 부분 수정](https://github.com/codeceptjs/CodeceptJS/pull/2911)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- ~~Do it TS 책 12장까지 읽고 스터디 참여~~
- ~~린 UX 책 8장까지 읽고 스터디 참여~~
- [ ] 프로그래머스 코테 문제들 풀기
- ~~코어 자바스크립트 마무리 짓기~~
- [x] 바닐라 자바스크립트 스터디 참여하기
- [x] 코드숨 개인 프로젝트 e2e 테스트를 위한 Codeceptjs 적용하기
- ~~페캠 네카라쿠배 지원~~
- [ ] 면접 질문 준비하기

### 🤔 공부하면서 배운것이 있다면?
- Codeceptjs에서 auto login 하는 방법
- auto login을 하면 따로 설정하지 않고 시나리오 이전에 로그인 후 작업을 처리할 수 있다.
- plugins에 autoLogin 추가

```js
// codecept.conf.js
// ...
exports.config = {
  // ...
  plugins: {
    // ...
    autoLogin: {
      enabled: true,
      saveToFile: true,
      inject: 'login',
      users: {
        user: {
          login: (I) => {
            I.amOnPage('/login');
            I.fillField('input[name=userEmail]', 'test@test.com');
            I.fillField('input[name=password]', '123123');
            I.click('button[type=submit]');
          },
          check: (I) => {
            I.seeCurrentUrlEquals('/');
            I.see('로그아웃');
            I.see('test@test.com');
          },
        },
      },
    },
  },
};
```

- 해당 e2e 테스트에 auto login 적용하기

```js
Feature('로그인 한 사용자가 메인 페이지에서 스터디에 대한 정보 및 관련 화면으로 이동할 수 있다.');

Before(({ login }) => { // 이 파일의 테스트의 이전에 login 적용
  login('user');
});

Scenario('올바르게 스터디 리스트가 보이는 경우', ({ I }) => {
  I.see('스터디 개설하기');
});
```

- 시나리오 마다 적용하기

```js
Feature('로그인 한 사용자가 메인 페이지에서 스터디에 대한 정보 및 관련 화면으로 이동할 수 있다.');

Scenario('올바르게 스터디 리스트가 보이는 경우', ({ I, login }) => {
  login('user');

  I.see('스터디 개설하기');
});
```

### ⚡ 아쉬운 점 및 회고
- 오늘 두근두근 하며 규모가 큰 Codecept.js에 PR을 날려보았다.
- 공식 문서를 읽다가 [commentstep](https://codecept.io/plugins/#commentstep)에 꺠진 JS 코드블럭을 확인하였다. 처음엔 별 생각이 없다가 오? 이거 PR을 날려보면 좋겠는걸? 해서 바로 날렸다.
- 그리고 [autoLoin부분도 잘못 작성](https://codecept.io/plugins/#usage-2)되어 있는걸 확인하였다. 현재 공식 문서에는 다음과 같이 되어있다.

```js
Before((login) => {
  login('user');
});
```

- 하지만, 실행해본결과 파라미터값이 없다고 나왔다. 객체형식으로 되어있었다.

```js
Before(({ login }) => {
  login('user');
});
```

- 이 두문제를 수정하여 [PR을 날렸다.](https://github.com/codeceptjs/CodeceptJS/pull/2911)
- 영어가 한심한 수준이다...ㅎ..
- 구글 번역기를 돌려가며 그냥 날려보았다. merge가 되었으면 좋을거 같다. 하지만, 잘 모르겠다.
- Contribute 규정을 문서 수정 PR에 대해서는 정해진 규정이나 제약은 없어보였다. 그리고 다른 사람들의 PR을 참고하였다.
- 굉장히 사소한거지만 이렇게 못하는 사람이 태반이다. 에이 그거 쉬운데? 뭐 그런걸 PR을 날려? 그럼 당신들도 하세요. 말만 하지말고. 말만 하는 사람이 대부분이다. 이걸 수행하는 게 어려운거지
- 그래서 계속 보이는거 마다 PR을 날려볼 생각이다. Contributor되는것도 재밌다. 그리고 Github에 하나씩 추가되는것도 재밌다.
- 점점 자는시간이 늦어진다. 그만큼 어짜피 아침까지 공부하긴 하는데 이러다가 진짜 저녁에 일어나거 같다.
- 오늘은 8시까지 공부했고, 어제도 9시에 잔거 같다. 흠.. 점점 자는 시간이 늦어지는데 어떻게 해야할 거 같다..

### 🚀 내일 할 일
- 바닐라 자바스크립트 과제 보너스 하나 풀기
- 프로그래머스 코테 문제들 풀기
- 코드숨 개인 프로젝트에 e2e 테스트를 위한 Codeceptjs를 적용하기

### 🎯 이번주 목표
- ~~Do it TS 책 12장까지 읽고 스터디 참여~~
- ~~린 UX 책 8장까지 읽고 스터디 참여~~
- 프로그래머스 코테 문제들 풀기
- ~~코어 자바스크립트 마무리 짓기~~
- 바닐라 자바스크립트 과제 풀기
- ~~페캠 네카라쿠배 지원~~
- 면접 질문 준비하기
- 코드숨 개인 프로젝트에 e2e 테스트를 위한 Codeceptjs를 적용하기
