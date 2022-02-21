## 📆 2021-09-07(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] ReScript 공식 문서 React 파트 훑어보기
- [ ] 블로그에 이직 후기 회고 작성

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 스터디 참여 및 오브젝트 12장까지 읽기
- [ ] 스터디를 위한 자바스크립트 코딩의 기술 4장까지 훑어보기
- [x] ReScript 공식 문서 React 파트 훑어보기
- [ ] 블로그에 이직 후기 회고 작성
- [ ] 개인 프로젝트 한피쳐씩 틈틈히

### 🤔 공부하면서 배운것이 있다면?

#### ReScript
리스크립트는 강한 타입 특성에서 생기는 제약조건이 있기 때문에 `element || null` 같은 타입을 허락하지 않는다. 값이 렌더링 되거나 렌더링 되지 않을 수 있는 조건을 표현할 때마다 `Nothingness`를 나타내는 `React.null` 상수가 필요.

```reason
let name = Some("Andrea")

let element = switch name {
  | Some(name) => <div> { React.string("Hello " ++ name) } </div>
  | None => React.null
}

<div> element </div>
```

- 가변 Children 넘기기

```reason
type props = {"title": string, "children": React.element};

let render = (article: props => React.element) => {
  let children = [React.string("Introduction"), React.string("Body")];

  let props = {"title": "Article #1", "children": React.null};

  { React.createElementVariadic(article, props, children) }
}
```

- DOM에 엘리먼트 렌더링하기

```reason
/* Dom 접근은 실패할 가능성이 있다. */
/* ReScript는 엣지 케이스에 대한 명시적인 핸들링을 할 수 있다 */
switch(ReactDOM.querySelector("#root")){
  | Some(root) => ReactDOM.render(<div> React.string("Hello Andrea") </div>, root)
  | None => () /* 아무것도 하지 않음 */
}
```

#### 참고 아티클
- [[번역] OOP를 빨리 잊을 수록 여러분과 여러분의 소프트웨어에 좋습니다](https://rinae.dev/posts/the-faster-you-unlearn-oop-the-better-for-you-and-your-software-kr)

### ⚡ 아쉬운 점 및 회고
오늘도 블로깅은 손도 못댔다. 급하지않게 써보자.   

ReScript는 흥미로운 부분이 많고, 꽤 좋아보인다. 하지만, functional 기반이다보니 러닝커브가 높다. 현재로써는 ReScript로 어떤 큰 서비스를 만들긴 힘들어보인다. ToDo list까지만 만들어보자.   

꽤 재미있는 아티클을 읽었다. OOP에 대한 부정적인 아티클.. 3년전 글이지만 흥미롭게 읽었다. 역시 이 글에 대해서 대다수의 사람들이 부정적인 의견이였고, 나 또한 글 타이틀을 보자마자 거부감이 들었다. 어떻게 OOP를 부정적이게 바라볼 수 있는거지..? 그래서 나는 이 분이 더 대단하다고 느껴졌다. 부정적이게 의견을 낼 수 있는 용기..! 박수를 보낸다.

오늘 비가 와서 재택하고 싶었을뿐 즐겁게 출근을 했다. 역시 적응기간은 딱 2주가 걸린다. 완전히 적응했고 할 일도 잘 진행하고 있는 중이다. 자유로운 분위기는 여전히 너무 좋다.   

반성할 점은. 효율적인 시간관리를 못했다는 점. 일하면서도 이것저것해본다고 너무 많은 시간을 쏟아부었다. 하지만 그만큼 얻은건 있어서 만족..? 리팩터링은 코드를 구현하는 것보다 중요하다..!

### 🚀 내일 할 일
- ReScript 공식 문서 React 파트 훑어보기
- 자바스크립트 코딩의 기술 3장 훑어보기

### 🎯 이번주 목표
- 스터디 참여 및 오브젝트 12장까지 읽기
- 스터디를 위한 자바스크립트 코딩의 기술 4장까지 훑어보기
- ReScript 공식 문서 React 파트 훑어보기
- 블로그에 이직 후기 회고 작성
- 개인 프로젝트 한피쳐씩 틈틈히
