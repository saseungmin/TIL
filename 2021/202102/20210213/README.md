## 📆 2021-02-13(토) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (todo item에 대한 css)
  - todo item에 대한 CSS 작업 ([PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/28))
  - todo item의 edit CSS 작업 ([PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/29))
  - 더블 클릭을 해야지 수정을 할 수 있게 때문에 잘 모르는 부분을 알려주기 위해 tooltip을 적용하였다. ([PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/30))
- [ ] 개인 프로젝트 진행하기

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 알고리즘 공부 시작하기
- [x] 리플레쉬 및 정리
- [ ] 긍정적이게 생각하기 😤
- [x] 설날

### 🤔 공부하면서 배운것이 있다면?
- `react-tooltip`을 사용하는 법을 배웠다.

```shell
> npm i react-tooltip
```

- 다음과 같이 적용해준다.
- tooltip css를 커스텀으로 변경해줄려면 `!important`를 적용하여 수정해줘야 한다.
- 자세한 내용은 공식 문서 참고
- 주의할 점은 아이디는 모두 다르게 해줘야 한다.

```jsx
import ReactTooltip from 'react-tooltip';

const EditTooltip = styled(ReactTooltip)`
  background: #91a7ff !important;
  opacity: 0.8 !important;
  &.place-top {
    &:after {
      border-top-color: #91a7ff !important;
      border-top-style: solid !important;
      border-top-width: 6px !important;
    }
  }
  & p {
    font-size: 0.9rem;
  }
`;

const TodoItemView = ({
  item, onDoubleClick, onRemove, onToggle,
}) => {
  const { task, isComplete, id } = item;

  return (
    <TodoItemViewWrapper>
      {/* 생략.. */}
      <TodoItemTextWrapper
        isComplete={isComplete}
        data-tip
        data-for={id} // mouseover 되면 툴팁이 보임
        data-testid="todo-text"
        onDoubleClick={onDoubleClick}
      >
        {task}
      </TodoItemTextWrapper>
      {/* 생략.. */}
      <EditTooltip // tooltip
        id={id}
      >
        <EditTooltipWrapper>
          <PencilIcon />
          <p>
            수정하려면 더블 클릭해주세요!
          </p>
        </EditTooltipWrapper>
      </EditTooltip>
    </TodoItemViewWrapper>
  );
};

export default TodoItemView;
```

### ⚡ 아쉬운 점 및 회고
- 오늘은 어느정도 했지만, 뭐... 그냥 구현만했다. 😅 그래도 재밌다..
- 카페를 가볼까했지만, 늦잠을 자서 그냥 집에서 했다. 사실 가기 귀찮은게 더 컸다.
- TIL를 너무 늦게 쓰고있다. 얼른 자야겠다.
- Recoil Todo 앱은 거의 마무리는 되었다. 하지만 백앤드도 차근차근 구현해봐야겠다.
- 알고리즘 공부... 화이팅..

### 🚀 내일 할 일
- Recoil를 사용한 ToDo 앱 만들기 진행하기 (todo item에 대한 css)
- 개인 프로젝트 진행하기

### 🎯 이번주 목표
- 알고리즘 공부 시작하기
- 리플레쉬 및 정리
- 긍정적이게 생각하기 😤
- 설날