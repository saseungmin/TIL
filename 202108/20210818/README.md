## 📆 2021-08-18(수) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] [ReScript 공식문서 훑어보기](https://github.com/saseungmin/Learn_ReScript_with_Official_Documentation)
- [x] 자취에 필요한 물건들 사기: 책상 구매하기
- [x] 보험 처리 끝내기
- [x] 입사 서류 관련하여 전 회사에 다시 전화 및 현 회사의 인사담당자님께 물어보기
- [x] reading_books_record_repository 사이트에 정리한 책 추가하기
  - [Do it! 타입스크립트 프로그래밍 웹사이트에 적용 PR](https://github.com/saseungmin/reading_books_record_repository/pull/106)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 스터디 참여 및 오브젝트 6장까지 읽기
- [x] reading_books_record_repository 사이트에 정리한 책 추가하기
- [x] ReScript 공식문서 훑어보기
- [x] 서울로 이사 준비 및 입사 준비!
- [x] 자취에 필요한 물건들 사기
- [x] 보험 처리 끝내기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 ReScript
##### Variant(배리언트)
- 배리언트 생성자 (또는 "배리언트 태그") 라고 한다. `|`(바)로 각 생성자를 구분한다.
- 배리언트 생성자는 대문자로 시작해야한다.

```reason
// 컴파일 된 배리언트 값은 타입 선언에 따라 세가지 자바스크립트 결과물로 컴파일된다.
// - 페이로드가 없는 생성자인 경우 숫자로 컴파일
type greeting = Hello | Goodbye
let g1 = Hello
let g2 = Goodbye

// - 페리로드가 있는 생성자인 경우, TAG 필드와 함께 첫 번째 페이로드는 _0 필드, 두 번째 페이로드는 _1 ...와 같이 순서가 적용된 객체로 컴파일 된다.
// - 예외로 배리언트 타입 선언에 페이로드가 있는 생성자가 하나만 있는 경우, 생성자는 TAG 필드가 없는 객체로 컴파일된다.
type outcome = Good | Error(string)
let o1 = Good
let o2 = Error("oops!")

type family = Child | Mom(int, string) | Dad (int)
let f1 = Child
let f2 = Mom(30, "Jane")
let f3 = Dad(32)

// - 이름이 있는 배리언트 페이로드(=인라인 레코드)는 _0, _1,... 대신 필드 이름을 사용한 객체로 컴파일된다. 객체는 이전 규칙에 따라 TAG 필드가 있을 수도 있고 없을 수도 있다.
type person = Teacher | Student({ gpa: float })
let p1 = Teacher
let p2 = Student({ gpa: 99.5 })

type s = { score: float }
type adventurer = Warrior(s) | Wizard(string)
let a1 = Warrior({ score: 10.5 })
let a2 = Wizard("Joe")
```

- 잠재적으로 성능 측면에서 배리언트는 프로그램 로직 속도를 엄청나게 높일 수 있다.
- 다음은 자바스크립트 코드 조각으로 이 코드 조각은 선형적으로 분기를 검사하고 있다. `(O (n))`.

```js
let data = 'dog'
if (data === 'dog') {
  // ...
} else if (data === 'cat') {
  // ...
} else if (data === 'bird') {
  // ...
}
```

- 리스크립트 배리언트를 사용한 것과 비교하면, 컴파일러는 배리언트를 본 다음, `type animal = 0 | 1 | 2` 으로 변환하고 `switch`를 상수 시간에 조회할 수 있게 변환한다. `(O(1))`.

```reason
type animal = Dog | Cat | Bird

let data = Dog

switch data {
  | Dog => Js.log("Wof")
  | Cat => Js.log("Meow")
  | Bird => Js.log("Kashiiin")
}
```

##### Null, Undefined 그리고 Option
- https://en.wikipedia.org/wiki/Option_type
- 리스크립트 자체는 `null` 또는 `undefined`에 대한 개념이 없다. 이건 버그의 전체 범주를 제거하는 정말 훌륭한 일. 더 이상 `undefined is not a function`, 그리고 `cannot access someAttribute of undefined` 오류는 없다!
- 그러나 잠재적으로 존재하지 않는 값의 개념은 여전히 유용하며, 리스크립트에서도 안전하게 존재한다.

```reason
type option<'a> = None | Some('a)


let licenseNumber =
  if personHasACar {
    Some(5)
  } else {
    None
  }

switch licenseNumber {
| None =>
  Js.log("The person doesn't have a car")
| Some(number) =>
  Js.log("The person's license number is " ++ Js.Int.toString(number))
}
```

### ⚡ 아쉬운 점 및 회고
ReScript에 흥미로운 점들이 정말 많은 거 같다. JavaScript와 비슷할 줄 알았지만 다른 부분도 많았고, 더 좋게 개선된 문법과 새로운 문법들이 흥미로웠다. 오늘은 배리언트부분을 봤었는데, 성능 측면에서 이점을 볼 수 있는 점이 많았다. 하지만 이런 새로운 문법을 잘 써먹기 위해서는 실제로 적용해봐야 좀 감이 올거 같다. 얼른 훑고 ReScript를 사용하여 리액트에서 적용해보자.   
그리고 리스크립트에는 `Null`과 `undefined`가 존재하지 않는건 정말 멋지고 좋은 판단이였다고 생각한다. `null`과 `undefined`는 결국 분기를 낳게 된다. 오류를 잡기 위해서 분기를 만들어야 한다. ReScript에서는 이러한 개념이 없기 때문에 이런 오류를 잡기 위해서 노력하지 않아도 된다. 물론 자바스크립트 기반이기 때문에 여전히 고려를 해야하는 부분이다. 그리고 이를 대안으로 `option`이라는게 있는데 보는 순간 "어! 이거 functional programming의 모나드 maybe와 유사한데?"라고 생각했는데 역시.. 그 원리에서 기반이 되었던 것이다. 함수형 프로그래밍을 공부할 때도 써먹어봐야겠다 했는데 ReScript에서도 이런 이론이 적용되어있다는게 놀라웠다. 어쨌든 이역시 리스크립트의 장점이 아닐까 싶다. 공부해보면서 느꼈던건 이렇게 좋은 언어인데 왜 뜨지 못했을까 생각을 해봤는데 언어는 아주 좋은 언어라해도 배우기 쉬운게 우선인거 같다. 아무리 잘 짜여진 언어라도 배우기가 어려우면 인기가 없어 조용히 사라지는 것 같다. 그래서 ReasonML과 버클스크립트가 대체되 ReScript 생겨났듯이... 과연 ReScript는 살아남을 수 있을 것인가..   

오늘 거의 모든 서류 작업은 끝냈다. 보험처리도 마무리지었고, 입사 서류도 뽑았다. 이제 이사 준비를 슬슬 해야한다. 오브젝트 책은 미리미리 읽어두자.   

오늘 아쉬운점은 그래도 평소보다 일찍 일어났는데 다시 자버렸다. 사실 별로 안졸렸는데... 자버렸다.😅 아니 일단 일찍자자. 첫 출근 후 후폭풍이 두렵다. 😅   

첫번째 우선순위는 입사에 관련된 것이다. 이사 포함. 그리고 쉬는것. 제일 마지막이 공부. 어차피 가면 이리치이고 저리치일텐데.. 적당히 하자 지금은. (제발;)

### 🚀 내일 할 일
- ReScript 공식문서 훑어보기
- 서울로 이사 준비 및 입사 준비!
- ConStu 내 정보 페이지

### 🎯 이번주 목표
- 스터디 참여 및 오브젝트 6장까지 읽기
- ConStu 내 정보 페이지
- reading_books_record_repository 사이트에 정리한 책 추가하기
- ReScript 공식문서 훑어보기
- 서울로 이사 준비 및 입사 준비!
- 자취에 필요한 물건들 사기
- 보험 처리 끝내기
