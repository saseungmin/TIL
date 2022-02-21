## 📆 2021-02-26(금) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 알고리즘 공부
  - 오늘은 Section4(완전 탐색)의 4, 5을 풀었다. ([PR Link](https://github.com/saseungmin/daily_coding_dojo/pull/6))
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (회원 인증 페이지 구현)
  - 회원가입 및 로그인 시 input onChange를 recoil selector를 사용하여 구현하였다.
  - [PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/39)
  - [PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/40)
- [ ] 개인 프로젝트(스터디 후기)


### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 공부
- [x] ~~앨래강트 오브젝트~~
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
- [ ] 개인 프로젝트(스터디 후기)

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 알고리즘 공부에서 배운 점
- 까먹고 있던 `Set`을 되새겨주었다.
- `Set`은 동알한 값이 있으면 값을 포함하지 않는다.
- 배열이 아니기 때문에 `[...result]`이런식으로 배열로 변경해 줄 수 있다.

```js
const result = new Set();
result.add(card[i] + card[j] + card[s]);
const answer = [...result].sort((a, b) => b - a);
```

#### 🎈 Recoil를 사용한 ToDo 앱 만들기 진행하기
- 오늘은 확실히 Recoil `selector`를 알 거 같다.
- 이제 비동기 통신시 사용하는 방법만 알면 어느정도는 안다고 할 수 있을 거 같다.


```js
const authStatusAtom = atom({
  key: AUTH_STATUS_ATOM_KEY,
  default: {
    type: '',
    visible: false,
  },
});

const authFieldsAtom = atom({
  key: AUTH_FIELDS_ATOM_KEY,
  default: {
    register: {
      userId: '',
      password: '',
      passwordConfirm: '',
    },
    login: {
      userId: '',
      password: '',
    },
  },
});

const authWithFields = selector({
  key: 'authWithFields',
  get: ({ get }) => {
    const { type } = get(authStatusAtom);
    const authFields = get(authFieldsAtom);

    return authFields[type];
  },
  set: ({ set }, { name, value, type }) => {
    set(
      authFieldsAtom, // 첫번째 파라미터는 대상이 되는 atom
      (prevState) => ({ // 이전의 State 값
        ...prevState, // 값 변경
        [type]: {
          ...prevState[type],
          [name]: value,
        },
      }),
    );
  },
});
```

- 위와 같이 `selector`를 사용해서 `get`과 `set`을 사용할 수 있었다.
- `atom`를 사용할 떄와 마찬가지로 `useRecoilState`과 같은 걸로 사용할 수 있다.

```js
const AuthInput = ({ formType, inputName }) => {
  const [authFieldsState, setAuthFieldsState] = useRecoilState(authWithFields);

  // 생략..
  const onChange = (e, type) => {
    const { name, value } = e.target;

    setAuthFieldsState({ name, type, value }); // selector set
  };

  return (
    <input
      // 생략..
      value={authFieldsState[inputName]} // get
      onChange={(e) => onChange(e, formType)}
    />
  );
};
```

- 이렇게 하면 관심사를 분리 시킬 수 있어서 atom만 사용했을 경우 때와 확연한 가독성이 올라간다.

```js
const AuthInput = ({ formType, inputName }) => {
  const [authFieldsState, setAuthFieldsState] = useRecoilState(authFieldsAtom);
  
  // 생략...
  
  const onChange = (e, type) => {
    const { name, value } = e.target;

    setAuthFieldsState({
      ...authFieldsState,
      [type]: {
        ...authFieldsState[type],
        [name]: value,
      },
    });
  };

  return (
    // 생략..
  );
};
```

### ⚡ 아쉬운 점 및 회고
- 아쉬운점은 늦게 일어났다. 늦게 잤다. 한심하구만..
- 그래도 오늘 할만큼 했다 생각한다. 금요일이니.. 오늘은 일찍 쉬어야겠다.
- 원래 약속이 있었지만, 내일로 밀렸다. 그래서 내일 오브젝트 책을 Chapter 1을 읽고 싶지만, 못 읽을 확률이 더 높다. 그러면 이게 계획일까? 그게 좀 의문이다.
- 계획은 내가 어떤 상황에서 내가 파악해서 할 수 있는 양을 잡고 할 수 있는 최선을 다해 계획을 뿌시는? 것이다. 만약 못할 확률이 더 높다는 건 계획이 아니라 나의 욕심일 뿐인 거 같다.
- 내가 할 수 없을 거 같은데... 하면서 하겠다고 하는건 뭘까? 욕심인 거 같다.
- 좀더 명확하게 계획을 세울 필요가 있다.

### 🚀 내일 할 일
- 알고리즘 공부
- Recoil를 사용한 ToDo 앱 만들기 진행하기 (회원 인증 페이지 구현)
- 오브젝트 책 Chapter 1 읽기 (아마 못할 수도 있다.)

### 🎯 이번주 목표
- 알고리즘 공부
- ~~앨래강트 오브젝트~~
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 개인 프로젝트(스터디 후기)