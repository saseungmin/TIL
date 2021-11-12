## 📆 2021-11-12(금) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 회사 브랜드 사이트 API 테스트 코드 작성
- [x] [개인 프로젝트 초기 세팅](https://github.com/jennie-harang/unnamed/pull/3)
- [x] 기부할 보육원 찾아보기

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 클린 코드 9 ~ 10장 읽기 및 스터디 참여
- ~~스칼라로 배우는 함수형 프로그래밍 3 ~ 4장~~
- ~~리팩터링 1장 및 스터디~~
- [ ] 테스트와 TDD에 대한 정리
- [ ] 인프런 강의 듣기
- [x] 개인 프로젝트 초기 세팅
- [x] Next.js 공부하기

### 🤔 공부하면서 배운것이 있다면?
- https://nextjs.org/

[import에 type](https://www.typescriptlang.org/ko/docs/handbook/release-notes/typescript-3-8.html#span-idtype-only-imports-exports--%ED%83%80%EC%9E%85-%EC%A0%84%EC%9A%A9-imports-%EC%99%80-exports-type-only-imports-and-exports)을 붙일 수 있는 것을 처음 알았다.   
typescript 전용으로 import의 type 전용 import기능이다.   

> TypeScript 3.8은 타입-전용 imports, exports를 위한 새로운 구문이 추가되었습니다.    
> import type은 타입 표기와 선언에 사용될 선언만 import 합니다. 이는 항상 완전히 제거되므로, 런타임에 남아있는 것은 없습니다. 마찬가지로, export type은 타입 문맥에 사용할 export만 제공하며, 이 또한 TypeScript의 출력물에서 제거됩니다.

```tsx
import '../styles/globals.css'
import type { AppProps } from 'next/app'

function MyApp({ Component, pageProps }: AppProps) {
  return <Component {...pageProps} />
}

export default MyApp
```

### ⚡ 아쉬운 점 및 회고
제니랑 할 프로젝트의 초기세팅을 진행했다. 제대로된 서비스를 만들려면 서버사이드 렌더링이 필요하기 때문에 Next.js를 선택. 처음 해보지만, 이 역시 배워나가면 된다. 역시나 Yarn berry를 사용했다. yarn berry의 pnp zero install 기능은 정말 좋은 거 같다.   

회사 브랜드 사이트의 테스트가 없는 레거시 코드를 걷어내기 위해 시간이 있을 때마다 테스트 코드를 작성하고 있다. 얼른 코드 커버리지 100%를 달성하고싶다!   

여기 저기 전화를 했지만, 아직 어디에다가 해야할지는 못정했다. 정말 필요하고 좋은 곳에 사용될 수 있는 믿을 수 있는 곳으로 하고 싶다.   

### 🚀 내일 할 일
- 회사 브랜드 사이트 API 테스트 코드 작성
- 개인 프로젝트 초기 세팅

### 🎯 이번주 목표
- 클린 코드 9 ~ 10장 읽기 및 스터디 참여
- 스칼라로 배우는 함수형 프로그래밍 3 ~ 4장
- 리팩터링 1장
- 테스트와 TDD에 대한 정리
- 인프런 강의 듣기
- 개인 프로젝트 초기 세팅
- Next.js 공부하기
