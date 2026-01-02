# Claude Skills: 전문화된 AI 워크플로우 시스템

## 개요

Claude Skills는 Anthropic이 2025년 10월 16일에 공개한 혁신적인 기능으로, Claude가 특정 작업을 더 효율적이고 일관되게 수행할 수 있도록 커스텀 능력을 부여하는 시스템입니다. Skills를 사용하면 반복적인 프롬프트 작성 없이 전문화된 워크플로를 만들고 재사용할 수 있습니다.

이 기능은 프롬프트 엔지니어링의 새로운 패러다임을 제시하며, 반복적인 긴 프롬프트 대신 재사용 가능한 모듈식 능력으로 Claude를 전문화할 수 있습니다.

## Claude Skills란?

Claude Skills는 지침(instructions), 스크립트, 리소스가 포함된 폴더 형태로 제공되며, Claude가 작업을 수행할 때 필요한 경우에만 동적으로 로드됩니다. 이는 마치 Claude에게 특정 업무에 대한 매뉴얼을 제공하는 것과 같습니다.

Skills는 Claude의 핵심 기능 중 하나로, 다음과 같은 차별화된 특징을 가지고 있습니다:

- **모듈화된 기능**: 특정 작업에 특화된 재사용 가능한 모듈
- **동적 로딩**: 필요할 때만 활성화되어 컨텍스트 효율성 향상
- **跨플랫폼 호환성**: Claude.ai, Claude Code, API 등에서 동일하게 작동
- **자동 조합**: 여러 Skills를 자동으로 식별하고 조합

## 핵심 특징

### 1. 점진적 공개 (Progressive Disclosure)
Claude는 시작할 때 모든 Skills의 이름과 설명만 로드합니다. 실제 작업에 필요한 Skill만 선택적으로 상세 내용을 불러와 컨텍스트 윈도우를 효율적으로 사용합니다.

### 2. 조합 가능성 (Composable)
여러 Skills를 함께 사용할 수 있습니다. Claude가 자동으로 필요한 Skills를 식별하고 조합하여 사용합니다.

### 3. 이식성 (Portable)
하나의 Skill은 Claude.ai 웹앱, Claude Code, API 등 모든 Claude 플랫폼에서 수정 없이 동일하게 작동합니다.

## Skills의 종류

### Anthropic 공식 Skills
Anthropic이 직접 제작하고 유지보수하는 Skills로, 모든 유료 사용자(Pro, Max, Team, Enterprise)가 자동으로 사용할 수 있습니다.

#### 문서 작성 Skills
- **docx**: Word 문서 생성 및 편집, 변경 사항 추적, 주석 처리
- **xlsx**: Excel 스프레드시트 생성, 수식 작성, 데이터 분석
- **pptx**: PowerPoint 프레젠테이션 생성, 레이아웃 및 차트 작성
- **pdf**: PDF 생성, 텍스트 추출, 양식 작성

#### 기타 공식 Skills
- **brand-guidelines**: Anthropic의 공식 브랜드 컬러와 타이포그래피 적용
- **theme-factory**: 10가지 사전 설정된 테마로 아티팩트 스타일링
- **skill-creator**: 새로운 Skill 생성을 돕는 대화형 가이드

### 커스텀 Skills
사용자나 조직이 직접 만드는 Skills로, 특정 워크플로나 도메인 전문 작업을 위해 사용됩니다.

## 활용 예시

- **회사의 브랜드 가이드라인을 문서에 자동 적용**
- **조직의 이메일 템플릿에 맞춰 커뮤니케이션 생성**
- **회사 형식에 맞는 회의록 작성**
- **JIRA, Asana, Linear 등의 도구에 팀 관례를 따라 작업 생성**
- **회사별 데이터 분석 워크플로 실행**

## Skills 구조

Skill은 기본적으로 SKILL.md 파일을 포함하는 폴더입니다.

### 최소 구조
```markdown
---
name: my-skill-name
description: 이 Skill이 무엇을 하고 언제 사용되는지에 대한 명확한 설명
---

# My Skill Name

[Claude가 이 Skill이 활성화될 때 따를 지침을 여기에 추가]

## Examples
- 예시 사용법 1
- 예시 사용법 2

## Guidelines
- 가이드라인 1
- 가이드라인 2
```

### YAML frontmatter 필수 필드

#### name
Skill의 고유 식별자. 소문자와 하이픈 사용 권장.

#### description
Skill이 무엇을 하고 언제 사용되는지에 대한 완전한 설명. Claude가 이 설명을 보고 Skill 사용 여부를 결정합니다.

### 추가 요소

#### 추가 파일
Python 스크립트, 템플릿, 이미지 등 추가 리소스 포함 가능. Claude가 필요에 따라 이러한 파일을 읽거나 실행합니다.

#### 코드 실행
Skills는 Python 코드를 포함하여 Claude가 실행하도록 할 수 있습니다.
예: 복잡한 데이터 처리, 파일 변환 등

## Skills 사용 방법

### Claude.ai에서 사용
설정(Settings) → 기능(Capabilities)에서 코드 실행 활성화 후:

- Anthropic Skills는 자동으로 사용 가능
- 커스텀 Skills는 "Upload skill" 버튼으로 ZIP 파일 업로드
- 작업을 요청하면 Claude가 자동으로 관련 Skill을 선택하여 사용합니다.

예: "Q3 실적에 대한 PowerPoint 프레젠테이션을 만들어줘" → Claude가 자동으로 pptx Skill을 사용

### Claude Code에서 사용
플러그인 마켓플레이스에서 설치:
```bash
/plugin install document-skills@anthropic-agent-skills
```

