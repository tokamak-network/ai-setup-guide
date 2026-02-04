# 6. Claude Code 설치 및 사용법

[← 목차로 돌아가기](../../README-KR.md)

---

Claude Code는 Anthropic에서 만든 공식 AI 코딩 어시스턴트입니다.

---

## ⚠️ 사전 준비: LiteLLM API 설정

Claude Code를 실행하기 전에 **반드시** API 키 설정을 완료해야 합니다.

> 📌 **[Chapter 5: API 키 설정](05-api-key-setup.md)**에서 환경 변수 설정을 먼저 완료하세요!

### 빠른 체크리스트

아래 명령어로 설정이 완료되었는지 확인하세요:

**Mac:**
```bash
echo $ANTHROPIC_AUTH_TOKEN && echo $ANTHROPIC_BASE_URL
```

**Windows:**
```powershell
echo $env:ANTHROPIC_AUTH_TOKEN; echo $env:ANTHROPIC_BASE_URL
```

값이 출력되면 설정 완료! → 아래 **설치** 단계로 진행

값이 비어있다면 → [Chapter 5: API 키 설정](05-api-key-setup.md)으로 이동

---

## 설치

### Windows

1. PowerShell 열기 (**새 창**으로!)
2. 아래 명령어 복사 → 붙여넣기 → Enter:

```powershell
npm install -g @anthropic-ai/claude-code
```

3. 설치 완료까지 대기 (1-2분 소요)

<!-- 스크린샷: Claude Code 설치 진행 화면 -->

4. **✅ 설치 확인**:

```powershell
claude --version
```

버전 번호가 나오면 **성공!**

<!-- 스크린샷: Claude Code 설치 성공 화면 -->

### Mac

1. 터미널 열기
2. 아래 명령어 복사 → 붙여넣기 → Enter:

```bash
npm install -g @anthropic-ai/claude-code
```

> **권한 오류 발생 시**:
> ```bash
> sudo npm install -g @anthropic-ai/claude-code
> ```
> (Mac 로그인 비밀번호 입력 필요)

3. **✅ 설치 확인**:

```bash
claude --version
```

---

## 첫 실행

1. 터미널에서 작업할 폴더로 이동:

```bash
# Windows
cd $env:USERPROFILE\Documents

# Mac
cd ~/Documents
```

2. Claude Code 실행 (모델 지정):

```bash
# 발급받은 Virtual Key에서 선택한 모델명을 입력
claude --model claude-opus-4.5
```

> **사용 가능한 모델:**
> - `claude-opus-4.5` - 최고 성능, 복잡한 작업에 적합
> - `claude-sonnet-4.5` - 균형 잡힌 성능과 속도
> - `claude-haiku-4.5` - 빠른 응답, 간단한 작업에 적합

3. 첫 실행 화면:

```
╭──────────────────────────────────────────────────────────╮
│                                                          │
│   Welcome to Claude Code!                                │
│                                                          │
│   Type your request and press Enter to start.            │
│                                                          │
╰──────────────────────────────────────────────────────────╯

>  █
   ↑
   여기에 요청 입력
```

<!-- 스크린샷: Claude Code 첫 실행 화면 -->

---

## 주요 명령어

| 명령어 | 설명 | 예시 |
|--------|------|------|
| `claude --model 모델명` | 모델 지정하여 시작 | `claude --model claude-opus-4.5` |
| `claude` | Claude Code 시작 | 터미널에서 `claude` 입력 |
| `claude "질문"` | 바로 질문하기 | `claude "hello world 출력하는 파이썬 코드"` |
| `/help` | 도움말 보기 | Claude Code 실행 중 `/help` 입력 |
| `/clear` | 대화 기록 초기화 | Claude Code 실행 중 `/clear` 입력 |
| `Ctrl + C` | 실행 중단 | AI 응답 중 중단하고 싶을 때 |
| `exit` | 종료 | Claude Code 종료 |

---

## 사용 예시

**간단한 질문:**
```
> 파이썬으로 1부터 10까지 더하는 코드 만들어줘
```

**파일 생성 요청:**
```
> index.html 파일을 만들어서 "Hello World"를 표시해줘
```

**프로젝트 생성:**
```
> 간단한 To-Do 앱을 만들어줘. 할 일 추가, 삭제, 완료 체크 기능이 필요해
```

---

[← 이전: API 키 설정](05-api-key-setup.md) | [다음: OpenCode 설치 →](07-opencode.md)
