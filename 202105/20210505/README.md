## 📆 2021-05-05(수) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 테스트 주도 개발로 배우는 객체 지향 설계와 실천 19장 읽고 스터디 참여
  - [19장 Link](https://github.com/saseungmin/reading_books_record_repository/tree/master/%ED%85%8C%EC%8A%A4%ED%8A%B8%20%EC%A3%BC%EB%8F%84%20%EA%B0%9C%EB%B0%9C%EB%A1%9C%20%EB%B0%B0%EC%9A%B0%EB%8A%94%20%EA%B0%9D%EC%B2%B4%20%EC%A7%80%ED%96%A5%20%EC%84%A4%EA%B3%84%EC%99%80%20%EC%8B%A4%EC%B2%9C/Chapter%2019)
- [x] 프로그래머스 코테 문제들 풀기
  - [괄호 회전하기](https://github.com/saseungmin/daily_coding_dojo/tree/master/programmers/Level%202/%EA%B4%84%ED%98%B8%20%ED%9A%8C%EC%A0%84%ED%95%98%EA%B8%B0)
  - [게임 맵 최단거리](https://github.com/saseungmin/daily_coding_dojo/tree/master/programmers/Level%202/%EA%B2%8C%EC%9E%84%20%EB%A7%B5%20%EC%B5%9C%EB%8B%A8%EA%B1%B0%EB%A6%AC)
- [x] 우아한 테크 캠프 4기 지원하기

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] Do it TS 책 7장까지 읽기
- [x] 테스트 주도 개발로 배우는 객체 지향 설계와 실천 19장까지 읽고 스터디 참여
- [ ] 인프런 알고리즘 Section 10 풀기
- [x] 프로그래머스 코테 문제들 풀기
- [x] 우아한 테크 캠프 4기 지원하기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 프로그래머스 문제를 풀면서..
- 프로그래머스의 문제를 풀면서 dfs랑 bfs를 어느때에 풀지를 다시한번 일깨워주었다.
- bfs는 최단거리를 구할 때 사용하자! 오늘 dfs를 풀때 모든 테스트케이스는 성공했지만, 효율성에서 실패했다.
- bfs로 사용하여 문제를 푸니까 효율성까지 가뿐히 성공하였다.
- 이 차이점은 dfs는 모든 경우의 수를 어떻게든 돌기 때문에 이미 최단거리가 나왔더라도 재귀가 끝날때까지 돌게된다.
- bfs는 queue에 순서대로 들어가기 때문에 결국 작은 수부터 빠져나오게된다. 그렇기 때문에 최단 거리를 찾으면 끝낼 수가 있다.

```js
function solution(maps) {
  const newMaps = [...maps];

  let answer = -1;
  const lenX = maps.length - 1;
  const lenY = maps[0].length - 1;

  const dx = [-1, 0, 1, 0];
  const dy = [0, 1, 0, -1];

  const queue = [];
  queue.push([0, 0, 1]);

  while (queue.length) {
    const [x, y, count] = queue.shift();

    if (x === lenX && y === lenY) {
      // 무조건 최단 거리 즉, 조건에 성립하는 맨 처음 들어오는 queue의 count가 최단 거리를 반환
      // 그렇기 때문에 찾으면 끝난다. 
      answer = count;
      break;
    }

    for (let i = 0; i < 4; i++) {
      const nx = x + dx[i];
      const ny = y + dy[i];

      if (nx >= 0 && nx <= lenX && ny >= 0 && ny <= lenY && newMaps[nx][ny] === 1) {
        newMaps[nx][ny] = 0;
        queue.push([nx, ny, count + 1]);
      }
    }
  }

  return answer;
}
```

#### 🎈 테스트 주도 개발로 배우는 객체지향 설계의 스터디를 통해서
- 오늘 이 책을 어떤 방식으로 읽어야할지 스터디를 통해 조금은 알 수 있었다.
- 책이 어려워서 사실상 이해를 포기하는 수준으로 읽고 있었는데 조금은 이 책을 읽어볼려고 노력해볼만 할 거 같다. 예제를 이해하기 힘드니 흐름을 읽는 식으로 읽기.
- 그리고 스터디를 통해서 배운점이 있다면 책 242P 내용이다.

> 다시 한 번 `allowing` 절을 사용해 테스트 구성 과 유의미한 테스트 단정을 구분했다.
> 표현력에 관해 아주 민감한데, 이런 표현력이 시간이 흘러도 테스트를 의미 있게, 즉 유용하게 유지하는 유일한 방법이라는 사실을 깨달았기 때문이다.

```java
@Test public void
doesNotBidAndReportsLosingIfSubsequentPriceIsAboveStopPrice() {
  allowingSniperBidding();
  context.checking(new Expectations() {{
    int bid = 123 + 45;
    allowing(auction).bid(bid); // allowing
    atLeast(1).of(sniperListener).sniperStateChanged(
      new SniperSnapshot(ITEM_ID, 2345, bid, LOSING)
    );
    when(sniperState.is("bidding"));
  }});

  sniper.currentPrice(123, 45, PriceSource.FromOtherBidder);
  sniper.currentPrice(2345, 25, PriceSource.FromOtherBidder);
}
```

- 스터디에서 이 부분에 대한 질문이 있었는데 `jest`로 비교하니까 확실히 이해가 빨리되었다.
- 우리가 React 에서 테스트를 작성할 때 다음과 같이 작성하는 거랑 같다.

```js
expect(handleClick).not.toBeCalled(); // allowing

doSomething();

expect(handleClick).toBeCalled();
```

- 위 예제와 같이 이전에 명확하게 해준다는 말이였다. 보통 이전에 실행되지 않았을 때는 `expect`를 사용하지 않았는데 이번에 이 책을 통해 이렇게 하는게 더 좋다는 것을 알게되었다. 여기서는 표현력이라고 말하는데 테스트를 의미있게 작성해보자는 걸 깨닫게 되었다.

#### 🎈 테스트 주도 개발로 배우는 객체지향 설계 19장에서 점진적 개발
- 이 부분에서는 스터디와 책을 읽으면서 느꼈던점이다. 확실히 좋았던 부분이라 다시 짚고 가고 싶었다.

> - 새 기능에 대해서는 해당 기능이 수행해야 할 일을 보여주는 **테스트를 어느 정도 작성하고, 코드가 통과할 만큼 변화하는 각 테스트를 작업하고, 신기능이 추가될 공간을 마련하거나 새로운 개념을 드러낼 필요에 따라 코드 구조를 변경**한다. 그러고 나서 출시한다.
> - 새로 발생하는 이벤트를 받아들이고자 코**드를 변경하고(Red), 깨진 부분을 확인하고, 고치고(Green), 변경 결과로 또 뭐가 깨지는지 확인하는 과정을 기능이 동작할 때까지 반복**한다.
> - 이러한 과정이 효과가 있으려면 코드를 점증적이고 비판적으로 변경하는 법을 이해해야 하고, 어디로든 가야 할 곳으로 향할 수 있게 코드를 잘 구조화된 상태로 유지해야 한다.
> - 이것이 **테스트 주도 개발 주기에서 리팩터링이 차지하는 부분이 중요한 이유**다. 즉, 리팩터링 주기를 잘 따르지 않으면 언제나 골란한 상황에 처하고 만다.

### ⚡ 아쉬운 점 및 회고
- 아쉬운점은 음... 없다!
- 만족스러운 하루!
- 왜냐하면 BFS와 DFS를 어떻게 어떠한때에 사용할지 감을 잡았기 때문!
- 그리고 코테 문제를 하나하나씩 풀어가는 재미를 다시 느꼈다는 점!
- 내일도 코테만 풀자.
- 그리고 오늘 스터디도 만족스러웠다. 책을 반포기상태로 읽고 있었는데 스터디를 통해서 동기부여도 얻었고 배운점도 많다.
- 나도 하나하나씩 계속 발전해나가는 개발자가 되고 싶다.
- 끝.

### 🚀 내일 할 일
- 프로그래머스 코테 문제들 풀기

### 🎯 이번주 목표
- Do it TS 책 7장까지 읽기
- ~~테스트 주도 개발로 배우는 객체 지향 설계와 실천 19장까지 읽고 스터디 참여~~
- 인프런 알고리즘 Section 10 풀기
- 프로그래머스 코테 문제들 풀기
- ~~우아한 테크 캠프 4기 지원하기~~
