## 📆 2021-03-24(수) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (프론트부분 로직 변경)
  - IOS 및 Safari에서 쿠키가 저장되지 않는 문제 원인 해결
  - [PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/71)
- [x] 오브젝트 Chapter 11 읽고 스터디 참여
  - 스터디 참여 및 11장을 읽었다.
  - [Chapter 11](https://github.com/saseungmin/reading_books_record_repository/tree/master/%EC%98%A4%EB%B8%8C%EC%A0%9D%ED%8A%B8/Chapter%2011)
- [x] 스터디 질문 선정하기
  - [질문 선정](https://github.com/Fortuna-Study/Frontend-Interview-Library/tree/main/week_1)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 알고리즘 공부 (Section 6)
- [x] 오브젝트 책 Chapter 11 까지 읽기 및 스터디 참여
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
- [x] 취업 준비 스터디 관련 준비 및 스터디 참여

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 Recoil을 사용한 To DO 애플리케이션 만들기
- 이슈란에 이번에 JWT를 쿠키에 담는 고민했던 문제를 작성하였다.([ISSUE-comment](https://github.com/saseungmin/Recoil_ToDo/issues/57#issuecomment-805893740))
- axios를 테스팅할 떄 알게된 것이 있는데, `jest.unmock`을 알게되었다.
- `jest.unmock`을 사용하면 mocking 되어있는 함수를 기존의 import받은 자체의 함수로 즉, 원래의 것으로 다시 바꿀 수가 있다.
- 이 방법을 사용한 계기는 전역으로 axios가 다음과 같이 mocking되어 있는데, 하나의 테스트에서 기존의 axios로 테스트 할 필요가 있어서 `unmock`을 사용해서 풀어주었다.

```js
// ./__mocks__/axios.js
const mockAxios = jest.genMockFromModule('axios');

mockAxios.create.mockReturnThis();

export default mockAxios;

// client.js
jest.mock('../cookie', () => ({
  getCookie: jest.fn(),
}));

jest.unmock('axios');
describe('request interceptor', () => {
  beforeEach(() => {
    jest.clearAllMocks();
  });

  it('API request should add authorization token to header', () => {
    getCookie.mockReturnValueOnce('token');

    const result = client.interceptors.request.handlers[0].fulfilled({ headers: {} });

    expect(getCookie.mock.calls.length).toBe(1);
    expect(result.headers).toHaveProperty('Authorization', 'token');
  });
});
```

- 브라우저 쿠키를 사용하는 방법을 알았다. [universal-cookie](https://www.npmjs.com/package/universal-cookie)를 이용하면 간단하게 사용할 수 있었다.

```js
import Cookies from 'universal-cookie';
 
const cookies = new Cookies();
 
cookies.set('myCat', 'Pacman'); // set
const pet = cookies.get('myCat');
console.log('Pacman'); // get
```

#### 🎈 오브젝트 Chapter 11 및 스터디를 통해 배운것
- 오브젝트 Chapter 11 정리 [링크](https://github.com/saseungmin/reading_books_record_repository/tree/master/%EC%98%A4%EB%B8%8C%EC%A0%9D%ED%8A%B8/Chapter%2011)
- 의존성 역전는 상위 수준의 클래스는 어떤 식으로든 하위 수준의 클래스에 의존해서는 안 되고 하위 수준의 변경으로 인해 상위 수준이 변경돼서는 안 된다.
- 의존성 역전 원칙이란 상위 수준의 모듈은 하위 수준의 모듈에 의존해서 안된다. 
- 의존성 역전은 추상화는 구체적인 사항에 의존해서는 안 된다는 것이다. 
- 즉, 상위와 하위 수준의 모듈 둘 다 추상화에 의존해야 하고, 구체적인 사항은 추상화에 의존해야 한다.
- 배운것 상속에서 합성으로 변경되는 과정
- 고민해볼것 트레이트와 믹스인

### ⚡ 아쉬운 점 및 회고
- 오늘 그래도 Recoil Todo 문제를 해결해서 다행이다. 이번 계기로 많은 것을 알게 되었다. 이번에 고통을 많이 받았는데 HTTP 책을 좀 읽어봐야겠다. 너무 무지하다...
- Recoil Todo 앱은 이제 Safari에서도 되고, IOS에서도 된다. 다만 한계점이 있었고 그 부분은 이슈란에 정리해놨다. 여태까지 TIL을 작성하고 있는데 굉장히 좋은 거 같지만, 매일 모르는 부분과 배운 부분을 정리하는데 이부분을 날짜별로 하니까 찾기가 어려운 거 같다. 방법을 바꿀 필요가 있어보인다. 그때 진유림님의 TIL처럼 정리해놓는게 좋아보인다. 이처럼 작성한 회고는 따로 빼놓고 배운 것들과 자료 찾은 것들을 정리해놓고 나중에 찾아보기 좋게 해놓는것이 좋을 거 같다.
- 오늘 오브젝트 스터디를 했는데 좋았따. 역시 스터디를 하니 모르는 부분도 다시 이해할 수 있게 되고, 제일 좋은 건 혼자 절대 안읽을 책들을 강제로라도 읽게 해준다. 이게 제일 좋은 거 같다.
- 취업 준비 스터디 질문을 정했다. 처음은 가볍게 할 수 있는 질문을 선정했는데, 이제 이 부분들을 공부해보자.


### 🚀 내일 할 일
- Recoil를 사용한 ToDo 앱 만들기 진행하기 (리팩토링 진행)
- 스터디 질문에 대해서 공부하기
- 알고리즘 공부 (스택 부분)

### 🎯 이번주 목표
- 알고리즘 공부 (Section 6)
- 오브젝트 책 Chapter 11 까지 읽기 및 스터디 참여
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 취업 준비 스터디 관련 준비 및 스터디 참여