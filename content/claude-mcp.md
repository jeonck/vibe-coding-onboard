# Claude Code에서 MCP 서버 추가하기

## 개요

MCP(Model Context Protocol)는 Claude Code를 외부 서비스 및 데이터 소스에 연결할 수 있는 시스템입니다. MCP 서버를 추가하면 Claude Code가 파일 시스템, 데이터베이스, 웹 API 등 외부 리소스와 상호 작용할 수 있는 새로운 기능을 사용할 수 있습니다.

이 문서에서는 Claude Code에 MCP 서버를 추가하는 방법을 설명합니다. 예제로는 Context7 MCP 서버를 사용합니다.

## MCP 서버 추가 단계

### 1. 프로젝트 디렉토리에서 .mcp.json 파일 생성

프로젝트 루트 디렉토리에 `.mcp.json` 파일을 생성하고 다음 내용을 추가합니다:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    }
  }
}
```

이 파일은 프로젝트별 MCP 서버 설정을 정의합니다. Git 저장소에 이 파일을 추가하면 팀원들과 MCP 설정을 공유할 수 있습니다.

### 2. Claude Code 재시작

설정 파일을 변경한 후에는 Claude Code를 종료하고 다시 시작해야 변경 사항이 적용됩니다.

### 3. MCP 서버 확인

Claude Code에 다시 진입한 후 다음 명령어를 실행하여 MCP 서버가 성공적으로 연결되었는지 확인합니다:

```
/mcp list
```

성공적으로 연결되면 다음과 유사한 결과가 표시됩니다:

```
─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 Manage MCP servers
 1 server

 ❯ 1. context7  ✔ connected · Enter to view details

 MCP Config locations (by scope):
  • User config (available in all your projects):
    • /Users/mac/.claude.json
  • Project config (shared via .mcp.json):
    • /Users/mac/ws/claude/.mcp.json
  • Local config (private to you in this project):
    • /Users/mac/.claude.json [project: /Users/mac/ws/claude]

 Tip: Use /mcp enable or /mcp disable to quickly toggle all servers

 For help configuring MCP servers, see: https://code.claude.com/docs/en/mcp

 Enter to confirm · Esc to cancel
```

## 다른 MCP 서버 예제

### GitHub MCP
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@github/mcp-github@latest"]
    }
  }
}
```

### Database MCP (예: PostgreSQL)
```json
{
  "mcpServers": {
    "database": {
      "command": "npx",
      "args": ["-y", "@database/mcp-postgres@latest"]
    }
  }
}
```

## MCP 서버 관리 명령어

- `/mcp list`: 연결된 MCP 서버 목록 표시
- `/mcp enable`: 모든 MCP 서버 활성화
- `/mcp disable`: 모든 MCP 서버 비활성화
- `/mcp logs`: MCP 서버 로그 보기

## 보안 고려사항

MCP 서버는 시스템에 대한 확장된 액세스 권한을 부여할 수 있으므로 다음 사항을 유의하세요:

- 신뢰할 수 있는 출처의 MCP 서버만 설치
- MCP 서버가 실행하는 명령어를 검토
- 필요 시 프로젝트별 설정이 아닌 사용자 전역 설정에 추가

## 문제 해결

### 서버가 연결되지 않는 경우
1. `.mcp.json` 파일이 프로젝트 루트에 있는지 확인
2. Claude Code를 재시작했는지 확인
3. 필요한 의존성이 설치되었는지 확인 (예: Node.js, npx)

### 권한 문제
- Claude Code가 해당 리소스에 액세스할 수 있는 권한이 있는지 확인
- MCP 서버가 요청하는 권한을 허용했는지 확인

MCP 서버를 사용하면 Claude Code의 기능을 크게 확장할 수 있으며, 외부 서비스와의 통합을 통해 더 강력한 자동화와 작업 처리가 가능해집니다.