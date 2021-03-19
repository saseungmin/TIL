## 📆 2021-03-19(금) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
  - 백엔드 부분에 여러 개의 ToDo 삭제 API를 새로 추가했다. ([PR Link](https://github.com/saseungmin/Recoil_Todo_Backend/pull/23))
  - todo edit input에 대한 update로직을 추가했다. ([PR Lin](https://github.com/saseungmin/Recoil_ToDo/pull/67))
- [x] 알고리즘 공부
  - Section 6의 [solution 1](https://github.com/saseungmin/daily_coding_dojo/commit/6016d8f4f3ba21f198773d616a198b100c4d63e6), [solution 2](https://github.com/saseungmin/daily_coding_dojo/commit/3e0eb73cdc0e2db1f758263976414f8f60ea4131)를 풀었다.

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 공부
- ~~오브젝트 책 Chapter 9 까지 읽기 및 스터디 참여~~
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
- [x] 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- [ ] 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기

### 🤔 공부하면서 배운것이 있다면?
- `event.target` 와 `event.currentTarget` 의 차이점. ([Link](https://webisfree.com/2017-09-06/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-event-target-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EC%99%80-currenttarget-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90%EC%9D%80))
- `mongoose`에서 여러개의 `Object._id`를 찾고, 삭제하는 방법을 알았다.

```js
const ownTodos = await Todo.find()
  .where('_id')
  .in(ids) // in 조건
  .where('writer._id')
  .equals(user._id)
  .exec();
```

- 여러 개의 `Object._id`에 일치하는 데이터를 삭제
- 여기서 `ids`는 다음과 같이 배열로 들어간다.

```js
const ids = ['1', '2', '3'];

await Todo.deleteMany({ _id: ids }).exec();
```

### ⚡ 아쉬운 점 및 회고
- 오늘은 좀 적당히? 공부했다.
- 사실 적당히 한지도 모르겠다. 아니다 평소와 같았던 거 같다.
- 내일은 라인 코딩테스트가 있다. 뭐.. 떨어질건 분명하지만, 코딩테스트는 계속 봐보는게 좋은거라 생각하기 때문에 꾸역꾸역 라인 자소서도 써서 내일 코테를 보게되었다.
- 어떤식으로 나오는지도 궁금하고, 내가 어느정도 풀 수 있을지도 궁금하다. 그래서 신청하게 되었다.
- 내일을 위해서 오늘은 좀 일찍 자봐야겠다.
- 오늘 e.target과 e.currentTarget의 차이점을 알게되었다. 여태까지 그냥 썼는데, 이유를 알게되니 더 명확하게 사용할 수 있을 거 같다.
- 항상 조금이라도 궁금하면 찾아보자. 그냥 넘어가면 그건 아무런 소용 없다.
- 내일은 공부를 좀 못할 거 같은 느낌이다. 코테는 한 번 보면 진이 너무 빠진다. 내일은 적당히 하고 쉬어야겠다.

### 🚀 내일 할 일
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 라인 코딩테스트

### 🎯 이번주 목표
- 알고리즘 공부
- ~~오브젝트 책 Chapter 9 까지 읽기 및 스터디 참여~~
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기
