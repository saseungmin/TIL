## 📆 2021-01-28(목) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [x] 만들기만한 코드숨에서 사용할 블로그를 사용할 수 있게 정리좀 해놔야겠다.
  - Github 및 facebook 링크를 icon으로 변경
  - 댓글 기능 추가.
  - mook blog 데이터 삭제
  - 잘못된 링크들 수정 및 about 페이지 정리
  - [PR Link](https://github.com/saseungmin/saseungmin/pull/3)
- [ ] 개인 프로젝트를 진행하자.(반응형 만들기)
  - 코드숨에서 사용할 블로그를 정리한다고 시간을 다 소비했다.

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [x] 윈도우 사용하지 않고 개발 및 공부하기 (Only Mac)
- [x] 코드숨 멤버쉽에 필요한 블로그 만들기
- [x] 인수인계서 작성하기 / 마무리 잘하기
- [ ] 퇴사 후 계획 가닥 잡기
- [ ] 긍정적이게 생각하기 😤
  - 뭔가.. 두렵다.

### 🤔 공부하면서 배운것이 있다면?
- 코드숨에서 사용할 블로그를 만들었다. 이 블로그는 사실 뭐 이력서만을 위해서 만들긴 했지만 하다보니 재밌어서 조금 수정했다.
- 배운것보단 [gatsby](https://www.gatsbyjs.com/)를 조금은 만져보았다.
- 조금 사용해봤는데 장점은 간단하게 플러그인들을 설치하면 사용할 수 있는게 많은거 같았다. 마크다운 문법으로 블로그 글을 쓸 수 있다는 장점이 있는 거 같다.
- 또한, graphql을 배워보고 싶었는데 gatsby의 컴포넌트를 만들 때에 기본적으로 제공한단다.

```jsx
import React from 'react'
import { StaticQuery, graphql, Link } from 'gatsby'

export const Bio = () => (
  <StaticQuery
    query={bioQuery} // 컴포넌트에 기본적으로 제공한다.
    render={data => {
      const { author, social, introduction } = data.site.siteMetadata

      return (
        // 셍략..
      )
    }}
  />
)

const bioQuery = graphql`
  query BioQuery {
    avatar: file(absolutePath: { regex: "/profile.png/" }) {
      childImageSharp {
        fixed(width: 72, height: 72) {
          ...GatsbyImageSharpFixed
        }
      }
    }
    site {
      siteMetadata {
        author
        introduction
        social {
          twitter
          github
          medium
          facebook
          linkedin
        }
      }
    }
  }
`

export default Bio
```

- 그리고 사용할 수 있는 오픈소스 테마들이 많아서 정말 손쉽게 만들 수 있었다.
- 그리고 오늘도 역시나 느꼈던 건 [netlify](https://app.netlify.com/)는 정말 좋은 거 같다. 너무 간단..

### ⚡ 아쉬운 점 및 회고
- 내일은 퇴사날이다. 막상 다가오니 두렵다. 백수가 되는 거다. 거기다 실엽급여 따위 없다.
- 흠.. 어떻게 시간을 활용해야할지.. 모르겠다.
- 정말 헛되이게 보내면 안된다.
- 그리고 집에서만 있으면서 공부하면 너무 우울해질 거 같고, 무기력해질 거 같다. 어떻게 해야할까요.
- 그래서 계획을 세워야한다..
- 마지막 출근이다. 잘하고 오자. 짧았던 8개월 동안 그래도 좋은 경험한 거 같다. 앞으로 더 노력해서 성장하자.. 


### 🚀 내일 할 일(퇴근 후)
- 개인 프로젝트를 진행하자.(반응형 만들기 or 스터디 후기)

### 🎯 이번주 목표
- 윈도우 사용하지 않고 개발 및 공부하기 (Only Mac)
- 코드숨 멤버쉽에 필요한 블로그 만들기
- 인수인계서 작성하기 / 마무리 잘하기
- 퇴사 후 계획 가닥 잡기
- 긍정적이게 생각하기 😤