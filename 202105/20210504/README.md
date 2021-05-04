## 📆 2021-05-04(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 테스트 주도 개발로 배우는 객체 지향 설계와 실천 17, 18 읽기
  - [17장](https://github.com/saseungmin/reading_books_record_repository/tree/master/%ED%85%8C%EC%8A%A4%ED%8A%B8%20%EC%A3%BC%EB%8F%84%20%EA%B0%9C%EB%B0%9C%EB%A1%9C%20%EB%B0%B0%EC%9A%B0%EB%8A%94%20%EA%B0%9D%EC%B2%B4%20%EC%A7%80%ED%96%A5%20%EC%84%A4%EA%B3%84%EC%99%80%20%EC%8B%A4%EC%B2%9C/Chapter%2017)
  - [18장](https://github.com/saseungmin/reading_books_record_repository/tree/master/%ED%85%8C%EC%8A%A4%ED%8A%B8%20%EC%A3%BC%EB%8F%84%20%EA%B0%9C%EB%B0%9C%EB%A1%9C%20%EB%B0%B0%EC%9A%B0%EB%8A%94%20%EA%B0%9D%EC%B2%B4%20%EC%A7%80%ED%96%A5%20%EC%84%A4%EA%B3%84%EC%99%80%20%EC%8B%A4%EC%B2%9C/Chapter%2018)
- [x] 프로그래머스 코테 문제들 풀기
  - 두 문제를 풀었다.
  - [로또의 최고 순위와 최저 순위](https://github.com/saseungmin/daily_coding_dojo/tree/master/programmers/Level%201/%EB%A1%9C%EB%98%90%EC%9D%98%20%EC%B5%9C%EA%B3%A0%20%EC%88%9C%EC%9C%84%EC%99%80%20%EC%B5%9C%EC%A0%80%20%EC%88%9C%EC%9C%84)
  - [메뉴 리뉴열](https://github.com/saseungmin/daily_coding_dojo/tree/master/programmers/Level%202/%EB%A9%94%EB%89%B4%20%EB%A6%AC%EB%89%B4%EC%96%BC)
- [x] 우아한 테크 캠프 4기 지원서 작성
  - 작성중..

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] Do it TS 책 7장까지 읽기
- [x] 테스트 주도 개발로 배우는 객체 지향 설계와 실천 19장까지 읽고 스터디 참여
- [ ] 인프런 알고리즘 Section 10 풀기
- [x] 프로그래머스 코테 문제들 풀기
- [x] 우아한 테크 캠프 4기 지원하기

### 🤔 공부하면서 배운것이 있다면?
- 프로그래머스의 카카오 코테를 풀면서 다시 dfs 재귀를 일깨워주었다.
- 아래 문제는 모든 경우의 수를 찾아야 했던 거였는데 그러기 위해서 재귀를 사용했다.

```js
function solution(orders, course) {
  const answer = [];
  let check = [];
  const courseMap = new Map();

  const isIncludesCourse = checkCourseCount(course);

  function dfs(level, menu) {
    if (level === menu.length) {
      if (!isIncludesCourse(check)) {
        return;
      }

      let temp = '';

      for (let i = 0; i < check.length; i++) {
        if (check[i] === 1) {
          temp += menu[i];
        }
      }

      if (temp.length > 1) {
        const sortStr = temp.split('').sort().join('');

        if (courseMap.has(sortStr)) {
          courseMap.set(sortStr, courseMap.get(sortStr) + 1);
        }

        if (!courseMap.has(sortStr)) {
          courseMap.set(sortStr, 1);
        }
      }

      return;
    }

    check[level] = 1;
    dfs(level + 1, menu);
    check[level] = 0;
    dfs(level + 1, menu);
  }

    orders.forEach((order) => {
    const menu = order.split('');
    check = Array.from({ length: menu.length + 1 }, () => 0);

    dfs(0, menu);
  });
}
```

### ⚡ 아쉬운 점 및 회고
- 오늘을 할 것을 다했다. 하지만 시간이 왜 5시 40분이지
- 그리고 5월 5일인 것도 몰랐다. 오늘 쉬는 날이였구나.. 백수가 되니 시간 개념도 없어졌다.
- 어제 블로그 쓴걸 사람들이 어느정도 봐준거 같다.
- 내 코드숨 프로젝트에 star가 3개나 늘어 8개가 되었다. 소소하지만 그래도 기분이 좋다. 그리고 팔로워도 한명 늘었고, 바로 팔로우를 했다. 이런 소소한 성취감으로 즐겁게 개발하고 있다. 
- 앞으로 더 유지보수해서 스터디 사이드 프로젝트를 키워나가고 싶다. 아직 많이 많이 부족하다.
- 프로그래머스 카카오 level 2 문제를 풀었는데 어우 풀긴풀었는데 코드도 너무 길었고, 효율성도 하위권일 것이다. 그리고 무엇보다 시간이 너무 오래걸렸다.. 더 풀어보자.. 계속 풀어보자..

### 🚀 내일 할 일
- 테스트 주도 개발로 배우는 객체 지향 설계와 실천 19장 읽고 스터디 참여
- 프로그래머스 코테 문제들 풀기
- 우아한 테크 캠프 4기 지원하기.

### 🎯 이번주 목표
- Do it TS 책 7장까지 읽기
- 테스트 주도 개발로 배우는 객체 지향 설계와 실천 19장까지 읽고 스터디 참여
- 인프런 알고리즘 Section 10 풀기
- 프로그래머스 코테 문제들 풀기
- 우아한 테크 캠프 4기 지원하기
