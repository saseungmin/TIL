## 📆 2021-09-12(일) TIL

### 📈 오늘 한 일
- [x] ReScript 공식 문서 React 파트 훑어보기
- [x] ReScript ToDo App 초기 세팅
  - [Repo](https://github.com/saseungmin/ReScript_ToDo)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 스터디 참여 및 오브젝트 12장까지 읽기
- ~~스터디를 위한 자바스크립트 코딩의 기술 4장까지 훑어보기~~
- [x] ReScript 공식 문서 React 파트 훑어보기
- [ ] 블로그에 이직 후기 회고 작성
- [ ] 개인 프로젝트 한피쳐씩 틈틈히

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 ReScript 
- 커스텀 훅 생성하기    

공통적인 비즈니스 로직을 분리하여 여러곳에서 재사용할 수 있게 사용하게 해준다.   

커스텀 훅은 항상 `use`로 시작해야한다. 이유는 그렇게 하지 않으면 특정 함수가 내부에 훅에 대한 호출을 포함하는지 아닌지 알 수 없다. 그렇기 때문에 우리는 훅의 규칙 위반을 자동으로 확인할 수 없다.    

동일한 훅을 사용하는 두 컴포넌트는 상태를 공유하지 않고 완벅하게 격리된다.   

```rescript
module ChatAPI = {
  /* Imaginary globally available ChatAPI for demo purposes */
  type status = { isOnline: bool };
  @val external subscribeToFriendStatus: (string, status => unit) => unit = "subscribeToFriendStatus";
  @val external unsubscribeFromFriendStatus: (string, status => unit) => unit = "unsubscribeFromFriendStatus";
}

type state = Offline | Loading | Online

let useFriendStatus = (friendId: string): state => {
  let (state, setState) = React.useState(_ => Offline)

  React.useEffect(() => {
    let handleStatusChange = status => {
      setState(_ => {
        status.ChatAPI.isOnline ? Online : Offline
      })
    }

    ChatAPI.subscribeToFriendStatus(friendId, handleStatusChange)
    setState(_ => Loading)

    let cleanup = () => {
      ChatAPI.unsubscribeFromFriendStatus(friendId, handleStatusChange)
    }

    Some(cleanup)
  })

  state
}
```

#### 🎈 ReScript useReducer

```rescript
type action = Inc | Dec
type state = {count: int}

let reducer = (state, action) => {
  switch action {
  | Inc => {count: state.count + 1}
  | Dec => {count: state.count - 1}
  }
}

@react.component
let make = () => {
  let (state, dispatch) = React.useReducer(reducer, {count: 0})

  <>
    {React.string("Count:" ++ Belt.Int.toString(state.count))}
    <button onClick={(_) => dispatch(Dec)}> {React.string("-")} </button>
    <button onClick={(_) => dispatch(Inc)}> {React.string("+")} </button>
  </>
}
```


#### 🎈 Vite
- https://vitejs.dev/
- Vite란 모던 브라우저에서 지원하는 `<script module>`을 이용해 개발시 번들링하지 않고 필요한 모듈만을 HTTP 요청으로 불러와서 실행하게 해주고, 프로덕션 빌드시에는 Rollup으로 코드를 번들링해주는 기능을 가지고 있는 떠오르는 웹 개발 도구다. Vite는 Vue 팀에서 만들었다.
- [Why Vite?](https://vitejs.dev/guide/why.html)

#### 🎈 Snowpack
- https://www.snowpack.dev/
- Snowpack은 최신 웹용으로 설계된 번개처럼 빠른 프론트엔드 빌드 도구. 개발 워크플로에서 webpack 또는 Parcel과 같은 더 무겁고 복잡한 번들러에 대한 대안이다. Snowpack은 JavaScript의 기본 모듈 시스템( ESM이라고 함)을 활용하여 불필요한 작업을 피하고 프로젝트 규모가 아무리 커지더라도 속도를 유지.

#### 🎈 [Vite vs Snowpack](https://blog.logrocket.com/vite-vs-snowpack-a-comparison-of-frontend-build-tools/)

### ⚡ 아쉬운 점 및 회고
드디어 ReScript 공식 문서를 다 읽었다. 하루에 한 두 섹션씩 읽느냐고 시간이 오래걸렸다. 다 읽었고 이제 이 공부한 것들을 바탕으로 정말 간단한 ReScript ToDo 어플리케이션을 만들어볼것이다. 아마.. 시간이 많이 걸릴듯 한데 이러면서 공부되는게 정말 많아서 이 방법을 선택할 수 밖에 없었따. 아니 다른 대안은 떠오르지 않았다.   

오늘도 이렇게 초기 세팅을 해보면서 프론트엔드 빌드 도구 2가지를 새롭게 알게 되었다. Vite는 알고 있었긴 했지만, 꽤 흥미로운 부분들이 많이 있었고, Snowpack역시 주목해볼만해보였다. 웹팩을 사용해보면서 아쉽고 어느정도의 귀찮고 최적화까지 하려면 러닝커브도 있다고 생각이 들었다. 뭐 vite나 snowpack도 최적화까지 가면 어렵겠지만, 확실히 간단해보였고, webpack보다도 빌드 속도도 빨라보였다.   

이제 좀만 지나면 이 webpack으로 번들링하고 빌드하는 세상도 대체될 거 같아보인다. 너무나도 빠른 프론트엔드 세계...   

내일 출근을 위해서 오늘은 여기까지만 공부하고 저녁은 쉬어야겠다!   

### 🚀 내일 할 일
- 스터디 참여 및 오브젝트 12장까지 읽기
- ReScript ToDo 앱 차근차근 봐보기

### 🎯 이번주 목표

- 스터디 참여 및 오브젝트 12장까지 읽기
- 스터디를 위한 자바스크립트 코딩의 기술 4장까지 훑어보기
- ReScript 공식 문서 React 파트 훑어보기
- 블로그에 이직 후기 회고 작성
- 개인 프로젝트 한피쳐씩 틈틈히
