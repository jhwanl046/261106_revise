# 261106_revise — GitHub 실습 워크스페이스

> 2026-11-06에 진행한 GitHub, 마크다운, 이슈/마일스톤 관리, 문서화 실습을 정리하고 학습할 수 있는 워크스페이스입니다.

## 1. 이 저장소는 무엇인가요?

이 저장소는 실습 과정에서 만든 산출물과 참고 문서를 한곳에 모아 둔 것입니다.  
각 폴더/파일은 독립적인 연습 주제를 다루며, `exercise.md`의 문제를 따라 하면서  
Git과 GitHub 기본기를 복습할 수 있습니다.

## 2. 디렉터리 구조

| 경로 | 설명 |
|------|------|
| `README.md` | 이 저장소 안내 문서 |
| `exercise.md` | 실습 학습용 문제집 |
| `memo.md` | 최초 생성 메모 (`mkdir 261106_revise`) |
| `step2.md` | `ai-issue` 레포 생성, 라벨, 마일스톤, 이슈 생성 명령어 모음 |
| `step3.md` | 문서 커밋/푸시, 문서 이슈 등록 및 종료 절차 |
| `syntax.md` | 마크다운 문법 완전 정리 가이드 |
| `5.txt` | 빈 연습 파일 |
| `ai-issue/` | 파이썬 통계 라이브러리 프로젝트 (서브 레포지토리) |
| `github-homepage/` | 개인 포트폴리오 홈피 (GitHub Pages용) |
| `jhwanl046/` | GitHub 프로필 README 레포 (서브 레포지토리) |

## 3. 실습 주제 요약

1. **레포지토리/프로젝트 관리** (`step2.md`)
   - `gh repo create`, 이슈/라벨/마일스톤 생성
   - Week 1 / Week 2 마일스톤으로 이슈 분류
2. **문서화와 이슈 정리** (`step3.md`)
   - `docs/TIL.md`, `docs/retrospective.md`, `docs/postmortem.md` 커밋
   - 문서 관련 이슈 등록 및 종료
3. **마크다운 문법** (`syntax.md`)
   - 제목, 목록, 코드 블록, 표, 링크, 이미지, HTML 보완
4. **웹 페이지** (`github-homepage/index.html`)
   - 정적 HTML 포트폴리오 페이지
5. **GitHub 프로필** (`jhwanl046/README.md`)
   - 프로필 README 작성

## 4. 빠른 시작

```powershell
# 현재 위치 확인
cd "C:\Git Workspace\261106_revise"

# Git 상태 확인
git status

# GitHub 인증 확인
gh auth status
```

학습은 `exercise.md`를 순서대로 진행하세요. 각 파트는 독립적으로 실행할 수 있으며,
명령어를 실제로 입력해 보는 것을 권장합니다.

## 5. 학습 순서 추천

1. Part 0~1: 환경/ Git 기본기 (`exercise.md`)
2. Part 2: GitHub CLI로 이슈/라벨/마일스톤 관리
3. Part 3: 마크다운 문법 적용
4. Part 4: 문서 작성과 릴리스 절차
5. Part 5: 브랜치와 Pull Request

## 6. 참고 문서

- `step2.md` — ai-issue 레포 관리 실습 명령어
- `step3.md` — 문서 커밋/이슈 종료 실습 명령어
- `syntax.md` — 마크다운 문법 레퍼런스
- GitHub Docs: https://docs.github.com

## 7. 라이선스

학습용 자료입니다. 자유롭게 참고·수정할 수 있습니다.
