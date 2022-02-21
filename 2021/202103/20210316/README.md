## 📆 2021-03-16(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
  - 로그인 폼과 회원가입 폼에 CSS를 적용시켰다.
  - [PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/62)
- [x] 오브젝트 책 9장 읽기
  - 오브젝트 책 9장 유연한 설계를 읽었다.
  - [PR Link](https://github.com/saseungmin/reading_books_record_repository/pull/45)
- [x] 알고리즘 공부
  - 해쉬 문제 두 문제를 풀었다.
  - Section 5에 solution 6, 7
  - [Link](https://github.com/saseungmin/daily_coding_dojo/tree/master/inflearn_algorism/section5)
- [x] 3월 우아한 세미나: ATDD 세미나 듣기
  - 참고 자료가 있는데 이걸 올려도 될지 모르겠다.
  - 링크 생략.

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 공부
- [x] 오브젝트 책 Chapter 9 까지 읽기 및 스터디 참여
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
- [x] 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- [x] 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기

### 🤔 공부하면서 배운것이 있다면?

#### 📌 오브젝트 Chapter 9을 읽으며..
- 작성 글 [참고](https://github.com/saseungmin/reading_books_record_repository/tree/master/%EC%98%A4%EB%B8%8C%EC%A0%9D%ED%8A%B8/Chapter%209)
- 개방-폐쇄 원칙은 소프트웨어 개체(클래스, 모듈, 함수 등등)는 확장에 대해 열려 있어야 하고, 수정에 대해서는 닫혀 있어야 한다.
- 개방-폐쇄 원칙을 수용하는 코드는 컴파일타임 의존성을 수정하지 않고도 런타임 의존성을 쉽게 변경할 수 있다.
- 유연하고 재사용 가능한 설계를 원한다면 객체와 관련된 두 가지 책임을 서로 다른 객체로 분리해야 한다.
- 의존성 주입이란 사용하는 객체가 아닌 외부의 독립적인 객체가 인스턴스를 생성한 후 이를 전달해서 의존성을 해결하는 방법이다.
- 의존성 주입은 의존성 해결 방법과 관련이 깊은데 방법으로는 생성자 주입, `setter` 주입, 메서드 주입이 있다.
- 의존성 역정 원칙이란 상위 수준의 모듈은 하위 수준의 모듈에 의존해서는 안되고 추상화는 구체적인 사항에 의존해서는 안 된다.
- 즉, 상위와 하위 수준의 모듈 둘 다 추상화에 의존해야 하고, 구체적인 사항은 추상화에 의존해야 한다.
- 숨겨진 의존성은 좋지 않다. 명시적인 의존성이 좋다. 가급적 의존성을 객체의 퍼블릭 인터페이스에 노출해야 한다.

#### 📌 Recoil를 사용한 ToDo 앱 만들기에서 배운것이 있다면..
- input에 대해서 Chrome의 autoComplete의 CSS를 수정하려면 다음과 같이 설정해줘야 한다.

```js
const AuthInputWrapper = styled.input`
  &:-webkit-autofill {
    border: 2px solid ${palette.twoTone[1]};
    transition: border-color .3s;
    box-shadow: 0 0 0px 1000px ${palette.twoTone[1]} inset;
    -webkit-box-shadow: 0 0 0px 1000px ${palette.twoTone[1]} inset;
    -webkit-text-fill-color: #5f5f5f;
    &:focus {
      border: 2px solid #5F4B8B;
    }
  }
`;
```

#### 📌 알고리즘 공부를 하며 배운 것은?
- `Map`을 복습하는 계기가 되었다.

```js
const map = new Map();
map.set('a', 'value');
map.has('a');
map.get('a');

// map에는 foreach 내장 메서드가 존재했다.
// 근데 기존 Object와 다른점은 value, key형식이다.
map.forEach((value, key) => {
  console.log(value, key);
});
for (const [key, value] of map.entries()) { // for of는 쓰지말자.
  console.log(value, key);
}

// 기존 Object
Object.entries(objects).forEach(([key, value]) => {
  console.log(key, value);
})
```

#### 📌 우아한 세미나 ATDD
- 생략.
- 자료를 공개해도 되는지 모르겠다.

### ⚡ 아쉬운 점 및 회고
- 오늘이 거의 최근들어 가장 만족스러운 날이였다!
- 할당한 양도 다채웠고, 시간낭비도 없었고, 심지어 우아한 세미나까지 들었다.
- 알고리즘 공부는 항상 느끼는 거지만, 시작은 너무 하기 싫은데 막상 문제 풀기 시작하면 나름 재밌다. 
- 특히 코테? 알고리즘 푸는 거는 안하는 거랑 하는 거랑은 차이가 너무 많이 난다. 역시 꾸준히 풀어야겠다.
- 내일도 오늘과 같은 내일이 되었으면!!
- TIL 끝!

### 🚀 내일 할 일
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 오브젝트 책 7,8,9장 복습 및 스터디 참여
- 알고리즘 공부

### 🎯 이번주 목표
- 알고리즘 공부
- 오브젝트 책 Chapter 9 까지 읽기 및 스터디 참여
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기
