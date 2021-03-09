## 📆 2021-03-09(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 알고리즘 공부
  - [section 5의 두 문제를 풀었다.](https://github.com/saseungmin/daily_coding_dojo/tree/master/inflearn_algorism/section5)
- [x] 오브젝트 5장 읽기
  - [PR Link](https://github.com/saseungmin/reading_books_record_repository/pull/41)
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
  - 한 아이디로 로그인 후 로그아웃 한 뒤, 다른 아이디로 로그인을 하면 전에 로그인한 정보가 로그인 되는 문제 해결
  - [PR Link](https://github.com/saseungmin/Recoil_ToDo/pull/53)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 공부
- [x] 오브젝트 책 Chapter 6 까지 읽기 및 스터디 참여
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기
- [x] 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- [ ] 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 알고리즘 공부
- 오늘은 슬라이드 윈도우 알고리즘을 알게 되었다.
- 슬라이드 윈도우는 주어진 크기에 연속된 정보를 가지고 비교하는 경우 사용할 수 있다.
- 푼 문제를 생각해보면 이 문제는 예를 들어 10개의 숫자가 연속되게 3개의 숫자를 더해 가장 큰 수를 반환하는 것이다.
- 배열이 `[1,4,5,2,7,2]`이면 `1,4,5`, `4,5,2`, `5,2,7`.... 이런식으로 반복되서 큰 수를 찾는 것이다.
- 처음 해결한 방법은 이중 for문을 돌며 해결하게 되었는데 이렇게 되면 시간복잡도가 `O(n*n)`이라는 크기가 되게 된다.

```js
function solution(M, arr) {
  let result = Number.MIN_SAFE_INTEGER;

  arr.forEach((_, index) => {
    const lastIndex = M + index;
    let sum = 0;
    if (lastIndex <= arr.length) {
      for (let i = index; i < lastIndex; i++) {
        sum += arr[i];
      }

      if (result < sum) {
        result = sum;
      }
    }
  });
  return result;
}
```

- 하지만, 이 문제를 슬라이드 윈도우 방식으로 해결하면 for문 한번 즉 배열 크기만큼만 비교하면 해결할 수 있다. 즉, 시간복잡도가 `O(n)`이 되게 된다.

```js
function solution(K, arr) {
  let result = 0;
  let sum = 0;

  for (let i = 0; i < K; i++) {
    sum += arr[i];
  }

  for (let i = K; i < arr.length; i++) {
    sum += (arr[i] - arr[i - K]);
    result = Math.max(sum, result);
  }

  return result;
}
```


#### 🎈 오브젝트 5장을 읽고 정리
- [오브젝트 5장](https://github.com/saseungmin/reading_books_record_repository/tree/master/%EC%98%A4%EB%B8%8C%EC%A0%9D%ED%8A%B8/Chapter%205)

#### 🎈 Recoil Todo 진행하면서
- `selector`와 `selectorFamily`는 cache를 사용한다. 이에 대한 문제가 발생하였는데 해결한 방법을 issue란에 남겼다.
- [Issue Link](https://github.com/saseungmin/Recoil_ToDo/issues/54)

### ⚡ 아쉬운 점 및 회고
- 오늘은 계획보다 많이 했다. 처음 있는 일이여서 나름 뿌듯한 하루였다.
- 하지만 공부시간은 많은 거 같았지만, 생각보다 딴짓한 시간이 있어서 순 공부시간은 많이 되지는 않는 거 같다.
- 시간 낭비하는 시간을 좀 줄일 필요가 있다고 생각한다. 진짜 집중해서 공부하면 현재 공부를 한다고 생각하는 시간보다 많이 적어질 거 같다.
- 시간을 효율적으로 쓰기 위해 방법을 찾아봐야겠다.
- 오늘은 좀 긍정적이게 생각했다. 역시 긍정적으로 생각하니 마음이 좀 편해졌다.
- 백수생활 1달하고 1주일이 되었는데 오늘 생각해보니 여유롭게 생각해도 된다는 느낌이 들었다.
- 그리고 내 페이스에 맞춰서 공부하기로 생각하니 오히려 많이 할 수 있었던 거 같다. 
- 오늘처럼 앞으로 여유를 가지고 생각했으면 좋겠다.

### 🚀 내일 할 일
- 알고리즘 공부
- 오브젝트 6장 읽기 및 스터디 참여

### 🎯 이번주 목표
- 알고리즘 공부
- 오브젝트 책 Chapter 6 까지 읽기 및 스터디 참여
- Recoil를 사용한 ToDo 앱 만들기 진행하기
- 긍적적 사고방식과 할 수 있는 것과 할 수 없는 것을 구분 잘하기
- 시간 분배 잘하기와 쓸대 없이 시간낭비하는 시간 아끼기