## 📆 2021-02-25(목) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 알고리즘 공부
  - 오늘은 Section4(완전 탐색)의 1, 2, 3을 풀었다. ([PR Link](https://github.com/saseungmin/daily_coding_dojo/pull/6))
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
  - 로그인 / 회원가입 / 로그아웃 버튼을 구현했다. ([PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/37))
  - 로그안과 회원가입 폼을 모달창으로 구현했다. ([PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/38))
- [ ] 개인 프로젝트(스터디 후기)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 공부
- [x] ~~앨래강트 오브젝트~~
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
- [ ] 개인 프로젝트(스터디 후기)

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 알고리즘 공부에서 배운 점
- 완전 탐색을 공부했다. 사실 생각보다 어렵다..
- 멘토링? 이 문제가 가장 어려웠다. 풀이를 봐도 잘이해가 안갔지만 이젠 이해했다. ([Link](https://github.com/saseungmin/daily_coding_dojo/tree/master/inflearn_algorism/section4/solution3))
- for문을 4번이나돌았는데 내가 도는줄 알았다.

#### 🎈 Recoil를 사용한 ToDo 앱 만들기 진행하기
- recoil을 사용해서 회원 인증 modal창을 관리해보았다.
- 원래 사용했던 방식은 react-hooks를 사용해서 관리하였지만, react-dom을 사용하지 않아서 전역으로 modal창의 상태와 로그인 모달을 원하는지 회원가입 모달을 원하는지를 관리해주었다.

```js
// recoil atom
export const authStatusAtom = atom({
  key: AUTH_STATUS_ATOM_KEY,
  default: {
    type: '', // 로그인인지 회원가입인지
    visible: false, // 모달창이 나타나는지 닫히는지
  },
});
```

- 그리고 로그인 또는 회원가입 버튼을 클릭할 때 recoil atom의 값을 변경해준다.

```js
const UserStatus = ({ user }) => {
  const setAuthStatus = useSetRecoilState(authStatusAtom);

  const onClickOpenModal = (type) => {
    setAuthStatus({
      type,
      visible: true,
    });
  };
  // 생략..
  return (
    <AuthButtonsWrapper>
      <AuthButton
        type={login}
        onClick={() => onClickOpenModal('login')}
      />
      <AuthButton
        type={register}
        onClick={() => onClickOpenModal('register')}
      />
    </AuthButtonsWrapper>
  );
};
```

- 모달창에 `visible` 값이 true이면 나타나게 해준다.
- 그리고 닫기 버튼을 클릭하면 `atom` 값을 default값으로 초기화 해준다. 이때 `useResetRecoilState`를 사용하면 된다.

```jsx

const AuthModalForm = () => {
  const authStatusState = useRecoilValue(authStatusAtom);
  const resetAuthStatusState = useResetRecoilState(authStatusAtom);

  const { type, visible } = authStatusState;

  if (!visible) {
    return null;
  }

  return (
    <AuthModalFormWrapper visible={visible}>
      <AuthModalBoxWrapper>
        <AuthFormWrapper>
          {/* 생략... */}
          <button
            type="button"
            onClick={resetAuthStatusState}
          >
            닫기
          </button>
        </AuthFormWrapper>
      </AuthModalBoxWrapper>
    </AuthModalFormWrapper>
  );
};
```

### ⚡ 아쉬운 점 및 회고
- 오늘은 좀 늦게 일어났다. 어제 잠을 제대로 못잤지만 일찍 일어났다. 하지만, 잠깐만 잔다는게 2시간을 더 자버렸다.
- 개인프로젝트에서 스터디 후기를 얼른 구현해야하는데 자꾸 미루게된다. 얼른 해야지..
- 벌써 내일이면 금요일이다 일주일이 너무 금방간다 시간이 순삭이다.. 쉬니까 시간이 더 빨리간다. 회사 다닐 땐 그렇게 안가더니만..
- 시간이 빠르게 흐르는 만큼 좀더 정신차리고 열심히하자. 이래서 취업할 수 있을까..
- 알고리즘 공부하니까 머리를 많이 쓰는 느낌이든다. 계속 풀어보자. 알고리즘은 반복이다. 꾸준히 풀어보면 다 원리는 비슷한 문제일 것이다.
- recoil도 거의 마무리 지어간다. 화이팅!

### 🚀 내일 할 일
- 알고리즘 공부
- Recoil를 사용한 ToDo 앱 만들기 진행하기 (회원 인증 페이지 구현)
- 개인 프로젝트(스터디 후기)

### 🎯 이번주 목표
- 알고리즘 공부
- ~~앨래강트 오브젝트~~
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 개인 프로젝트(스터디 후기)