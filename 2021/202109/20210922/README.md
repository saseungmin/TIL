## 📆 2021-09-22(수) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] ReScript ToDo 앱 차근차근 봐보기
  - [등록된 할 일을 수정할 수 있게 하라 PR](https://github.com/saseungmin/ReScript_ToDo/pull/22)
- [ ] 블로그에 이직 후기 회고 작성

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 스터디를 위한 자바스크립트 코딩의 기술 8장까지 훑어보기
- [x] ReScript ToDo 앱 차근차근 봐보기
- [ ] 블로그에 이직 후기 회고 작성
- [ ] 개인 프로젝트 한피쳐씩 틈틈히

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 ReScript
- `option<string>`

```rescript
let isEmptyValue = value => value->Js.String.trim === "" ? None : Some(value)

let handleBlur = useCallback(id => {
  switch isEmptyValue(inputValue) {
  | Some(_) => ItemView->onToggleShowEdit
  | None => onRemove(id)
  }
}, [inputValue])
```

- rescript에서 `React.useRef`

```rescript
// Dom.element focus를 가져와야한다.
@send external focus: Dom.element => unit = "focus"

@react.component
let make = () => {
  let inputEl = React.useRef(Js.Nullable.null)

  let onClick = _ => {
    // 비구조화 할당은 불가능
    inputEl.current
    ->Js.Nullable.toOption
    ->Belt.Option.forEach(input => input->focus)
  }

  // ReactDOM.Ref.domRef 명식적으로 변환해줘야한다.
  <>
    <input ref={ReactDOM.Ref.domRef(inputEl)} type_="text" />
    <button onClick> {React.string("Focus the input")} </button>
  </>
}
```

### ⚡ 아쉬운 점 및 회고
결국 추석 연휴동안 블로그는 한자도 못 작성했다. 요즘 몸이 안좋아지는 신호가 오고있다. 몸이 뭔가 아프다해야할까.. 몸도 휴식이 필요하고 운동도 필요하고 달래가며 써야하는데 근 2년동안 공부만하다보니 몸이 점점 삐꺽거린다해야할까... 아무리 생각해도 이제는 휴식과 공부를 잘 조절해가면서 해야할듯하다.   

ReScript ToDo 만드는건 너무 재밌다. 역시 뭔가 고민해며 뚜딱뚜딱 만들어가는 과정 속에서 많은 것들을 배운다. ReScript는 참고할만한 포럼도 많이 부족해서 시간은 많이 걸리지만 오늘도 정말 많은 것들을 배울 수 있는 하루였다. 그리고 배우면 배울 수록 왜 null과 undefined없이 사용할 수 있는지 확실히 감을 잡을 수 있게되었다. 또한 정말 매력적인 점이 많다고 느꼈고, 그린랩스에서 왜 사용할까 생각해봤는데 그만한 이유가 있어보였다.   

추석 연휴동안 만족할만큼 많이 쉬었다. 하지만, 뭔가 쉬면서도 뒤쳐지지 않을까 생각때문에 스트레스는 풀었다?할 수는 없던 거 같다. 이런 스트레스가 계속 반복되면 나만 힘들어지기 떄문에 이젠 좋은 회사에 취업도 했고 조금은 더 긴 마라톤을 할 수 있도록 페이스 조절을 하면서 나아가야겠다.   

몸 관리 잘하자.

### 🚀 내일 할 일
- 스터디를 위한 자바스크립트 코딩의 기술 8장까지 훑어보기 및 스터디 참여
- ReScript ToDo 앱 차근차근 봐보기

### 🎯 이번주 목표
- 스터디를 위한 자바스크립트 코딩의 기술 6장까지 훑어보기
- ReScript ToDo 앱 차근차근 봐보기
- 블로그에 이직 후기 회고 작성
- 개인 프로젝트 한피쳐씩 틈틈히
- 추석연휴! 리플레쉬!
