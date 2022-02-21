## 📆 2021-06-09(수) TIL

### 📈 오늘 한 일
- [x] junior-recruit-scheduler에 PR 날리기
  - [PR](https://github.com/jojoldu/junior-recruit-scheduler/pull/371)
- [x] codewars 코테 2문제 풀기
  - [codewars Link](https://github.com/saseungmin/daily_coding_dojo/tree/master/codewars)
- [x] 바닐라 자바스크립틑 스터디 참여 및 과제 수행

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 부스트캠프 지원서 작성
- [ ] 회사 찾아보고 지원준비
- [ ] 면접 준비
- ~~코드숨 개인 프로젝트 e2e 테스트를 위한 Codeceptjs 적용 마무리~~
- [x] 바닐라 자바스크립트 스터디 참여하기
- [x] 프로그래머스 및 codewars 코테 문제들 풀기

### 🤔 공부하면서 배운것이 있다면?

#### 👉 참고할 링크들
- [당근 마켓 웹사이트 레포 공개](https://github.com/daangn/websites)
- [리액트 18 릴리즈를 위한 working group 레포](https://github.com/reactwg/react-18)
  - 벌써부터 기대된다.
  - 해당 레포에 [discussions](https://github.com/reactwg/react-18/discussions)에 다양한 얘기가 오고갈거 같다. 앞으로 계속 지켜봐야할 레포
  - 분명 내가 star를 추가했을 때 900명이였는데 볼때마다 100명씩 늘어나고 있다.
  - [React 18에 즉시 사용 가능한 개선 사항](https://github.com/reactwg/react-18/discussions/4)
  - [React 18 Alpha 설치](https://github.com/reactwg/react-18/discussions/9)
- [어제 있었던 Fastly CDN 문제로 인해 해외사이트 접속 장애 문제](https://www.bbc.com/news/technology-57413224)
- [코드숨 Real World HTTP 정리 레포](https://github.com/CodeSoom/study-real-world-http)
- [네이버 파이낸셜 인턴십](https://naverfincorp-career.com/nfin/job/detail/developer?annoId=20005945&classId=&jobId=&entTypeCd=&searchTxt=)

#### 👉 isPlainObject
- 바닐라 자바스크립트 스터디 과제를 하면서 리뷰를 받으며 `isObject`에 대한 깊은 생각을 하게 되었다.
- 기존에 `isObject`는 다음과 같이 구현되어 있었다.

```js
const isObject = (value) => typeof value === 'object' && value !== null; 
```

- `null`은 `object`이기 떄문에 다음과 같이 오브젝트인지 아닌지를 판별했다.
- 하지만, 위 검증 로직은 문제가 있다.
- 만약 빈 배열일 경우에는 다음 로직이 `true`를 반환하기 떄문이다.
- 그래서 위와 같은 문제를 좀더 해결하기 위해서 plain한 object 검증을 해야했다.
- 그래서 아래와 같이 구현을 내가 하지는 않았다. 다음 object 구현 로직은 [lodash의 `isPlainObject`의 소스코드](https://github.com/lodash/lodash/blob/4.17.15/lodash.js#L12036)를 분석하여 사용한 것이다.
- 다음과 같이 구현한 경우 `[]`도 `false`를 반환하고 `array`조차 `false`를 반환한다.

```js
const { hasOwnProperty } = Object.prototype;

const undefinedTag = '[object Undefined]';
const nullTag = '[object Null]';
const objectTag = '[object Object]';

const symToStringTag = Symbol ? Symbol.toStringTag : undefined;

const objectProto = Object.prototype;
const funcToString = Function.prototype;
const objectCtorString = funcToString.call(Object);
const nativeObjectToString = objectProto.toString;

// Object.getPrototypeOf(Object(value));
function overArg(func, transform) {
  return function (arg) {
    return func(transform(arg));
  };
}

// https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/getPrototypeOf
const getPrototype = overArg(Object.getPrototypeOf, Object);

// https://lodash.com/docs/4.17.15#isObjectLike
function isObjectLike(value) {
  return value != null && typeof value == 'object';
}

// [] : "[object Array]"
// {} : "[object Object]"
// '' : "[object String]"
function objectToString(value) {
  return nativeObjectToString.call(value);
}

// [] : "[object Array]"
// {} : "[object Object]"
// '' : "[object String]"
// ...
// object.prototype.tostring를 해결하는데 도움을 줌
// http://ecma-international.org/ecma-262/7.0/#sec-object.prototype.tostring
function getRawTag(value) {
  const isOwn = hasOwnProperty.call(value, symToStringTag);
  const tag = value[symToStringTag];

  try {
    value[symToStringTag] = undefined;
    var unmasked = true;
  } catch (e) {}

  const result = nativeObjectToString.call(value);
  if (unmasked) {
    if (isOwn) {
      value[symToStringTag] = tag;
    } else {
      delete value[symToStringTag];
    }
  }
  return result;
}

function baseGetTag(value) {
  if (value == null) {
    // undefined, null 체크
    return value == undefined ? undefinedTag : nullTag;
  }

  // 심볼이 존재하고 Object(value)에 심볼이 존재하면
  return (symToStringTag && symToStringTag in Object(value))
    ? getRawTag(value) // 심볼까지 체크?
    : objectToString(value); // 그냥 objectToString
}

function isPlainObject(value) {
  // !(null이 아니고 typeof가 object) || object.prototype.tostring != '[object Object]'
  if (!isObjectLike(value) || baseGetTag(value) != objectTag) {
    return false;
  }

  // Object.getPrototypeOf(Object(value));
  const proto = getPrototype(value);

  if (proto == null) {
    return true;
  }

  // hasOwnProperty.call(proto, 'constructor'): Object.create 체크?
  // Object.create는 constructor가 존재하지 않음
  const Ctor = hasOwnProperty.call(proto, 'constructor') && proto.constructor;

  // constructor typeof가 function이고
  // Ctor instanceof Ctor?
  // Function.prototype.call(Object) => undefined
  return typeof Ctor == 'function' && Ctor instanceof Ctor
    && funcToString.call(Ctor) == objectCtorString;
}
```

### ⚡ 아쉬운 점 및 회고
- 기존에 매주 월요일마다 하고 있던 스터디에 대해서 어떻게 해야할지 고민할 필요성이 생겼다.
- 같이 스터디를 진행하던 철웅님의 건강상의 문제로 앞으로 같이 참석하기 힘들어졌다. 어쩔 수 없는 일이다. 건강이 최우선이다.
- 이번에 스터디를 모집했는데 굉장히 아쉽긴하다. 내 비젼?은 무조건 참여하면 손해볼건 없다는 마인드라 했으면 좋겠지만, 잘 모르겠다.
- 그래서 혼자 해야할까.. 아니면 다음번을 기약해야할까.. 굉장히 고민된다. 내 상황을 좀 지켜보면.. 좀... 시기가 안좋은 거 같기도 하다.
- 고민 좀 더 해봐야겠다..
- 요즘 신경쓸게 정말 너무 많다. 어떻게 해야할지 갈팡질팡에 뭔가 홀린듯한 기분이다. 다잡고 정신차리고 준비해야한다. 너무 안일하게 생각한다.

### 🚀 내일 할 일
- 프로그래머스, codewars 알고리즘 문제들 풀기
- 부스트캠프 지원서 작성
- 코드숨 개인 프로젝트 README 수정하기
- 바닐라 자바스크립트 과제 수행

### 🎯 이번주 목표
- ~~Do it TS 책 12장까지 읽고 스터디 참여~~
- ~~린 UX 책 8장까지 읽고 스터디 참여~~
- ~~프로그래머스 코테 문제들 풀기~~
- ~~코어 자바스크립트 마무리 짓기~~
- 바닐라 자바스크립트 과제 풀기
- ~~페캠 네카라쿠배 지원~~
- 면접 질문 준비하기
- 코드숨 개인 프로젝트에 e2e 테스트를 위한 Codeceptjs를 적용하기
