# Claude Code 설정 가이드

## 개요

Claude Code는 사용자의 필요에 맞게 동작을 구성할 수 있는 다양한 설정을 제공합니다. 이 가이드에서는 가장 활용성이 높은 설정들만 간략히 소개하고, 자세한 내용은 공식 문서를 참조할 수 있도록 링크를 제공합니다.

## 설정 방법

Claude Code를 구성하는 방법은 여러 가지가 있습니다:

1. **대화형 설정**: `/config` 명령을 실행하여 GUI 기반 설정 인터페이스를 엽니다.
2. **설정 파일**: `settings.json` 파일을 직접 편집하여 구성을 관리합니다.

## 주요 설정 파일 위치

- **전역 설정**: `~/.claude/settings.json` (모든 프로젝트에 적용)
- **프로젝트 설정**: `.claude/settings.json` (소스 컨트롤에 포함, 팀과 공유)
- **로컬 설정**: `.claude/settings.local.json` (개인 설정, 소스 컨트롤에 포함되지 않음)

## 실용적인 설정 예제

가장 많이 사용되는 설정들을 다음과 같은 `settings.json` 파일 예제로 정리했습니다:

```json
{
  "permissions": {
    "allow": [
      "Bash(npm run lint)",
      "Bash(npm run test:*)",
      "Read(~/.zshrc)"
    ],
    "deny": [
      "Bash(curl:*)",
      "Read(./.env)",
      "Read(./.env.*)",
      "Read(./secrets/**)"
    ]
  },
  "env": {
    "CLAUDE_CODE_ENABLE_TELEMETRY": "1"
  },
  "model": "claude-sonnet-4-5-20250929",
  "cleanupPeriodDays": 30
}
```

## 권한 설정

Claude Code의 보안은 권한 설정으로 관리됩니다:

- **allow**: 도구 사용을 허용할 규칙 (예: `"Bash(git diff:*)"` )
- **ask**: 사용자 확인이 필요한 규칙 (예: `"Bash(git push:*)"` )
- **deny**: 도구 사용을 거부할 규칙 (예: `"Read(./.env)"` )

## 민감한 파일 보호

API 키, 비밀 정보 등 민감한 정보가 포함된 파일을 보호하려면 다음과 같이 설정합니다:

```json
{
  "permissions": {
    "deny": [
      "Read(./.env)",
      "Read(./.env.*)",
      "Read(./secrets/**)",
      "Read(./config/credentials.json)"
    ]
  }
}
```

## 샌드박스 설정 (고급)

bash 명령을 파일 시스템 및 네트워크에서 격리하는 샌드박스 기능을 활성화할 수 있습니다:

```json
{
  "sandbox": {
    "enabled": true,
    "autoAllowBashIfSandboxed": true,
    "excludedCommands": ["docker"],
    "network": {
      "allowUnixSockets": ["/var/run/docker.sock"],
      "allowLocalBinding": true
    }
  }
}
```

## 자세한 설정 정보

이 가이드에서 다루지 않은 고급 설정, 환경 변수, 플러그인 설정, 서브에이전트 구성 등에 대한 자세한 내용은 공식 문서를 참조하세요:

[전체 Claude Code 설정 문서](https://code.claude.com/docs/ko/settings)

여기에는 다음과 같은 고급 기능들이 포함되어 있습니다:
- 엔터프라이즈 배포를 위한 관리 정책
- 플러그인 시스템과 마켓플레이스
- MCP 서버 구성
- 서브에이전트 설정
- 훅(Hooks)을 통한 도구 확장