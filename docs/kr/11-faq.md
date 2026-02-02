# 11. FAQ

[← 목차로 돌아가기](../../README-KR.md)

---

## Q: IDE는 꼭 설치해야 하나요?
**A**: 필수는 아닙니다. 터미널만으로도 Claude Code를 사용할 수 있습니다. 하지만 IDE를 사용하면:
- 생성된 코드를 보기 쉽습니다
- 파일 구조를 한눈에 파악할 수 있습니다
- 코드 수정이 편리합니다

---

## Q: VS Code, Cursor, Antigravity 중 뭘 써야 하나요?
**A**:
| IDE | 추천 대상 |
|-----|----------|
| VS Code | 처음 시작하시는 분, 무료 원하시는 분 |
| Cursor | AI 코딩 보조를 많이 사용하실 분 |
| Antigravity | 자율적인 AI 에이전트 코딩을 원하시는 분 |

---

## Q: API 키가 노출되면 어떻게 하나요?
**A**: **즉시** IT팀에 연락하세요!
1. 기존 키 폐기 요청
2. 새 키 발급
3. 환경 변수 업데이트

---

## Q: Claude Code와 OpenCode 중 뭘 써야 하나요?
**A**:
| 도구 | 특징 | 추천 |
|------|------|------|
| Claude Code | Anthropic 공식, 안정적, Windows/Mac 모두 지원 | 일반적인 사용 |
| OpenCode | 오픈소스, 다양한 AI 모델 지원, **Mac만 지원** | Mac에서 여러 모델 테스트 |

**처음 시작하시면 Claude Code를 추천합니다!**
**Windows 사용자는 Claude Code만 사용 가능합니다.**

---

## Q: 오류가 발생하면 어떻게 하나요?
**A**:
1. 오류 메시지를 **복사**
2. Claude Code에게 직접 물어보기:
   ```
   > 이 오류가 발생했어: [오류 메시지 붙여넣기]
   ```
3. 해결 안 되면 → Jason에게 문의

---

## Q: 인터넷 없이도 사용 가능한가요?
**A**: 아니요, AI 서비스 연결을 위해 **인터넷이 필수**입니다.

---

## Q: 회사 밖에서도 사용할 수 있나요?
**A**: LiteLLM 서버 접근 정책에 따라 다릅니다.
- VPN 필요 여부
- 외부 접근 허용 여부
→ IT팀에 확인하세요.

---

## Q: 생성된 코드를 어떻게 실행하나요?
**A**: 코드 종류에 따라 다릅니다:
- **HTML 파일**: 브라우저로 열기
- **Python 파일**: `python 파일명.py`
- **JavaScript 파일**: `node 파일명.js`
- **React 앱**: Claude Code가 실행 방법을 알려줍니다

---

## Q: Skills이나 Agents를 따로 설치해야 하나요?
**A**: 아니요! 모두 **Claude Code에 기본 내장**되어 있습니다. 별도 설치 없이 바로 사용 가능합니다.

---

## 추가 리소스

- [Claude Code 공식 문서](https://docs.anthropic.com/en/docs/build-with-claude/claude-code)
- [VS Code 공식 문서](https://code.visualstudio.com/docs)
- [Node.js 공식 문서](https://nodejs.org/docs)
- [OpenCode GitHub](https://github.com/opencode-ai/opencode)

---

## 지원 연락처

| 문의 유형 | 연락처 |
|----------|--------|
| API 키 발급 | Kevin |
| 기술 문제 | Jason |
| 일반 문의 | Jason |

---

[← 이전: 문제 해결](10-troubleshooting.md) | [목차로 돌아가기 →](../../README-KR.md)
