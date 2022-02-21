## 📆 2021-09-09(목) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 스터디 참여 및 자바스크립트 코딩의 기술 4장까지 훑어보기
- [x] ReScript 공식 문서 React 파트 훑어보기

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 스터디 참여 및 오브젝트 12장까지 읽기
- [x] 스터디를 위한 자바스크립트 코딩의 기술 4장까지 훑어보기
- [x] ReScript 공식 문서 React 파트 훑어보기
- [ ] 블로그에 이직 후기 회고 작성
- [ ] 개인 프로젝트 한피쳐씩 틈틈히

### 🤔 공부하면서 배운것이 있다면?

#### ReScript
- 키 갑은 형제 요소들 사이에서 각각 고유해야한다.
- 배열 내에서 사용되는 키는 형제 요소 사이에서 고유해야한다.
- 하지만 글로벌한 영역에서 고유할 필요는 없다. 두 개의 다른 배열을 생성할 때 고유한 키를 사용할 수 있다.

```rescript
type post = { id: string, title: string, content: string }

module Blog = {
  @react.component
  let make = (~posts: array<post>) => {
    let sidebar = {
      <ul>
        {
          Belt.Array.map(posts, (post) => {
            <li key={post.id}>
              {React.string(post.title)}
            </li>
          })->React.array
        }
      </ul>
    }

    let content = Belt.Array.map(posts, (post) => {
        <div key={post.id}>
          <h3>{React.string(post.title)}</h3>
          <p>{React.string(post.content)}</p>
        </div>
    });

    <div>
      {sidebar}
      <hr />
      {React.array(content)}
    </div>
  }
}

let posts = [
  {id: "1", title: "Hello World", content: "Welcome to learning ReScript & React!"},
  {id: "2", title: "Installation", content: "You can install reason-react from npm."}
]

let blog = <Blog posts/>
```

- 리스트로 렌더링할 땐 결국 list를 array로 변환해야한다. 이때 추가적인 변환 비용이 발생한다.
- 아마 99%의 경우에는 배열을 사용한다.
- 하지만 경우에 따라서 고급 패턴 매칭 기능을 사용하고 싶을 때 list 타입을 사용하기도 한다.

### ⚡ 아쉬운 점 및 회고
스터디를 진행했는데 시간을 좀 더 활용을 잘해야겠다. 오늘도 2시간이나 소요됐는데 이건 좋지 못하다. 좀 더 정해진 시간안에서 효율적으로 사용하도록 노력해야겠다.   

ReScript 공식 문서에 PR올린 건 바로 merge가 되었다. 이렇게 오픈소스에 또 하나의 내 기여가 포함되니 기분이 좋다. 이젠 여기서 더 나아가서 좀 더 의미있고 확실히 도움될만한 기여를 하고 싶다. 영어는 못하지만 번역도 하고싶다.   

내일은 재택! 내일만 하면 주말! 그리고 추석! 그리고 드디어 월급날!! 시간아 얼른 흘러라~   

끝!

### 🚀 내일 할 일
- ReScript 공식 문서 React 파트 훑어보기

### 🎯 이번주 목표
- 스터디 참여 및 오브젝트 12장까지 읽기
- 스터디를 위한 자바스크립트 코딩의 기술 4장까지 훑어보기
- ReScript 공식 문서 React 파트 훑어보기
- 블로그에 이직 후기 회고 작성
- 개인 프로젝트 한피쳐씩 틈틈히

### 😤 Affirmation
- 나는 프론트엔드가 즐겁다.
