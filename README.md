# ✦ devlog — Netlify CMS 블로그 템플릿

Netlify + GitHub으로 글을 작성하면 GitHub 저장소에 마크다운 파일로 자동 저장됩니다.

---

## 📁 폴더 구조

```
your-repo/
├── index.html              ← 블로그 프런트엔드 (단일 파일)
├── netlify.toml            ← Netlify 배포 설정
├── admin/
│   ├── index.html          ← Netlify CMS 관리자 UI
│   └── config.yml          ← ⭐ 저장소 정보 설정 (필수)
├── _posts/
│   ├── manifest.json       ← 글 파일 목록 (자동 관리)
│   └── *.md                ← 글 마크다운 파일들
└── static/
    └── uploads/            ← 이미지 업로드 폴더
```

---

## 🚀 배포 방법 (10분)

### 1단계 — GitHub 저장소 생성

```bash
git init
git add .
git commit -m "first commit"
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

### 2단계 — admin/config.yml 수정

```yaml
backend:
  name: git-gateway
  branch: main          # 브랜치명 확인

# ⭐ 이 줄은 Netlify Identity 사용 시 필요 없음 (git-gateway가 자동 처리)
# repo: 설정은 직접 GitHub API 사용 시에만 필요
```

### 3단계 — Netlify에 배포

1. [app.netlify.com](https://app.netlify.com) → **Add new site → Import from Git**
2. GitHub 저장소 선택
3. Build command: 비워두기 / Publish directory: `.`
4. **Deploy**

### 4단계 — Netlify Identity 활성화

1. Netlify 대시보드 → **Identity** 탭
2. **Enable Identity** 클릭
3. **Git Gateway** 탭 → **Enable Git Gateway** 클릭
4. Registration preferences: **Invite only** (본인만 가입)
5. **Invite users** → 본인 이메일 초대 → 이메일에서 수락

### 5단계 — 완료!

- 블로그: `https://your-site.netlify.app`
- 관리자: `https://your-site.netlify.app/admin`

---

## ✏️ 글 작성 방법

### 방법 A: Netlify CMS 관리자 (추천)
1. `/admin` 접속 → Netlify Identity로 로그인
2. **New Post** → 제목/카테고리/본문 입력
3. **Publish** → GitHub `_posts/` 폴더에 자동 커밋!

### 방법 B: 블로그에서 직접 작성
1. 블로그 우상단 **🔑 로그인** → GitHub Personal Access Token 입력
2. **+ 글쓰기** → 작성 → **저장하기**
3. GitHub API를 통해 `_posts/` 폴더에 직접 커밋

### 방법 C: 직접 파일 편집 (개발자용)
`_posts/` 폴더에 마크다운 파일을 추가하고 `manifest.json` 업데이트:

```markdown
---
title: "글 제목"
category: 개발
tags:
  - 태그1
  - 태그2
summary: "한 줄 설명"
date: "2026-04-12"
draft: false
---

# 본문

마크다운으로 작성합니다.

## Python 차트

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 10, 100)
plt.plot(x, np.sin(x))
plt.title('사인 파형')
plt.show()
```
```

그리고 `_posts/manifest.json`에 파일명 추가:
```json
[
  "2026-04-12-새글.md",
  "기존글.md"
]
```

---

## 🔑 로그인 방법 비교

| 방법 | 용도 | 설정 필요 |
|------|------|-----------|
| Netlify Identity | `/admin` CMS 관리 | Netlify Identity 활성화 |
| GitHub PAT | 블로그에서 직접 작성/수정/삭제 | GitHub 토큰 발급 |

**GitHub PAT 발급:** [github.com/settings/tokens](https://github.com/settings/tokens)  
→ `public_repo` 권한 선택

---

## 🎨 커스터마이징

### 블로그 제목 변경
`index.html` 에서:
```html
<span class="nav-logo">✦ devlog</span>
<title>My Blog</title>
```

### 카테고리 추가
`admin/config.yml` 의 options 섹션과 `index.html` 의 사이드바 버튼 모두 수정

### 테마 색상
`index.html` CSS `:root` 섹션의 `--accent` 변수 수정

---

## 📝 마크다운 지원

- `# 제목` `## 소제목` `**굵게**` `*기울임*` `` `코드` ``
- `> 인용구` `- 목록` `1. 번호목록`
- ` ```python ``` ` → 블로그에서 ▶ 실행 가능한 matplotlib 차트
- `[링크](URL)` `![이미지](URL)`
