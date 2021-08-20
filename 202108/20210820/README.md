## 📆 2021-08-20(금) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 오브젝트 5장까지 읽기
- [x] ReScript 공식문서 훑어보기
- [x] 서울로 이사 준비 및 입사 준비!
- [x] [NEXT IT Organization 생성](https://github.com/NEXT-IT-STUDY?type=source) 및 [Git 연습 Repo](https://github.com/NEXT-IT-STUDY/practice_for_git) 초기 세팅
  - [초기 세팅 PR](https://github.com/NEXT-IT-STUDY/practice_for_git/pull/1)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 스터디 참여 및 오브젝트 6장까지 읽기
- [ ] reading_books_record_repository 사이트에 정리한 책 추가하기
- [x] ReScript 공식문서 훑어보기
- [x] 서울로 이사 준비 및 입사 준비!
- ~~자취에 필요한 물건들 사기~~
- ~~보험 처리 끝내기~~

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 오브젝트 5장
- 책임을 수행할 정보를 알고 있는 객체에게 책임을 할당하는 것을 GRASP에서 이를 INFORMATION EXPERT(정보 전문가) 패턴이라고 한다.
- 책임을 할당할 수 있는 다양한 대안들이 존재한다면 응집도와 결합도의 측면에서 더 나은 대안을 선택하는 것이 좋다. 다시 말해 두 협력 패턴 중에서 높은 응집도와 낮은 결합도를 얻을 수 있는 설계가 있다면 그 설계를 선택해야 한다는 것이다. GRASP에서는 이를 LOW COUPLING(낮은 결합도) 패턴과 HIGH COHESION(높은 응집도) 패턴이라고 부른다.
- GRASP의 CREATOR(창조자) 패턴은 객체를 생성할 책임을 어떤 객체에게 할당할지에 대한 지침을 제공한다.
- 객체의 타입에 따라 변하는 행동이 있다면 타입을 분리하고 변화하는 행동을 각 타입의 책임으로 할당하라는 것을 GRASP에서는 이를 POLYMORPHISM(다형성) 패턴이라고 부른다.
- 변경을 캡슐화하도록 책임을 할당하는 것을 GRASP에서는 PROTECTED VARIATIONS(변경 보호) 패턴이라고 부른다.

#### 🎈 ReScript
#### If-Else and Loops
```reason
let message = if isMorning {
  "Good morning!"
} else {
  "Hello!"
}
```

- `if-else` 표현에서 `else` 브랜치가 없는 경우, 암시적으로 `()`를 제공.

```reason
if showMenu {
  displayMenu()
}

// 위와 같다
if showMenu {
  displayMenu()
} else {
  ()
}
```

- 리스크립트는 삼항 연산자도 제공하지만, `if-else`를 사용 할 것을 장려한다.

```reason
let message = isMorning ? "Good morning!" : "Hello!"
```

- 리스크립트에서는 다른 언어에서보다 `if-else`와 삼항 표현(ternary)을 극히 드물게 사용한다.
- For 루프(loop)는 시작 값부터 끝 값까지(끝 값도 포함) 반복.

```reason
for x in 1 to 3 {
  Js.log(x)
  Js.log(" ")
}

// for 루프 카운트에 downto를 이용하면 반대 방향으로 반복할 수 있다.
for x in 3 downto 1 {
  Js.log(x)
  Js.log(" ")
}
```

- While 루프(loop)

```reason
while testCondition {
  /* body here */
}
```

- 리스크립트는 루프를 탈출하는 `break` 키워드가 없다.
- 하지만, 가변 바인딩을 이용해 `while` 문을 탈출할 수 있다.

```reason
let break = ref(false)

while !break.contents {
  if Js.Math.random() > 0.3 {
    break := true
  } else {
    Js.log("Still running")
  }
}
```

##### 파이프
- 리스크립트는 파이프 연산자(`->`)를 지원한다. 파이프를 이용하면 `a(b)`를 `b->a`와 같이 작성할 수 있다. 파이프는 단순히 방향을 바꿔주는 문법일 뿐이어서 사용할 때 별도의 성능 저하는 없다.

```reason
validateAge(getAge(parseData(person)))

person
  ->parseData
  ->getAge
  ->validateAge

let result = [1, 2, 3]
  ->map(a => a + 1)
  ->filter(a => mod(a, 2) == 0)

asyncRequest()->setWaitDuration(4000)->send
```
### ⚡ 아쉬운 점 및 회고
오브젝트 2장의 내용를 GRASP 패턴으로 나눠본 것이다. 결국 하고자하는 얘기는 같다. 자율적인 객체를 만들자. 스스로가 소유하고 있는 데이터를 자기 스스로 처리하도록 만드는 것이 자율적인 객체를 만드는 지름길. 따라서 메서드가 사용하는 데이터를 저장하고 있는 클래스로 메서드를 이동시키면된다!   

오늘 회사에서 쓸 장비가 도착했다고 한다. 언박싱이 기대가 된다..!! ㅎㅎ   

NEXT IT Organization 만들었다. 원래 개인 Repo에 Git 연습을 위한 Repo를 만들려고 했는데, 어찌됬든 스터디로도 아니면 따른 일로도 쓸 일이 있을 거 같아서 생성했다. 원래 Private로 만들려고 했는데, 돈을 달마다 내기 싫어서 안했다. 월급받으면 Private Organization이든 Repo로든 변경해야겠다. 간단하게 어떤 식으로 브랜치를 생성해서 공용 Repo에 PR을 날리는 지 연습하는 Repo로 흐름을 이해하는 목적으로 만든 Repo이다. CI/CD 구축하고, 간단하게 이름?을 적으면 사이트에 리스트가 보이게 만들것이다. PR이 main으로 merge가 되면. 아, 설명을 위한 Readme 작성도 해야되는군..   

오늘은 일찍 퇴근! 어차피 공부한 시간을 얼마 안되지만!😤

### 🚀 내일 할 일
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
