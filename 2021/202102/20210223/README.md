## 📆 2021-02-23(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 알고리즘 공부
  - 오늘은 Section3에 두 문제를 풀었다. ([Link](https://github.com/saseungmin/daily_coding_dojo/tree/master/inflearn_algorism/section3))
- [x] 앨래강트 오브젝트 Chapter 3 마무리
  - 3장을 읽고 정리했다. ([PR Link](https://github.com/saseungmin/reading_books_record_repository/pull/36))
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (BackEnd)
  - Update api 구현 ([PR Link](https://github.com/saseungmin/Recoil_Todo_Backend/pull/15))
  - Remove api 구현 ([PR Link](https://github.com/saseungmin/Recoil_Todo_Backend/pull/14))

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 알고리즘 공부
- [x] 앨래강트 오브젝트
- [x] Recoil를 사용한 ToDo 앱 만들기 진행하기 (BackEnd 마무리)
- [ ] 개인 프로젝트(스터디 후기)

### 🤔 공부하면서 배운것이 있다면?

#### 🎈 Recoil를 사용한 ToDo 앱 만들기(백앤드)
- Todo 삭제와 수정시에는 해당 Todo의 Id를 사용해야되기 떄문에 Id를 params로 넘겨줘야 한다.
- 이 때 router를 등록하여 사용할 수 있다. 또한, `delete`와 `patch`시 해당 Todo의 `ObjectId`를 검증하는 미들웨어와 자신의 `Todo`인지 검증하는 middleware를 추가해줄 수 있었다.
- `/:id` (예. `/api/todo/123123`)에 매핑되면 해당 미들웨어의 검증 후 삭제 및 수정을 할 수 있게 된다.

```javascript
import Router from 'koa-router';

import {
  write, list, remove, getTodoById, update, checkOwnTodo,
} from './todos.ctrl';

const todos = new Router();

todos.get('/', list);
todos.post('/', write);

const todo = new Router();

todo.delete('/', remove);
todo.patch('/', update);

todos.use('/:id', getTodoById, checkOwnTodo, todo.routes());

export default todos;
```

- mongoose에서 `ObjectId`로 삭제와 수정을 할 수 있는 메서드가 존재한다.

```javascript
// 삭제
await Todo.findByIdAndRemove(id).exec();

// 수정
// 첫번째 인자는 ObjectId, 두번째 인자는 변경을 원하는 값
// 세번째 인자는 option으로 new:true를 할 시 반환값은 새로 변경된 값이다.
const todo = await Todo.findByIdAndUpdate(id, value, {
  new: true,
}).exec();
```
- 위의 메서드를 사용하면 deprecation warning이 발생하는데, 이 문제는 아래의 mongoose의 `connect` 옵션에서 `useFindAndModify`를 `false`로 변경해주면 된다.
- [공식 문서의 deprecated warning 참고](https://mongoosejs.com/docs/deprecations.html)

```javascript
export function connectDatabase(mongoUrl) {
  return mongoose.connect(
    mongoUrl,
    {
      useUnifiedTopology: true,
      useNewUrlParser: true,
      useCreateIndex: true,
      useFindAndModify: false,
    },
    callback,
  );
}
```

#### 🎈엘레강트 오브젝트 Chapter 3, Section 4, 5, 6, 7
- [정리 내용 참고](https://github.com/saseungmin/reading_books_record_repository/tree/master/%EC%97%98%EB%A0%88%EA%B0%95%ED%8A%B8%20%EC%98%A4%EB%B8%8C%EC%A0%9D%ED%8A%B8/Chapter%203#-%EC%A0%88%EB%8C%80-getter%EC%99%80-setter%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EB%A7%88%EC%84%B8%EC%9A%94)

#### 🎈 알고리즘 공부에서 배운 점
- [정리 참고](https://github.com/saseungmin/daily_coding_dojo/tree/master/inflearn_algorism/section3/solution2#-%EC%A0%95%EB%A6%AC)


### ⚡ 아쉬운 점 및 회고
- Recoil_Todo 백앤드 부분은 마무리가 다 된 거 같다. 이제 프론트에서 api 호출과 회원인증 부분을 만들어 줘야한다. 사실 백앤드 부분은 굉장히 간단했다. 핵심은 프론트앤드이기 때문.. Recoil_Todo의 계획은 Theme을 밝은 테마와 어두운 테마로 나누는 것과 회원인증까지 하는 것이 목표이다.
- 오늘은 할당량은 다해서 기분은 좋다. 하지만, 엘레강트 오브젝트 책은 오늘도 읽었지만 여전히 어렵다. 흠.. 내가 지금 읽어야 하는 수준이 아닌가보다.. 객체지향은 너무 어렵다.. 어려워..
- 알고리즘은 시간 투자를 얼마 못했다. 그래도 두 문제라도 건들여서 다행이다.
- 시간이 너무 빠르게 흐른다. 벌써 퇴사한지도 다음주가 지나면 1달이 지난다. 심리적으로 불안한 건 그래도 조금은 괜찮아졌다. 좋은 회사에 아니, 그래도 괜찮은, 선임이 좋은 그런 회사에 들어갈 수 있을까..? 의문이다.
- 맨날 1시쯤에는 침대에 누워있지만 거의 3시가 다되서 잠에 든다. 이러니 아침에 일찍 일어나기 힘들지. 하지만 잠이 안온다..


### 🚀 내일 할 일
- 알고리즘 공부
- 앨래강트 오브젝트 Chapter 4 및 스터디 참여
- Recoil를 사용한 ToDo 앱 만들기 진행하기

### 🎯 이번주 목표
- 알고리즘 공부
- 앨래강트 오브젝트
- Recoil를 사용한 ToDo 앱 만들기 진행하기 (BackEnd 마무리)
- 개인 프로젝트(스터디 후기)