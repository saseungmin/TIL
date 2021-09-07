## 📆 2021-09-05(일) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] ReScript 공식 문서 훑어보기
- [ ] 블로그에 이직 후기 회고 작성

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- ~~회사 문화에 적응하기~~
- [ ] 스터디 참여 및 오브젝트 10장까지 읽기
- [ ] 스터디를 위한 자바스크립트 코딩의 기술 훑어보기
- [x] ReScript 공식 문서 훑어보기
- [ ] 블로그에 이직 후기 회고 작성

### 🤔 공부하면서 배운것이 있다면?

#### ReScript

```reason
@bs.module("path") external dirname: string => string = "dirname"
let root = dirname("/User/github") // returns "User"
// 객체 메소드
type document // document 객체를 위한 추상 타입
@send external getElementById: (document, string) => Dom.element = "getElementById"
@val external doc: document = "document"

let el = getElementById(doc, "myId")

// 폴리모픽 함수 모델링
// 트릭 1: 여러개의 external을 사용
@module("MyGame") external drawCat: unit => unit = "draw"
@module("MyGame") external drawDog: (~giveName: string) => unit = "draw"
@module("MyGame") external draw: (string, ~useRandomAnimal: bool) => unit = "draw"
drawCat()
drawDog(~giveName="Dog")
draw("test", ~useRandomAnimal=true)

// 트릭 2: 폴리모픽 배리언트 + unwrap을 사용
@val
external padLeft: (
  string,
  @unwrap [
    | #Str(string)
    | #Int(int)
  ])
  => string = "padLeft"
let pad1 = padLeft("Hello World", #Int(4))
let pad2 = padLeft("Hello World", #Str("Message from ReScript: "))

// 특수한 경우: 이벤트 리스너
type readline

@send
external on: (
    readline,
    @string [
      | #close(unit => unit)
      | #line(string => unit)
    ]
  )
  => readline = "on"

let register = rl =>
  rl
  ->on(#close(event => Js.log(event)))
  ->on(#line(line => Js.log(line)));

// 고정된 인자
// 때때로 인자의 기본값을 자바스크립트 함수에 전달하면서 external을 사용하면 편리하다.
@val
external processOnExit: (
  @as("exit") _,
  int => unit
) => unit = "process.on"

processOnExit(exitCode =>
  Js.log("error code: " ++ Js.Int.toString(exitCode))
);

// 함수의 Nullable 반환 값 래핑
// undefined 또는 null을 반환하는 자바스크립트 함수를 위해 @return(...) 을 제공한다.
// 해당 값을 option 타입으로 자동으로 변환하려면 (ReScript option 타입의 None 값은 null이 아닌 undefined 로만 컴파일된다.)
type element
type dom

@send @return(nullable)
external getElementById: (dom, string) => option<element> = "getElementById"

let test = dom => {
  let elem = dom->(getElementById("haha"))

  switch (elem) {
  | None => 1
  | Some(_ui) => 2
  }
}
// return(nullable) 속성은 자동으로 null과 undefined를 option 타입으로 바꾸어준다.
```

#### 참고 링크
- [ES2022에 class static 초기화 블록 추가](https://2ality.com/2021/09/class-static-block.html)
- [class 101 디자인 시스템](https://ui.class101.dev/core/colors)
- [vscode-edge-devtools](https://github.com/microsoft/vscode-edge-devtools)

### ⚡ 아쉬운 점 및 회고
이번 주말은 정말 딱히 한게 없다. 공부량을 많지 않았고, 거의 쉬었다. 흠.. 취업했다고 소홀히하는 건가..? 그럴정도로 여유를 부릴 시간과 실력이 없을텐데..?   

다시 위기 의식을 느낄 필요가 있다. 아직 너무 많이 부족하고, 배워야할것도 많고 해야할 일들도 너무 많다. 정신을 다시 차릴 필요가 있다. 하기 싫은건 전혀 아닌데, 이번 주말은 정말 많이 나태해졌었다. 동기부여를 얻을 자극제?가 필요해보인다. 커뮤니티를 좀더 보자. 열심히 하시고 잘하시는 분들의 글을 보면 없던 동기뷰여는 저절로 생겨난다. 오브젝트 책도 하나도 안봤고 심지어 까먹고 지금 TIL을 작성하면서 생각났다. 내일 재택이니 좀 시간있을때마다 읽어야겠다...   

반성할 점이 너무 많다. 쓸대없이 시간보낸 점. 딴 생각한 점. 나태한 점. 이번주는 좀 더 의미있게 시간을 써보자. 블로그는 언제쓰지... 한글자도 안썼다...

### 🚀 내일 할 일
- Object 9, 10장 훑어보고 스터디 참여
- ReScript 공식 문서 훑어보기

### 🎯 이번주 목표
- 스터디 참여 및 오브젝트 10장까지 읽기
- 스터디를 위한 자바스크립트 코딩의 기술 4장까지 훑어보기
- ReScript 공식 문서 훑어보기
- 블로그에 이직 후기 회고 작성
- 개인 프로젝트 한피쳐씩 틈틈히

### 😤 Affirmation
- 나는 동기부여를 얻고 다시 나아갈 사람이다.
