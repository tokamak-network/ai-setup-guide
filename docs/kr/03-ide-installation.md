# 3. IDE 설치

[← 목차로 돌아가기](../../README-KR.md)

---

IDE(통합 개발 환경)는 코드를 작성하고 관리하는 도구입니다.

```
┌─────────────────────────────────────────────────────────────┐
│  💡 어떤 IDE를 선택해야 할까요?                                │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  🥇 VS Code (추천)                                          │
│     - 무료, 자료 많음, 가장 보편적                             │
│     - 처음 시작하시는 분께 추천                                │
│                                                             │
│  🥈 Cursor                                                  │
│     - AI 기능 내장, VS Code 기반                              │
│     - AI 코딩 보조를 많이 사용하실 분께 추천                     │
│                                                             │
│  🥉 Antigravity                                             │
│     - AI 에이전트 기반 IDE                                    │
│     - 자율적인 AI 코딩을 원하시는 분께 추천                      │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**3가지 중 하나만 설치하세요!**

---

## VS Code 설치 (무료) ⭐ 추천

### Windows

1. 웹 브라우저에서 **https://code.visualstudio.com** 접속
2. 파란색 **Download for Windows** 버튼 클릭

<!-- 스크린샷: VS Code 다운로드 페이지 -->

3. 다운로드 폴더에서 `VSCodeUserSetup-x64-*.exe` 파일 더블클릭
4. "동의합니다" 선택 → **다음** 클릭
5. 설치 경로 확인 → **다음** 클릭
6. **⚠️ 중요**: 아래 옵션들을 **모두 체크**:

```
☑️ "PATH에 추가" (반드시 체크!)
☑️ "Code로 열기" 작업을 파일 컨텍스트 메뉴에 추가
☑️ "Code로 열기" 작업을 디렉터리 컨텍스트 메뉴에 추가
```

<!-- 스크린샷: VS Code 설치 옵션 화면 -->

7. **설치** 클릭 → 완료까지 대기
8. **마침** 클릭

### Mac

1. 웹 브라우저에서 **https://code.visualstudio.com** 접속
2. **Download for Mac** 버튼 클릭

**내 Mac 칩 확인하는 방법:**
```
1. 화면 좌측 상단  아이콘 클릭
2. "이 Mac에 관하여" 클릭
3. "칩" 또는 "프로세서" 확인:
   - "Apple M1/M2/M3/M4" → Apple Silicon 선택
   - "Intel" → Intel 선택
```

<!-- 스크린샷: Mac에서 칩 확인하는 방법 -->

3. 다운로드된 `.zip` 파일 더블클릭 (자동 압축 해제)
4. `Visual Studio Code` 앱을 **응용 프로그램** 폴더로 드래그

<!-- 스크린샷: VS Code를 응용 프로그램으로 이동 -->

5. **응용 프로그램** 폴더에서 **Visual Studio Code** 더블클릭
6. "인터넷에서 다운로드한 앱입니다" 경고 → **열기** 클릭

**터미널에서 `code` 명령어 사용 설정 (선택):**
1. VS Code 실행
2. `Cmd + Shift + P` 키 동시에 누르기
3. "shell command" 입력
4. **Shell Command: Install 'code' command in PATH** 선택

<!-- 스크린샷: code 명령어 설치 화면 -->

---

## Cursor 설치 (AI 기능 내장)

### Windows

1. 웹 브라우저에서 **https://cursor.com** 접속
2. **Download for Windows** 클릭
3. 다운로드된 `Cursor Setup *.exe` 파일 더블클릭
4. 설치 마법사 따라 진행
5. 완료 후 실행

### Mac

1. 웹 브라우저에서 **https://cursor.com** 접속
2. **Download for Mac** 클릭
3. 다운로드된 `.dmg` 파일 더블클릭
4. Cursor 아이콘을 **응용 프로그램** 폴더로 드래그
5. 응용 프로그램에서 실행

---

## Antigravity 설치 (AI 에이전트 기반)

> **참고**: Antigravity는 AI 에이전트가 자율적으로 코딩을 도와주는 IDE입니다.

### Windows

1. 웹 브라우저에서 **https://antigravity.dev** 접속
2. **Download** 버튼 클릭
3. Windows용 설치 파일 다운로드
4. 다운로드된 `.exe` 파일 더블클릭
5. 설치 마법사 따라 진행
6. 완료 후 실행

### Mac

1. 웹 브라우저에서 **https://antigravity.dev** 접속
2. **Download** 버튼 클릭
3. Mac용 (Intel 또는 Apple Silicon) 선택하여 다운로드
4. 다운로드된 `.dmg` 파일 더블클릭
5. Antigravity를 **응용 프로그램** 폴더로 드래그
6. 응용 프로그램에서 실행

---

[← 이전: 터미널 사용법](02-terminal-usage.md) | [다음: Node.js 설치 →](04-nodejs-installation.md)
