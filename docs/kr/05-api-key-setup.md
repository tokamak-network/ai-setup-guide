# 5. API 키 설정 (LiteLLM)

[← 목차로 돌아가기](../../README-KR.md)

---

LiteLLM은 여러 AI 모델(Claude, GPT 등)을 하나의 통합 API로 사용할 수 있게 해주는 프록시 서비스입니다.

---

## Step 1: API 키 발급받기

```
┌─────────────────────────────────────────────────────────────┐
│  📋 API 키 발급 절차                                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  1️⃣  Kevin에게 LiteLLM API 키 요청                           │
│      - 이메일, 슬랙, 또는 내부 시스템으로 요청                   │
│                                                             │
│  2️⃣  API 키와 서버 주소 수신                                  │
│      - API 키 예시: sk-xxxxxxxxxxxxxxxxxxxxxxxx              │
│      - 서버 주소 : https://api.ai.tokamak.network/               │
│                                                             │
│  3️⃣  API 키를 안전한 곳에 임시 보관                            │
│      - 메모장에 복사해두기                                     │
│      - 설정 완료 후 메모 삭제                                  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Step 2: API 키 보안 주의사항 ⚠️

```
┌─────────────────────────────────────────────────────────────┐
│  🔐 API 키 보안 수칙 (반드시 지켜주세요!)                       │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ❌ 하지 말아야 할 것:                                        │
│     • API 키를 다른 사람에게 공유하지 마세요                     │
│     • 코드 파일에 API 키를 직접 작성하지 마세요                  │
│     • GitHub 등 공개 저장소에 업로드하지 마세요                  │
│     • 카카오톡, 슬랙 등 메신저로 전달하지 마세요                  │
│     • 스크린샷에 API 키가 보이지 않게 주의하세요                  │
│                                                             │
│  ✅ 해야 할 것:                                              │
│     • 환경 변수로만 설정하세요 (아래 방법 참고)                   │
│     • 유출이 의심되면 즉시 IT팀에 연락하세요                     │
│     • 설정 완료 후 임시 메모는 삭제하세요                        │
│                                                             │
│  ⚠️  API 키가 유출되면?                                      │
│     → 즉시 IT팀에 연락하여 키 폐기 및 재발급 요청!               │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Step 3: 환경 변수 설정

API 키를 컴퓨터에 안전하게 저장합니다. **운영체제별로 방법이 다릅니다.**

### Windows

**방법 1: GUI로 설정 (쉬움)** ⭐ 추천

1. `Windows 키` 누르고 **"환경 변수"** 검색
2. **시스템 환경 변수 편집** 클릭


3. 열린 창에서 **환경 변수** 버튼 클릭


4. **"사용자 변수"** 섹션에서 **새로 만들기** 클릭

5. 첫 번째 변수 입력:
   ```
   변수 이름: ANTHROPIC_API_KEY
   변수 값: (IT팀에서 받은 API 키 붙여넣기)
   ```
   → **확인** 클릭

6. 다시 **새로 만들기** 클릭, 두 번째 변수 입력:
   ```
   변수 이름: ANTHROPIC_BASE_URL
   변수 값: (IT팀에서 받은 서버 주소 붙여넣기)
   ```
   → **확인** 클릭


7. 모든 창에서 **확인** 클릭하여 닫기

8. **⚠️ 중요**: 열려있는 **모든 PowerShell 창을 닫고 새로 열기**

**방법 2: PowerShell 명령어로 설정**

PowerShell을 열고 아래 명령어 실행 (**API 키와 URL 부분을 수정**하세요):

```powershell
[System.Environment]::SetEnvironmentVariable('ANTHROPIC_API_KEY', 'sk-여기에API키입력', 'User')
[System.Environment]::SetEnvironmentVariable('ANTHROPIC_BASE_URL', 'https://api.ai.tokamak.network/', 'User')
```

**✅ 설정 확인** (새 PowerShell 창에서):

