## 📆 2021-03-11(목) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
  - user의 [token값 확인](https://github.com/saseungmin/Recoil_ToDo/pull/55)
  - [회원가입 및 로그인 에러 처리 메시지](https://github.com/saseungmin/Recoil_ToDo/pull/56)
- [ ] 알고리즘 공부 (section 5)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 알고리즘 공부
- [ ] 오브젝트 책 Chapter 6 까지 읽기 및 스터디 참여
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
- [x] 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- [ ] 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 Recoil를 사용한 ToDo 앱 만들기 진행하기
- recoil의 `useRecoilCallback`을 알게되었다.

```jsx
const checkUser = useRecoilCallback(({ snapshot, set }) => async () => {
  const { data } = await userCheckErrorHandling(snapshot.getPromise(userWithCheck()));
  set(userAtom, { user: data });
}, []);
```

- 생각보다 편리했는데 `useCallback` 과 비슷하다.
- 후처리가 가능하다.

### ⚡ 아쉬운 점 및 회고
- 오늘 계획을 지키지 못했다.
- 내일은 오늘보다 더 나은 내일이 되길!
- 화이이이이티이잉!
- 그래도 만족스러운 하루였다. 오늘 회고는 간단하게 적고 쉬어야겠다.

### 🚀 내일 할 일
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 알고리즘 공부 (section 5)

----

- 시간 남으면 진행할 예정 javascript 공부

### 🎯 이번주 목표
- 알고리즘 공부
- 오브젝트 책 Chapter 6 까지 읽기 및 스터디 참여
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기