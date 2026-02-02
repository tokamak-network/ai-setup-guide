# 10. 문제 해결

[← 목차로 돌아가기](../../README-KR.md)

---

## Node.js 설치 확인 실패

**증상**: `node --version` 실행 시 "명령을 찾을 수 없습니다" 오류

```
PS C:\Users\홍길동> node --version
node : 'node' 용어가 cmdlet, 함수, 스크립트 파일...
```

**해결**:
1. 현재 터미널 창을 **완전히 닫기** (X 버튼)
2. **새 터미널 창** 열기
3. 다시 `node --version` 시도

그래도 안 되면 → Node.js **재설치**

---

## npm 권한 오류 (Mac)

**증상**: `npm install -g` 실행 시 "EACCES" 오류

```
npm ERR! Error: EACCES: permission denied
```

**해결**:
```bash
sudo npm install -g @anthropic-ai/claude-code
```
Mac 로그인 비밀번호 입력 → Enter

---

## Claude Code 실행 안 됨

**증상**: `claude` 명령어 입력 시 "명령을 찾을 수 없습니다"

**해결 순서**:

1. Node.js 설치 확인:
```bash
node --version
```
버전이 안 나오면 → Node.js 설치부터 다시

2. Claude Code 설치 확인:
```bash
npm list -g @anthropic-ai/claude-code
```
설치되어 있으면 버전 정보가 나옴

3. npm 글로벌 경로 확인:
```bash
npm config get prefix
```

4. 해당 경로가 시스템 PATH에 있는지 확인
   - PATH에 없으면 환경 변수에 추가 필요

---

## API 연결 오류

**증상**: "API key invalid", "Connection refused" 등 오류

**해결**:

1. 환경 변수 확인:

```powershell
# Windows
echo $env:ANTHROPIC_API_KEY
echo $env:ANTHROPIC_BASE_URL
```

```bash
# Mac
echo $ANTHROPIC_API_KEY
echo $ANTHROPIC_BASE_URL
```

2. 값이 비어있으면 → [5장 API 키 설정](05-api-key-setup.md) 다시 수행

3. 값이 있는데 안 되면:
   - API 키가 올바른지 Kevin에게 확인
   - 서버 주소가 올바른지 확인
   - 회사 네트워크(VPN)에 연결되어 있는지 확인

---

## Claude Code 401/404 오류 (모델 이름 불일치) ⚠️ 중요

**증상**: Claude Code 사용 중 401 (Unauthorized) 또는 404 (Not Found) 오류 발생

```
Error: 401 Key model access denied
```

**원인 분석**:

Claude Code는 복잡한 작업 수행 시 내부적으로 **Task Splitting**을 수행합니다. 이때 백그라운드 작업(파일 인덱싱, 계획 수립, 문법 검사 등)에 비용 효율적인 Haiku 모델을 자동으로 사용합니다.

문제는 Claude Code가 요청하는 모델명이 **구체적인 버전명** (예: `claude-haiku-4-5-20251001`)인데, 프록시 서버에는 **별칭** (예: `claude-haiku-4.5`)만 허용되어 있어 불일치가 발생합니다.

```
┌─────────────────────────────────────────────────────────────┐
│  🔍 오류 발생 구조                                           │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Claude Code 요청: claude-haiku-4-5-20251001                │
│           ↓                                                 │
│  프록시 서버 허용: claude-haiku-4.5 (별칭만 허용)            │
│           ↓                                                 │
│  결과: 401 Key model access denied 오류!                    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**해결 방법**:

환경 변수를 추가로 설정하여 Claude Code가 별칭 모델명을 사용하도록 강제합니다.

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

**설정 확인**:

```bash
# Mac
echo $ANTHROPIC_DEFAULT_HAIKU_MODEL
# 출력: claude-haiku-4.5 가 나오면 성공!
```

```powershell
# Windows
echo $env:ANTHROPIC_DEFAULT_HAIKU_MODEL
# 출력: claude-haiku-4.5 가 나오면 성공!
```

**환경 변수 설명**:

| 환경 변수 | 용도 |
|----------|------|
| `ANTHROPIC_DEFAULT_OPUS_MODEL` | 메인 작업에 사용할 Opus 모델 별칭 |
| `ANTHROPIC_DEFAULT_HAIKU_MODEL` | 백그라운드 작업에 사용할 Haiku 모델 별칭 |
| `CLAUDE_CODE_SUBAGENT_MODEL` | 서브 에이전트가 사용할 모델 별칭 |

> **참고**: OpenCode는 이 문제가 발생하지 않습니다. Claude Code 특유의 Task Splitting 기능 때문에 발생하는 문제입니다.

---

## 환경 변수가 적용되지 않음

**증상**: 설정한 환경 변수가 인식되지 않음

**해결**:
- **Windows**: 모든 PowerShell 창을 **닫고 새로 열기**
- **Mac**: `source ~/.zshrc` 실행 또는 터미널 **재시작**

---

## "Permission denied" 오류

**증상**: 파일/폴더 접근 권한 오류

**해결 (Mac)**:
```bash
sudo 명령어
```
예: `sudo npm install -g @anthropic-ai/claude-code`

**해결 (Windows)**:
1. PowerShell을 **관리자 권한**으로 실행
2. 시작 메뉴에서 "PowerShell" 검색 → 우클릭 → **관리자 권한으로 실행**

---

[← 이전: 첫 프로젝트](09-first-project.md) | [다음: FAQ →](11-faq.md)