```powershell
echo $env:ANTHROPIC_API_KEY
```

API 키 값이 출력되면 **성공!**

---

### Mac

**영구 설정 방법** (터미널을 닫아도 유지됨)

1. 터미널 열기

2. 아래 명령어 **한 줄씩** 실행 (**API 키와 URL 부분을 수정**하세요):

```bash
echo 'export ANTHROPIC_API_KEY="sk-여기에API키입력"' >> ~/.zshrc
echo 'export ANTHROPIC_BASE_URL="https://api.ai.tokamak.network/"' >> ~/.zshrc
```

3. 설정 적용:

```bash
source ~/.zshrc
```

4. **✅ 설정 확인**:

```bash
echo $ANTHROPIC_API_KEY
```

API 키 값이 출력되면 **성공!**


> **참고**: `~/.zshrc` 파일은 터미널이 시작될 때마다 자동으로 읽히는 설정 파일입니다.

---

## Step 4: 모델 별칭 설정 (필수) ⚠️

Claude Code가 프록시 서버와 정상적으로 통신하려면 **모델 별칭 환경 변수**를 추가로 설정해야 합니다.

> **왜 필요한가요?**
> Claude Code는 백그라운드 작업 시 내부적으로 구체적인 모델 버전명을 사용합니다.
> 하지만 프록시 서버는 별칭(alias)만 허용하므로, 이를 맞춰주지 않으면 401 오류가 발생합니다.

### Windows (PowerShell)

```powershell
[System.Environment]::SetEnvironmentVariable('ANTHROPIC_DEFAULT_OPUS_MODEL', 'claude-opus-4.5', 'User')
[System.Environment]::SetEnvironmentVariable('ANTHROPIC_DEFAULT_HAIKU_MODEL', 'claude-haiku-4.5', 'User')
[System.Environment]::SetEnvironmentVariable('CLAUDE_CODE_SUBAGENT_MODEL', 'claude-opus-4.5', 'User')
```

설정 후 **PowerShell 창을 닫고 새로 열기**

### Mac (터미널)

```bash
echo 'export ANTHROPIC_DEFAULT_OPUS_MODEL="claude-opus-4.5"' >> ~/.zshrc
echo 'export ANTHROPIC_DEFAULT_HAIKU_MODEL="claude-haiku-4.5"' >> ~/.zshrc
echo 'export CLAUDE_CODE_SUBAGENT_MODEL="claude-opus-4.5"' >> ~/.zshrc
source ~/.zshrc
```

### 전체 환경 변수 요약

| 환경 변수 | 값 | 용도 |
|----------|---|------|
| `ANTHROPIC_API_KEY` | `sk-xxxxx` (발급받은 키) | API 인증 |
| `ANTHROPIC_BASE_URL` | `https://api.ai.tokamak.network/` | 프록시 서버 주소 |
| `ANTHROPIC_DEFAULT_OPUS_MODEL` | `claude-opus-4.5` | 메인 작업용 모델 |
| `ANTHROPIC_DEFAULT_HAIKU_MODEL` | `claude-haiku-4.5` | 백그라운드 작업용 모델 |
| `CLAUDE_CODE_SUBAGENT_MODEL` | `claude-opus-4.5` | 서브 에이전트용 모델 |

### ✅ 전체 설정 확인

```bash
# Mac
echo $ANTHROPIC_API_KEY
echo $ANTHROPIC_BASE_URL
echo $ANTHROPIC_DEFAULT_HAIKU_MODEL
```

```powershell
# Windows
echo $env:ANTHROPIC_API_KEY
echo $env:ANTHROPIC_BASE_URL
echo $env:ANTHROPIC_DEFAULT_HAIKU_MODEL
```

모든 값이 정상적으로 출력되면 설정 완료입니다!

---

[← 이전: Node.js 설치](04-nodejs-installation.md) | [다음: Claude Code 설치 →](06-claude-code.md)
