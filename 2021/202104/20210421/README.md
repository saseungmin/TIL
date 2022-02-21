## 📆 2021-04-21(수) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 알고리즘 Section8 풀기
  - [순열 구하기](https://github.com/saseungmin/daily_coding_dojo/tree/master/inflearn_algorism/section8/solution10) 
  - [팩토리얼](https://github.com/saseungmin/daily_coding_dojo/tree/master/inflearn_algorism/section8/solution11)
  - [조합의 경우수](https://github.com/saseungmin/daily_coding_dojo/tree/master/inflearn_algorism/section8/solution12)
- [x] 테스트 주도 개발로 배우는 객체 지향 설계와 실천 9장 읽고 다시 정리 및 스터디 참여
  - [Chapter 9 PR](https://github.com/saseungmin/reading_books_record_repository/pull/64)
- [ ] 코드숨에서 진행했던 프로젝트 더 꾸며보기 (반응형)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 인프런 알고리즘 Section 8 풀기
- [ ] 기술 면접 준비 스터디 관련 준비 및 스터디 참여
- [ ] 코드숨에서 진행했던 프로젝트 더 꾸며보기 (반응형)
- [x] 테스트 주도 개발로 배우는 객체 지향 설계와 실천 9장까지 읽고 스터디 참여
- [ ] Core JavaScript 4장 읽기

### 🤔 공부하면서 배운것이 있다면?
- 재귀함수에서의 메모이제이션하는 방법을 알게되었다. 굉장히 유용하다고 생각이 들었다.
- 재귀함수를 사용할 때 스택이 쌓이고 점점 커지면 시간복잡도에 있어서 굉장히 오래걸릴 수 있다. 그 부분을 이미 재귀를 수행한 값들을 저장시켜놓고 다음번에 해당 값이 존재하면 그 값을 반환시켜주기만하여 다시 재귀를 돌지 않아도된다. 이렇게 시간복잡도를 줄일 수 있엇따.

```js
// 이 2차원배열에 해당 값을 저장시킨다.
const dynamic = Array.from(Array(n + 1), () => Array(r + 1).fill(0));

function dfs(a, b) {
  if (dynamic[a][b] > 0) { // 캐시 히트?
    return dynamic[a][b];
  }

  if (a === b || b === 0) {
    return 1;
  }

  // 값을 저장
  dynamic[a][b] = dfs(a - 1, b - 1) + dfs(a - 1, b);

  return dynamic[a][b];
}
```

### ⚡ 아쉬운 점 및 회고
- 오늘은 나쁘지 않은 하루였지만, 역시 만족스럽다할 순 없었다. 이유는 공부를 늦게 시작했다는점. 그렇기 때문에 생각보다 많은 양을 할 수 없었다. 그리고 동생 하는 걸 도와주다보니 시간이 너무 소비되긴한다. 어쩔 수 없다.
- 토요일에 네이터 코테가있는데 2시간 밖에 코테를 안본다. 이유는 뭘까? 문제가 간단했으면 좋겠다. 더 열심히 풀어보자. 아직 너무너무 많이 부족하다. 최대한 코테 대비 알고리즘 문제 푸는거에 집중해보자.
- 오늘 스터디를 참여했는데 책을 제대로 읽지않았던거 같다. 아는거 같으면서도 모르는느낌... 그래도 오늘 스터디를 통해서 좀 많이 알게되었다! 역씌.. 윤석님...
- 너무 늦어버렸다. 얼른자자.

### 🚀 내일 할 일
- 알고리즘 Section8 마무리
- 기술 면접 질문 스터디 질문 선정하기
- 코드숨에서 진행했던 프로젝트 더 꾸며보기 (반응형)

### 🎯 이번주 목표
- 인프런 알고리즘 Section 8 풀기
- 기술 면접 준비 스터디 관련 준비 및 스터디 참여
- 코드숨에서 진행했던 프로젝트 더 꾸며보기 (반응형)
- 테스트 주도 개발로 배우는 객체 지향 설계와 실천 9장까지 읽고 스터디 참여
- Core JavaScript 4장 읽기
