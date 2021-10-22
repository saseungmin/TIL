## 📆 2021-10-22(금) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 클린 코드 2장 읽기
  - [PR](https://github.com/saseungmin/reading_books_record_repository/pull/157)
- [x] 건강검진 접수

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 클린 코드 1, 2장 읽기
- [ ] ReScript ToDo 앱 CSS 적용 작업
- [ ] 테스트와 TDD에 대한 정리
- [ ] 개인 프로젝트 한피쳐씩 틈틈히
- [x] Kasa Blog 구현에 대한 gatsby 공부

### 🤔 공부하면서 배운것이 있다면?

#### given2 with ts
- given2를 typescript를 사용하여 global로 사용할 때, given type을 인식하지 못한다. 그래서 `global.d.ts`로 declare 정의를 해줘야한다.

```ts
declare const given: {
  <T = any>(key: string, callback: () => T): T
  [key: string]: any
};
```

- import를 해주지 않아도 global로 인식하여 사용가능

```ts
  context('모바일인 경우', () => {
    given('isMobile', () => true);

    describe('수정 날짜 파이프(span)', () => {
      it('display 속성이 "none"이어야 한다', () => {
        renderDisclosureItem({ disclosure: DISCLOSURE_FIXTURE });

        expect(screen.getByTestId('test-span')).toHaveStyle('display: none');
      });
    });
  });

  context('모바일이 아닌 경우', () => {
    given('isMobile', () => false);

    describe('수정 날짜 파이프(span)', () => {
      it('display 속성이 "inline"이어야 한다', () => {
        renderDisclosureItem({ disclosure: DISCLOSURE_FIXTURE });

        expect(screen.getByTestId('test-span')).toHaveStyle('display: inline');
      });
    });
  });
```

#### [클린코드 Chapter 2](https://saseungmin.github.io/reading_books_record_repository/docs/clean/clean-code/chapter-2)

### ⚡ 아쉬운 점 및 회고
회사 코드에 테스트 코드가 작성안되어 있는 부분을 작성했다. 모든 곳에 테스트 코드를 작성해서 레거시 코드를 제거하자. 브랜드 사이트는 금방 테스트코드를 다 작성할 수 있을 듯하다.   

오늘 드디어 건강검진을 접수했는데 분명 12월달밖에 없다고 했었는데 운좋게 다음주에 바로 건강검진을 받을 수 있게되었다.   

주말에는 회사 교육비 지원으로 결제한 강의를 들어야겠다!   

집에서 재택을 했는데 역시나 회사에 출근했을때보다 더 많이 공부하고 일했다. 나는 출근이 더 좋은 거 같은...

### 🚀 내일 할 일
- 인프런 강의 듣기
- 개인 프로젝트 한피쳐씩 틈틈히

### 🎯 이번주 목표
- ~~클린 코드 1, 2장 읽기~~
- ReScript ToDo 앱 CSS 적용 작업
- ~~코어 자바스크립트 스터디 진행하기~~
- 테스트와 TDD에 대한 정리
- 개인 프로젝트 한피쳐씩 틈틈히
- ~~Kasa Blog 구현에 대한 gatsby 공부~~
- 인프런 강의 듣기
