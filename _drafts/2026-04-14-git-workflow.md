---
layout: post
title: "실전에서 쓰는 Git 워크플로우 정리"
description: >
  혼자 혹은 팀으로 작업할 때 자주 쓰는 Git 명령어와 브랜치 전략을 정리했습니다.
categories: [code]
tags: [git, 개발도구, workflow]
sitemap: true
---

매번 헷갈리는 Git 명령어와 브랜치 전략을 한 곳에 정리합니다.

## 기본 브랜치 전략

```
main        ← 배포용 (항상 안정)
  └─ develop  ← 통합 브랜치
       ├─ feature/login
       ├─ feature/dashboard
       └─ fix/navbar-bug
```

## 자주 쓰는 명령어

### 브랜치 작업

```bash
# 브랜치 만들고 바로 이동
git switch -c feature/my-feature

# 원격 브랜치 가져오기
git fetch origin
git switch feature/existing-branch

# 브랜치 목록 (원격 포함)
git branch -a
```

### 커밋 관리

```bash
# 변경사항 확인 후 스테이징
git diff
git add -p          # 헝크별로 선택 추가

# 커밋 메시지 컨벤션
git commit -m "feat: 로그인 기능 추가"
git commit -m "fix: 버튼 클릭 이벤트 오류 수정"
git commit -m "docs: README 업데이트"
```

### 실수 되돌리기

```bash
# 마지막 커밋 메시지 수정 (push 전에만)
git commit --amend -m "수정된 메시지"

# 스테이징 취소
git restore --staged <file>

# 작업 임시 저장
git stash
git stash pop
```

## 협업할 때 충돌 해결

```bash
# rebase로 깔끔하게 병합
git switch feature/my-feature
git rebase develop

# 충돌 발생 시
# 1. 파일 직접 수정
# 2. git add <file>
# 3. git rebase --continue
```

## 유용한 alias 설정

```bash
# ~/.gitconfig 에 추가
[alias]
  lg = log --oneline --graph --decorate --all
  st = status -s
  sw = switch
```

이 정도만 알아도 대부분의 상황을 커버할 수 있습니다.
