## 📆 2021-01-30(토) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 개인 프로젝트를 진행하자.(반응형 만들기 or 스터디 후기)
  - 스터디 후기 작성에 대한 firestore에 저장?하는 로직 추가.
  - [PR Link](https://github.com/CodeSoom/ConStu/pull/152)
- [x] 루비로 배우는 객체지향 디자인 Chapter 6 읽고 정리하기
  - Chapter 6장을 읽고 정리했다. ([PR Link](https://github.com/saseungmin/reading_books_record_repository/pull/30))

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 윈도우 사용하지 않고 개발 및 공부하기 (Only Mac)
- ~~코드숨 멤버쉽에 필요한 블로그 만들기~~ (완료)
- ~~인수인계서 작성하기 / 마무리 잘하기~~ (완료)
- [x] 퇴사 후 계획 가닥 잡기
  - 가닥을 잡는중..
- [x] 긍정적이게 생각하기 😤
  - 흠.. 나쁘지 않다.

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 루비로 배우는 객체지향 디자인 Chapter 6: 상속을 이용해 새로운 행동 얻기
- 상속 관계를 만드는 데는 높은 비용이 든다. 이 비용을 최소화하기 위해서 하위클래스가 추상 클래스를 필요로 하기 바로 직전에 추상 클래스를 만든다.
- 하위클래스의 코드를 상위클래스로 올리는 것이 상위클래스의 코드를 하위클래스로 내리는 것보다 수월하다.
- 새로운 상속 관계를 만드는 리팩터링을 진행할 때의 기본 원칙은 **구체적인 것을 내리기보다는 추상적인 것을 끌어올리는 방식을 취해야한다.**
- **템플릿 메서드 패턴이란 기본 구조를 상위클래스가 정의하고 상위클래스에서 메시지를 전송하여 하위 클래스의 특수한 값을 얻는 기술**
- `super`를 전송하는 대신 다음과 같이 훅 메시지를 전송할 수 있다.

```ruby
class Bicycle
  attr_reader :size, :chain, :tire_size

  def initialize(args={})
    @size = args[:size]
    @chain = args[:chain] || default_chain
    @tire_size = args[:tire_size] || default_tire_size

    post_initialize(args) # 훅
  end

  def post_initialize(args)
    nil
  end
  # ...
end

class RoadBike < Bicycle
  def post_initialize(args)
    @tape_color = args[:tape_color]
  end
  # ...
end
```
- 훅 메서드를 이용하면 하위클래스가 추상화 알고리즘을 알지 못해도 자신의 특수한 내용을 추가할 수 있다.
- `super`를 전송하지 않아도 되기 때문에 상속 관계의 층위 사이의 결합이 느슨해진다.

#### 🎈 개인프로젝트를 하면서 배운점
- firebase의 fireStore에 스터디 리뷰를 저장할려고 했었다. fireStore에 스터디 리뷰에 필드가 처음엔 존재하지 않는다.
- 그래서 필드를 생성하고 어떻게 저장할지에 대해서 찾아보게 되었다. 이전까지는 필드가 항상 존재했었고 문제가 되지 않았다.
- 아래의 코드에서 `set`을 사용하는 것은 필드를 생성하는 것이다. 기본적인 `set`은 다시 `set`을 하게되면 기존의 값은 덮어씌여지게 된다.
- `set`의 두번째 인자에 `{ merge: true }`값을 주면 기존의 값이랑 병합을 해준다.
- 하지만, 계속 시도해보았지만 병합이 안되었다. 
- 그래서 아래의 예제는 배열의 값을 추가하는 것이기 때문에 `fireStore.FieldValue.arrayUnion`사용하였더니 병합을 할 수 있게 되었다.
```js
export const postUpdateStudyReview = async ({ id, review }) => {
  const group = db.collection('groups').doc(id);

  await group.set({
    reviews: fireStore.FieldValue.arrayUnion(review),
  }, { merge: true });
};
```

- `set`과 `update`의 차이점은 `set`은 필드가 존재하지 않으면 생성한다. 하지만 `update`는 필드가 존재하지 않으면 오류가 발생한다.

```js
export const updatePostParticipant = async ({ id, user }) => {
  const group = db.collection('groups').doc(id);

  await group.update({
    participants: fireStore.FieldValue.arrayUnion(user),
  });
};
```

### ⚡ 아쉬운 점 및 회고
- 퇴사를 해서 그런가 마음이 조금 무거운 하루였다. 이제 백수라는 생각에 조금은 조급해지는거 같다.
- 오늘은 주말이라 여유롭게 공부를 하려고 했지만, 그마저도 잘 안된거 같다. 마음의 여유를 갖는 힘을 얻고 싶다. 어떻게 하는 걸까..?
- 오늘의 계획은 다 지킨 거 같아서 만족스럽다.

### 🚀 내일 할 일
- 개인 프로젝트를 진행하자.(반응형 만들기 or 스터디 후기 보여주기)
- 루비로 배우는 객체지향 디자인 Chapter 7 읽고 정리하기

### 🎯 이번주 목표
- 윈도우 사용하지 않고 개발 및 공부하기 (Only Mac)
- ~~코드숨 멤버쉽에 필요한 블로그 만들기~~
- ~~인수인계서 작성하기 / 마무리 잘하기~~
- 퇴사 후 계획 가닥 잡기
- 긍정적이게 생각하기 😤