## 📆 2021-01-23(토) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 다음 스터디인 루비로 배우는 객체지향 디자인 책 Chapter 2 읽고 정리하기
  - Chapter 2: 단일 책임 원칙을 따르는 클래스 디자인하기([PR Link](https://github.com/saseungmin/reading_books_record_repository/pull/26))
- [x] 개인 프로젝트 진행하기 (반응형으로 만들기)
  - 진행하였지만, 오늘도 역시 삽질이 많았다.([PR Link](https://github.com/CodeSoom/ConStu/pull/149))
- [ ] 코드숨 멤버쉽에 필요한 블로그랑 퇴사 후 계획 가닥 잡기
  - 실패.
  - 많은 삽질로 인해 시간 분배를 못했다.
- [x] 긍정적이게 생각하기😤
  - 즐거운 주말은 긍정적인 법이지!

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 윈도우 사용하지 않고 개발 및 공부하기 (Only Mac)
- [ ] 코드숨 멤버쉽 블로그 만들기
- [ ] 퇴사 후 계획 가닥 잡기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 루비로 배우는 객체지향 디자인 Chapter 2
- 수정하기 쉬다는 의미는 수정이 예상치 못한 부작용을 낳지 않는다. 요구사항이 조금 변했을 때 연관된 코드들을 조금만 수정하면 된다. 현재 코드를 다시 사용하기 쉽다.
- 그러기 위해서는 코드는 투명하고 적절하며 사용가능해야 되고, 모법이 되야 된다.
- 클래스는 최대한 작으면서 하나의 책임만 있어야 한다.
- 단일 책임 원칙이 중요한 이유는 재사용할 수 있다.
- 클래스 안에 모든 것들이 하나의 핵심 목표와 연관되어 있을 때 이 클래스는 **강하게 응집되어 있다**고 할수 있고 하나의 책임만을 갖고 있다고 말할 수 있다.
- 루비에서 변수를 메서드로 감싸는 방법으로 캡슐화된 메서드를 쉽게 만들 수 있도록 `attr_reader`를 제공한다.

```ruby
class Gear
  attr_reader :chainring, :cog
  def initialize(chainring, cog)
    @chainring = chainring
    @cog = cog
  end

  def ratio
    chainring / cog.to_f
  end
end
```

`Struct`는 명시적으로 클래스를 만들지 않고도 엑세서 메서드를 이용해 여러 어트리뷰트들을 묶어내는 편리한 방법이라고 정의한다.

```ruby
class RevealingReferences
  attr_reader :wheels
  def initialize(data)
    @wheels = wheelify(data)
  end

  def diameters
    wheels.collect {|wheel|
      wheel.rim + (wheel.tire * 2)}
  end
  
  Wheel = Struct.new(:rim, :tire)
  def wheelify(data)
    data.collect {|cell|
      Wheel.new(cell[0], cell[1])}
  end
end
```

- 모든 곳에 단일 책임 원칙을 강제하는 방법으로 메서드에서 추가적인 책임을 뽑아내고, 클래스의 추가적인 책임을 격리시켜 놓는다.


```ruby
class Gear
  attr_reader :chainring :cog, :wheel
  def initialize(chainring, cog, wheel=nil)
    @chainring = chainring
    @cog = cog
    @wheel = wheel
  end

  def ratio
    chainring / cog.to_f
  end

  def gear_inches
    ratio * wheel.diameter
  end
end


class Wheel
  attr_reader :rim, :tire
  def initialize(rim, tire)
    @rim = rim
    @tire = tire
  end

  def diameter
    rim + (tire * 2)
  end

  def circumference
    diameter * Math::PI
  end
end

@wheel = Wheel.new(26, 1.5)
puts @wheel.circumference
# 91.1061...

puts Gear.new(52, 11, @wheel).gear_inches
# 137.0909090..

puts Gear.new(52, 11).ratio
# 4.727272...
```

#### 🎈 개인 프로젝트를 진행하면서 알게된 점
- `emotion-js`의 `facepaint`를 사용하여 반응형을 구현중이다.
- 아직도 솔직히 어떻게 해야될지 잘 모르겠지만. 사용법은 조금은 익혔다. 

```js
import facepaint from 'facepaint';

const mq = facepaint([
  '@media(min-width: 767px)',
  '@media(min-width: 1024px)',
]);

const StudyGroupWrapper = styled.div(() => mq({
  margin: ['1rem 0px 0px 0px', '.5rem', '1rem'],
  width: ['100%', 'calc(50% - 2rem)', '19rem'],
}));
```

- 위와 같이 설정해주면 `767px`보다 작으면 배열의 첫번째, `767px`과 `1024px`사이은 배열의 두번째, `1024px` 보다 크면 마지막 배열이 적용된다.

### ⚡ 아쉬운 점 및 회고
- 계획했던 것들을 못했다. 1주일의 계획으로 세웠던 것을 오늘 했어야 했지만 할 수가 없었다.
- 루비로 배우는 객체지향 2장을 읽으면서 확실히 이론적으로 설명하는 거보다 코드로 보며 설명을 해주니 좀 더 이해하기 쉬웠던 거 같다. 하지만 이게 그 전 책인 객체지향의 사실과 오해를 읽어서 그런게 아닐까싶다. 루비는 다뤄본적은 없지만 어느정도 이해는 가서 읽는데 문제는 없다.
- 오늘 잠을 많이 잤다. 잠을 줄였어야 했지만 주말은 인정
- 해본적없던 반응형을 해볼려니 쉽지않았다. 하지만 어제보단 좋아졌으니 만족한다.

### 🚀 내일 할 일
- 다음 스터디인 루비로 배우는 객체지향 디자인 책 Chapter 3 읽고 정리하기
- 개인 프로젝트 진행하기 (반응형으로 만들기)
- Pro Git Chapter 3 진행하기?
- 긍정적이게 생각하기😤

### 🎯 이번주 목표
- 윈도우 사용하지 않고 개발 및 공부하기 (Only Mac)
- 코드숨 멤버쉽에 필요한 블로그 만들기
- 퇴사 후 계획 가닥 잡기