## 📆 2021-02-06(일) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 앨레강트 오브젝트 1장 읽고 정리하기
  - 1장을 읽고 정리했다.
  - [PR Link](https://github.com/saseungmin/reading_books_record_repository/pull/34)
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기(필터)
  - 필터 버튼에 따른 Todo의 상태 변화 (전체, 완료, 미완료 상태)
  - [PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/14)
- [ ] 개인 프로젝트 진행(스터디 후기)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 알고리즘 공부 계획 세우기
- [ ] 리플레쉬 및 정리
- [x] 긍정적이게 생각하기 😤

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 앨레강트 오브젝트 Chapter 1
- 클래스 이름을 -er로 끝나는 이름을 사용하지 말아야 한다.
- 클래스는 객체의 팩토리이다.
- 클래스의 이름은 무엇을 하는지가 아니라 무엇인지에 기반해야 한다.
- 객체는 캡슐화된 데이터의 대표자이다. 즉, 대표자는 스스로 결정을 내리고 행동할 수 있는 자립적인 엔티티이다.
- 생성자 하나를 주 생성자로 만들어야 한다.
- `constructor`의 주된 작업은 제공된 인자를 사용해서 캡슐화하고 있는 프로퍼티를 초기화하는 일이다. 때문에 `constructor`안에는 코드가 없어야한다. 생성자는 코드가 없어야하고, 오직 할당문만 포함해야 한다.
- 주 `constructor`에는 객체 초기화 프로세스를 시작하는 유일한 장소이기 떄문에 제공되는 인자들은 완전해야 한다.

```java
class Cash {
  private Number dollars;

  Cash(String dlr) { // 부 constructor
    this(new StringAsInteger(dlr));
  }

  Cash(Number dlr) { // 주 constructor
    this.dollars = dlr;
  }
}

class StringAsInteger implements Number {
  private String source;

  StringAsInteger(String src) {
    this.source = src;
  }

  int intValue() {
    return Integer.parseInt(this.source);
  }
}

Cash five = new Cash("5");
```

#### 🎈 Recoil을 사용한 ToDo 앱 만들기
- Recoil의 `selector`를 사용해보았다.
- Todo가 `completed`된 상황 `completed`가 안 된 상황, 전체 이 세 가지의 버튼을 클릭 할 때마다 해당 Todo들이 보이게 하는 것이다.
- 기본 베이스는 Recoil 공식 문서를 보면서 진행하였지만, 전체적 코드는 많이 변경하였다.
- 아래는 `filter`의 상태를 나타내기 위해서 `atom`를 선언하였다.

```js
const todosAtom = atom({ // todo 리스트
  key: 'todosAtom',
  default: [],
});

const filterAtom = atom({ // 필터 상태 (All, Active, Completed)
  key: 'filterAtom',
  default: 'All',
});
```

- 그리고 `todosAtom`을 `filterAtom` 상태에 따라서 변경해준다.

```js
const filteredTodos = {
  All: (state) => (state),
  Active: (state) => (state.filter((todo) => !todo.isComplete)),
  Completed: (state) => (state.filter((todo) => todo.isComplete)),
};

const filterWithTodos = selector({
  key: 'filterWithTodos',
  get: ({ get }) => {
    const filter = get(filterAtom);
    const todos = get(todosAtom);

    return filteredTodos[filter](todos);
  },
});
```

### ⚡ 아쉬운 점 및 회고
- 잠을 늦게 자서 늦잠을 잤다.
- 개인 프로젝트를 진행하지 못했다. 하지만 생각보단 많은 것을 해서 나쁘지는 않다.
- 다음주는 좀 규칙적으로 생활해야겠다.
- 퇴사 후 벌써 1주일이 지났다. 이번주는 잘 보냈나? 라고 물어본다면.. 괜찮았다고 생각한다.
- 그리고 이번주는 리플레쉬를 할려했지만 그냥 평소와 같았다. 다른 점은 출근을 안한다는 점과 시간대가 바꼈다는것.

### 🚀 내일 할 일
- 앨레강트 오브젝트 2장 반 읽고 정리하기(양이 많다.)
- 알고리즘 공부하기
- Recoil를 사용한 ToDo 앱 만들기 진행하기

### 🎯 이번주 목표
- 알고리즘 공부 시작하기
- 리플레쉬 및 정리
- 긍정적이게 생각하기 😤
- 설날