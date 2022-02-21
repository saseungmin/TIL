## 📆 2021-02-04(목) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
  - 오늘은 Todo item에 대한 수정 로직에 관한 내용을 추가했다.
- [ ] 개인 프로젝트 진행(스터디 후기 😓)
  - 진행 못함.

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 알고리즘 공부 계획 세우기
- [x] 리플레쉬 및 정리
- [x] 긍정적이게 생각하기 😤

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 Recoil을 사용한 ToDo 앱 만들기
- `lodash`를 적용하였다.
- 점점 함수형 프로그래밍에 매료되는 기분이다. 쓰면 쓸 수록 마음에 든다. 아직은 사용을 어떻게 해야할지 좀더 알아봐야하지만, 더 잘하고 싶다. 함수형 프로그래밍 공부를 많이 해야할 거 같다.
- 그래서 lodash와 Ramda, RxJS도 잘 쓰고 싶다. 확실히 코드가 깔끔해지는 거 같다.
- 근데 굳이 lodash를 사용하지 않고 할 때와 코드의 가독성이 비슷하면 그냥 쓰는 것이 맞는거 같다.

```js
// 빈 값일 때
if (_.isEmpty(todos)) {
  return (
    <div>{NOTING_TO_DO}</div>
  );
}

// 빈 칸 제거
export const isCheckInputTrim = (value) => _.trim(value).length > 0;

// 일치, 널 값 체크
if (_.eq(editToggleState, true) && !_.isNull(editInput.current)) {
  editInput.current.focus();
}
```

- todo item 수정 로직을 구현하면서 해당 할 일을 더블클릭하면 인풋창이 생기고 focus가 인풋창으로 이동하고 수정한 뒤 인풋창에서 enter를 클릭하거나 focus를 떠날 때 인풋창이 사라지게 만들려고 하고 있다.
- 아직은 미완성이지만 디자인만 입히면된다.
- 그래서 인풋창의 DOM을 건들여 `focus`를 사용하기 위해 `ref`를 사용하게되었는데, react의 `createRef`를 사용하였다.

```js
// 생략..
const TodoItem = ({ item }) => {
  const editInput = createRef();
  // 생략.. 

  useEffect(() => {
    if (_.eq(editToggleState, true) && !_.isNull(editInput.current)) {
      editInput.current.focus();
    }
  }, [editToggleState, editInput]);

  return (
    // 생략..
  );
};
```

### ⚡ 아쉬운 점 및 회고
- 아쉬운 점은 공부를 얼마 못했다는 점이다. 하지만 아쉽다는 것뿐이지 후회? 따윈 없다. 오히려 오늘이 훨씬 좋았다.
- 약속이 있어서 낮과 저녁을 밖에서 보냈지만, 오히려 오늘이 더 좋은 하루였다. 리플레쉬하기 정말 좋았던 날이였다.
- 그래서 느낀점은 집에서만 하는 것보다 맥북들고 카페가서 공부하는 것도 좋을 거 같다. 그래서 내일은 맥북을 들고 카공을 해볼까한다. ㅎㅎ
- 또 여행을 너무 가고싶어졌다. 갈 수는 없지만...
- 그리고 또.. 음.. 나는 확실히 코드를 짜고 무언가 결과물이 나오면서 해쳐나가는 걸 정말 좋아하는 거 같다. 즐겁다.. 매일매일 코드짜는게.. 긍정적인 요소이라고 생각한다. 너무 즐겁다! 이 즐거움 평생 갈 수 있었으면 좋겠다.

### 🚀 내일 할 일
- 개인 프로젝트 진행(스터디 후기 😓)
- Recoil를 사용한 ToDo 앱 만들기 진행하기

### 🎯 이번주 목표
- 알고리즘 공부 계획 세우기
- 리플레쉬 및 정리
- 긍정적이게 생각하기 😤