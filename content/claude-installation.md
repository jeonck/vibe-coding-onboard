# Claude Code 설치 가이드

## 설치 방법

Claude Code를 설치하는 가장 쉬운 방법은 아래의 명령어를 터미널에 입력하는 것입니다:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

이 명령어는 Claude Code 설치 스크립트를 다운로드하고 실행합니다.

## 설치 과정

설치를 완료하면 다음과 유사한 메시지를 확인할 수 있습니다:

```
Setting up Claude Code...

✔ Claude Code successfully installed!

  Version: 2.0.75

  Location: ~/.local/bin/claude


  Next: Run claude --help to get started

⚠ Setup notes:
  • Native installation exists but ~/.local/bin is not in your PATH. Run:

  echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc && source ~/.zshrc


✅ Installation complete!
```

## 경로 설정 (PATH)

설치 후 `claude` 명령어가 작동하지 않는 경우 (예: `zsh: command not found: claude`), PATH 설정이 필요합니다.

터미널에 다음 명령어를 입력하여 PATH를 설정하고 현재 세션에 적용합니다:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc && source ~/.zshrc
```

이 명령어는:
- `~/.zshrc` 파일에 `~/.local/bin` 디렉토리를 PATH에 추가
- 현재 터미널 세션에 변경 사항을 적용

## 설치 확인

설치가 완료되면 다음 명령어로 Claude Code가 정상적으로 설치되었는지 확인할 수 있습니다:

```bash
claude --help
```

이 명령어를 실행하면 Claude Code의 사용 가능한 옵션과 명령어가 표시됩니다.

## 시작하기

설치가 완료되면 다음 명령어로 Claude Code를 시작할 수 있습니다:

```bash
claude
```

이 명령어는 Claude와의 대화형 세션을 시작합니다.

## 문제 해결

### 명령어를 찾을 수 없음 (command not found)
- PATH 설정 명령어를 실행했는지 확인 (`echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc && source ~/.zshrc`)
- 터미널을 새로 열고 다시 시도

### 권한 문제
- 설치 스크립트가 `~/.local/bin` 디렉토리를 생성하고 쓰기 권한이 있는지 확인
- 필요시 `~/.local/bin` 디렉토리의 권한을 확인 (`ls -la ~/.local/bin`)

### 버전 확인
설치된 Claude Code의 버전을 확인하려면:

```bash
claude --version
```

Claude Code가 성공적으로 설치되면, 터미널에서 강력한 AI 코딩 도우미를 사용할 수 있습니다.