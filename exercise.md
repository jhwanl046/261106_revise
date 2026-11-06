# Exercise — 261106 실습 학습 문제집

이 문서는 현재까지 진행한 실습을 **직접 다시 수행하면서** Git/GitHub 기본기를 익히기 위한 문제집입니다.  
각 문제 아래의 명령어를 참고하되, 먼저自分で 시도한 뒤 확인하세요.

> 표기: `[ ]` 미완료, `[x]` 완료. 스스로 체크하며 진행하세요.

---

## Part 0. 사전 확인 Lab

### 문제 0-1. 현재 저장소 상태 확인
- 목표: 워킹 디렉터리와 Git 상태를 확인합니다.
- 명령어:
  ```powershell
  cd "C:\Git Workspace\261106_revise"
  git status
  git branch -a
  gh auth status
  ```
- 확인 포인트: 현재 브랜치가 `main`인지, 인증 계정이 `jhwanl046`인지.

### 문제 0-2. 원격 저장소 확인
- 목표: origin URL과 기본 브랜치를 확인합니다.
- 명령어:
  ```powershell
  git remote -v
  gh repo view jhwanl046/261106_revise --json defaultBranchRef,url
  ```

---

## Part 1. Git 기본기 Lab

### 문제 1-1. 새 브랜치 만들고 전환하기
- 목표: `feature/hello` 브랜치를 만들고 전환합니다.
- 명령어:
  ```powershell
  git switch -c feature/hello
  git branch --show-current
  ```
- 정리:
  ```powershell
  git switch main
  git branch -D feature/hello
  ```

### 문제 1-2. 파일 수정 → 스테이징 → 커밋
- 목표: `5.txt`에 한 줄을 추가하고 커밋합니다.
- 명령어:
  ```powershell
  echo "hello git" >> 5.txt
  git add 5.txt
  git commit -m "chore: update 5.txt for practice"
  ```
- 확인: `git log --oneline -3`

### 문제 1-3. 변경 사항 되돌리기
- 목표: 워킹 트리 변경을 stash로 임시 저장했다가 복원합니다.
- 명령어:
  ```powershell
  git stash
  git stash list
  git stash pop
  ```

---

## Part 2. GitHub CLI Lab

### 문제 2-1. 인증/레포 목록 확인
- 목표: CLI로 접근 가능한 레포지토리를 봅니다.
- 명령어:
  ```powershell
  gh repo list --limit 10
  ```

### 문제 2-2. 이슈 생성
- 목표: 연습용 이슈를 만듭니다.
- 명령어:
  ```powershell
  gh issue create --repo jhwanl046/ai-issue --title "[연습] CLI 이슈 생성 테스트" --body "GitHub CLI 연습용 이슈입니다."
  ```
- 확인: `gh issue list --repo jhwanl046/ai-issue --limit 5`

### 문제 2-3. 라벨/마일스톤 둘러보기
- 목표: 라벨과 마일스톤을 확인합니다.
- 명령어:
  ```powershell
  gh label list --repo jhwanl046/ai-issue
  gh api repos/jhwanl046/ai-issue/milestones | ConvertFrom-Json | Select-Object number,title,open_issues
  ```

### 문제 2-4. 이슈 종료
- 목표: 방금 만든 이슈를 닫습니다.
- 명령어:
  ```powershell
  gh issue close <ISSUE_NUMBER> --repo jhwanl046/ai-issue --comment "실습 완료"
  ```

---

## Part 3. 마크다운 Lab

### 문제 3-1. README 뼈대 작성
- 목표: `README.md`에 다음을 포함하세요.
  - h1 제목 1개
  - 기능 목록 (순서 없는 목록)
  - 설치 방법 (펜스드 코드 블록, `bash`)
  - 간단한 표 (2~3열)
- 참고: `syntax.md` 20장 템플릿.

