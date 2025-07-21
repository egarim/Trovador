# Contributing to Trovador

Thank you for your interest in contributing to Trovador! This document provides guidelines and instructions for contributing.

## Getting Started

1. Fork the repository
2. Clone your fork: `git clone https://github.com/yourusername/trovador.git`
3. Create a feature branch: `git checkout -b feature/your-feature-name`
4. Install dependencies: `npm install`
5. Start development: `npm run dev`

## Development Setup

### Prerequisites

- Node.js v14 or higher
- npm v6 or higher
- Git

### Environment Setup

1. Copy `.env.example` to `.env` (if applicable)
2. Install recommended VS Code extensions
3. Run `npm install` to install dependencies

## Code Style

We use ESLint and Prettier for code formatting:

```bash
# Run linting
npm run lint

# Fix linting issues
npm run lint:fix

# Format code
npm run format
```

## Project Structure

- `src/main/` - Electron main process code
- `src/renderer/` - React application code  
- `src/shared/` - Shared types and utilities
- `public/` - Static assets
- `scripts/` - Build and utility scripts

## Making Changes

1. Ensure your changes follow the existing code style
2. Add tests for new functionality
3. Update documentation as needed
4. Commit messages should follow conventional commits format

### Commit Message Format

```
type(scope): subject

body (optional)

footer (optional)
```

Types: feat, fix, docs, style, refactor, test, chore

## Testing

```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run e2e tests
npm run test:e2e
```

## Pull Request Process

1. Update the README.md with details of changes if applicable
2. Ensure all tests pass
3. Update documentation
4. Request review from maintainers
5. Once approved, your PR will be merged

## Reporting Issues

- Use the issue tracker to report bugs
- Describe the issue in detail
- Include steps to reproduce
- Mention your OS and Trovador version

## Questions?

Feel free to open an issue for any questions about contributing.
