## 📆 2021-08-24(화) TIL

### 📈 오늘 한 일
- [x] 회사 문화에 적응하기
- [x] ReScript 공식문서 훑어보기

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 회사 문화에 적응하기
- [x] 자취에 필요한 물품들 구매하기
- [ ] 스터디 참여 및 오브젝트 8장까지 읽기
- [x] ReScript 공식문서 훑어보기
- [ ] 거주시에 처리하지 못한 일들 처리하기
- [ ] NEXT-IT Repos 관리하기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 ReScript

##### 패턴 매칭
- 배열과 리스트을 올바르게 구조분해하는 방법은 `switch`를 사용하는 것이다.

```reason
// 데이터 형태에 따른 switch 구문
type payload =
  | BadResult(int)
  | GoodResult(string)
  | NoResult

// if-else 대신 초강력한 switch 패턴 매칭으로 구조 분해를 하고,
// 각각 분해된 결과의 오른편에 작성된 코드가 실행되도록 한다.
let data = GoodResult("Product shipped!")
switch data {
| GoodResult(theMessage) =>
  Js.log("Success! " ++ theMessage)
| BadResult(errorCode) =>
  Js.log("Something's wrong. The error code is: " ++ Js.Int.toString(errorCode))
| NoResult =>
  Js.log("Bah.")
}
```

- `payload`를 완전히 무시하려는 경우, 다음과 같이 `_` 와일드 카드를 사용할 수 있다.

```reason
switch person1 {
| Teacher(_) => Js.log("Hi teacher")
| Student(_) => Js.log("Hey student")
}
```

- `switch`는 패턴을 선형으로 유지하기 위해 `if` 조건을 같이 사용할 수 있는 기능을 지원. `When` 절

```reason
switch person2 {
| Teacher(_) => () // 아무것도 안함
| Student({reportCard: {gpa}}) when gpa < 0.5 =>
  Js.log("What's happening")
| Student(_) =>
  /* fall-through, 모든 값 케이스 */
  Js.log("Heyo")
}
```

- 예외 매칭

```reason
let theItem = 5
let myItems = list{ 1, 2, 3, 4, 5 }

switch List.find(i => i === theItem, myItems) {
| item => Js.log(item)
| exception Not_found => Js.log("No such item found!")
}
```

- 배열 매칭

```reason
let students = ["Jane", "Harvey", "Patrick"]
switch students {
| [] => Js.log("There are no students")
| [student1] =>
  Js.log("There's a single student here: " ++ student1)
| manyStudents =>
  /* 배열에 있는 이름들 출력 */
  Js.log2("The students are: ", manyStudents)
}
```

- 리스트 매칭
- 리스트 패턴 매칭은 배열과 유사하지만 리스트의 꼬리(tail)를 추출하는 추가 기능이 있다. 
```reason
let rec printStudents = (students) => {
  switch students {
  | list{} => () // 끝
  | list{student} => Js.log("Last student: " ++ student)
  | list{student1, ...otherStudents} =>
    Js.log(student1)
    printStudents(otherStudents)
  }
}

let result = printStudents(list{"Jane", "Harvey", "Patrick"})
```

- 리스크립트는 가장 중요한 패턴 매칭 기능으로 누락된 패턴이 있는지 컴파일 시점에 검사하는 기능을 제공.
- 와일드카드 `_` 를 너무 남용하지 마라. 이렇게하면 컴파일러가 더 나은 완전성 검사를 제공하지 못한다.
- `when` 절을 아껴서 사용. 가능하면 패턴 매칭를 평평하게(flatten) 만들어라. 이게 진짜 버그를 제거하는 좋은 방법이다.
- 분기가 많은 `if-else`를 사용할 때마다 패턴 매칭을 고려해봐라. 더 간결하고 성능도 더 뛰어나다.

##### Mutation
- 기본적으로 Let 바인딩은 불변이지만, ref로 값을 감싸면 표준 라이브러리가 하나의 필드로 구성된 레코드를 반환.

```reason
let myValue = ref(5)

let five = myValue.contents

myValue.contents = 6

// or

myValue := 6
```

### ⚡ 아쉬운 점 및 회고
출근 둘째날. 여전히 온보딩 프로세스를 진행하고 있다. 설정할게 정말 많다. 설치할 것들은 또 많고.   
회사 분위기는 즐길만해보인다. 어딜가나 사람이 제일 중요한데 뭐 이제 이틀되서 잘 모르겠지만, 다들 너무 좋다. 출근시간이 너무 자유로워서 언제쯤 출근해야할지 감이 잘 안잡힌다. 일단.. 9시 반에 가고있는데 재택근무에 출근하시는 분들도 10시는 되야 출근하시는 거 같다. 이건 뭐.. 잘 모르겠다. 닉네임으로 부르는건 여전히 어색.. 듣는것도 어색.. 얼른 적응하자.   

오늘 시니어 프론트엔드 면접에 참여했는데 좋은 경험이였다. 동료분들은 시니어는 우리가 결국 따르고 배워야하기 때문에 어떻게든 늦어지더라도 잘하시는 분을 뽑자는 마인드였다. 나또한 같은 의견이여서 눈이 높은건지 아니면 없는건지 모르겠다. 오늘 진행한 면접분은 시니어 프론트엔드 개발자이기보단 프로젝트 관리자 또는 팀장에 가까웠다. 그렇기에 기본적인 자바스크립트의 기본 동작 원리와 프론트 개발에 대해서는 대부분 모르셨다. 거기다 아키텍처에 관한 설계도 갸우둥.. 그리고 이 면접을 참여하고 진행하면서 우리는 여기서 바로 오늘의 면접진행 방식에 대해서 피드백 시간을 가졌다. 보완할 점이 충분히 많아보였고, 다음번 면접부턴 라이브코딩 프로세스를 추가하기로 했다. 구체적인 설계 아키텍처에 관해서 직접적으로 자세히 볼 수 없다는 판단이였다. 이런 부분에서 이런 실수와 실패는 결국 감추는 것이 아닌 수용해야한다. 그리고 이렇게 빠르게 피드백을 얻어 고쳐나가는 것. 그게 정말 중요하다고 다시 느낀다. 또한, 연구결과와 같이 어느정도의 경력이 있다면 경력은 채용에 있어서 전혀 중요하지 않다는 점. 직접 느꼈다.   

회사 적응 기간 동안은 공부양을 많이 줄일 것이다. 회사의 적응과 프로세스를 따라가는게 우선이다.

### 🚀 내일 할 일
- 회사 문화에 적응하기
- ReScript 공식문서 훑어보기

### 🎯 이번주 목표
- 회사 문화에 적응하기
- 자취에 필요한 물품들 구매하기
- 스터디 참여 및 오브젝트 8장까지 읽기
- ReScript 공식문서 훑어보기
- 거주시에 처리하지 못한 일들 처리하기
- NEXT-IT Repos 관리하기
