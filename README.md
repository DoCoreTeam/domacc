# DOCORE ADK — Agent Development Kit for Claude Code

> 16 AI Agents. One command. Full development pipeline.
>
> 16개 AI 에이전트. 명령 하나. 완전한 개발 파이프라인.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-ADK-blue)](https://claude.ai/code)

---

## What is DOCORE? / DOCORE란?

**EN** — DOCORE is an **Agent Development Kit (ADK)** for [Claude Code](https://claude.ai/code) that turns Claude into a **CEO orchestrator** managing 16 specialized AI agents — from business planning to deployment.

**KO** — DOCORE는 [Claude Code](https://claude.ai/code)용 **에이전트 개발 키트(ADK)**입니다. Claude를 **CEO 오케스트레이터**로 전환하여 기획부터 배포까지 16개의 전문 AI 에이전트를 관리합니다.

One command triggers the full pipeline / 명령 하나로 전체 파이프라인이 실행됩니다:

```bash
/ceo "Build a SaaS todo app with authentication and payments"
/ceo "인증과 결제 기능이 있는 SaaS 투두앱 만들어줘"
```

**EN** — Before executing, CEO always asks clarifying questions first (tech stack, platform, completion criteria, constraints). No blind execution.

**KO** — 실행 전 CEO가 먼저 핵심 질문을 합니다 (기술스택, 플랫폼, 완료 기준, 제약사항). 묻지도 않고 실행하지 않습니다.

---

## Quick Install / 빠른 설치

```bash
curl -sSL https://raw.githubusercontent.com/DoCoreTeam/docore/main/docore/install.sh | bash
```

**EN** — The installer automatically sets up everything in one shot:
1. 16 DOCORE agents → `~/.claude/agents/`
2. `/ceo`, `/ceo-init`, `/ceo-status` → `~/.claude/commands/`
3. CEO skill → `~/.claude/skills/ceo-system/`
4. `~/.claude/CLAUDE.md` (auto-loaded on every Claude Code session)
5. **ECC (Everything Claude Code)** — 183 skills + 79 commands agents rely on → `~/.claude/skills/` + `~/.claude/commands/`
6. **gstack** → `~/.claude/skills/gstack/` (skipped if already installed)
7. **Superpowers** → installed via `claude plugin` or GitHub fallback (skipped if already present)

Then open any project in Claude Code — CEO mode activates automatically. Run `/ceo-init` to initialize the project.

**KO** — 설치 스크립트가 한 번에 모든 것을 자동 설치합니다:
1. DOCORE 에이전트 16개 → `~/.claude/agents/`
2. `/ceo`, `/ceo-init`, `/ceo-status` → `~/.claude/commands/`
3. CEO 스킬 → `~/.claude/skills/ceo-system/`
4. `~/.claude/CLAUDE.md` (Claude Code 세션마다 자동 로드)
5. **ECC (Everything Claude Code)** — 에이전트가 의존하는 스킬 183개 + 커맨드 79개 자동 설치
6. **gstack** → `~/.claude/skills/gstack/` (이미 설치된 경우 스킵)
7. **Superpowers** → `claude plugin`으로 설치 시도, 불가 시 GitHub fallback (이미 설치된 경우 스킵)

설치 후 Claude Code에서 아무 프로젝트나 열면 CEO 모드가 자동 활성화됩니다. `/ceo-init`으로 프로젝트를 초기화하세요.

---

## How It Works / 작동 방식

```
/ceo "task"
     │
     ▼
⓪ Q&A ──── CEO asks 3~7 clarifying questions before any work
     │       CEO가 3~7개 질문 후 답변 받으면 진행
     │       (tech stack / platform / done criteria / constraints)
     │       (기술스택 / 플랫폼 / 완료기준 / 제약)
     │
     ▼
① PLANNER ── DC-BIZ + DC-RES + DC-OSS → PLAN.md
     │
     ▼
② GENERATOR (parallel / 병렬)
     │  DC-DEV-FE + DC-DEV-BE + DC-DEV-DB + DC-DEV-MOB
     │  DC-DEV-OPS + DC-DEV-INT + DC-WRT + DC-DOC + DC-SEO
     │
     ▼  ┌─────────────────────────────────────────┐
③ CYCLE │  IMPLEMENT → CODE REVIEW → TEST          │
     │  │      └─ bug found → FIX → REVIEW → TEST │  max 3x / 최대 3회
     │  │      └─ pass → next                      │
     │  └─────────────────────────────────────────┘
     │
     ▼
④ GATE 1-5
     │  GATE 1: error patterns + 300-line file limit / 금지패턴 + 300줄 초과 차단
     │  GATE 2: completion check / 완료조건
     │  GATE 3: version tag v0.0.0 / 버전태그
     │  GATE 4: builder ≠ reviewer / 역할분리
     │  GATE 5: breaking change detection / 브레이킹 체인지 감지
     │
     ▼
⑤ REPORT ── code + tests + docs + git commit v0.x.0
```

---

## 16 Agents / 16개 에이전트

| Phase / 단계 | Agent | Role (EN) | 역할 (KO) | Model |
|------|-------|-----------|-----------|-------|
| PLANNER | DC-BIZ | Business Judge | 사업 타당성 판단 | Opus |
| PLANNER | DC-RES | Researcher | 리서치 | Haiku |
| PLANNER | DC-OSS | Open Source Scout | 오픈소스 탐색 | Opus |
| GENERATOR | DC-DEV-FE | Frontend Developer | 프론트엔드 개발 | Sonnet |
| GENERATOR | DC-DEV-BE | Backend Developer | 백엔드 개발 | Sonnet |
| GENERATOR | DC-DEV-DB | Database Engineer | 데이터베이스 설계 | Sonnet |
| GENERATOR | DC-DEV-MOB | Mobile Developer | 모바일 개발 | Sonnet |
| GENERATOR | DC-DEV-OPS | DevOps Engineer | DevOps / 인프라 | Sonnet |
| GENERATOR | DC-DEV-INT | Integration Engineer | 외부 API 연동 | Sonnet |
| GENERATOR | DC-WRT | Writer / Copywriter | 카피라이팅 | Sonnet |
| GENERATOR | DC-DOC | Documentation Writer | 문서 작성 | Haiku |
| GENERATOR | DC-SEO | SEO / AEO / GEO Specialist | SEO 최적화 | Haiku |
| EVALUATOR | DC-QA | QA Engineer | 품질 검증 | Haiku |
| EVALUATOR | DC-SEC | Security Reviewer | 보안 검토 | Opus |
| EVALUATOR | DC-REV | Code Reviewer | 코드 리뷰 | Opus |
| SUPPORT | DC-TOK | Token Optimizer | 토큰 비용 최적화 | Haiku |

---

## Commands / 명령어

DOCORE ADK installs commands from three sources: DOCORE (CEO system), ECC (Everything Claude Code), and gstack.

DOCORE ADK는 세 가지 소스에서 커맨드를 설치합니다: DOCORE(CEO 시스템), ECC, gstack.

### DOCORE Commands (CEO System)

| Command | Description (EN) | 설명 (KO) |
|---------|-----------------|-----------|
| `/ceo "task"` | Q&A → full pipeline: PLANNER → GENERATOR → EVALUATOR → GATE → REPORT | Q&A 후 전체 파이프라인 실행 (16개 에이전트) |
| `/ceo-init` | Initialize project — create registries, harness, CLAUDE.md | 프로젝트 최초 셋업 (레지스트리 + 하네스 초기화) |
| `/ceo-status` | Show current project status, active agents, and gate results | 현재 프로젝트 상태 / 활성 에이전트 / 게이트 결과 조회 |

### Development Commands (ECC)

#### Code Review & Quality
| Command | Description |
|---------|-------------|
| `/code-review` | Review local uncommitted changes or GitHub PR (pass PR number/URL) |
| `/review-pr` | Comprehensive PR review using specialized agents |
| `/security-review` | Security audit — OWASP Top 10, secrets, injection, auth |
| `/quality-gate` | Run all quality gates and report status |
| `/santa-loop` | Adversarial dual-review loop — two independent reviewers must both approve |
| `/refactor-clean` | Remove dead code, consolidate duplicates, clean unused imports |
| `/perf-check` | Performance analysis — bottlenecks, bundle size, runtime speed |
| `/test-coverage` | Analyze test coverage and identify gaps |

#### Build & Fix
| Command | Description |
|---------|-------------|
| `/build-fix` | Diagnose and fix build errors incrementally |
| `/go-build` | Fix Go build errors, go vet warnings, linter issues |
| `/rust-build` | Fix Rust build errors, borrow checker, Cargo issues |
| `/cpp-build` | Fix C++ build errors, CMake issues, linker problems |
| `/flutter-build` | Fix Dart analyzer errors and Flutter build failures |
| `/kotlin-build` | Fix Kotlin/Gradle build errors, compiler warnings |
| `/gradle-build` | Fix Gradle build errors for Android and KMP projects |

#### Test & TDD
| Command | Description |
|---------|-------------|
| `/tdd` | TDD workflow — write test first (RED), implement (GREEN), refactor |
| `/test` | Run tests and report failures |
| `/e2e` | End-to-end testing with Playwright |
| `/go-test` | TDD for Go — table-driven tests, 80%+ coverage with go test |
| `/rust-test` | TDD for Rust — write tests first, verify with cargo-llvm-cov |
| `/cpp-test` | TDD for C++ — GoogleTest first, then implement |
| `/flutter-test` | Flutter/Dart tests — unit, widget, golden, integration |
| `/kotlin-test` | TDD for Kotlin — Kotest first, verify with Kover |

#### Code Review (Language-specific)
| Command | Description |
|---------|-------------|
| `/python-review` | Python code review — PEP 8, type hints, security, idioms |
| `/go-review` | Go code review — idiomatic patterns, concurrency, error handling |
| `/rust-review` | Rust code review — ownership, lifetimes, unsafe, idioms |
| `/cpp-review` | C++ code review — memory safety, modern idioms, concurrency |
| `/flutter-review` | Flutter/Dart review — widget best practices, state management |
| `/kotlin-review` | Kotlin review — null safety, coroutine safety, Compose |

#### Planning & Feature Development
| Command | Description |
|---------|-------------|
| `/plan` | Create step-by-step implementation plan. Waits for user confirmation before touching code |
| `/feature-dev` | Guided feature development with codebase analysis and architecture focus |
| `/implement` | Execute an implementation plan |
| `/spec` | Generate technical specification for a feature |
| `/prp-prd` | Interactive PRD generator — problem-first, hypothesis-driven product spec |
| `/prp-plan` | Comprehensive feature implementation plan with codebase pattern extraction |
| `/prp-implement` | Execute a PRP implementation plan with rigorous validation loops |
| `/prp-commit` | Quick commit with natural language file targeting |
| `/prp-pr` | Create GitHub PR from current branch with unpushed commits |
| `/multi-plan` | Multi-model collaborative planning |
| `/multi-execute` | Multi-model collaborative execution |
| `/multi-frontend` | Frontend-focused multi-model development |
| `/multi-backend` | Backend-focused multi-model development |
| `/multi-workflow` | Full multi-model collaborative workflow |

#### Design & UI
| Command | Description |
|---------|-------------|
| `/design` | Design system and UI generation |
| `/ui-design` | UI component design and generation |

#### Debugging & Investigation
| Command | Description |
|---------|-------------|
| `/debug` | Diagnose and fix bugs systematically |
| `/evaluate-oss` | Evaluate open source library quality and fit |

#### Session & Context Management
| Command | Description |
|---------|-------------|
| `/save-session` | Save current session state to `~/.claude/session-data/` for future resume |
| `/resume-session` | Load most recent session and resume with full context |
| `/sessions` | Manage Claude Code session history and metadata |
| `/checkpoint` | Save a checkpoint of current progress |
| `/context-budget` | Monitor and manage context window usage |
| `/aside` | Answer a quick side question without losing current task context |
| `/s` | Orchestration workflow shortcut |

#### Learning & Instincts
| Command | Description |
|---------|-------------|
| `/learn` | Extract reusable patterns from current session |
| `/learn-eval` | Extract patterns, self-evaluate quality, save to global or project scope |
| `/evolve` | Analyze instincts and suggest evolved structures |
| `/instinct-status` | Show learned instincts (project + global) with confidence scores |
| `/instinct-import` | Import instincts from file or URL |
| `/instinct-export` | Export instincts to file |
| `/promote` | Promote project-scoped instincts to global scope |
| `/prune` | Delete stale pending instincts older than 30 days |
| `/projects` | List known projects and instinct statistics |

#### Hooks & Automation
| Command | Description |
|---------|-------------|
| `/hookify` | Create hooks from conversation analysis to prevent unwanted behaviors |
| `/hookify-configure` | Enable or disable hookify rules interactively |
| `/hookify-help` | Get help with the hookify system |
| `/hookify-list` | List all configured hookify rules |

#### DevOps & Deployment
| Command | Description |
|---------|-------------|
| `/pipeline` | Set up CI/CD pipeline |
| `/pm2` | Initialize and configure PM2 process manager |
| `/setup-pm` | Configure preferred package manager (npm/pnpm/yarn/bun) |
| `/devfleet` | Claude DevFleet multi-agent deployment |
| `/promote` | Promote instincts or changes to global scope |

#### Docs & Reporting
| Command | Description |
|---------|-------------|
| `/docs` | Documentation lookup via Context7 |
| `/update-docs` | Update project documentation |
| `/update-codemaps` | Regenerate codebase codemaps |
| `/report` | Generate project status report |

#### Cost & Performance
| Command | Description |
|---------|-------------|
| `/cost-estimate` | Estimate token cost before running expensive operations |
| `/model-route` | Route tasks to the optimal model (Haiku/Sonnet/Opus) |
| `/prompt-optimize` | Optimize prompts to reduce cost and improve accuracy |

#### Loop & Orchestration
| Command | Description |
|---------|-------------|
| `/loop-start` | Start a recurring agent loop on an interval |
| `/loop-status` | Show status of running loops |
| `/orchestrate` | Multi-agent orchestration workflow |
| `/santa-loop` | Adversarial dual-review convergence loop |

#### Misc
| Command | Description |
|---------|-------------|
| `/jira` | Retrieve Jira ticket, update status, add comments |
| `/skill-create` | Analyze git history to extract patterns and generate SKILL.md |
| `/skill-health` | Show skill portfolio health dashboard |
| `/agent-sort` | Sort and prioritize agents for a task |
| `/rules-distill` | Distill project rules from codebase patterns |
| `/claw` | nanoclaw REPL shortcut |
| `/ceo-init` | Project initialization (also listed under DOCORE) |

### gstack Commands

gstack provides battle-tested workflows for shipping code.

| Command | Description |
|---------|-------------|
| `/ship` | Full ship workflow — test, build, review, deploy |
| `/qa` | QA the running app — browser, flows, screenshots, bugs |
| `/qa-only` | QA without shipping |
| `/investigate` | Diagnose bugs, errors, 500s with evidence |
| `/review` | Code review for current diff |
| `/health` | Project health check — code quality, coverage, security |
| `/plan` | Plan a feature with interactive Q&A (gstack version) |
| `/design` | Design system, brand, and component guidance |
| `/design-review` | Visual design review and polish |
| `/design-consultation` | Design consultation and direction |
| `/design-html` | Generate HTML/CSS from design specs |
| `/design-shotgun` | Rapid design exploration — multiple directions at once |
| `/docs` | Update or generate documentation (gstack version) |
| `/document-release` | Update docs after shipping |
| `/learn` | Extract and save learnings from session (gstack version) |
| `/retro` | Weekly retrospective |
| `/checkpoint` | Save a progress checkpoint (gstack version) |
| `/freeze` | Freeze — stop all changes to a file or module |
| `/unfreeze` | Unfreeze a file or module |
| `/canary` | Deploy a canary release |
| `/guard` | Add guards to prevent regressions |
| `/careful` | Enable extra-careful mode for sensitive changes |
| `/browse` | Open and inspect a URL in the browser |
| `/connect-chrome` | Connect to a running Chrome instance |
| `/setup-deploy` | Set up deployment configuration |
| `/setup-browser-cookies` | Configure browser session cookies |
| `/benchmark` | Run performance benchmarks |
| `/autoplan` | Auto-generate implementation plan from context |
| `/office-hours` | Office hours — brainstorm, product ideas, feasibility |
| `/investigate` | Investigate bugs and errors with root cause analysis |
| `/land-and-deploy` | Land changes and deploy to production |
| `/codex` | Code exploration and understanding |
| `/cso` | Chief of Staff — communication triage and management |
| `/plan-ceo-review` | CEO-level plan review |
| `/plan-eng-review` | Engineering architecture review |
| `/plan-design-review` | Design review at plan stage |
| `/test` | Run tests (gstack version) |
| `/gstack-upgrade` | Upgrade gstack to the latest version |

---

## Quality Gates / 품질 게이트

**EN** — Every output passes 5 gates before delivery.

**KO** — 모든 산출물은 5개 게이트를 통과한 후 사용자에게 전달됩니다.

| Gate | Check (EN) | 검사 항목 (KO) |
|------|------------|---------------|
| GATE 1 | Error registry pattern scan + **file exceeds 300 lines** | 알려진 오류 패턴 차단 + **파일 300줄 초과 차단** |
| GATE 2 | Completion criteria verification | 완료 조건 충족 여부 |
| GATE 3 | Version tag `v0.0.0` present | 버전 태그 존재 여부 |
| GATE 4 | Builder ≠ Reviewer (role separation) | 개발자 ≠ 리뷰어 역할 분리 |
| GATE 5 | Breaking change detection | 브레이킹 체인지 감지 |

---

## Coding Standards / 코딩 표준

**EN** — Enforced on every file generated by agents.

**KO** — 에이전트가 생성하는 모든 파일에 강제 적용됩니다.

| Rule | EN | KO |
|------|----|----|
| File size | **300 lines max** (GATE 1 auto-blocks) | **파일당 300줄 이하** (GATE 1 자동 차단) |
| Function size | 50 lines max | 함수당 50줄 이하 |
| Nesting depth | 4 levels max | 중첩 4단계 이하 |
| Immutability | Always create new objects | 항상 새 객체 생성, 기존 객체 변경 금지 |
| Error handling | Explicit at every level | 모든 레벨에서 명시적 처리 |
| Input validation | Validate at all system boundaries | 모든 시스템 경계에서 검증 |

---

## Security Built-in / 내장 보안

- OWASP Top 10 review on every sprint / 매 스프린트 OWASP Top 10 검토
- JWT httpOnly cookies only (no localStorage) / JWT는 httpOnly 쿠키만 사용
- AES-256-GCM for PII encryption / 개인정보 AES-256-GCM 암호화
- Rate limiting on all endpoints / 모든 엔드포인트 레이트 리미팅
- Input validation with Zod / Zod 기반 입력 검증
- RLS (Row Level Security) enforcement / RLS 필수 구현

---

## What Gets Installed / 설치 후 구조

**EN** — The installer places each file exactly where Claude Code expects it.

**KO** — 설치 스크립트가 Claude Code가 인식하는 위치에 정확히 파일을 배치합니다.

```
~/.claude/
├── CLAUDE.md                    ← Auto-loaded on every session / 세션마다 자동 로드
├── agents/
│   ├── dc-biz.md                ← Recognized as agents by Claude Code
│   ├── dc-dev-be.md               Claude Code가 에이전트로 인식
│   └── ... (16 total / 16개)
├── commands/
│   ├── ceo.md                   ← Becomes /ceo slash command
│   ├── ceo-init.md                /ceo 슬래시 명령어로 등록
│   └── ceo-status.md
├── skills/
│   ├── ceo-system/
│   │   └── SKILL.md             ← CEO orchestration brain / CEO 오케스트레이션
│   ├── gstack/                  ← Auto-installed / 자동 설치
│   └── superpowers/             ← Auto-installed (plugin or GitHub) / 자동 설치
├── error-registry.md            ← Gate 1 error pattern log
├── skill-registry.md
├── project-registry.md
└── decision-log.md
```

## Repository Structure / 저장소 구조

```
docore/                          ← Source package (repo)
├── CLAUDE.md                    ← Copied to ~/.claude/CLAUDE.md
├── install.sh                   ← Installer / 설치 스크립트
├── agents/                      ← Copied to ~/.claude/agents/
│   ├── dc-biz.md
│   └── ... (16 total)
├── commands/                    ← Copied to ~/.claude/commands/
│   ├── ceo.md
│   ├── ceo-init.md
│   └── ceo-status.md
├── skills/ceo-system/           ← Copied to ~/.claude/skills/ceo-system/
│   └── SKILL.md
└── templates/                   ← Copied to ~/.claude/*.md
    ├── error-registry.md
    ├── skill-registry.md
    ├── project-registry.md
    └── decision-log.md
```

---

## Manual Install / 수동 설치

```bash
git clone https://github.com/DoCoreTeam/docore.git /tmp/docore
bash /tmp/docore/docore/install.sh
```

---

## Dependencies / 의존성

DOCORE relies on three external skill systems. The installer handles all automatically.

DOCORE는 세 가지 외부 스킬 시스템에 의존합니다. 설치 스크립트가 자동으로 처리합니다.

| Dependency | Repo | What it provides | Installed to |
|------------|------|-----------------|-------------|
| **ECC** | [affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code) | 183 skills + 79 commands agents rely on | `~/.claude/skills/` + `~/.claude/commands/` |
| **gstack** | [garrytan/gstack](https://github.com/garrytan/gstack) | Garry Tan's 23-tool Claude Code setup | `~/.claude/skills/gstack/` |
| **Superpowers** | obra/superpowers-marketplace | Claude Code plugin marketplace superpowers | via `claude plugin` or `~/.claude/skills/superpowers/` |

**EN** — All three are installed automatically by the installer. No manual steps needed.

**KO** — 설치 스크립트가 세 가지 모두 자동 설치합니다. 별도 작업 불필요.

---

## Requirements / 요구사항

- [Claude Code](https://claude.ai/code) CLI
- Anthropic API key with access to Claude Opus, Sonnet, and Haiku
- Anthropic API 키 (Opus, Sonnet, Haiku 모델 접근 권한 필요)

---

## License / 라이선스

MIT — see [LICENSE](LICENSE)

---

## Author / 만든 사람

Built by **Docore** / DoCoreTeam
