## 📆 2021-08-16(월) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [ ] 오브젝트 4장까지 읽기
- [x] ReScript 공식문서 훑어보기
- [x] reading_books_record_repository 사이트에 정리한 책 추가하기
  - [테스트 주도 개발로 배우는 객체 지향 설계와 실천 PR](https://github.com/saseungmin/reading_books_record_repository/pull/105)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 스터디 참여 및 오브젝트 4장까지 읽기
- [x] reading_books_record_repository 사이트에 정리한 책 추가하기
- [ ] ConStu 내 정보 페이지
- [x] ReScript 공식문서 훑어보기
- ~~함께 자라기 책 읽기 마무리~~
- ~~입사 관련 서류 준비 및 500만원 한도 장비 구입~~
- ~~집 알아보기~~

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 ReScript
##### 흥미로웠던 것들   

- Private let bindings

```rs
module A: {
  // public 필드로 타입을 선언하며 모듈 A의 a는 접근 불가능 하고, b만 접근 가능
  let b: int
} = {
  let a = 3 // 외부에서 a는 접근 불가
  let b = 4
}
// 직접 %%private 키워드로 private 필드를 직접 만들 수 있다
module B = {
  %%private(let a = 3)
  let b = 4
}
```

- 문자열

```rs
// ++ 문자열 이어 붙이기
let greetings = "Hello " ++ "earth!"

// 문자열 보간
let name = "Joe"
let greeting1 = `Hello
World
👍
${name}
`

// 문자열 보간을 하려면 바인딩을(name) 문자열로 변환해야 한다. 
// 보간을 통해 바인딩을 암시적으로 문자열로 변환하려면 앞에 j를 추가.
let age = 10
let message = j`Today I am $age years old.`
```

- 튜플

```rs
let my3dCoordinates = (20.0, 30.5, 100.0)

// 튜플의 특정 요소를 얻으려면 튜플을 구조분해한다.
// _: 일부 요소를 무시
let (_, y, _) = my3dCoordinates
// 튜플은 작은 범위에서 사용하도록 노력.
```

- 타입

```rs
// 리스크립트의 타입은 다른 타입으로 바뀌지 않는다.
// 라스크립트의 타입들은 컴파일 후에 사라지고 타입이 필요없는 런타입 단게에서는 그 정보들이 남아있지 않는다.
// 리스크립트는 모든 정보들(특히 모든 타입 오류들)을 컴파일 중에 알려준다.
// 리스크립트의 타입 시스템은 절대 틀리지 않는다.
// 리스크립트의 타입 검사기는 가장 빠른 검사기 중 하나다.
// 타입을 하나하나 쓸 필요가 없다. 리스크립트는 변수의 값에서 타입을 유추할 수 있다.

// 타입 인자(A.k.a Generic)
// 타입들은 인자를 받을 수 있다. 다른 언어에서는 Generics라고 한다. 매개변수들의 이름은 꼭 '으로 시작해야 한다.
type coordinates<'a> = ('a, 'a, 'a)

let a: coordinates<int> = (10, 20, 20)
let b: coordinates<float> = (10.5, 20.5, 20.5)

type result<'a, 'b> = 
  | Ok('a)
  | Error('b)

type myPayload = {
  data: string
}

type myPayloadResults<'errorType> = array<result<myPayload, 'errorType>>

let payloadResults: myPayloadResults<string> = [
  Ok({ data: "hi" }),
  Ok({ data: "bye" }),
  Error("Something wrong happened!")
]
```

### ⚡ 아쉬운 점 및 회고
아쉬운점은 오브젝트 4장을 안읽었다. 내일 스터디이니까 내일 스터디전에 읽자.   

ReScript를 공부하면서 흥미로운 점들이 많이 보였다. javascript의 `const`, `let`이 `let`으로 통합되었다는 점, `null`과 `undefined`가 존재하지 않는다는 점, 자신있게 리스크립트 타입 시스템은 절대 틀리지 않는다는 점. 이외에 자바스크립트에 없는 튜플까지.. 흥미로운 문법들도 많았다. 리스크립트 공식문서 훑어보는건 궁극적으로는 React에 적용하여 구현하는 것까지이다. 그래도 ToDo 앱 까지는 만들어봐야되지 않겠어?   

이번주는 이사 준비로 바쁠것이다. 이번주만 바쁘고 다음주부터 새로운 환경에서 새로운 사람들과 적응하느라 바쁠것이고 회사 업무에 바쁠것이다. 그래도 어느 정도 설레임도 있어서 기분은 좋다. 이직하면 하고 싶었던게 있었는데 퇴사 후 취준에서 이직까지 회고를 블로그에 작성하는 것이다. 입사하면 블로그에 회고를 작성해야겠다. 즉, 다음주에 작성해야지~   

블로그에 글도 좀 많이 써야겠다. 너무 안썼다. 사실 마음 잡고 글 쓸려면 정말 하루 전체를 투자해야해서 시간 소모가 심하다. 그래도 이제 이직해서 어려운 문제 또는 고민한 문제를 해결한 것들을 블로그에 정리를 해야겠다.   

1day 1commit은 회사에 다녀서도 최대한 아니 무조건 하는데까지 할것이다. 화이팅! 😤

### 🚀 내일 할 일
- 오브젝트 4장 읽고 스터디 참여
- ReScript 공식문서 훑어보기

### 🎯 이번주 목표
- 스터디 참여 및 오브젝트 6장까지 읽기
- reading_books_record_repository 사이트에 정리한 책 추가하기
- ReScript 공식문서 훑어보기
- 서울로 이사 준비 및 입사 준비!
- 자취에 필요한 물건들 사기
- 보험 처리 끝내기
