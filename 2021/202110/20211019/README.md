## 📆 2021-10-19(화) TIL

### 📈 어제의 계획이 예상대로 진행됐나요?
- [ ] 클린 코드 1장 읽기
- [x] 페이스북에 채용 홍보글 올리기
  - https://www.facebook.com/groups/codingeverybody/permalink/6598463276860819/
- [ ] 건강검진 접수

### 🦄 이번주 목표 진행사항은요? (오늘 조금이라도 진행했으면 체크)
- [ ] 클린 코드 1, 2장 읽기
- [ ] ReScript ToDo 앱 CSS 적용 작업
- [ ] 테스트와 TDD에 대한 정리
- [ ] 개인 프로젝트 한피쳐씩 틈틈히
- [x] Kasa Blog 구현에 대한 gatsby 공부

### 🤔 공부하면서 배운것이 있다면?

#### auto assign
- https://github.com/kentaro-m/auto-assign
- 자동으로 Reviewer와 assign을 가능하게 해줌
- [CODEOWNERS](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners)

#### Gatsby 
- Lazy Loading blur 처리

[option](https://www.gatsbyjs.com/docs/reference/built-in-components/gatsby-plugin-image/#placeholder)

```graphql
query($id: String!) {
  tech: markdownRemark(id: { eq: $id }) {
    frontmatter {
      date(formatString: "MM-DD-YYYY")
      category
      title
      thumbnail {
        name
        childImageSharp {
          gatsbyImageData(placeholder: BLURRED) # ...
        }
      }
    }
    html
  }
}
```

- Netlify CMS Setting

https://www.netlifycms.org/docs/gatsby/

내부 코드로 config 비공개

```yml
backend:
  name: github
  repo: ##
  branch: main

media_folder: #
public_folder: #

collections:
  - name: #
    label: #
    folder: #
    path: #
    create: true
    fields:
      - { name: title, label: Title, widget: string }
      - { name: thumbnail, label: Thumbnail, widget: image, default: '#' }
      - { name: date, label: 'Publish Date', widget: datetime }
      - { name: category, label: Category, widget: string }
      - { name: body, label: Body, widget: markdown }
```

### ⚡ 아쉬운 점 및 회고
오늘 출근을 했지만, 같은 위워크 건물 9층에서 코로나 확진자가 나와서 다같이 일하는 도중에 쫓겨났다.. 집에서 재택을 했고 언제까지 재택할지는 모르겠다. 빨리 다시 출근하는 날이 오길..   

페이스북에 채용 홍보글을 올렸다. 실력 좋은신 분들이 많이 많이 지원해줬으면! 아주 좋은 회사인데 말이지..   

오늘의 아쉬운점은.. 건강상태가 별로였다.. 환절기라 비염 때문에 죽는게 나을 수도.. 있다는 생각이.. 후.. 그리고 클린 코드 책을 읽기 시작하려고 했지만, 할게 생각보다 많고, 다른 할 일이 생겨서 그 문제를 해결하니 시간이 다갔다. 내일 1장 읽자.

내일 어쩔 수 없이 재택이기에 잠이라도 더 자야겠답.

아 그리고.. 건강검진 접수좀 하자...

### 🚀 내일 할 일
- 클린 코드 1장 읽기
- 건강검진 접수
- 테스트와 TDD에 대한 정리

### 🎯 이번주 목표
- 클린 코드 1, 2장 읽기
- ReScript ToDo 앱 CSS 적용 작업
- 코어 자바스크립트 스터디 진행하기
- 테스트와 TDD에 대한 정리
- 개인 프로젝트 한피쳐씩 틈틈히
- Kasa Blog 구현에 대한 gatsby 공부
