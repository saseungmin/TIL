## 📆 2021-01-22(일) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 다음 스터디인 루비로 배우는 객체지향 디자인 책 Chapter 3 읽고 정리하기
  - Chapter 3인 의존성 관리하기를 읽었다.([PR Link](https://github.com/saseungmin/reading_books_record_repository/pull/27))
- [x] 개인 프로젝트 진행하기 (반응형으로 만들기)
  - 소개 페이지의 서브인포 정보 부분을 반응형으로 만들었고, 메인페이지에서 깨지는 부분을 수정했다.([PR Link](https://github.com/CodeSoom/ConStu/pull/150))
- [ ] Pro Git Chapter 3 진행하기?
  - 진행하지 못했다.
- [x] 긍정적이게 생각하기😤
  - 만족!

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 윈도우 사용하지 않고 개발 및 공부하기 (Only Mac)
  - 한주동안 사용하니까 이제는 맥이 더 편한 거 같다.
  - 앞으로도 계속 사용해야겠다!!
- [ ] 코드숨 멤버쉽 블로그 만들기
  - 다음주까지 만들자 2월부터 본격적으로 시작이다.
- [ ] 퇴사 후 계획 가닥 잡기
  - 이것도 다음주 금요일 퇴사니까 얼른 계획잡아보자.

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 루비로 배우는 객체지향 디자인 Chapter 3
- 의존성에 대한 부분을 배웠다.
- Chapter 2장의 예제를 그대로 설명하였다. 이어져서 설명해주니 확실히 좋았다.
- 각 클래스가 자신이 해야 하는 일을 하기 위한 최소한의 지식만을 알고 그 외에는 아무것도 모르도록 의존성을 관리해야 한다.
- 인자 순서에 대한 의존성 제거하기 위해서 초기화 인자로 해시를 사용했다.
- 루비에서 기본값을 사용하는 방법에 대해 배웠다. (3가지)

```ruby
# ||를 이용한 기본값 설정
def initialize(args)
  @chainring = args[:chainring] || 40
  @cog = args[:cog] || 18
  @wheel = args[:wheel]
end

# fetch를 이용한 기본값 설정
def initialize(args)
  @chainring = args.fetch(:chainring || 40)
  @cog = args.fetch(:cog || 18)
  @wheel = args[:wheel]
end

# default 해시를 merge해서 기본값을 설정
def initialize(args)
  args = defaults.merge(args)
  @chainring = args[:chainring]
  # ...
end

def defaults
  { :chainring => 40, :cog => 18 }
end
```

- 메서드를 수정할 수 없는 상황이 있을 때 순서가 고정된 인자들을 수정할 때는 다음과 같이 외부 인터페이스와 연결되는 지점, 인스턴스를 생성하는 지점을 하나의 메서드로 감싸준다.

```ruby
# Gear가 외부 프레임워크의 한 부분일 때
module SomeFramework
  class Gear
    attr_reader :chainring, :cog, :wheel
      def initialize(chainring, cog, wheel)
        @chainring = chainring
        @cog = cog
        @wheel = wheel
      end
    # ...
  end
end

# 외부 인터페이스를 감싸는 모듈을 만들어 변화를 받아들일 수 있도록 하자.
module GearWrapper
  def self.gear(args)
    SomeFramework::Gear.new(args[:chainring],
                            args[:cog],
                            args[:wheel])
  end
end

# 해시를 통해 Gear 인스턴스를 생성할 수 있게 되었다.
GearWrapper.gear(
  :chainring => 52,
  :cog => 11,
  :wheel => Wheel.new(26, 1.5)
).gear_inches
```

- `GearWrapper` 모듈은 오로지 다른 클래스의 인스턴스를 생성하기 위해서만 존재


#### 🎈 개인 프로젝트를 진행하면서 알게 된 점

- `flex`가 다음처럼 되어 있을 때 어떤 속성을 의미하는지 알게 되었다.([참고](https://developer.mozilla.org/ko/docs/Web/CSS/flex))
```css
flex: 1 1 100px;

/* flex-item 요소가, flex-container 요소 내부에서 할당 가능한 공간의 정도를 선언 */
flex-grow: 1; 
flex-shrink: 1; /* flex-item 요소의 flex-shrink 값을 설정하는 속성입니다. */ 
flex-basis: 100px; /* flex 아이템의 초기 크기를 지정 */
```

- `facepaint`를 사용할 때 `object` 방식으로만 가능한줄 알았지만, 공식문서를 참고한 결과 Styled-component 방식으로도 가능했다.
- 하지만 `mq`를 사용하는 곳은 오브젝트 방식으로만 사용가능했다.

```jsx
const mq = facepaint([
  '@media(min-width: 1024px)',
  '@media(min-width: 1150px)',
]);

const DateTimeStatusWrapper = styled.div`
  ${mq({
    fontSize: ['1.5vw', '0.8rem', '1.1rem'],
    height: ['30px', '30px', '40px'],
  })};

  font-weight: 600;
  font-family: 'Gamja Flower', cursive;
`;
```

- 한가지 궁금한 점이 있는데 분명 반응형으로 만들었고 화면을 줄이면 제대로 작동하는데 모바일 버전으로 바꿔서 보면 왜 크게 나오는지 모르겠다.. 무슨 문제인지 firebase의 자체적인 크기가 크게 잡고있는건지 .. 이건 내일 윤석님께 질문해봐야겠다.

### ⚡ 아쉬운 점 및 회고
- 계획했던 것을 다 못했다. 하지만, 만족한다.
- 내일은 출근하는데 너무 늦게잔다. 일찍잘려했지만, 삽질하니까 시간이 너무 많이 지나갔다. 시간을 보면서 하자.
- 이번주에 하기로 했던 블로그 만들기와 퇴사후 계획 가닥 잡는 것을 하나도 못 지켰다. 다음주 주말까지 해보도록 노력해야겠다. 자꾸 우선순위에서 밀려 안하게 되는 거 같다.
- 내일을 위해 얼른 자야겠다. 다음주는 회사에서의 마지막 한주이니.. 인수인계서도 작성해야되고 할게 많다.

### 🚀 내일 할 일
- 다음 스터디인 루비로 배우는 객체지향 디자인 책 Chapter 4 읽고 정리하기
- 개인 프로젝트 진행하기 (반응형으로 만들기)

### 🎯 다음주 목표
- 윈도우 사용하지 않고 개발 및 공부하기 (Only Mac)
- 코드숨 멤버쉽에 필요한 블로그 만들기
- 인수인계서 작성하기 / 마무리 잘하기
- 퇴사 후 계획 가닥 잡기
- 긍정적이게 생각하기 😤