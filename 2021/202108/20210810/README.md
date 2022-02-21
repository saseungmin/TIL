## 📆 2021-08-10(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 집 알아보기
- [ ] 함께 자라기 책 읽기
- [x] reading_books_record_repository 사이트에 정리한 책 추가하기
  - [오브젝트 웹사이트에 적용 PR](https://github.com/saseungmin/reading_books_record_repository/pull/102)
- [x] ConStu 내 정보 페이지
  - [비밀번호 재설정 기능 구현 PR](https://github.com/CodeSoom/ConStu/pull/227)
- 스터디를 할지 말지 정하기 만약 하기로 한다면, DDD 책 읽기 안한다면 보험처리 서류 제출

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 스터디 참여 및 오브젝트 4장까지 읽기
- [x] reading_books_record_repository 사이트에 정리한 책 추가하기
- [x] ConStu 내 정보 페이지
- [ ] 함께 자라기 책 읽기 마무리
- [ ] 입사 관련 서류 준비 및 500만원 한도 장비 구입
- [x] 집 알아보기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 firebase 비밀번호 재설정 with test
```jsx
export const sendPasswordResetEmail = async (email) => {
  await auth.sendPasswordResetEmail(
    email,
    actionCodeSettings(isDevLevel(process.env.NODE_ENV)),
  );
};

// test
describe('sendPasswordRestEmail', () => {
  const email = 'test@test.com';

  const mockPasswordResetEmail = jest.fn();

  beforeEach(() => {
    auth.sendPasswordResetEmail = mockPasswordResetEmail;
  });

  it('call sendPasswordResetEmail api', async () => {
    await sendPasswordResetEmail(email);

    expect(mockPasswordResetEmail).toBeCalledWith(email, {
      url: 'http://localhost:8080/myinfo/setting/?email=test@test.com',
    });
  });
});
```

### ⚡ 아쉬운 점 및 회고
DDD스터디는 다음 기회로.. 이 스터디까지 신경쓸 시간이 없을 것으로 판단. 분명 또 다른 기회가 올꺼라 믿는다.   

공부량이 어쩔 수 없이 많이 줄었다. 집 알아보기.. 입사 관련 서류, 장비 구입을 위한 선택, 보험처리 서류 제출.. 어쩔 수 없다. 그래도 가서 회사 생활할 생각에 두려움도 있지만 설렘도 있다. 재밌을거 같다. 드디어 내가 원하는 '개발'을 할 수 있으니.. 얼른 조직 문화에 적응하고 싶다.   

내일은 전 회사에 전화를 해서 서류 준비도 해야하고, 보험 문제 서류도 해결해야하고, 부동산에 전화도 해야하고, 장비도 결정해야한다. 아마 내일 다 못할 거 같다. 오후에는 약속이 있으니.   

오늘 아쉬웠던 점은 우선순위를 잘 지키지 못한것. 일의 우선순위는 중요성과 긴급성의 기준으로 정할 수 있지만, 현재 상황이 중요성과 긴급성이 높은 할 일이 많다. 만약 우선순위가 같을 때는 더 빨리 끝나는 할 일부터 해치워나가는걸 잊지말자.

### 🚀 내일 할 일
- 집 알아보기
- 입사 관련 서류 준비 (전 회사에 전화)
- 장비 구입을 위한 확실한 선택
- 함께 자라기 chapter 2 마무리

### 🎯 이번주 목표
- 스터디 참여 및 오브젝트 4장까지 읽기
- reading_books_record_repository 사이트에 정리한 책 추가하기
- ConStu 내 정보 페이지
- 함께 자라기 책 읽기 마무리
- 입사 관련 서류 준비 및 500만원 한도 장비 구입
- 집 알아보기
