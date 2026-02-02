# 8. Skills & Agents 가이드

[← 목차로 돌아가기](../../README-KR.md)

---

Skills과 Agents는 Claude Code의 기능을 확장하는 도구입니다.

---

## Skills이란?

Skills은 Claude Code가 **특정 작업을 더 잘 수행**할 수 있도록 도와주는 추가 기능입니다.

```
┌─────────────────────────────────────────────────────────────┐
│  💡 Skills 작동 방식                                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Skills은 Claude Code에 기본 내장되어 있습니다.                 │
│  별도 설치가 필요 없습니다!                                    │
│                                                             │
│  작동 방식:                                                  │
│  • 자동 활성화: 요청 내용에 따라 자동으로 적용됨                  │
│  • 수동 활성화: /명령어로 직접 호출                             │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 자주 사용하는 Skills

### 자동 활성화 Skills (요청하면 알아서 적용)

| Skill | 용도 | 자동 활성화 조건 |
|-------|------|------------------|
| `frontend-design` | 웹 UI/UX 디자인 | "웹페이지", "랜딩페이지", "UI" 등 요청 시 |
| `web-artifacts-builder` | React 웹 앱 생성 | "React 앱", "웹 앱" 등 요청 시 |
| `security-review` | 보안 검토 | 인증, 로그인, API 코드 작성 시 |

**예시:**
```
> 회사 소개 웹페이지를 만들어줘
  → frontend-design 자동 적용!

> React로 대시보드를 만들어줘
  → web-artifacts-builder 자동 적용!
```

---

### 수동 활성화 Skills (명령어로 호출)

| Skill | 용도 | 호출 방법 |
|-------|------|-----------|
| `tdd-workflow` | 테스트 주도 개발 | `/tdd 기능설명` |
| `doc-coauthoring` | 문서 공동 작성 | 문서 작성 요청 시 |

**예시:**
```
> /tdd 로그인 기능을 만들어줘
  → 테스트 코드 먼저 작성 후 구현
```

---

### 문서 관련 Skills

| Skill | 용도 | 지원 형식 |
|-------|------|-----------|
| `pdf` | PDF 생성/편집 | `.pdf` |
| `docx` | Word 문서 | `.docx` |
| `pptx` | 프레젠테이션 | `.pptx` |
| `xlsx` | 스프레드시트 | `.xlsx`, `.csv` |

**예시:**
```
> 이 데이터를 엑셀 파일로 저장해줘
  → xlsx skill 활성화
```

---

## Agents란?

Agents는 **특화된 역할을 수행하는 AI 전문가**입니다.

```
┌─────────────────────────────────────────────────────────────┐
│  💡 Agents 작동 방식                                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Agents도 Claude Code에 기본 내장되어 있습니다.                 │
│  별도 설치가 필요 없습니다!                                     │
│                                                             │
│  Claude Code가 필요에 따라 자동으로 적절한 Agent를               │
│  선택하여 작업을 수행합니다.                                    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 주요 Agents

| Agent | 역할 | 언제 사용되나요? |
|-------|------|------------------|
| `planner` | 구현 계획 수립 | 복잡한 기능을 요청할 때 |
| `frontend-engineer` | UI/UX 개발 | 웹 컴포넌트 개발할 때 |
| `code-reviewer` | 코드 리뷰 | 코드 품질 검토할 때 |
| `security-reviewer` | 보안 검토 | 보안 관련 코드 작성할 때 |
| `document-writer` | 문서 작성 | README, 가이드 작성할 때 |

---

## Skills 커스텀 폴더 (고급)

나만의 Skills을 추가하고 싶다면 아래 폴더에 파일을 추가하세요:

| OS | 경로 |
|----|------|
| Windows | `C:\Users\사용자명\.claude\skills\` |
| Mac | `~/.claude/skills/` |

**폴더 생성 명령어:**

```powershell
# Windows (PowerShell)
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills"
```

```bash
# Mac (터미널)
mkdir -p ~/.claude/skills
```

> **참고**: 커스텀 Skills 설정은 고급 사용자를 위한 것입니다. 처음에는 기본 내장 Skills만 사용해도 충분합니다!

---

[← 이전: OpenCode 설치](07-opencode.md) | [다음: 첫 프로젝트 시작하기 →](09-first-project.md)
