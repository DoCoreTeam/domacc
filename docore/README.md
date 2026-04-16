# 🏢 DOCORE — 16 AI Agents Orchestration for Claude Code

> One command. All agents. Full pipeline. Every time.

```bash
/ceo "Build a todo app with authentication"
```

This single command activates **16 specialized AI agents** that plan, develop, test, and deploy your project — in the correct development order, with no steps skipped.

> Before executing, CEO always asks clarifying questions first (tech stack, platform, completion criteria). No blind execution.
> 실행 전 CEO가 먼저 핵심 질문을 합니다. 묻지도 않고 실행하지 않습니다.

## ⚡ Install

```bash
# One-line install
curl -sSL https://raw.githubusercontent.com/DoCoreTeam/docore/main/docore/install.sh | bash

# Or manual
git clone https://github.com/DoCoreTeam/docore.git /tmp/docore && bash /tmp/docore/docore/install.sh
```

Installs automatically: **16 DOCORE agents** + **/ceo commands** + **ECC (183 skills)** + **gstack** + **Superpowers**
자동 설치: **16개 에이전트** + **/ceo 커맨드** + **ECC (183개 스킬)** + **gstack** + **Superpowers**

## 🎯 How It Works

You type one command → CEO asks questions → then orchestrates everything:

```
/ceo "원하는 것"
     │
     ▼
⓪ Q&A ──── CEO가 3~7개 질문 (기술스택, 플랫폼, 완료기준, 제약)
     │       답변 후 → [Q&A COMPLETE] → 파이프라인 시작
     ▼
① PLANNER ──── DC-BIZ (사업판단) + DC-RES (리서치) + DC-OSS (라이브러리)
     │            → PLAN.md 산출
     ▼
② GENERATOR ── DC-DEV-FE + DC-DEV-BE + DC-DEV-DB + DC-DEV-MOB
     │          DC-DEV-OPS + DC-DEV-INT + DC-WRT + DC-DOC + DC-SEO
     │            → 병렬 개발
     ▼
③ EVALUATOR ── DC-QA (테스트) + DC-SEC (보안) + DC-REV (리뷰)
     │            → FAIL이면 ②로 재작업 (최대 3회)
     ▼
④ GATE 1-5 ── 금지패턴 + 완료조건 + 버전태그 + 역할분리 + 변경감지
     │
     ▼
⑤ CEO REPORT ─ 완성된 코드 + 테스트 + 문서 + git commit v0.x.0
```

## 📋 Commands

### DOCORE (CEO System)

| Command | What it does |
|---------|-------------|
| `/ceo "task"` | Q&A → full pipeline with all 16 agents (PLANNER→GENERATOR→EVALUATOR→GATE→REPORT) |
| `/ceo-init` | Initialize project — registries, harness, CLAUDE.md |
| `/ceo-status` | Show current project status, gate results, active agents |

### Development (ECC — Everything Claude Code)

