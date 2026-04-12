---
title: GitHub Pages 블로그 시작하기
category: 개발
tags:
  - GitHub
  - Blog
  - 정적사이트
summary: GitHub Pages로 무료 블로그를 만드는 완전한 가이드
date: "2026-04-10"
draft: false
---

GitHub Pages는 GitHub 저장소에서 직접 웹사이트를 호스팅할 수 있는 무료 서비스입니다.

## 왜 GitHub Pages인가?

- **무료 호스팅**: 광고 없이 완전 무료
- **커스텀 도메인**: 자신만의 도메인 연결 가능
- **버전 관리**: Git으로 모든 변경사항 추적
- **빠른 배포**: push만 하면 자동 반영

## 시작하는 법

1. GitHub에서 `username.github.io` 형태의 저장소 생성
2. Settings → Pages 에서 소스 브랜치 설정
3. HTML/CSS/JS 파일을 push

> 이 템플릿은 별도 빌드 과정 없이 바로 사용 가능합니다!

## 글 추가하기

Netlify CMS Admin(`/admin`)에서 글을 작성하면 자동으로 `_posts/` 폴더에 마크다운 파일로 저장되고, GitHub에 커밋됩니다.

```javascript
// _posts/ 폴더의 마크다운 파일 구조 예시
---
title: 첫 번째 글
category: 개발
tags: [GitHub, Blog]
date: "2026-04-10"
---
본문 내용...
```
