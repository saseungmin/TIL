## 📆 2021-03-03(수) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 알고리즘 공부
  - Section 5의 two pointer 문제 3문제를 풀었다.
  - [Link](https://github.com/saseungmin/daily_coding_dojo/tree/master/inflearn_algorism/section5)
- [x] 오브젝트 책 Chapter 3 읽기 및 스터디 참여
  - [Chapter 1](https://github.com/saseungmin/reading_books_record_repository/pull/40)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 공부
- [x] 오브젝트 책 Chapter 3 까지 읽기 및 스터디 참여
- [ ] Recoil를 사용한 ToDo 앱 만들기 진행하기
- [ ] 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- [x] 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 알고리즘 공부에서 배운 점
- 알고리즘을 풀면서 Two Pointers Algorism이라는 것을 배웠다.
- 생각보다 간단한데 알고리즘 방법이다.
- 두가지의 포인터를 사용하여 시간복잡도를 단축시킬 수 있는 방법이다.

```js
function solution(a, b) {
  return [...a, ...b].sort((x, y) => x - y);
}
```
- 위와 같이 그냥 두 배열을 더해서 sort 해주면 된다고 생각했지만 이렇게 하면 `sort`를 사용하기만 하더라도 `O(nlogn)`이라는 시간이 걸린다.
- 하지만 한 번의 반복문을 사용하면 즉, 예에서 a 길이 더하기 b 길이가되면 시간복잡도는 O(a+b)가 된다.

```js
function solution(a, b) {
  const aLen = a.length;
  const bLen = b.length;
  const result = [];

  let aPointer = 0;
  let bPointer = 0;

  while (aPointer < aLen && bPointer < bLen) {
    if (a[aPointer] <= b[bPointer]) {
      result.push(a[aPointer]);

      aPointer += 1;
    }

    if (a[aPointer] > b[bPointer]) {
      result.push(b[bPointer]);

      bPointer += 1;
    }
  }

  while (aPointer < aLen) {
    result.push(a[aPointer]);

    aPointer += 1;
  }

  while (bPointer < bLen) {
    result.push(b[bPointer]);

    bPointer += 1;
  }

  return result;
}
```

- 하지만 이렇게 풀면 당연히 저 한줄짜리 코드가 이렇게나 길어지게 된다. 효율성이 중요한 문제에서는 Two Pointer알고리즘을 사용하되, 굳이 필요없을 때는 안사용하는게 좋을 거 같다.
- readability가 많이 떨어진다..

#### 🎈 Object 책을 읽고 1차 오브젝트 스터디를 통해 알게된 점
- [3장 정리한 링크](https://github.com/saseungmin/reading_books_record_repository/tree/master/%EC%98%A4%EB%B8%8C%EC%A0%9D%ED%8A%B8/Chapter%203)
- [디미터의 법칙](https://johngrib.github.io/wiki/law-of-demeter/)
- 객체지향에서 설계란 서로 의존하면서 협력하는 객체들의 공동체를 구축하는 것. 필요한 최소한의 의존성만 유지하고 불필요한 의존성을 제거하는 것. 설계란 코드를 배치하는 것.
- 좋은 설계란 코드를 짜는 동시에 내일 쉽게 변경할 수 있는 코드를 짜는 것. 내일의 변경을 매끄럽게 수용할 수 있는 설계.
- 객체지향 설계를 할 때 중요한 건 도메인을 이해하는 것이 중요하다. 도메인을 이해하고 있지 못한 상태에서 설계를 하면 굉장히 어려워진다.
- 다형성이란 동일한 메시지를 전송하지만 실제로 어떤 메서드가 실행될 것인지는 메시지를 수신하는 객체의 클래스가 무엇이냐에 따라서 달라진다. 이를 다형성이라고 부른다. 동일한 메시지를 수신했을 떄 객체의 타입에 따라 다르게 응답할 수 있는 능력을 의미한다.
- 상속은 코드를 재사용하기 위해 사용하면 안된다. 그 이유는 설계를 유연하게 못하게 만든다. 상속은 하나만 받을 수 있기 때문이다.

```ts
class Greeter1 {
  // ...
}

class Greeter2 {
  // ...
}

// 상속을 하나 밖에 할 수 없다.
class Foo extends Greater1 {
 // ... 
}
```
- 만약 여기서 상속을 두개를 받고 싶으면? 불가능하다. 때문에 상속에 상속으로 연쇄?적으로 해야할 수밖에 없어진다.

```ts
// 만약 Greater2를 상속받고 싶으면
class Greeter1 {
  // ...
}

class Greeter2 extends Greater1 {
  // ...
}

// 상속을 하나 밖에 할 수 없다.
class Foo extends Greater1 {
 // ... 
}
```

- 이렇게 해야하기 때문에 굉장히 좋지않은 코드가 되어버린다.
- 코드를 재사용하기 위해서는 합성을 사용해야 한다. 인터페이스를 통해 약하게 결합한다. 인터페이스를 사용하여 정의된 메시지를 통해서만 코드를 재사용할 수 있다.

### ⚡ 아쉬운 점 및 회고
- 오늘의 아쉬운 점은 또 스터디에 아쉬운점이 많이 남는다. 좀 말좀 잘해야할텐데..
- 말을 잘 못하는 것으로 봐서 내가 아직 객체지향을 이해하지 못했나보다. 벌써 객체지향 4번째 책인데 흠... 책을 보면 알겠는데. 책을 안보고 얘기하려고 하면 정리가 안되서 말을 잘 못하겠다.
- 스터디를 위해서 좀 더 공부를 해야겠다.
- 알고리즘 공부를 했는데. 뭔가 열심히 안한? 느낌이다. 좀 더 시간 투자를 많이해서 많이 풀어보자.
- 그리고 모르는 부분은 강의를 들었는데. 내가 몰랐던 알고리즘으로 푸는 것을 보면서 도움이 많이 되고 있다. 하지만, 이 알고리즘을 풀때 중요한 건 효율성일까? 가독성일까? 잘 모르겠다.
- 내일은 다시 얼른 Recoil를 마무리 지어야겠다. 얼른 끝내고 이제 이력서 정리도 하고, 취업 준비에 본격적으로 뛰어들어야겠다. CS공부와 JS공부등...
- 오늘 회고 TIL 끝!

### 🚀 내일 할 일
- 알고리즘 공부
- Recoil를 사용한 ToDo 앱 만들기 진행하기

### 🎯 이번주 목표
- 알고리즘 공부
- ~~오브젝트 책 Chapter 3 까지 읽기 및 스터디 참여~~
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기