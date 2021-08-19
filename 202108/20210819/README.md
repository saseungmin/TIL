## 📆 2021-08-19(목) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] [ReScript 공식문서 훑어보기](https://github.com/saseungmin/Learn_ReScript_with_Official_Documentation)
- [x] 서울로 이사 준비 및 입사 준비!
- [ ] ConStu 내 정보 페이지
- [x] [junior-recruit-scheduler에 PR 날리기](https://github.com/jojoldu/junior-recruit-scheduler/pull/391)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 스터디 참여 및 오브젝트 6장까지 읽기
- [ ] reading_books_record_repository 사이트에 정리한 책 추가하기
- [x] ReScript 공식문서 훑어보기
- [x] 서울로 이사 준비 및 입사 준비!
- ~~자취에 필요한 물건들 사기~~
- ~~보험 처리 끝내기~~

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 ReScript
#### Array
- 리스크립트의 배열에 있는 항목들은 꼭 같은(homogeneous) 타입이어야 한다.

```reason
let myArray = ["hello", "world", "how are you"]
```

##### List
- 리스트는 불변이고, 선두의 항목을 가져오는 것이 빠르다.
- 꼬리(마지막) 항목을 가져오는 것이 빠르다.
- 나머지 다른 것들은 느리다.
- 리스트의 항목들은 꼭 같은 타입이어야 한다.
- 리스트는 불변하고, 효율적인 기능(크기의 가변성, 빠른 속도로 선두 항목 추가, 항목 분해)을 사용하고자 하는 경우에 적합하다.
- 만약 어느 항목에 무작위로 접근하거나 선두가 아닌 위치에 항목을 추가해야한다면 리스트를 쓰면 안된다.

```reason
let myList = list{1, 2, 3}
```

#### Function

```reason
let greet = (name) => "Hello " ++ name
```

- 이름이 있는 인자

```reason
let addCoordinates = (~x, ~y) => {
  /* 여기서 x, y를 사용 */
}
/* ... */
// 순서에 관계없이 전달할 수 있다
addCoordinates(~y=5, ~x=6)
```

- 이름이 있는 선택 인자

```reason
/* radius 는 생략 가능 */
let drawCircle = (~color, ~radius=?, ()) => {
  setColor(color)
  switch radius {
  | None => startAt(1, 1)
  | Some(r_) => startAt(r_, r_)
  }
}
```

- 시그니쳐 및 타입 어노테이션

```reason
let drawCircle: (~color: color, ~radius: int=?, unit) => unit =
  (~color: color, ~radius: option<int>=?, ()) => {
    setColor(color)
    switch radius {
    | None => startAt(1, 1)
    | Some(r_) => startAt(r_, r_)
    }
  }
```

- 재귀함수

리스크립트는 기본적으로 함수내에서 재귀적으로 호출하는 것을 방지. 재귀함수를 만들려면 `let` 뒤에 `rec` 키워드 추가   

```reason
let rec neverTerminate = () => neverTerminate()
```

- [꼬리재귀 최적화](https://stackoverflow.com/questions/33923/what-is-tail-recursion)

### ⚡ 아쉬운 점 및 회고
ReScript에 꼬리재귀 최적화가 구현되어있다니.. 충격 그 자체.. 대단.. 재귀함수에 스택이 쌓여 성능을 해결하기 위해서 나온 꼬리재귀 최적화는 직접 구현을 해주어야하는데 이걸 신경쓸 필요가없다라.. 근데 브라우저상에서 이 꼬리재귀 최적화가 적용되어있는 브라우저는 파이어폭스가 유일하고 그마저도 제대로 되어있지 않는데.. 이게 효과가 있을까 싶다. 어차피 최적화시켜놔도 브라우저에서 인식을 못할텐데. 나중을 위한 방법인가..? 그냥 리스크립트 팀이 말한대로 재귀적인 호출은 사용하지 않는게 좋을 듯 싶다. 어차피 알고리즘 뺴면 재귀는 사용할 일이 거의 없기 때문에..   
얼른 ReScript를 사용하여 React로 구현해보고 싶다. 아마 테스트 코드는 작성 못할 듯 싶다.

벌써 금요일. 시간이 너무 빠르다. 이제 3일뒤면 첫 출근! 아직은 두려움보단 설렘으로 가득하다! 재밌겠다! 이런 마음가짐은 아마 1주일도 안갈 거 같다 ㅎㅎ   

공부는 얼마 못했다. 아니 안했다. 출근할떄까지 이럴꺼다.   

오늘 이사준비를 했다. 월급받기 전 한 달 동안은 거지처럼 살아야한다. 한 달만 참자..! ㅎㅎ   

자는 시간을 더 당겨서 더 일찍 일어나자! 그리고 오브젝트 읽기!

### 🚀 내일 할 일
- 오브젝트 5장까지 읽기
- ReScript 공식문서 훑어보기
- 서울로 이사 준비 및 입사 준비!

### 🎯 이번주 목표
- 스터디 참여 및 오브젝트 6장까지 읽기
- ConStu 내 정보 페이지
- reading_books_record_repository 사이트에 정리한 책 추가하기
- ReScript 공식문서 훑어보기
- 서울로 이사 준비 및 입사 준비!
- ~~자취에 필요한 물건들 사기~~
- ~~보험 처리 끝내기~~
