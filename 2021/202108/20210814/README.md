## 📆 2021-08-14(토) TIL

### 📈 오늘 한 일
- [x] 집 계약으로 인해 서울 갔다옴
- [x] ConStu 내 정보 페이지
  - [회원 탈퇴 PR](https://github.com/CodeSoom/ConStu/pull/228)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 스터디 참여 및 오브젝트 4장까지 읽기
- [ ] reading_books_record_repository 사이트에 정리한 책 추가하기
- [x] ConStu 내 정보 페이지
- [ ] ReScript 공식문서 훑어보기
- ~~함께 자라기 책 읽기 마무리~~
- ~~입사 관련 서류 준비 및 500만원 한도 장비 구입~~
- ~~집 알아보기~~

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 firebase 사용자 재인증

```js
export const postReauthenticateWithCredential = async (password) => {
  const user = auth.currentUser;

  const credential = authProvider.EmailAuthProvider.credential(
    user.email,
    password,
  );

  await user.reauthenticateWithCredential(credential);
};

// test
describe('postReauthenticateWithCredential', () => {
  const password = 'test';
  const mockCredential = jest.fn().mockReturnValue({
    email: 'test@test.com',
    password,
  });
  const mockEeauthenticateWithCredential = jest.fn();

  beforeEach(() => {
    auth.currentUser = {
      email: 'test@test.com',
      reauthenticateWithCredential: mockEeauthenticateWithCredential,
    };

    authProvider.EmailAuthProvider = {
      credential: mockCredential,
    };
  });

  it('call postReauthenticateWithCredential api', async () => {
    await postReauthenticateWithCredential(password);

    expect(mockCredential).toBeCalledWith('test@test.com', password);
    expect(mockEeauthenticateWithCredential).toBeCalledTimes(1);
  });
});
```

### ⚡ 아쉬운 점 및 회고
입사 준비가 마무리 되어 간다. 오늘은 건대를 가서 집을 알아봤고 계약했다. 계약하며 경험했던건 건대 주변 상권 조건들이 다 하나같이 맞춰져있었다. 무조건 2년 계약, 퇴실시 8만원 청소비... 1년 계약을 원했지만, 어찌할 도리가 없었다. 물론 그 전에 나갈 순 있지만, 수수료비와 새로운 입주자가 들어와야 나갈 수 있는 점. 뭔가 손해 보는 느낌이었다. 앞으로 돈내야할 월세를 생각하면 너무 너무 아깝다. 대전에서 그냥 살고 싶다. 방법은 없지만...   

다음주면 출근하는데 내가 지금 공부를 하는게 맞는걸까?라는 생각이 든다. 가서 진짜 열심히 또 달려나갈텐데.. 적어도 지금은 쉬어야하지 않을까? 생각이 든다. 하지만, 생각처럼 쉬지 않고 있어서 문제다. 이것 또한 남들이랑 비교해서 뒤쳐지는 급한 마음가짐에서 오는 것인데 스스로 스트레스를 만드는 안좋은 습관이다. 고칠필요가 필히 있어보인다... 1주일 동안만이라도 할 일을 줄이고 할 것만 딱 해야겠다.

오늘은 서울도 가고 오면서 또한 집와서 그래도 개인 프로젝트 한 피쳐를 해서 만족스럽다. 근데 한 피쳐가 또 켜저서 하나의 PR에 두개의 커밋을 해서 잘못한 부분이다. 한 피쳐를 작게 가져가야하는데 계속 구현해보고싶은 습관때문에 자주 못지키는 것 같다. 최대한 작게 작게 빠르게 배포하자. 요즘 CI/CD 자동화를 해논 e2e 테스트 부분이 자꾸 첫번째 자동화에서 깨진다. 그리고 다시 Rerun 하면 되긴하지만 그만큼 시간이 소요가 된다. 자동화라하면 시간을 줄이기 위해서 사용하는건데 한 번더 하니까 더 오래걸려진다. 이건 옛날에도 그랬었는데 Conceptjs의 문제인거 같았다. 뭔가 github actions에서 타 CI action과 충돌이 나는건가..? 관련 자료를 더 찾아보고 해결해봐야겠지만, 아마 저번에도 물어봤었는데 확실한 이유는 잘 모르는거 같았다.   

### 🚀 내일 할 일
- 오브젝트 3장까지 읽기
- ReScript 공식문서 훑어보기
- 머리 자르기

### 🎯 이번주 목표
- 스터디 참여 및 오브젝트 4장까지 읽기
- reading_books_record_repository 사이트에 정리한 책 추가하기
- ConStu 내 정보 페이지
- 함께 자라기 책 읽기 마무리
- 입사 관련 서류 준비 및 500만원 한도 장비 구입
- ReScript 공식문서 훑어보기
- 집 알아보기
