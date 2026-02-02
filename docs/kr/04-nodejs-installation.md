# 4. Node.js 설치

[← 목차로 돌아가기](../../README-KR.md)

---

Node.js는 JavaScript 실행 환경입니다. **Claude Code와 OpenCode 설치에 필수입니다.**

---

## Windows

1. 웹 브라우저에서 **https://nodejs.org** 접속
2. **LTS** (장기 지원 버전) 버튼 클릭 - **왼쪽 초록색 버튼**

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│    [ 20.x.x LTS ]      [ 21.x.x Current ]                   │
│    Recommended for        Latest Features                   │
│    Most Users                                               │
│         ↑                                                   │
│    이 버튼 클릭!                                              │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

<!-- 스크린샷: Node.js 다운로드 페이지, LTS 버튼 강조 -->

3. 다운로드된 `node-v*-x64.msi` 파일 더블클릭
4. **Next** 클릭
5. "I accept the terms" 체크 → **Next**
6. 설치 경로 확인 → **Next**
7. **Next** (기본 설정 유지)
8. **Install** 클릭
9. 설치 완료 → **Finish**

### ✅ 설치 확인

1. **새 PowerShell 창** 열기 (기존 창 말고 새로 열어야 합니다!)
2. 아래 명령어 복사 → 붙여넣기 → Enter:

```powershell
node --version
```

3. `v20.x.x` 같은 버전 번호가 나오면 **성공!**

```
PS C:\Users\홍길동> node --version
v20.11.0   ← 이런 식으로 나오면 성공!
```

<!-- 스크린샷: 설치 확인 성공 화면 -->

4. npm도 확인:

```powershell
npm --version
```

---

## Mac

### 방법 1: 공식 설치 프로그램 (쉬움) ⭐ 추천

1. 웹 브라우저에서 **https://nodejs.org** 접속
2. **LTS** 버튼 클릭
3. 다운로드된 `.pkg` 파일 더블클릭
4. **계속** → **동의** → **설치** 클릭
5. 비밀번호 입력 → 설치 완료

### 방법 2: Homebrew 사용

```bash
# Homebrew 설치 (없는 경우)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Node.js 설치
brew install node
```

### ✅ 설치 확인

```bash
node --version
npm --version
```

버전 번호가 나오면 성공입니다!

---

[← 이전: IDE 설치](03-ide-installation.md) | [다음: API 키 설정 →](05-api-key-setup.md)
