## 📆 2021-08-03(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 클린 애자일을 웹사이트에 적용
  - [PR](https://github.com/saseungmin/reading_books_record_repository/pull/96)
- [x] ConStu Private Route 구현
  - [PR](https://github.com/CodeSoom/ConStu/pull/222)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 스터디 참여 및 오브젝트 2장까지 읽기
- [x] reading_books_record_repository 사이트에 정리한 책 추가하기
- [x] ConStu 내 정보 페이지 구현 시작하기
- [ ] 함께 자라기 책 읽기
- [ ] 집 알아보기

### 🤔 공부하면서 배운것이 있다면?
- [React-Router-dom Redirect](https://reactrouter.com/web/example/auth-workflow)
- 간단하게 Redirect 컴포넌트 Mock하여 테스트

```js
jest.mock('react-router-dom', () => ({
  ...jest.requireActual('react-router-dom'),
  Redirect: jest.fn(({ to: { pathname } }) => (`Redirected to ${pathname}`)),
}));

//...

context('without user', () => {
  given('user', () => null);
  const MockComponent = () => (
    <h1>실패입니다!</h1>
  );

  it('redirect to "/login"', () => {
    const { container } = renderPrivateRoute({
      component: MockComponent,
    });

    expect(container).toHaveTextContent('Redirected to /login');
  });
});
```

### ⚡ 아쉬운 점 및 회고
- 오늘은 악속이 있어서 공부를 많이 하지는 못했다. 그래도 권한에 따라 Redirect 시켜주는 Private Route를 구현했다. 이로써 앞으로 로그인이 필요한 부분을 재사용할 수 있게 되었다.
- 내 정보 페이지를 구현을 할 수 있다.
- 내가 계속 유지보수 하는 이유는 그냥 의미있는 가치있는 시스템을 만들고 싶어졌다. 그냥 하나씩 하다보면 뭔가 그럴듯한 뭔가가 만들어지지 않을까하는 생각이다 하하...
- 내일도 내일 나름대로 할일이 많다. 약속도 있고, 처우협의도 진행해야 한다. 오전중에 보내기로했다.
- 방도 얼른 알아보자. 시간이 없다.

### 🚀 내일 할 일
- 처우협의 관련 메일 보내기 / 전회사 연봉계약서 PDF로 보내기
- 방 알아보기 시작!
- ConStu 내정보 페이지 시작!
- 함께자라기 책 읽기

### 🎯 이번주 목표
- 스터디 참여 및 오브젝트 2장까지 읽기
- reading_books_record_repository 사이트에 정리한 책 추가하기
- ConStu 내 정보 페이지 구현 시작하기
- 함께 자라기 책 읽기
- 집 알아보기
