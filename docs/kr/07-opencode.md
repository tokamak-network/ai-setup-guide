# 7. OpenCode 설치 및 사용법

[← 목차로 돌아가기](../../README-KR.md)

---

OpenCode는 다양한 AI 모델을 지원하는 오픈소스 AI 코딩 도구입니다.
여기서는 자동 컨텍스트 압축, 커스텀 Provider 등을 지원하는 **Tokamak 커스텀 빌드**를 기준으로 설명합니다.

---

## 설치

### 플랫폼별 바이너리 다운로드

[OpenCode GitHub 릴리즈](https://github.com/anomalyco/opencode/releases/latest)에서 본인 플랫폼에 맞는 바이너리를 다운로드합니다.

| 플랫폼 | 다운로드 |
|--------|---------|
| Mac M1/M2/M3/M4 | [opencode-darwin-arm64.zip](https://github.com/anomalyco/opencode/releases/latest/download/opencode-darwin-arm64.zip) |
| Mac Intel | [opencode-darwin-x64.zip](https://github.com/anomalyco/opencode/releases/latest/download/opencode-darwin-x64.zip) |
| Linux x64 | [opencode-linux-x64.tar.gz](https://github.com/anomalyco/opencode/releases/latest/download/opencode-linux-x64.tar.gz) |
| Windows x64 | [opencode-windows-x64.zip](https://github.com/anomalyco/opencode/releases/latest/download/opencode-windows-x64.zip) |

### Mac

> **참고**: 이전에 `brew install opencode-ai/tap/opencode`로 설치한 적이 있다면, 먼저 제거해주세요:
> ```bash
> brew uninstall opencode
> ```

**Step 1: 바이너리 설치**

```bash
# 설치 디렉토리 생성
mkdir -p ~/.opencode/bin

# 다운로드한 zip 압축 해제 (Mac Apple Silicon 기준)
unzip ~/Downloads/opencode-darwin-arm64.zip -d ~/.opencode/bin/

# 실행 권한 부여
chmod +x ~/.opencode/bin/opencode
```

**Step 2: PATH에 추가**

```bash
echo 'export PATH="$HOME/.opencode/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### Windows

```
┌─────────────────────────────────────────────────────────────┐
│  Windows 사용자 안내                                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Windows 사용자는 아래 방법 중 선택하세요:                    │
│                                                             │
│  방법 1: Claude Code 사용 (권장)                             │
│  방법 2: WSL(Linux 환경)에서 OpenCode 설치                   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**방법 1: Claude Code 사용 (권장)**

Windows 사용자는 **Claude Code**를 사용하는 것을 강력 권장합니다.
→ [Claude Code 설치 가이드](06-claude-code.md)로 이동

**방법 2: WSL에서 설치**

1. **WSL 설치** (PowerShell 관리자 권한):
```powershell
wsl --install
```

2. 컴퓨터 **재시작**

3. **Ubuntu 터미널** 열기 (시작 메뉴에서 "Ubuntu" 검색)

4. 바이너리를 `opencode-linux-x64`로 다운로드 후 위 Mac 설치 방법을 따라 설치
   (`~/.zshrc` 대신 `~/.bashrc` 사용)

---

## 설정

### 설정 파일 생성

```bash
mkdir -p ~/.config/opencode
nano ~/.config/opencode/opencode.json
```

아래 내용 입력 (**API 키 수정**):

```json
{
  "$schema": "https://opencode.ai/config.json",
  "model": "tokamak/gpt-5.2-pro",
  "permission": {
    "external_directory": "allow"
  },
  "compaction": {
    "auto": true,
    "prune": true
  },
  "provider": {
    "tokamak": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "Tokamak AI",
      "options": {
        "baseURL": "https://api.ai.tokamak.network",
        "apiKey": "sk-여기에API키입력"
      },
      "models": {
        "gpt-5.2-pro": {
          "name": "GPT 5.2 Pro",
          "limit": {
            "context": 131072,
            "input": 131072,
            "output": 16384
          }
        }
      }
    }
  }
}
```

`Ctrl + X` → `Y` → `Enter`로 저장

### 주요 설정 설명

| 설정 | 설명 |
|------|------|
| `model` | 사용할 기본 모델 (`provider명/모델명` 형식) |
| `compaction.auto` | 세션이 토큰 한도에 근접하면 자동으로 대화를 압축 |
| `compaction.prune` | 불필요한 이전 메시지 정리 |
| `limit.input` | 토큰 계산에 필요하므로 반드시 설정 |
| `permission.external_directory` | 프로젝트 디렉토리 외부 파일 읽기 허용 |

---

## 설치 확인

```bash
opencode --version
```

버전 번호가 나오면 **성공!**

---

## 첫 실행 및 사용법

1. 터미널에서 작업할 폴더로 이동:

```bash
cd ~/Documents
```

2. OpenCode 실행:

```bash
opencode
```

---

## 주요 명령어

| 명령어 | 설명 |
|--------|------|
| `opencode` | OpenCode 시작 |
| `opencode --help` | 도움말 보기 |
| `opencode --version` | 버전 확인 |
| `/help` | 실행 중 도움말 |
| `/clear` | 대화 초기화 |
| `/compact` | 수동으로 대화 압축 |
| `Ctrl + C` | 실행 중단 |
| `/quit` 또는 `exit` | 종료 |

---

## 사용 예시

```
> 현재 폴더에 있는 파일 목록을 보여줘

> index.html 파일 내용을 읽어줘

> React로 간단한 버튼 컴포넌트 만들어줘
```

---

[← 이전: Claude Code 설치](06-claude-code.md) | [다음: Skills & Agents →](08-skills-agents.md)
