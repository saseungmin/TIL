## 📆 2021-01-10 TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 객체지향의 사실과 오해 [Chapter 3 읽고 정리](https://github.com/saseungmin/reading_books_record_repository/pull/19)하기
  - Chapter 3: 타입과 추상화를 읽었다.
- [x] 이력서 수정하기
  - 이력서 쓰는 건 항상 어렵다.
- [x] 개인 프로젝트의 에디터에 이미지 넣는 로직 추가하기
  - 반은 성공 반은 실패.
  - 미리보기까지는 했는데.. 계속 찾아보다가 시간을 날렸다.
- [ ] 월요일을 위해서 적당히 하고 쉬기 제발.
  - 실패! 실패! 실패! 아오


### 🤔 공부하면서 배운것이 있다면?

#### 🎈 객체지향의 사실과 오해 Chapter 3
- 객체에서의 추상화를 알았다. 추상화를 통해 현실의 복잡성을 극복한다.

> 어떤 양상, 세부 사항, 구조를 좀 더 명확하게 이해하기 위해 특정 절차나 물체를 의도적으로 생략하거나 감춤으로써 복잡도를 극복하는 방법이다.   
> 복잡성을 다루기 위해 추상환느 두 차원에서 이뤄진다.   
> - 첫 번째 차원은 구체적인 사물들 간의 **공통점은 취하고 차이점은 버리는 일반화**를 통해 단순하게 만드는 것이다.
> - 두 번째 차원은 **중요한 부분을 강조하기 위해 불필요한 세부 사항을 제거**함으로써 단순하게 만드는 것이다.
> 
> 모든 경우에 추상화의 목적은 **복잡성을 이해하기 쉬운 수준으로 단순화하는 것**이라는 점이다.

- 개념의 세 가지 관점

> - 심볼(symbol): 개념을 가리키는 간략한 이름이나 명칭
> - 내연(intension): 개념의 완전한 정의를 나타내며 내연의 의미를 이용해 객체가 개념에 속하는지 여부를 확인할 수 있다.
> - 외연(extension): 개념에 속하는 모든 객체의 집합(set)

- 분류는 추상화를 위한 도구이다.
- 타입은 개념이다.

> 타입은 개념과 동일하다. 따라서 타입이란 우리가 인식하고 있는 다양한 사물이나 객체에 젹용할 수 있는 아이디어나 관념을 의미한다.   
> 어떤 객체에 타입을 적용할 수 있을 때 그 객체를 타입의 인스턴스라고 한다.   
> 타입의 인스턴스는 타입을 구성하는 외연인 객체 집합의 일원이 된다.

- 일반화/특수화 관계
- 슈퍼타입과 서브타입
- 그래서 결국 타입은 추상화다
- 동적 모델과 정적 모델

#### 🎈 개인프로젝트를 진행하면서 알게된 점
- react-draft-wysiwyg을 사용한 이미지 업로드를 배웠다. 이미 만들어져있는 에디터라 더 적용하기가 힘든거 같다.
- 뭔가 자꾸 안된다..

```js
  function uploadImageCallBack(file) {
    return new Promise(
      (resolve, reject) => {
        const reader = new FileReader();
        reader.onload = (e) => {
          resolve({ data: { link: e.target.result } });
        };
        reader.onerror = (e) => reject(e);
        reader.readAsDataURL(file);
      },
    );
  }
```

- `URL.createObjectURL`를 알았다. ([MDN 참고](https://developer.mozilla.org/ko/docs/Web/API/URL/createObjectURL))
- `createObjectURL()`을 매번 호출할 때마다 새로운 객체 URL을 생성한다. 각각의 URL을 더는 쓰지 않을 땐 `URL.revokeObjectURL()`을 사용해 하나씩 해제해줘야 한다.
- 최적의 성능과 메모리 사용량을 위해서, 객체 URL을 해제해도 안전하다면 그렇게 해야 한다.

### ⚡ 아쉬운 점
- 늦잠을 잤다. 오전시간을 모두 날렸다. 어제 늦게 잤다.
- 오늘은 조금만 공부하고 쉴려했는데 그렇게 못했다. 벌써 오후 11시 20분이다. 내일을 위해서라도 휴식을 취했어야 했는데 그러지 못했다.
- 항상 그래야겠다 말하지만 못하고 있다.
- 개인 프로젝트 진행을 얼마 못했다.

### 🚀 내일 할 일 (퇴근 후)
- 객체지향의 사실과 오해 Chapter 4 읽고 정리하기
- 코드숨 멤버쉽 신청하기..? (미정)
- 개인 프로젝트 진행하기 또는 Pro Git 읽기
- 긍정적이게 생각하기 😤