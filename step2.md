# STEP2 작업 명령어 목록

대상 레포지토리: `jhwanl046/ai-issue` (파이썬 통계 라이브러리 프로젝트 가정)
작업 디렉터리: `C:\Git Workspace\261106_revise`

## 0. 사전 확인

```powershell
gh auth status
git remote -v
git status --short
gh repo list --limit 100
```

## 1. 신규 레포지토리 생성 (이미 존재하는 경우 확인/클론)

```powershell
# 신규 생성 시도 (--public, README 포함)
gh repo create ai-issue --public --add-readme --description "ai-issue"

# 이미 존재할 때 확인
gh repo view jhwanl046/ai-issue --json name,description,isPrivate,url,defaultBranchRef,createdAt
gh issue list --repo jhwanl046/ai-issue

# 로컬 클론
git clone https://github.com/jhwanl046/ai-issue.git ai-issue
```

## 2. "배포됨" 이슈 생성

```powershell
gh issue create --repo jhwanl046/ai-issue --title "배포됨" --body "배포됨"
```

## 3. 라벨(Label) 생성

기본 라벨은 GitHub가 제공하므로, 아래는 추가 생성한 커스텀 라벨입니다.

```powershell
gh label create refactor      --repo jhwanl046/ai-issue --description "Code restructuring"    --color fbca04 2>$null
gh label create test          --repo jhwanl046/ai-issue --description "Testing"               --color bfd4f2 2>$null
gh label create data          --repo jhwanl046/ai-issue --description "Data handling"          --color c5def5 2>$null
gh label create visualization --repo jhwanl046/ai-issue --description "Charts/plots"           --color e99695 2>$null
gh label create priority:high   --repo jhwanl046/ai-issue --description "High priority"         --color b60205 2>$null
gh label create priority:medium --repo jhwanl046/ai-issue --description "Medium priority"      --color fbca04 2>$null
gh label create priority:low    --repo jhwanl046/ai-issue --description "Low priority"          --color 0e8a16 2>$null
```

라벨 확인:

```powershell
gh label list --repo jhwanl046/ai-issue
```

## 4. 마일스톤(Milestone) 생성 (2주치)

```powershell
# Week 1 (due 2026-11-13)
gh api repos/jhwanl046/ai-issue/milestones --method POST `
  --field title="Week 1 - Core implementation" `
  --field description="Basic structure, stats, data loader, tests/docs (week 1)" `
  --field due_on="2026-11-13T23:59:59Z"

# Week 2 (due 2026-11-20)
gh api repos/jhwanl046/ai-issue/milestones --method POST `
  --field title="Week 2 - Analysis and visualization" `
  --field description="Hypothesis tests, correlation/regression, visualization, CI/CD (week 2)" `
  --field due_on="2026-11-20T23:59:59Z"
```

마일스톤 확인:

```powershell
gh api repos/jhwanl046/ai-issue/milestones | ConvertFrom-Json | Select-Object number,title,open_issues,due_on
```

## 5. 예시 이슈 생성 (Week 1)

```powershell
gh issue create --repo jhwanl046/ai-issue --title "Scaffold project structure (pyproject.toml, src layout)" --body "Set up package layout, pyproject.toml, dependencies, and entry points for the Python statistics toolkit." --milestone "Week 1 - Core implementation" --label "enhancement,priority:high"

gh issue create --repo jhwanl046/ai-issue --title "Implement basic descriptive statistics (mean, median, mode, variance, std)" --body "Add core descriptive statistics functions with numerical stability." --milestone "Week 1 - Core implementation" --label "enhancement,priority:high"

gh issue create --repo jhwanl046/ai-issue --title "CSV/JSON data loader with type inference" --body "Implement data loading from CSV/JSON with automatic column type inference." --milestone "Week 1 - Core implementation" --label "enhancement,data"

gh issue create --repo jhwanl046/ai-issue --title "Add unit tests for stats module (pytest)" --body "Achieve >80% coverage on stats module." --milestone "Week 1 - Core implementation" --label "test"

gh issue create --repo jhwanl046/ai-issue --title "Write README and usage examples" --body "Document installation, quickstart, and example usage." --milestone "Week 1 - Core implementation" --label "documentation"

gh issue create --repo jhwanl046/ai-issue --title "Fix floating-point precision in variance calculation" --body "Variance shows small errors for large numbers; use Welford's algorithm." --milestone "Week 1 - Core implementation" --label "bug,priority:medium"

gh issue create --repo jhwanl046/ai-issue --title "Add docstrings and type hints across modules" --body "Improve IDE support and docs via type hints and docstrings." --milestone "Week 1 - Core implementation" --label "documentation,refactor"
```

## 6. 예시 이슈 생성 (Week 2)

```powershell
gh issue create --repo jhwanl046/ai-issue --title "Implement hypothesis tests (t-test, chi-square)" --body "Add t-test (one/two sample) and chi-square goodness-of-fit/independence." --milestone "Week 2 - Analysis and visualization" --label "enhancement,priority:high"

gh issue create --repo jhwanl046/ai-issue --title "Correlation and simple linear regression module" --body "Pearson/Spearman correlation and OLS simple linear regression." --milestone "Week 2 - Analysis and visualization" --label "enhancement"

gh issue create --repo jhwanl046/ai-issue --title "Visualization utilities (histogram, boxplot, scatter)" --body "Matplotlib/seaborn-based plotting helpers." --milestone "Week 2 - Analysis and visualization" --label "visualization"

gh issue create --repo jhwanl046/ai-issue --title "Set up GitHub Actions CI (lint, test)" --body "Run ruff + pytest on push/PR." --milestone "Week 2 - Analysis and visualization" --label "enhancement,refactor"

gh issue create --repo jhwanl046/ai-issue --title "Add sample datasets and tutorial notebook" --body "Bundle example datasets and a Jupyter tutorial." --milestone "Week 2 - Analysis and visualization" --label "documentation,data,good first issue"
```

## 7. 결과 확인

```powershell
gh issue list --repo jhwanl046/ai-issue --state all --limit 100
gh api repos/jhwanl046/ai-issue/milestones | python -c "import sys,json; d=json.load(sys.stdin); [print(m['number'], m['title'], 'open=', m['open_issues']) for m in d]"
```
