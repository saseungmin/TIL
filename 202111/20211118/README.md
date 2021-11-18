## 📆 2021-11-18(목) TIL

### 📈 오늘 한 일
- [x] 개인 프로젝트 초기 세팅
  - [[Fix] Next.js Pages 폴더 안에 테스트 코드로 인해 빌드되지 않는 오류를 수정하라](https://github.com/jennie-harang/unnamed/pull/17)
- [x] [Auto](https://github.com/intuit/auto) release 알아보기

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 클린 코드 11 ~ 13장 읽기 및 스터디 참여
- ~~스칼라로 배우는 함수형 프로그래밍 4장 읽고 스터디 참여~~
- [ ] 리팩터링 2 ~ 3장 읽고 스터디 참여
- [ ] 테스트와 TDD에 대한 정리
- [ ] 인프런 강의 듣기
- [x] 개인 프로젝트 초기 세팅
- [x] Next.js 공부하기

### 🤔 공부하면서 배운것이 있다면?

#### Next.js pages 폴더 안에 테스트 파일이 있을 때 깨지는 문제 해결
Next.js index.tsx의 테스트 코드르 작성할 때 index.test.tsx 테스트 파일이 pages 폴더에 존재하면 index.tsx를 index.test.tsx도 인식해  빌드시 다음과 같은 오류가 발생.    

```
Build error occurred
ReferenceError: describe is not defined
```

해결방법    
1. https://github.com/vercel/next.js/issues/3728#issuecomment-523789071
2. https://github.com/vercel/next.js/issues/3728#issuecomment-363964953

두 방법중 첫번째 방법을 사용해서 index.page.tsx로 명시적으로 page가 붙은 파일을 찾게 함. 즉, page가 붙지 않은 파일은 제외 시킴    

```js
// next.config.js
module.exports = {
  // ...
  pageExtensions: ['page.tsx', 'page.ts', 'page.jsx', 'page.js'],
}
```

#### auto
- https://github.com/intuit/auto
- https://intuit.github.io/auto/

auto git tagging, auto release, auto changelog...   

### ⚡ 아쉬운 점 및 회고
너무 진빠지는 하루였다. 할 테스크들이 한꺼번에 들어온 느낌..? 어쨌든. 오늘 요 근래들어서 제일 뭔가 힘든 날이였다. 정신 없는 하루..! 내일만 지나면 금요일이지만 역시나 뭔가 즐겁지가 않은 주말..?    

오늘 auto를 공부?해봤는데 아주 좋은 걸 찾은 느낌.. 자동 릴리즈, 자동 tag 자동 changelog까지.. label도 자동으로 생성해준다. 릴리즈할 때 아주 요긴하게 써먹을 수 있겠다. 메시지를 직접적으로 입력해줄 필요도 없고.. 이렇게 편리하다니..!   

next.js에서 test 때문에 build가 안되는 문제가 있는데 이건 아무리 생각해도 아직까지 issue에 올라오는게 핫한거봐서는 역시 pages에 있는 index 파일을 찾아주는 걸 해줬으면 좋겠는데.. 좀 아쉬웠다. 어쨌든.. 간단하게 수정하여 빌드를 할 수 있었다.   

아쉬운점은 정신없는 하루 뭔가 이거했다 저거했다 하루종일 정리가 안된 느낌이었다. 그래서 덩달아 일의 효율도 떨어진거 같은 하루였다. 내일은 오늘보다 나은 하루였으면 좋겠다.

### 🚀 내일 할 일
- 리팩터링 2장

### 🎯 이번주 목표
- 클린 코드 11 ~ 13장 읽기 및 스터디 참여
- 스칼라로 배우는 함수형 프로그래밍 4장 읽고 스터디 참여
- 리팩터링 2 ~ 3장 읽고 스터디 참여
- 테스트와 TDD에 대한 정리
- 인프런 강의 듣기
- 개인 프로젝트 초기 세팅
- Next.js 공부하기