| Command | Category | What it does |
|---------|----------|-------------|
| `/plan` | Planning | Step-by-step implementation plan, waits for confirm before coding |
| `/feature-dev` | Planning | Guided feature development with codebase analysis |
| `/prp-prd` | Planning | Interactive PRD generator — problem-first product spec |
| `/prp-plan` | Planning | Comprehensive implementation plan with pattern extraction |
| `/prp-implement` | Planning | Execute PRP plan with validation loops |
| `/prp-pr` | Planning | Create GitHub PR from current branch |
| `/prp-commit` | Planning | Smart commit with natural language file targeting |
| `/multi-plan` | Planning | Multi-model collaborative planning |
| `/multi-execute` | Planning | Multi-model collaborative execution |
| `/multi-frontend` | Planning | Frontend-focused multi-model development |
| `/multi-backend` | Planning | Backend-focused multi-model development |
| `/multi-workflow` | Planning | Full multi-model collaborative workflow |
| `/code-review` | Review | Review local changes or GitHub PR |
| `/review-pr` | Review | Comprehensive PR review with specialized agents |
| `/security-review` | Review | OWASP Top 10, secrets, injection, auth audit |
| `/python-review` | Review | Python — PEP 8, type hints, security, idioms |
| `/go-review` | Review | Go — idiomatic patterns, concurrency, error handling |
| `/rust-review` | Review | Rust — ownership, lifetimes, unsafe, idioms |
| `/cpp-review` | Review | C++ — memory safety, modern idioms, concurrency |
| `/flutter-review` | Review | Flutter/Dart — widgets, state management, performance |
| `/kotlin-review` | Review | Kotlin — null safety, coroutines, Compose |
| `/quality-gate` | Quality | Run all quality gates |
| `/santa-loop` | Quality | Adversarial dual-review — two reviewers must both approve |
| `/refactor-clean` | Quality | Remove dead code, consolidate duplicates |
| `/perf-check` | Quality | Performance analysis — bottlenecks, bundle size |
| `/test-coverage` | Quality | Analyze coverage gaps |
| `/tdd` | Test | TDD workflow — RED → GREEN → REFACTOR |
| `/test` | Test | Run tests and report failures |
| `/e2e` | Test | End-to-end testing with Playwright |
| `/go-test` | Test | TDD for Go — table-driven, 80%+ coverage |
| `/rust-test` | Test | TDD for Rust — cargo-llvm-cov |
| `/cpp-test` | Test | TDD for C++ — GoogleTest |
| `/flutter-test` | Test | Flutter — unit, widget, golden, integration |
| `/kotlin-test` | Test | TDD for Kotlin — Kotest + Kover |
| `/build-fix` | Build | Fix build errors incrementally |
| `/go-build` | Build | Fix Go build, vet, linter issues |
| `/rust-build` | Build | Fix Rust build, borrow checker, Cargo |
| `/cpp-build` | Build | Fix C++ build, CMake, linker |
| `/flutter-build` | Build | Fix Dart analyzer, Flutter build |
| `/kotlin-build` | Build | Fix Kotlin/Gradle, compiler warnings |
| `/gradle-build` | Build | Fix Gradle for Android and KMP |
| `/debug` | Debug | Diagnose and fix bugs systematically |
| `/investigate` | Debug | Root cause analysis with evidence |
| `/design` | Design | Design system and UI generation |
| `/ui-design` | Design | UI component design |
| `/save-session` | Session | Save session state for future resume |
| `/resume-session` | Session | Load last session and resume with full context |
| `/sessions` | Session | Manage session history and metadata |
| `/checkpoint` | Session | Save a progress checkpoint |
| `/context-budget` | Session | Monitor context window usage |
| `/aside` | Session | Quick side question without losing task context |
| `/learn` | Learning | Extract reusable patterns from session |
| `/learn-eval` | Learning | Extract and self-evaluate patterns before saving |
| `/evolve` | Learning | Analyze instincts and suggest improvements |
| `/instinct-status` | Learning | Show learned instincts with confidence scores |
| `/instinct-import` | Learning | Import instincts from file or URL |
| `/instinct-export` | Learning | Export instincts to file |
| `/promote` | Learning | Promote project instincts to global scope |
| `/prune` | Learning | Delete stale instincts older than 30 days |
| `/hookify` | Hooks | Create hooks from conversation analysis |
| `/hookify-configure` | Hooks | Enable/disable hookify rules |
| `/hookify-help` | Hooks | Get help with hookify system |
| `/hookify-list` | Hooks | List all configured hookify rules |
| `/pipeline` | DevOps | Set up CI/CD pipeline |
| `/pm2` | DevOps | Initialize PM2 process manager |
| `/setup-pm` | DevOps | Configure package manager (npm/pnpm/yarn/bun) |
| `/devfleet` | DevOps | Claude DevFleet multi-agent deployment |
| `/docs` | Docs | Documentation lookup via Context7 |
| `/update-docs` | Docs | Update project documentation |
| `/update-codemaps` | Docs | Regenerate codebase codemaps |
| `/report` | Docs | Generate project status report |
| `/cost-estimate` | Cost | Estimate token cost before operations |
| `/model-route` | Cost | Route tasks to optimal model |
| `/prompt-optimize` | Cost | Optimize prompts for cost and accuracy |
| `/loop-start` | Loop | Start a recurring agent loop |
| `/loop-status` | Loop | Show status of running loops |
| `/orchestrate` | Loop | Multi-agent orchestration |
| `/jira` | Misc | Retrieve Jira ticket, update status |
| `/skill-create` | Misc | Generate SKILL.md from git history |
| `/skill-health` | Misc | Skill portfolio health dashboard |
| `/rules-distill` | Misc | Distill rules from codebase patterns |
| `/agent-sort` | Misc | Sort and prioritize agents |
| `/evaluate-oss` | Misc | Evaluate open source library fit |
| `/spec` | Misc | Generate technical specification |

### gstack Commands

