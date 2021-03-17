## 📆 2021-03-17(수) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
  - 처음 랜더링시 유저의 토큰 검사 로직을 수정했다. ([PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/63))
  - ToDo를 삭제하는 로직을 추가시켰다. API Call ([PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/64))
- [x] 오브젝트 책 7,8,9장 복습 및 스터디 참여
- [ ] 알고리즘 공부

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 알고리즘 공부
- [x] 오브젝트 책 Chapter 9 까지 읽기 및 스터디 참여
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
- [x] 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- [x] 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기

### 🤔 공부하면서 배운것이 있다면?

#### 📌 오브젝트 스터디를 참여한 후..
- 추상 데이터 타입에 대해서 다시 알게 되었다.
- 추상 데이터 타입과 클래스의 차이는 일단, 상속과 다형성이 있냐 없냐.
- 추상 데이터 타입은 오퍼레이션으로 타입을 분리한다. 그렇기 때문에 하나의 오퍼레이션에 여러 개의 타입이 존재할 수 있다.
- 그래서 분기가 생길 수 밖에 없게 된다. 즉, 책임을 두 가지를 가지게 된다.

```rb
Employee = Struct.new(:name, :basePay, :hourly, :timeCard) do
  def calculatePay(taxRate)
    if (hourly) then
      return calculateHourlyPay(taxRate)
    end
    return calculateSalariedPay(taxRate)
  end

private
  def calculateHourlyPay(taxRate)
    # ...
  end

  def calculateSalariedPay(taxRate)
    # ...
  end
end
```

- 이런 방식을 클래스를 사용해서 상속과 다형성을 이용해 변경할 수 있다.

```rb
class Employee
  attr_reader :name, :basePay

  def initialize(name, basePay)
    @name = name
    @basePay = basePay
  end

  def calculatePay(taxRate)
    raise NotImplementedError
  end
end

class SalariedEmployee < Employee
  def initialize(name, basePay)
    super(name, basePay)
  end

  def calculatePay(taxRate)
    # ...
  end
end

class HourlyEmployee < Employee
  def initialize(name, basePay)
    super(name, basePay)
  end

  def calculatePay(taxRate)
    # ...
  end
end
```

#### 📌 Recoil를 사용한 ToDo 앱 만들기에서 배운것이 있다면..
- `useRecoilCallback`의 좋은 점을 찾았다! 생각보다 편리하다.
- `useRecoilLoadable`만 고집해서 하려다보니 이 방법이 더 편하고 더 좋은 거 같다..

```js
const useCheckCallback = () => useRecoilCallback(({ snapshot, set, reset }) => async () => {
  set(isLoadingAtom, true);

  const { data } = await userCheckErrorHandling(snapshot.getPromise(userWithCheck()));

  set(userAtom, { user: data });
  reset(isLoadingAtom);
}, []);

export default useCheckCallback;


const useRemoveCallback = () => useRecoilCallback(({ snapshot, set, reset }) => async (id) => {
  set(isLoadingAtom, true);

  try {
    await snapshot.getPromise(todoWithRemove(id));

    set(
      todosResultAtom,
      (prevState) => ({
        ...prevState,
        todos: prevState.todos.filter((todo) => todo._id !== id),
      }),
    );
  } catch (error) {
    set(todosResultAtom, (prevState) => ({
      ...prevState,
      todoError: todoErrorMessage(error),
    }));
  } finally {
    reset(isLoadingAtom);
  }
}, [todosResultAtom, isLoadingAtom]);
```


### ⚡ 아쉬운 점 및 회고
- 무슨.. 시간이 2시 20분... 너무 늦어버렸다.
- RecoilTodo의 로직을 고민하다 시간을 너무 많이 써버렸다.
- useRecoilCallback의 간편함을 알게되었다. 근데 이렇게 써도 되는지는 모르겠다. 왜냐하면 공식 문서에는 Api를 useRecoilLoadable이나 noWait 같은 것을 사용하라고? 나와있었기 때문이다. 에러 처리와 loading처리가 간편해보이지만 뭔가 전역으로 하기가 useRecoilCallback이 더 간편해서 Todo는 useCheckCallback을 사용했다.
- Todo 삭제 하는 것을 금방 할 줄 알았는데 생각보다 고민해서 오래걸려버렸다.
- 그래도 오늘 한 양에 대해서는 만족스럽다..
- 얼른 자야겠다. 너무 오래했다. 허리가 아파아아아
- 오늘 스터디를 했는데 스터디를 안했으면 그냥 넘어갔을 것을 다시 한 번 알게 되서 좋았다. 역시 역시 스터디를 해야지 뭔가 더 열심히 하게 된다.
- 알고리즘 공부를 못한 건 아쉽지만. 내일 다시 해보자!
- 오늘 TIL 마무리. 끝!

### 🚀 내일 할 일
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 알고리즘 공부

### 🎯 이번주 목표
- 알고리즘 공부
- ~~오브젝트 책 Chapter 9 까지 읽기 및 스터디 참여~~
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기
