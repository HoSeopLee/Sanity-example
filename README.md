# Sanity로 Blog 모델 만들기

1. Sanity Project 만들고 Deploy하기

- npm install @sanity/cli -g
- sanity init
  - npm i @sanity/cl -g
  - sanity login
  - mkdir my-blog-contents
  - cd my-blog-contents
  - sanity init
  - sanity start

2. Schema 만들기 - author
3. Schema 만들기 - post
4. Schema 만들기 - home
5. Schema 만들기 - blockContent
6. Studio 의 input창 커스터마이징
7. query 사용하기

```
*[_type == 'home'][0]{'mainPostUrl': mainPost -> slug.current}
*[_type == 'post']{
  title,
  subtitle,
  createdAt,
  'content': content[]{
        ...,
        ...select(_type == 'imageGallery' => {'images': images[]{..., 'url': asset -> url}})
        },
  'slug': slug.current,
  'thumbnail': {
    'alt': thumbnail.alt,
    'imageUrl': thumbnail.asset -> url
  },
  'author': author -> {
    name,
role,
    'image': image.asset -> url
  },
  'tag': tag -> {
    title,
    'slug': slug.current
  }
}
```

---

- Sanity 는 팀이 실시간으로 협력하여 여러 채널에서 매력적인 디지털 경험을 구축할 수 있도록 하는 통합 콘텐츠 플랫폼이라고 하는데 재밌는 경험이였던거같다. 사용법이 익숙하지 않아 어려운거 같은데 익숙해지면 사용하는데는 큰 무리 없을거라 생각한다.
