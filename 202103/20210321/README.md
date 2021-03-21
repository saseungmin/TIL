## 📆 2021-03-21(일) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
  - todo input에 대한 refactoring을 했다
  - [PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/69)
- [x] 오브젝트 Chapter 10 반 읽기
  - [PR Link](https://github.com/saseungmin/reading_books_record_repository/pull/46)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 알고리즘 공부
- ~~오브젝트 책 Chapter 9 까지 읽기 및 스터디 참여~~
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
- [ ] 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- [ ] 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 Recoil을 사용한 To DO 애플리케이션 만들기

- `useRecoilCallback` 의 편리함을 다시 알게되었다.
- 버튼 액션 일때 useRecoilCallback을 사용하면 너무 간편하게 사용할 수 있는데 `useRecoilCallback`은 `snapshot`으로 비동기 처리를 하고, 파라미터도 받을 수 있고, `set`으로 후처리 및 전처리도 가능하고, `atom`을 초기화 시킬 수도 있다.
- 이 세가지의 `useRecoilCallback`의 파라미터를 사용해서 로딩과 에러처리 성공 처리를 한번에 가능하게 해준다.

```jsx
import { useRecoilCallback } from 'recoil';

import isLoadingAtom from '../recoil/common/atom';
import todosResultAtom, { todoWithWrite } from '../recoil/todos';

import { todoErrorMessage } from '../utils/errorMessageHandling';

const useWriteCallback = () => useRecoilCallback(({
  snapshot, set, reset,
}) => async (task) => {
  set(isLoadingAtom, true); // 로딩 처리

  try {
    // api 호출 POST /api/todos/
    const { data } = await snapshot.getPromise(todoWithWrite(task));

    set(
      todosResultAtom,
      (prevState) => ({
        ...prevState,
        // 성공 시 성공 메시지를 담는다.
        todoSuccess: 'Success in entering To-Do!',
        todos: [ // 성공시 받은 데이터로 atom 정보를 업데이트 시켜준다.
          data,
          ...prevState.todos,
        ],
      }),
    );
  } catch (error) {
    set(todosResultAtom, (prevState) => ({
      ...prevState,
      todoError: todoErrorMessage(error), // 에러 정보를 todoError 정보에 데이터를 조작하여 담아준다.
    }));
  } finally {
    reset(isLoadingAtom); // 모든 로직이 끝나고 로딩을 초기화 즉 로딩을 없앤다.
  }
}, [isLoadingAtom, todosResultAtom]);

export default useWriteCallback;
```

- 이제 `useRecoilCallback`을 사용해서 위와 같이 커스텀 훅을 만들고 작동 로직을 뒤로 감춘뒤 react 컴포넌트에서는 hook만 불러와서 사용하기만 하면 된다.

```jsx
const TodoInput = () => {
  const setTodo = useWriteCallback();

  const onSubmit = ({ task }) => {
    setTodo(task);
  };

  return (
    // ... 
  )
};
```

#### 🎈 오브젝트 Chapter 10
- 오브젝트 Chapter 10 정리 [링크](https://github.com/saseungmin/reading_books_record_repository/pull/46)

### ⚡ 아쉬운 점 및 회고
- 오늘은 공부가 참으로 하기 싫은 날.. 가끔씩 이러는데 이럴 땐 억지로 붙잡고 해야할까 아니면 쉬어야 할까
- 당연히 쉬는게 맞다고 생각하는데, 진짜 마음 편하게 쉴 수가 없어서 맨날 붙잡고 그래도 조금은 해야지라는 생각으로 하고 있다..
- 그래서 오늘은 좀 억지로 공부한 감이 없지않다. 그리고 일찍 쉴래.
- 생각해보면 퇴사 후 마음편하게 진짜 쉰적이 없다. 항상 뭐라도 붙잡고 공부를 하고 쉬었다.
- 내일은 또 어떤 일이 있을까. 내일은 새로 시작한 스터디를 시작한다. 이것도 잘해보자.
- 오늘 하기 싫어서 오브젝트 책도 한 10쪽 정도 덜읽었다. 내일 마저 읽자.
- 루비콘 프로젝트를 지원했다. 붙었으면 좋겠다. 별 기대는 안하지만.. 하면 사이드 프로젝트를 진행하면서 재밌게 할 수 있을 거 같은데ㅠㅠ

### 🚀 내일 할 일
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 오브젝트 Chapter 10 다 읽기
- 취업 준비 스터디 참여하기

### 🎯 이번주 목표
- 알고리즘 공부 (Section 6)
- 오브젝트 책 Chapter 11 까지 읽기 및 스터디 참여
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 취업 준비 스터디 관련 준비 및 스터디 참여