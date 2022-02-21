## 📆 2021-06-01(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [ ] 바닐라 자바스크립트 스터디 과제 하기
- [x] 코어 자바스크립트 마무리 짓기
  - [Chapter 7: 클래스](https://github.com/saseungmin/reading_books_record_repository/tree/master/%EC%BD%94%EC%96%B4%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/Chapter%207)
- [ ] 프로그래머스 코테 문제들 풀기
- [x] 코드숨 개인 프로젝트
  - [e2e 테스트를 위한 Codeceptjs 초기 설정](https://github.com/CodeSoom/ConStu/pull/194)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- ~~Do it TS 책 12장까지 읽고 스터디 참여~~
- ~~린 UX 책 8장까지 읽고 스터디 참여~~
- [ ] 프로그래머스 코테 문제들 풀기
- [x] 코어 자바스크립트 마무리 짓기
- [ ] 바닐라 자바스크립트 스터디 참여하기
- [x] 코드숨 개인 프로젝트 e2e 테스트를 위한 Codeceptjs 적용하기
- ~~페캠 네카라쿠배 지원~~
- [ ] 면접 질문 준비하기


### 🤔 공부하면서 배운것이 있다면?

#### 🎈 코어 자바스크립트: 클래스
- 클래스는 어떤 사물의 공통 속성을 모아 정의한 추상적인 개념
- 인스턴스는 클래스의 속성을 지닌 구체적인 사례이다.
- 상위 클래스의 조건을 충족하면서 더욱 구체적인 조건이 추가된 것을 하위 클래스라고 한다.
- 클래스의 `prototype` 내부에 정의된 메서드를 프로토타입 메서드라고 하며, 이들은 인스턴스가 마치 자신의 것처럼 호출할 수 있다.
- 클래스(생성자 함수)에 직접 정의한 메서드를 스태틱 메서드라고 하며, 이들은 인스턴스가 직접 호출할 수 없고 클래스(생성자 함수)에 의해서만 호출할 수 있다.
- 클래스 상속을 흉내 내기 위해 세 가지 방법이 있는데 `SubClass.prototype`에 `SuperClass`의 인스턴스를 할당한 다음 프로퍼디를 모두 삭제하는 방법, 빈 함수(`Bridge`)를 활용하는 방법, `Object.create`를 이용하는 방법이다.
- 이 세 방법 모두 `constructor` 프로퍼티가 원래의 생성자 함수를 바라보도록 조정해야 한다.
- 상속 및 추상화를 구현하기 위해 상당히 복잡한 방법을 사용해야 했는데, ES6에서는 상당히 간단하게 처리할 수 있다.
- 자세한 내용은 [정리 참고](https://github.com/saseungmin/reading_books_record_repository/tree/master/%EC%BD%94%EC%96%B4%20%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8/Chapter%207)

#### 🎈 Codeceptjs
- [공식 사이트](https://codecept.io/)
- [Github](https://github.com/codeceptjs/CodeceptJS)
- [아샬님 CodeceptJS TIL](https://github.com/ahastudio/til/blob/main/test/20201207-codeceptjs.md)
- [아샬님 유튜브 CodeceptJS로 인수 테스트 작성하기](https://www.youtube.com/watch?v=Q6TkggwPzFA&ab_channel=%EC%BD%94%EB%94%A9%EC%9D%98%EC%8B%A0%EC%95%84%EC%83%AC)
- [Playwright](https://github.com/microsoft/playwright)
- e2e(인수) 테스트를 위한 선택 중 cypress와 Codeceptjs 두가지가 있었다. 제일 대중적이고 가장 압도적으로 많이 사용하는 건 cypress였다. [npm 다운로드 수만봐도 압도적.](https://www.npmtrends.com/codeceptjs-vs-cypress)
- Codeceptjs 3이 나옴.
- 간단한 적용방법

```bash
npx create-codeceptjs .
```

- [Testing with Playwright](https://codecept.io/playwright/#testing-with-playwright)
- Playwright는 브라우저에 맞게 알아서 변경해준다. MS에서 만듬 하지만 IE는 빠져있음 (Chromium, Firefox, WebKit) 예전엔 `Puppeteer` 많이 사용. 하지만 Puppeteer는 Chromium에서 밖에 사용 불가.

```bash
# 웹 브라우저를 화면에 띄워 테스트를 실행합니다.
npm run codeceptjs

# 웹 브라우저를 화면에 띄우지 않고 테스트를 실행합니다.
npm run codeceptjs:headless

# 웹 브라우저에 CodeceptUI를 띄워 훨씬 편학게 테스트를 실행합니다.
npm run codeceptjs:ui
```

- codeceptjs 초기 설정

```bash
npx codeceptjs init
```

- 다음 파일들이 생성

```
jsconfig.json
codecept.conf.js
steps.d.ts
steps_file.js
tests/.._test.js
```
- 추가적으로 eslint error를 없애기 위해 설치

```bash
npm i -S @codeceptjs/configure
```

- `.gitignore`에 추가

```bash
## codeceptjs
output
```

- `steps.d.ts`, `steps_file.js` 이 파일은 tests 파일 안으로 옮기는걸 선호
- 그러면 `codecept.conf.js`의 `include` 부분의 경로를 다음과 같이 변경

```js
// ...
exports.config = {
  tests: './tests/**/*_test.js',
  // ...
  include: {
    I: './tests/steps_file.js',
  },
  // ...
};
```


- 테스트 코드 작성시 다음과 같이 Given When Then으로 명확하게 작성하기

```js
Feature('사용자가 스터디 개설 및 스터디 참여를 하기 위해 회원가입을 할 수 있다.');

Scenario('올바르게 회원가입에 성공한 경우', ({ I }) => {
  // Given - 회원가입 페이지에서
  I.amOnPage('/register');
  // When - 이메일, 비밀번호, 비밀번호 확인을 입력 후 회원가입 버튼을 클릭하면

  // Then - 메인 페이지로 이동한다.
});
```

### ⚡ 아쉬운 점 및 회고
- 나는 조용한 새벽이 공부가 더 잘된다. 근데 이렇게 살다가 죽을지도 모를거 같다는 느낌이 든다.
- 일어났을때 현타가... 남들 다 일하고 출근하고 공부할 시간에 나는 잠을 자다니..
- 아쉬운것 공부량이 부족했다. 열심히 했다고는 말 못하겠다.
- 갈팡질팡 어떻게 해야하나.. 생각이 오늘도 많았다.
- 집중을 할 때 확 깊은 집중력을 가지고 싶다. 남들보다 집중력이 부족한 거 같다. 특히 하기 싫은 거할때.
- 아니면 재미없는 거 할때. 나는 그게 너무 심하다. 하고 싶은 건 미친듯이 집중하고 몰두해서 파는 성격이지만, 하기 싫은건 진짜 죽어도 하기 싫다. 너무 극과 극..
- 하지만, 내가 그 하고싶은 걸 더 잘하기 위해서 하는 하기 싫은 건 억지로 더 실력을 키우기 위해서 하려고 노력 뿐만 아니라 한다. 하지만, 생각보다 시간대비 공부효율이 안나오는거 같은.. 그런 느낌?
- 명확한 목표의식과 확고한 자기반성과 할 수 있다는 자신감, 자신에 대한 믿음이 필요할 때다. 그렇게 느낀다. 아니 그래야만 한다.
- 졸립다. 얼른 자야겠다.

### 🚀 내일 할 일
- 바닐라 자바스크립트 스터디 참여하기
- 프로그래머스 코테 문제들 풀기
- 코드숨 개인 프로젝트에 e2e 테스트를 위한 Codeceptjs를 적용하기

### 🎯 이번주 목표
- ~~Do it TS 책 12장까지 읽고 스터디 참여~~
- ~~린 UX 책 8장까지 읽고 스터디 참여~~
- 프로그래머스 코테 문제들 풀기
- 코어 자바스크립트 마무리 짓기
- 바닐라 자바스크립트 스터디 참여하기
- ~~페캠 네카라쿠배 지원~~
- 면접 질문 준비하기
- 코드숨 개인 프로젝트에 e2e 테스트를 위한 Codeceptjs를 적용하기