또는 수동 설치:
```bash
# ~/.claude/skills 디렉토리에 Skill 폴더 추가
```

Claude가 작업 내용에 따라 자동으로 관련 Skills를 로드합니다.

### API에서 사용
Code Execution Tool 베타 기능이 필요하며, /v1/skills 엔드포인트를 통해 Skill을 프로그래밍 방식으로 관리할 수 있습니다.

## Skill 생성하기

### skill-creator 사용
Claude.ai에서 "skill-creator" Skill이 활성화된 상태에서:
```
"새로운 Skill을 만들고 싶어. 우리 회사의 브랜드 가이드라인을 적용하는 Skill이야."
```

Claude가 대화형으로 워크플로를 파악하고, 폴더 구조를 생성하며, SKILL.md 파일을 포매팅합니다.

### 수동 생성
공식 GitHub 저장소(anthropics/skills)의 template-skill을 참고하여 직접 작성할 수 있습니다.

### 작성 모범 사례
- **명확한 설명 작성**: Claude가 언제 이 Skill을 사용할지 판단할 수 있도록
- **구체적인 예시 포함**: 다양한 사용 시나리오 제공
- **점진적 구조화**: SKILL.md가 너무 길어지면 별도 파일로 분리
- **코드는 도구와 문서 양면으로 작용**: 실행 가능한지 명확히 표시

## Skills vs 다른 기능

### Projects
- 대화 시작 시 항상 로드되는 정적 배경 지식 제공

### Skills
- 필요할 때만 동적으로 활성화되는 작업별 절차 지식. 모든 Claude 플랫폼에서 작동

### MCP (Model Context Protocol)
- Claude를 외부 서비스 및 데이터 소스에 연결하는 도구. Skills는 MCP 도구를 효과적으로 사용하는 방법을 가르칠 수 있음

### Custom Instructions
- 모든 대화에 광범위하게 적용되는 지침. Skills는 특정 작업에 특화되어 있어 더 효율적

## 실제 활용 사례

### Box와의 통합
Box의 콘텐츠를 PowerPoint, Excel, Word 문서로 변환하며 조직의 표준을 따르도록 함.

### Notion과의 통합
Notion의 데이터를 빠르게 검색하고 작업으로 전환. 복잡한 작업에서 프롬프트 조정 필요성 감소.

### Rakuten의 활용
Rakuten은 Skills를 통해 관리 회계 및 재무 워크플로를 간소화. 여러 스프레드시트를 처리하고 중요한 이상 징후를 포착하며, 절차에 따라 보고서를 생성. 하루 걸리던 작업을 1시간으로 단축.

### CrowdStrike와 RBC Wealth Management
Salesforce의 Agentforce와 Amazon Bedrock을 통해 Claude를 사용하여 규제 산업에서 안전하게 AI 활용.

## 주의사항

### 보안
Skills는 코드 실행 권한을 갖습니다. 신뢰할 수 있는 출처의 Skills만 사용해야 합니다.

#### 신뢰할 수 없는 출처의 Skill 설치 전 주의사항
- Skill 폴더 내 모든 파일의 내용을 철저히 검토
- 코드 의존성과 번들된 리소스(이미지, 스크립트) 확인
- 신뢰할 수 없는 외부 네트워크 소스에 연결하는 지침이나 코드 확인

### 프롬프트 인젝션 위험
악의적인 Skill이 Claude를 조작하여 의도하지 않은 작업을 실행하도록 할 수 있습니다. 공식 Anthropic Skills나 검증된 출처의 Skills 사용을 권장합니다.

## 커뮤니티와 생태계

Anthropic은 Skills 생태계가 빠르게 성장하고 있으며, GitHub에서 다양한 커뮤니티 제작 Skills를 찾을 수 있다고 밝혔습니다.

### 공식 저장소
- **anthropics/skills**: Anthropic의 공식 예제 Skills

### 커뮤니티 컬렉션
- 텍스트 정리, 자동화, 디자인, 분석 등 다양한 니치 영역의 Skills

## 향후 전망

Anthropic은 다음과 같은 방향으로 Skills를 발전시킬 계획입니다.

### 간소화된 생성 워크플로
더 쉽게 Skills를 만들 수 있도록 지원.

### 기업 전체 배포 기능
조직 내에서 Skills를 팀 전체에 쉽게 배포할 수 있는 기능.

### AI 자체 Skill 생성
장기적으로는 AI가 스스로 Skills를 생성, 편집, 평가하여 재사용 가능한 능력으로 만들 수 있도록 할 계획.

### MCP와의 통합 강화
MCP 서버와 Skills를 결합하여 외부 도구와 소프트웨어를 포함하는 더 복잡한 워크플로를 가르칠 수 있도록 지원.

## 결론

Claude Skills는 프롬프트 엔지니어링의 새로운 패러다임을 제시합니다. 반복적인 긴 프롬프트 대신 재사용 가능한 모듈식 능력으로 Claude를 전문화할 수 있습니다. 특히 기업 환경에서 조직의 워크플로와 컨텍스트를 Claude에게 효과적으로 전달할 수 있는 강력한 도구입니다.

OpenAI의 AgentKit 발표와 시기를 같이하며, 2025년 AI 에이전트 경쟁의 핵심 전장이 프로토타입에서 실제 프로덕션 환경으로 옮겨가고 있음을 보여줍니다.

Skills는 Claude Code의 핵심 기능 중 하나로, 개발자들이 반복적인 작업을 자동화하고, 일관성 있는 결과를 얻으며, 전문적인 워크플로우를 구축할 수 있는 강력한 도구입니다. 이 기능을 효과적으로 활용하면 개발 생산성을 크게 향상시킬 수 있습니다.