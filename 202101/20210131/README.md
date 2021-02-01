## 📆 2021-01-31(일) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 개인 프로젝트를 진행하자.(반응형 만들기 or 스터디 후기 보여주기)
  - 개인 프로젝트를 진행했는데 테스트와 리팩토링하는 시간을 다 쏟아부었다.
  - [PR Link](https://github.com/CodeSoom/ConStu/pull/153)
- [x] 루비로 배우는 객체지향 디자인 Chapter 7 읽고 정리하기
  - 7장인 모듈을 통한 역할 공유를 진행하였다.
  - [PR Link](https://github.com/saseungmin/reading_books_record_repository/pull/31)

### 🎯 이번주 목표
- [x] 윈도우 사용하지 않고 개발 및 공부하기 (Only Mac)
- ~~코드숨 멤버쉽에 필요한 블로그 만들기~~
- ~~인수인계서 작성하기 / 마무리 잘하기~~
- [x] 퇴사 후 계획 가닥 잡기
- [x] 긍정적이게 생각하기 😤


### 🤔 공부하면서 배운것이 있다면?

#### 🎈개인 프로젝트를 진행하면서 배운것
- 오늘 테스트 코드 작성하는데에 있어서 시간을 많이 보냈다.
- 그래도 고민한만큼 성과가 있어서 만족스럽다. 이것저것 해보면서 함수를 mocking하는 방법을 좀 더 알게되었다.
- 또한, 테스트 코드도 리팩토링의 대상이라는 것을 명심하자.
- `mockReturnValueOnce`는 리턴 값을 어떻게 받을 것을 정해주는 것이다.
- 
```js
const data = jest.fn().mockReturnValueOnce(settings);

getStudyGroups.mockReturnValueOnce([{
  data,
  id: '1',
}]);
```

- `mockImplementationOnce`는 함수자체를 아예 mocking 할 수 있다.
- 해당 파일의 전체를 mocking 할려면 아래와 같이 해주고 `__mocks__` 파일 밑에에다 만들어준다.
- 그리고 필요한 함수들을 mocking 함수로 만들어준다.

```js
jest.mock('../util/utils');

// __mocks__/util/utils
export const dateToString = jest.fn((date) => date);
```

#### 🎈 루비로 배우는 객체지향 디자인 Chapter 7: 모듈을 통한 역할 공유
- 루비에서 `module`를 사용하는지 알게 되었다. 또한, 어떤 상황에서 사용해야 하는지 알게 되었다.

```rb
module Schedulable
  attr_writer :schedule

  def schedule
    @schedule ||= ::Schedule.new
  end

  def schedulable?(start_date, end_date)
    !scheduled?(start_date - lead_days, end_date)
  end

  def scheduled?(start_date, end_date)
    schedule.scheduled?(self, start_date, end_date)
  end

  # 이 모듈을 인클루드 하는 객체가 재정의할 수 있다.
  def lead_days
    0
  end
end
```

- 위와 같이 `Schedulable` 모듈을 만든다. 이렇게 모듈을 만들면 다른 객체들도 이 모듈을 사용해서 객체들은 중복 코드를 작성하지 않고도 이 역할을 수행할 수 있게 된다.


```ruby
class Bicycle
  include Schedulable

  def lead_days
    1
  end

  # ...
end

class Vehicle
  include Schedulable

  def lead_days
    3
  end

  # ...
end

class Mechanic
  include Schedulable

  def lead_days
    4
  end

  # ...
end

require 'date'
starting = Date.parse("2015/09/04")
ending = Date.parse("2015/09/10")

b = Bicycle.new
b.schedulable?(starting, ending)

v = Vehicle.new
v.schedulable?(starting, ending)

m = Mechanic.new
m.schedulable?(starting, ending)
```


- 추상화된 상위클래스에 포함된 모든 코드는 이 클래스를 상속받는 모든 하위클래스에도 적용될 수 있어야 한다.
- 리슼코프 치혼의 원칙
- 템플릿 메서드 패턴을 사용하자.
- `super`는 사용하지 말자. (대신 훅 메서드)


### ⚡ 아쉬운 점 및 회고
- 1월달이 벌써 지나갔다.. 아오 시간은 너무 빠르게 흐른다.. 짜증날 정도로.. 정말로..
- 오늘은 잠을 10시간 정도 잤다. 너무 많이 잤다. 반성..
- 내일부터 본격적인 취준생이다. 이번 한 주는 리플레쉬를 하면서 못했던 정리와 약속도 잡고 여유롭게 공부를 할 생각이다.
- 한 주 정도는 쉴만하다고 생각한다. 조금 지칠려한다. 하지만, 멈추지는 못할것이다. 또한, 이렇게 말하고 분명히 열심히 할 거 같긴하다. 조금은 여유를 갖고 싶은데..

### 🚀 내일 할 일
- 개인 프로젝트를 진행하자.(반응형 만들기 or 스터디 후기 보여주기)
- 루비로 배우는 객체지향 디자인 Chapter 8 읽고 정리하기

### 🎯 이번주 목표
- 알고리즘 공부 계획 세우기
- 리플레쉬 및 정리
- 긍정적이게 생각하기 😤