### 문제 3-2. 줄바꿈 함정 해결
- 아래 입력이 한 줄로 보인다면 이유와 해결법을 서술하세요.
  ```markdown
  첫 줄
  둘째 줄
  ```
- 정답 키: 단일 개행은 soft break. `<br>` 또는 줄 끝 공백 2개 사용.
- 실습: `<br>`로 강제 줄바꿈을 추가하고 렌더링 확인.

### 문제 3-3. 코드 블록 중첩
- 목표: 문서 안에서 마크다운 예제를 보여주는 4-백틱 중첩 블록을 작성하세요.
- 힌트: 바깥 ```` ````, 안쪽 ``` ``` ```.

### 문제 3-4. 표 정렬
- 목표: 아래 표를 가운데/오른쪽 정렬로 바꾸세요.
  ```markdown
  | 이름 | 점수 |
  |------|------|
  | Alice | 95 |
  | Bob   | 88 |
  ```

---

## Part 4. 문서화 Lab

### 문제 4-1. TIL 한 줄 추가
- 목표: `ai-issue/docs/TIL.md`에 Day 15 항목을 추가하고 커밋합니다.
- 예시:
  ```markdown
  ## Day 15 — 회고
  - **What:** 릴리스 전 체크리스트가 장애를 줄인다.
  - **How:** 버전 bump → 태그 → 릴리스 노트 → 테스트.
  ```
- 명령어:
  ```powershell
  git -C "C:\Git Workspace\261106_revise\ai-issue" add docs/TIL.md
  git -C "C:\Git Workspace\261106_revise\ai-issue" commit -m "docs: add Day 15 entry"
  ```

### 문제 4-2. 포스트모템 액션 아이템 점검
- 목표: `postmortem.md`의 Action Items 표에서 완료 표시(`[x]`)를 추가해 봅니다.
- 확인: 마크다운 렌더링에서 표가 유지되는지.

---

## Part 5. 브랜치 & Pull Request Lab (이번 과제)

### 문제 5-1. release 브랜치 생성
- 목표: `main`에서 `release` 브랜치를 생성합니다.
- 명령어:
  ```powershell
  cd "C:\Git Workspace\261106_revise"
  git switch -c release
  ```

### 문제 5-2. README.md / exercise.md 커밋
- 목표: 이 저장소 루트에 `README.md`와 `exercise.md`를 추가(또는 수정)하고 커밋합니다.
- 명령어:
  ```powershell
  git add README.md exercise.md
  git commit -m "docs: add README and exercise for practice"
  ```

### 문제 5-3. 브랜치 푸시
- 명령어:
  ```powershell
  git push -u origin release
  ```

### 문제 5-4. Pull Request 생성
- 목표: `release` → `main` PR을 생성합니다.
- 명령어:
  ```powershell
  gh pr create --base main --head release --title "docs: add README and exercise" --body "실습 학습용 README.md와 exercise.md 추가"
  ```

### 문제 5-5. 리뷰/머지
- 목표: PR을 확인하고 (가능하면) squash 머지합니다.
- 명령어:
  ```powershell
  gh pr view
  gh pr merge --squash --delete-branch
  ```

---

## 자기 점검 체크리스트

- [ ] Git 기본 명령(add/commit/push)을 직접 실행했다.
- [ ] GitHub CLI로 이슈/라벨/마일스톤을 조회했다.
- [ ] 마크다운 제목/목록/코드/표를 직접 작성했다.
- [ ] 문서 변경을 커밋하고 브랜치를 푸시했다.
- [ ] `release` → `main` Pull Request를 생성했다.

## 보너스 과제

1. `ai-issue` 레포에 `CHANGELOG.md`를 추가하고 릴리스 노트를 작성해 보세요.
2. `github-homepage/index.html`을 수정해 본인 소개로 바꾸고 Pages에 반영해 보세요.
3. `syntax.md`의 예제를 자신의 README에 적용해 보세요.
