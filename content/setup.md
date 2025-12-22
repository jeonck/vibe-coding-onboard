# Development Environment Setup

## Prerequisites

Before starting with your development environment, ensure you have:

- Administrative access to your machine (for installing tools)
- A stable internet connection
- Basic familiarity with command-line tools

## Essential Tools

### Version Control
- **Git**: We use Git for version control with GitHub as our remote repository host
- Install Git from [git-scm.com](https://git-scm.com/)
- Configure your Git identity:
  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "your.email@company.com"
  ```

### Code Editor
We recommend using **Visual Studio Code** or **Claude Code** with the following extensions:
- GitLens: Enhanced Git capabilities
- Prettier: Code formatter
- ESLint: JavaScript/TypeScript linting
- Bracket Pair Colorizer: Colorized brackets
- Path Intellisense: Autocompletes filenames

#### Claude Code Installation
For an AI-enhanced coding experience, consider installing Claude Code:
- Visit [Claude Code Setup Guide](https://code.claude.com/docs/ko/setup) for installation instructions
- Claude Code provides AI-powered assistance for coding, debugging, and code review
- The tool integrates with your existing development workflow

##### Command Line Installation
You can also install Claude Code via command line:
```bash
curl -fsSL https://claude.ai/install.sh | bash
```

After installation, you should see output similar to:
```
Setting up Claude Code...

✔ Claude Code successfully installed!

  Version: 2.0.75

  Location: ~/.local/bin/claude


  Next: Run claude --help to get started

⚠ Setup notes:
  • Native installation exists but ~/.local/bin is not in your PATH. Run:

  echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc && source ~/.zshrc
```

If you see the PATH warning, run the suggested command to add Claude Code to your PATH, then you can use `claude` commands from anywhere in your terminal.

### Package Managers
- **Node Version Manager (nvm)**: For managing Node.js versions
- **Homebrew** (macOS): For managing system packages

## Project-Specific Setup

### Backend Development
1. Install Node.js using nvm:
   ```bash
   nvm install --lts
   nvm use --lts
   ```

2. Install project dependencies:
   ```bash
   npm install
   ```

3. Set up environment variables using the `.env.example` file as reference

### Frontend Development
1. Install additional tools:
   - Webpack for module bundling
   - Babel for JavaScript transpilation
   - PostCSS for CSS processing

2. Use the development server:
   ```bash
   npm run dev
   ```

### Database Setup
1. Install Docker for containerized database management
2. Use the provided docker-compose file to set up databases
3. Run database migrations with the provided scripts

## Development Workflow

### Branch Strategy
- Use feature branches from `develop` for new features
- Keep branches focused on a single task or feature
- Use descriptive branch names: `feature/user-authentication`, `bugfix/login-error`

### Commit Messages
- Follow the conventional commits format
- Use imperative mood: "Add feature" not "Added feature" or "Adds feature"
- Keep the first line under 50 characters
- Include a more detailed description if needed

### Local Development
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <project-name>
   ```

2. Create your feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. Make your changes and test them locally

4. Commit your changes with a descriptive message

5. Push your branch and create a pull request

## Useful Commands

- `npm run dev`: Start the development server
- `npm run test`: Run all tests
- `npm run lint`: Check code formatting and linting
- `npm run build`: Create a production build
- `npm run format`: Format code using Prettier

## Troubleshooting

### Common Issues
- If dependencies fail to install, try clearing the cache: `npm cache clean --force`
- For permission errors, ensure you're not running as root/administrator unless necessary
- If the development server won't start, check that no other processes are using the same port

### Getting Help
- Check the README files in each project
- Look for documentation in the `/docs` directory
- Ask in the `#dev-help` channel in our communication platform