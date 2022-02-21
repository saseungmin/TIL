## 📆 2021-09-02(목) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] ReScript 공식 문서 훑어보기
- [x] 스터디 참여 및 자바스크립트 코딩의 기술 2장 훑어보기
- [ ] 블로그에 이직 후기 회고 작성

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 회사 문화에 적응하기
- [ ] 스터디 참여 및 오브젝트 10장까지 읽기
- [x] 스터디를 위한 자바스크립트 코딩의 기술 훑어보기
- [x] ReScript 공식 문서 훑어보기
- [ ] 블로그에 이직 후기 회고 작성

### 🤔 공부하면서 배운것이 있다면?

#### ReScript

```reason
type coordinates = {x: float, y: float}
@unboxed type localCoordinates = Local(coordinates)
@unboxed type worldCoordinates = World(coordinates)

let renderDot = (World(coordinates)) => {
  Js.log3("Pretend to draw at:", coordinates.x, coordinates.y)
}

let toWorldCoordinates = (Local(coordinates)) => {
  World({
    x: coordinates.x +. 10.,
    y: coordinates.x +. 20.,
  })
}

let playerLocalCoordinates = Local({x: 20.5, y: 30.5})

/* 이제 이렇게 호출하면 오류가 발생합니다! */
/* renderDot(playerLocalCoordinates) */
/* 대신 이렇게 사용하도록 강제합니다. */
renderDot(playerLocalCoordinates -> toWorldCoordinates)
// 이제 renderDot은 worldCoordinates만을 입력으로 받는다.
// 배리언트 타입으로 구분 + 인자 구조분해를 써서 더 안전한 코드를 만들었다.
// 성능 저하는 없다.
// unboxed 속성 덕분에 배리언트 래퍼 없이 깔끔하게 JS 코드로 컴파일됐다.
```

#### 참고 링크
- [Mono Repo를 위한 Lerna 간단 정리](https://pks2974.medium.com/mono-repo-%EB%A5%BC-%EC%9C%84%ED%95%9C-lerna-%EA%B0%84%EB%8B%A8-%EC%A0%95%EB%A6%AC%ED%95%98%EA%B8%B0-65c22029988)
- [husky](https://github.com/typicode/husky)
- [lerna](https://github.com/lerna/lerna)

### ⚡ 아쉬운 점 및 회고
현재 카사 웹 사이트에 웹 거레소가 없다. 이 부분에 대해서 이야기를 했는데 재밌을거 같았다. 앞으로 할 생각에 기대가 된다. 뭐든 좋으니 다같이 재밌게 했으면 좋겠다. 이것도 아직 졍식으로? 하는건 아닌데, 다들 열정이 넘처서 시간 날때마다 하자고 했다. 빨리 결과물을 보고 싶어 한다. 나도 빨리 해보고 싶다. 하기로 했지만, 앞으로의 아키텍처 설계부터 프로젝트 구조, TDD를 잘 할 수 있을까? 앞으로의 고민들이 저절로 많아진다. 일은 많아지겠지만, 이런걸들을 고민해보며 적용해보는건 어디서도 못할 듯 싶다. 그리고 이러한 고민들이 결국 더 빠르게 성장하는 지름길이 될꺼라 생각한다.    

스터디를 했는데 뭔가 의식의 흐름대로 진행하다보니 정신이 없었던거 같다. 먼저 어떤식으로 얘기를 해서 정리를 할지부터 고민해봐야겠다. 뭔가 중요한 지식들이 많은데 이걸 설명하기 시작하니까 꼬리에 꼬리를 물어 새로운 얘기들이 생겨나서 쉽게 설명하기가 꽤 까다로웠다. 조금은 책을 집중해서 흘러가는게 맞는거 같기도 하다.    

이직 회고글은 얼른 쓰자.   

TIL에 긍정적 자기 선언(Affirmation)을 추가해봐야겠다.

### 🚀 내일 할 일
- ReScript 공식 문서 훑어보기
- 블로그에 이직 후기 회고 작성

### 🎯 이번주 목표
- 회사 문화에 적응하기
- 스터디 참여 및 오브젝트 10장까지 읽기
- 스터디를 위한 자바스크립트 코딩의 기술 훑어보기
- ReScript 공식 문서 훑어보기
- 블로그에 이직 후기 회고 작성


### 😤 Affirmation
- 나는 성장에 두려움이 없고 도전을 즐기는 사람이다.
