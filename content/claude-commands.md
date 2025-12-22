# Claude Code 명령어집

## 개요

Claude Code CLI는 터미널에서 작동하는 AI 기반 코딩 도우미로, 코드베이스를 이해하고, 명령을 실행하며, 프로젝트의 복잡성을 학습할 수 있는 에이전트 코딩 파트너입니다. 이 명령어집은 생산성을 극대화하는 데 필요한 핵심 명령어들을 요약한 것입니다.

## 설치 및 설정

### 1. 설치
AI 기반 개발을 위한 첫걸음

```bash
npm install -g @anthropic-ai/claude-code
```

### 2. 구성
경험 미세 조정

```bash
claude config set --global preferredNotifChannel terminal_bell
```

## 세션 관리

### 3. 새 대화 시작
```bash
claude
```

### 4. 이전 대화 이어가기
```bash
claude --continue  # 또는 claude -c
```

### 5. 여러 세션 관리
```bash
claude --resume  # 또는 claude -r
```

## 핵심 슬래시 명령어

### 6. 프로젝트 초기화
```bash
/init
```
- 프로젝트 루트에 CLAUDE.md 파일 생성
- Claude에게 프로젝트에 대한 정보 제공

### 7. 컨텍스트 관리
```bash
/clear
```
- 현재 세션의 대화 기록과 컨텍스트를 재설정

### 8. 대화 요약
```bash
/compact
```
- 대화를 요약하여 토큰 수를 줄임

### 9. 코드 리뷰
```bash
/review
```
- 풀 리퀘스트, 특정 파일 또는 코드 블록 검토

### 10. 도움말
```bash
/help
```
- 사용 가능한 모든 슬래시 명령어 목록

### 11. 모델 선택
```bash
/model
```
- 현재 세션에 사용할 Claude 모델 변경 (Opus, Sonnet 등)

## 프로젝트 탐색 명령어

### 12. 프로젝트 요약
```
> summarize this project
```

### 13. 폴더 구조 설명
```
> explain the folder structure
```

### 14. 특정 기능 파일 찾기
```
> find the files that handle user authentication
```

### 15. 아키텍처 패턴 분석
```
> explain the main architecture patterns used here
```

## 고급 기능

### 16. 사용자 정의 슬래시 명령어
- `.claude/commands/` 디렉토리에 마크다운 파일 생성
- 예: `.claude/commands/test.md` 파일 생성 후 `/project:test` 실행

### 17. MCP 확장
Model Context Protocol을 통해 Claude 기능 확장
```bash
claude mcp add playwright npx @playwright/mcp@latest
```

### 18. 권한 관리
`.claude/settings.json` 파일에서 실행 명령 허용/거부 설정

### 19. 사용량 확인
```bash
npx ccusage @latest
```

### 20. 심층 사고
```
> ultrathink how to design a scalable real-time chat application
```

## 에이전트 워크플로우

### TDD 워크플로우
1. `> write a failing test for the new feature`
2. 테스트 실행 (실패 확인)
3. `> write the code to make the test pass`
4. 테스트 재실행 (성공 확인)
5. 리팩토링 요청

### 다중 Claude 사용
- 개발자: 코드 작성
- 리뷰어: 코드 검토
- 리팩토링: 피드백 반영

Claude Code CLI는 단순한 도구가 아니라 지능적인 코딩 파트너입니다. 위 명령어들을 활용하여 대화형 방식으로 코드를 작성하고, 리뷰하고, 개선하세요.