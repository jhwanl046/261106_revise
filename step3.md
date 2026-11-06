# STEP3 작업 명령어 목록

대상 레포지토리: `jhwanl046/ai-issue`
작성물: `docs/TIL.md`, `docs/retrospective.md`, `docs/postmortem.md`

## 1. 문서(docs) 커밋 및 푸시

```powershell
git -C "C:\Git Workspace\261106_revise\ai-issue" add docs
git -C "C:\Git Workspace\261106_revise\ai-issue" commit -m "docs: add TIL (14 days), sprint retrospectives, and postmortem"
git -C "C:\Git Workspace\261106_revise\ai-issue" push origin master
```

## 2. docs 내용을 이슈로 등록

```powershell
gh issue create --repo jhwanl046/ai-issue --title "[Docs] TIL 14-day learning log" --body "docs/TIL.md: 14일간 파이썬 통계 프로젝트 개발에서의 학습 내용." --milestone "Week 2 - Analysis and visualization" --label "documentation"

gh issue create --repo jhwanl046/ai-issue --title "[Docs] Sprint retrospectives (Week 1 & Week 2)" --body "docs/retrospective.md: Sprint 1/Sprint 2 회고." --milestone "Week 2 - Analysis and visualization" --label "documentation"

gh issue create --repo jhwanl046/ai-issue --title "[Docs] Postmortem: variance NaN incident" --body "docs/postmortem.md: 가상 장애 부검 + 액션 아이템." --milestone "Week 2 - Analysis and visualization" --label "documentation,bug"
```

## 3. 문서 반영 완료로 이슈 종료

```powershell
gh issue close 14 --repo jhwanl046/ai-issue --comment "docs/에 반영 완료"
gh issue close 15 --repo jhwanl046/ai-issue --comment "docs/에 반영 완료"
gh issue close 16 --repo jhwanl046/ai-issue --comment "docs/에 반영 완료"
```

## 4. 결과 확인

```powershell
gh issue list --repo jhwanl046/ai-issue --state all --limit 100
```
