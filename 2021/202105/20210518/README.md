## 📆 2021-05-18(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 린 UX 책 3장 읽기
  - [Chapter 3](https://github.com/saseungmin/reading_books_record_repository/tree/master/LEAN-UX/Part%202/Chapter%203)
- [x] 인프런 알고리즘 Section 10 풀기
  - [동전교환](https://github.com/saseungmin/daily_coding_dojo/tree/master/inflearn_algorism/section10/solution4)
  - [최대점수 구하기](https://github.com/saseungmin/daily_coding_dojo/tree/master/inflearn_algorism/section10/solution5)
- [x] 코드숨 프로젝트 Dark 모드 적용
  - [모달창들과 스터디 승인 상태 및 스터디 모집 기간 상태 dark theme 적용](https://github.com/CodeSoom/ConStu/pull/190)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] Do it TS 책 9장까지 읽고 스터디 참여
- [x] 린 UX 책 4장까지 읽고 스터디 참여
- [x] 인프런 알고리즘 Section 10 풀기
- [ ] 프로그래머스 코테 문제들 풀기
- [x] 코드숨 프로젝트 Dark 모드 적용
- [ ] 코어 자바스크립트 마무리 짓기 
- [ ] 우아한 테크러닝 4기 신청하기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 LEAN UX 3장
- [Link](https://github.com/saseungmin/reading_books_record_repository/tree/master/LEAN-UX/Part%202/Chapter%203)

#### 🎈 dp 알고리즘 (냅색 알고리즘)

```js
function solution(m, coins) {
  // 1000으로 초기화
  const dy = Array.from({ length: m + 1 }, () => 1000);

  dy[0] = 0;

  coins.forEach((coin) => { // [1, 2, 5]
    // 코인 이전 for문은 돈이 모자르기 떄문에 i의 시작은 1, 2, 5부터
    for (let i = coin; i <= m; i++) {
      // 현재 개수와 이전 돈 위치의 코인의 개수 + 1한 값중 작은 값을 치환
      // 이유는 만약 coin이 2이고 i는 6일 때
      // dy[6]와 dy[4]위치를 비교한다. 이 둘의 인덱스 차이는 2가 되고
      // coin의 수가 2이기 때문에 dy[4] 위치에서 + coin을 할 수 있게 된다.
      // 그리고 + 1을 해줌으로써 딱 맞아 떨어지게 6이라는 값으로 코인의 개수를 찾게 된다.
      // coin이 5이고 i가 5인 경우도 마찬가지다
      // 둘의 차이는 0이 되고 현재 dy[i]는 5이기 때문에 0의 값에서 5를 더하면 dy[5]번째
      // 값에 5를 더함으로써 거스름돈 개수를 찾을 수 있게 된다.
      dy[i] = Math.min(dy[i], dy[i - coin] + 1);
    }

    console.log(dy); // 아래 참고
  });

  return dy[m];
}
```

### ⚡ 아쉬운 점 및 회고
- 적은 공부시간? 아니다. 오늘 많이 했다. 나름..
- 알고리즘 코테 공부를 어떻게 해야할지 잘 모르겠다. 내가 열심히 안하는 건지.. 사고력이 딸리는 건지.. 응용을 못하는건지.. 각자의 알고리즘의 원리부터 알고 풀여아 할텐데 그렇지 못하고 있는 거 같다.
- 학교때 공부했던 알고리즘 책을 다시 펼처봐야할 거 같다. 다 읽는다는건 아니고 중요하게 생각드는 부분..
- 예를 들어 그리디, dp, 다익스트라, 벨만포드.. 등등.. 한 번 다시 읽어봐야할 거 같다. 다 까먹었다.
- 코드숨에서 했던 프로젝트는 dark theme 적용까지 끝났다. 마지막으로 적용할 부분은 content loader 부분이다. 이 부분을 다시 반응형에 dark theme까지 적용하면 dark theme 적용은 끝난다.
- 다음으로 적용해볼 것들은 너무 많다. 채팅기능도 만들고 싶고, 내 정보 페이지, e2e 테스트를 위한 CodeceptJS 적용, 기타 이슈사항들.. 계속 키워나가볼것이다.
- 맨날 같은 일상이 반복이라 내일 쉬는날 인것도 몰랐다. 내일도 공부해야지.ㅜ

### 🚀 내일 할 일
- 린 UX 책 4장 읽고 스터디 참여
- 프로그래머스 코테 문제 풀기
- 코드숨 프로젝트 Dark 모드 적용

### 🎯 이번주 목표
- Do it TS 책 11장까지 읽고 스터디 참여
- 린 UX 책 4장까지 읽고 스터디 참여
- ~~인프런 알고리즘 Section 10 풀기~~
- 프로그래머스 코테 문제들 풀기
- 코드숨 프로젝트 Dark 모드 적용
- 코어 자바스크립트 마무리 짓기
- 우아한 테크러닝 4기 신청하기
