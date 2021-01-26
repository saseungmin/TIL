## 📆 2021-01-26(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 다음 스터디인 루비로 배우는 객체지향 디자인 책 Chapter 5 읽고 정리하기
  - Chapter 5 장인 오리 타입으로 비용 줄이기를 읽었다. ([PR Link](https://github.com/saseungmin/reading_books_record_repository/pull/29))
- [ ] 코드숨 멤버쉽에 사용할 블로그 만들기
  - 못했다.

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 윈도우 사용하지 않고 개발 및 공부하기 (Only Mac)
- [ ] 코드숨 멤버쉽에 필요한 블로그 만들기
- [x] 인수인계서 작성하기 / 마무리 잘하기
- [ ] 퇴사 후 계획 가닥 잡기
- [x] 긍정적이게 생각하기 😤

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 루비로 배우는 객체지향 디자인 Chapter 5
- 오리 타입에 대해 조금이나마 알게 되었다.
- 의존성을 제거하기 위해서 사용된다. 
- 의존성이 존재하는 메서드는 하나의 목적을 갖고 있기 때문에 같은 목표를 이루기 위해 협업하는 객체일 수 밖에 없다.
- 다음과 같이 의존성을 제거해줄 수 있다. 
```ruby
class Trip
  attr_reader :bicycles, :customers, :vehicle

  def prepare(perparers)
    perparers.each {|perparer|
      perparer.prepare_trip(self)}
  end
end

# 모든 preparer가 오리 타입일 때
# 이 객체들은 모두 prepare_trip 메서드를 이해한다.
class Mechanic
  def prepare_trip(trip)
    trip.bicycles.each {|bicycle|
      prepare_bicycle(bicycle)}
  end

  # ...
end

class TripCoordinator
  def prepare_trip(trip)
    buy_food(trip.customers)
  end

  # ...
end

class Driver
  def prepare_trip(trip)
    vehicle = trip.vehicle
    gas_up(vehicle)
    fill_water_tank(vehicle)
  end

  # ...
end
```

- 오리 타입을 사용하면 추상적이어지고, 손쉬운 확장성을 제공한다.
- 기존 코드를 수정하지 않고도 애플리케이션에서 새로운 행동을 이끌어낼 수 있다.
- 오리 타입은 퍼블릭 인터페이스를 클래스로부터 분리해낸다. 그리고 객체가 누구인지가 아니라 객체가 무엇을 하는지에 따라 가상의 타입을 만들어 낸다.
- 추상화에 의존할 때 애플리케이션의 위험성은 줄어들고 유연성은 증가한다.


### ⚡ 아쉬운 점 및 회고
- 얼른 블로그를 만들어야 되는데 자꾸 미루게 된다. 얼른 해야되는데.. 우선순위를 어떻게 잡고 해야할지 모르겠다.
- 평일에 공부할 수 있는 시간이 적게는 3시간에서 많게는 5시간 정도이다. 이 정도 시간으로 평일에 많은 것을 할 수는 없는 거 같다. 시간 분배를 잘해야 된다.
- 어짜피 금요일이면 이제 백수라 시간도 많으니... 늦었다. 이미. 퇴사 준비나 잘하고 퇴사 후 계획이나 잘 세우자.
- 내일 스터디를 위해서 루비로 배우는 객체지향 디자인 책을 다시 복습해야겠다.

### 🚀 내일 할 일(퇴근 후)
- 루비로 배우는 객체지향 디자인 스터디 참여 및 참여 전 복기
- 코드숨 멤버쉽에 사용할 블로그 만들기 OR 개인 프로젝트(반응형)

### 🎯 이번주 목표
- 윈도우 사용하지 않고 개발 및 공부하기 (Only Mac)
- 코드숨 멤버쉽에 필요한 블로그 만들기
- 인수인계서 작성하기 / 마무리 잘하기
- 퇴사 후 계획 가닥 잡기
- 긍정적이게 생각하기 😤