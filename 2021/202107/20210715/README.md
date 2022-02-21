## 📆 2021-07-15(목) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 자바스크립트 패턴과 테스트 Chapter 1
  - [Link](https://github.com/saseungmin/reading_books_record_repository/tree/master/summarize_books_in_markdown/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20%ED%8C%A8%ED%84%B4%EA%B3%BC%20%ED%85%8C%EC%8A%A4%ED%8A%B8/Part%201/Chapter%201)
- 프로그래머스 코테 문제 풀기
  - [보석 쇼핑](https://github.com/saseungmin/daily_coding_dojo/tree/master/programmers/Level%203/%EB%B3%B4%EC%84%9D%20%EC%87%BC%ED%95%91)
- 기술 면접 질문 공부하기
- 코드숨 한 피처
  - [NotFound 페이지에 일부 Theme이 적용되지 않는 오류를 고쳐라](https://github.com/CodeSoom/ConStu/pull/217)

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 자바스크립트 패턴과 테스트 Part 1 읽기
- [ ] 함께자라기 책 읽기
- [ ] 기술 면접 질문 공부하기
- [x] 프로그래머스 코테 문제 풀기
- [ ] 2021 오픈소스 컨트리뷰션 아카데미 지원하기
- [ ] reading_books_record_repository에 docusaurus를 사용하여 GitBook 만들어보기

### 🤔 공부하면서 배운것이 있다면?

#### 프로그래머스 문제를 풀며
- [보석 쇼핑](https://github.com/saseungmin/daily_coding_dojo/tree/master/programmers/Level%203/%EB%B3%B4%EC%84%9D%20%EC%87%BC%ED%95%91)
- 알고리즘은 투포인트 알고리즘이였다.
- `gemMap.values()`로 배열을 생성하는것과 `gemMap.values().next().value`로 값 하나만 꺼내는 속도차이가 어마무시하다.

```js
function solution(gems) {
  const answer = [];

  const { size } = new Set(gems);
  const gemMap = new Map();

  for (let i = 0; i < gems.length; i++) {
    const gem = gems[i];

    gemMap.delete(gem);
    gemMap.set(gem, i);

    if (size === gemMap.size) {
      // 모든 Map을 배열로 변환해 첫번째 인덱스의 값과 마지막 인덱스의 값을 찾았다.
      const selectedGem = [...gemMap.values()];
      
      answer.push([selectedGem[0] + 1, selectedGem[selectedGem.length - 1] + 1]);
    }

    // if (size === gemMap.size) {
    //   answer.push([gemMap.values().next().value + 1, i + 1]);
    // }
  }

  return sortByDistance(answer)[0];
}
```

#### 자바스크립트 패턴과 테스트 Chapter 1
**테스트 주도 개발**(**Test-Driven Development**, **TDD**)은 처음부터 프로그램을 제대로 작성했는지 확실히 보장한다. TDD에서는 애플리케이션 코드를 짜기 **전에** 이 코드가 통과해야 할 단위 테스트를 **먼저** 작성한다. 마치 **애플리케이션을 개발하듯 전체 단위 테스트 케이스를 만들어가는 TDD 방식을 따르면 단위 정의와 인터페이스 설계에 도움이 많이 된다.**   

1. 완벽히 변경하면 성공하거나 그렇기 되기 전까지는 반드시 실패하는 단위 테스트를 작성한다. (Red)
2. 테스트가 성공할 수 있을 만큼만 **최소한으로** 코딩한다. (Green)
3. 애플리케이션 코드를 리팩토링하며 중복을 제거한다. (Refactor)

TDD가 개발 속도를 늦출 것으로 생각하는 사람도 있으리라. **관심사를 제대로 분리하지 않은 채 먼저 코딩하고 테스트를 작성하는 식으로 진행하면 정말 늦어지게 될 것이라 확신한다.**   

**테스트 주도 개발을 실천하면 여러 가지 혜택이 있다. 첫째, 장기적인 믿음성을 보장하는 단위 테스트 꾸러미를 구축한다. 둘째, 애플리케이션 객체에 적확한 인터페이스를 설계할 때 도움이 된다. 셋째, 놀랍게도 단위 테스트를 통해 코드를 더 빨리 개발할 수 있다.**   

테스트성을 높이려면 **관심사를 분리**하는 일에 집중하고 **단일 책임 원칙**이나 **의존성 주입** 같은 소프트웨어 공학 원칙을 잘 써먹는 게 중요하다.   

#### React에서 커스텀 훅 테스트하는 법
- 다음과 같이 `theme`에 대한 커스텀 훅이다.

```js
// ...
function useTheme() {
  const dispatch = useDispatch();

  const theme = useSelector(getCommon('theme'));

  const changeMode = useCallback(() => dispatch(changeTheme()), [dispatch]);

  return {
    theme,
    changeMode,
  };
}

export default useTheme;
```

- 다음은 `@testing-library/react-hooks`를 사용하여 테스트를 간단하게 할 수 있었다.

```js
import { useDispatch, useSelector } from 'react-redux';

import { renderHook, act } from '@testing-library/react-hooks';

import useTheme from './useTheme';

import { LIGHT } from '../util/constants/theme';

describe('useTheme', () => {
  // ...

  const renderUseTheme = () => renderHook(() => useTheme());

  describe('theme', () => {
    it('should return LIGHT(false)', () => {
      const { result } = renderUseTheme();

      expect(result.current.theme).toBe(LIGHT);
    });
  });

  describe('Calls changeMode', () => {
    it('should be listens dispatch action', () => {
      const { result } = renderUseTheme();

      act(() => {
        result.current.changeMode();
      });

      expect(dispatch).toBeCalledWith({
        type: 'common/changeTheme',
      });
    });
  });
});
```

이 라이브러리를 사용할 때 주의사항은 공식 문서 1면에 써있었다.   
이 라이브러리를 사용하는 경우

1. **하나 이상**의 custom hooks가 Component에 직접 연결되지 않은 있는 경우 이 라이브러리를 사용합니다.
2. Component와 상호 작용을 통해 테스트하기 어려운 복잡한 custom hooks가 있습니다.

이 라이브러리를 사용하지 말아야 하는 경우

1. hook은 Component와 함께 정의되며 하나의 해당 Component에서만 사용됩니다.
2. hook은 Component만 사용하여 테스트하기만 하면 Hook를 쉽게 테스트할 수 있습니다.

### ⚡ 아쉬운 점 및 회고
- 자바스크립트 패턴과 테스트 책을 읽고 있는데 TDD에 대한 내용이 나오고 다시금 일깨워주고 있어서 좋은거 같다. 처음에는 나온지 좀 된 책이라 괜찮을까? 싶었는데 괜찮은거 같다. 복습하는 느낌이랄까? 오늘 이 책을 읽으며 느낀점은 내가 지금 TDD를 제대로 안하고 있다는 것을 다시 일깨워주었다. 하다가 TDD가 아닌 테스트를 작성하려고 한다는 점이다. 
- 이 책에서도 나왔지만, 그런 욕망를 극복해야한다. 이러한 사고를 하는게 아니 고치는게 쉽지 않다. TDD를 안지도 꽤 되고 어떤 코드를 작성할 때도 TDD 적으로 생각하려고 노력하지만, 기존에 코딩하던 습관과 사람의 급함? 꼭 보여야져야 할꺼같은? 그런 의심이랄까.. 그런게 지배적이다. 늘 얘기하고 생각하지만 실천은 쉽지 않다. 그래도 자꾸 꺠닫고 생각하고 노력하려고 한다는 점에 칭찬하고 싶다. TDD를 실천하려고 노력하자.
- CS 공부를 좀 해야겠다.
- 오늘 날씨가 무척 더웠다. 내일은 약속이 있어 아마 공부할 시간이 많이? 거의 없을 듯 싶다.
- 오늘 내가 시간 낭비를 했던가? 안했다고 할 수는 없지만 많이 줄었고, 공부하고 끄적인 시간도 이번주중 가장 많은 하루였다.

### 🚀 내일 할 일
- 프로그래머스 코테 문제 풀기
- 기술 면접 질문 공부하기

### 🎯 이번주 목표
- 자바스크립트 패턴과 테스트 Part 1 읽기
- 함께자라기 책 읽기
- 기술 면접 질문 공부하기
- 프로그래머스 코테 문제 풀기
- 2021 오픈소스 컨트리뷰션 아카데미 지원하기
- reading_books_record_repository에 docusaurus를 사용하여 GitBook 만들어보기
- ConStu 프로젝트에 존재하는 간단한 오류를 수정하기