| Command | What it does |
|---------|-------------|
| `/ship` | Full ship workflow — test, build, review, deploy |
| `/qa` | QA the running app — browser, flows, screenshots |
| `/qa-only` | QA without shipping |
| `/investigate` | Diagnose bugs and errors with root cause |
| `/review` | Code review for current diff |
| `/health` | Project health — quality, coverage, security |
| `/plan` | Plan a feature with interactive Q&A |
| `/design` | Design system, brand, component guidance |
| `/design-review` | Visual design review and polish |
| `/design-consultation` | Design direction consultation |
| `/design-html` | Generate HTML/CSS from design specs |
| `/design-shotgun` | Rapid multi-direction design exploration |
| `/docs` | Update or generate documentation |
| `/document-release` | Update docs after shipping |
| `/learn` | Extract and save session learnings |
| `/retro` | Weekly retrospective |
| `/checkpoint` | Save a progress checkpoint |
| `/freeze` | Freeze a file/module — stop all changes |
| `/unfreeze` | Unfreeze a frozen file or module |
| `/canary` | Deploy a canary release |
| `/guard` | Add guards against regressions |
| `/careful` | Enable extra-careful mode for sensitive changes |
| `/browse` | Open and inspect a URL in the browser |
| `/connect-chrome` | Connect to a running Chrome instance |
| `/setup-deploy` | Set up deployment configuration |
| `/setup-browser-cookies` | Configure browser session cookies |
| `/benchmark` | Run performance benchmarks |
| `/autoplan` | Auto-generate implementation plan from context |
| `/office-hours` | Brainstorm, product ideas, feasibility check |
| `/land-and-deploy` | Land changes and deploy to production |
| `/codex` | Code exploration and understanding |
| `/cso` | Chief of Staff — communication triage |
| `/plan-ceo-review` | CEO-level plan review |
| `/plan-eng-review` | Engineering architecture review |
| `/plan-design-review` | Design review at plan stage |
| `/test` | Run tests |
| `/gstack-upgrade` | Upgrade gstack to the latest version |

## 🤖 16 Agents

### PLANNER (기획)
| Agent | Role | Model |
|-------|------|-------|
| DC-BIZ | Business Judge | Opus |
| DC-RES | Researcher | Haiku |
| DC-OSS | Open Source Scout | Opus |

### GENERATOR (개발)
| Agent | Role | Model |
|-------|------|-------|
| DC-DEV-FE | Frontend Developer | Sonnet |
| DC-DEV-BE | Backend Developer | Sonnet |
| DC-DEV-DB | Database Engineer | Sonnet |
| DC-DEV-MOB | Mobile Developer | Sonnet |
| DC-DEV-OPS | DevOps Engineer | Sonnet |
| DC-DEV-INT | Integration Engineer | Sonnet |
| DC-WRT | Writer/Copywriter | Sonnet |
| DC-DOC | Documentation Writer | Haiku |
| DC-SEO | SEO/AEO/GEO Specialist | Haiku |

### EVALUATOR (검증)
| Agent | Role | Model |
|-------|------|-------|
| DC-QA | QA Engineer | Haiku |
| DC-SEC | Security Reviewer | Opus |
| DC-REV | Code/Content Reviewer | Opus |

### SUPPORT (지원)
| Agent | Role | Model |
|-------|------|-------|
| DC-TOK | Token Optimizer | Haiku |

## 🔧 Quality Gates

Every output passes through 5 gates before delivery:

- **GATE 1**: Error registry pattern scan
- **GATE 2**: Completion criteria verification
- **GATE 3**: Version tag (v0.0.0) check
- **GATE 4**: Builder ≠ Reviewer separation
- **GATE 5**: Breaking change detection

## 📁 Structure

```
docore/
├── CLAUDE.md                    ← Entry point (auto-loaded)
├── install.sh                   ← One-line installer
├── skills/ceo-system/SKILL.md   ← CEO brain (full system)
├── agents/                      ← 16 agent definitions
│   ├── dc-biz.md ... dc-tok.md
├── commands/                    ← Slash commands
│   ├── ceo.md                   ← /ceo "task"
│   ├── ceo-init.md              ← /ceo-init
│   └── ceo-status.md            ← /ceo-status
└── templates/                   ← Registry templates
    ├── error-registry.md
    ├── skill-registry.md
    ├── project-registry.md
    └── decision-log.md
```

## 🛡️ Security Built-in

- OWASP Top 10 review on every sprint
- JWT httpOnly cookies only (no localStorage)
- AES-256-GCM for PII encryption
- Rate limiting on all endpoints
- Input validation with Zod
- RLS (Row Level Security) enforcement

## 📄 License

MIT

## 🙋 Author

Built by **Docore** — CEO of KDC (Korea Digital Certification)
