---
layout: post
title: "첫 번째 포스트: Jekyll 블로그 시작하기"
description: >
  Hydejack 테마로 Jekyll 블로그를 시작하는 방법과 포스트 작성 가이드
image: /assets/img/blog/hydejack-9.jpg
categories: [code]
tags: [jekyll, hydejack, 블로그]
sitemap: true
---

Jekyll과 Hydejack 테마로 블로그를 시작했습니다.

## 포스트 작성 방법

포스트는 `_posts` 폴더 안에 아래 형식으로 파일을 만들면 됩니다.

```
YYYY-MM-DD-제목.md
```

예: `2026-04-14-hello-world.md`

## Front Matter (머리말)

모든 포스트는 파일 맨 위에 `---`로 감싼 YAML 머리말이 필요합니다.

```yaml
---
layout: post
title: "포스트 제목"
description: >
  포스트 설명 (목록에 미리보기로 표시됨)
tags: [태그1, 태그2]
---
```

## 마크다운으로 글쓰기

### 제목

```
# H1 제목
## H2 제목
### H3 제목
```

### 강조

**굵게**, *기울임*, ~~취소선~~

### 코드 블록

인라인 코드: `print("Hello, World!")`

블록 코드:

```python
def hello():
    print("Hello, Jekyll!")
```

### 링크와 이미지

[링크 텍스트](https://example.com)

![이미지 설명](/assets/img/blog/hydejack-9.jpg)

### 목록

- 항목 1
- 항목 2
  - 중첩 항목

1. 순서 있는 항목
2. 두 번째 항목

### 인용

> 인용문은 이렇게 씁니다.

---

이제 `_posts` 폴더에 파일을 추가하면 블로그에 글이 올라옵니다!
