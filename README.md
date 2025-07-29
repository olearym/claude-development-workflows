# Claude Development Workflows

Personal Claude commands for systematic AI-assisted development. These evolved from real projects and enable parallel development with GitHub Issues/PRs.

## What This Is

A collection of structured prompts (Claude commands) that turn Claude into a development workflow orchestrator. Instead of ad-hoc conversations, these commands provide repeatable, context-aware workflows for common development tasks.

## Prerequisites

- [Claude CLI](https://docs.anthropic.com/en/docs/claude-code)
- GitHub CLI (`gh`) - for issue/PR workflows
- Git
- Python environment (examples use Python, but adaptable to other languages)

## Installation

1. Clone this repository
2. Copy commands to your Claude commands directory:
   ```bash
   cp *.md ~/.claude/commands/
   ```

Or reference directly from this repo:
```bash
claude --command ./design-feature.md "Add user authentication"
```

## Available Commands

### Planning & Design
- **`design-feature.md`** - Turn ideas into structured implementation plans
- **`create-implementation-tickets.md`** - Break epics into concrete GitHub issues

### Implementation
- **`implement-issue.md`** - TDD-driven issue implementation
- **`resume-work.md`** - Restore context and continue interrupted work

### Code Review
- **`review-pr.md`** - Systematic PR reviews
- **`respond-to-review.md`** - Address review feedback comprehensively

## Usage Examples

```bash
# Design a new feature
claude --command design-feature.md "Add real-time notifications"

# Implement a GitHub issue
claude --command implement-issue.md "Fix #123"

# Resume after interruption
claude --command resume-work.md

# Review a PR
claude --command review-pr.md "Review PR #456"
```

## Key Concepts

### GitHub Integration
These workflows assume GitHub-based development. Commands use `gh` CLI to:
- Read issue descriptions and context
- Check related PRs and design docs
- Understand project structure from existing code

### Parallel Development
Commands are designed to support working on multiple features simultaneously:
- Each issue gets its own branch
- Context restoration via `resume-work.md`
- Clear entry/exit points for switching tasks

### Systematic Approach
- **Context First**: Commands start by gathering project context
- **Validation Built-in**: Test-driven development, pre-commit checks
- **State Management**: TodoWrite tool tracks multi-step processes

## Adapting to Your Workflow

### Language Adaptation
Examples use Python/pytest, but the patterns work for any language:
- Replace `python3 -m pytest` with your test runner
- Update file extensions and import patterns
- Adjust linting/formatting commands

### Workflow Customization
- Remove TDD requirements if not applicable
- Adjust GitHub integration for other platforms
- Modify validation steps to match your process

## Caveats

- **Opinionated**: Assumes TDD, GitHub, systematic commits
- **Python-centric**: Examples need adaptation for other languages
- **Claude CLI Required**: Not for web interface usage
- **Learning Curve**: Commands are comprehensive, start with one

## Contributing

These are personal workflows - fork and adapt rather than submitting PRs. Share your adaptations!

## License

MIT License - see LICENSE file

---

*These commands demonstrate moving from ad-hoc AI assistance to systematic AI-integrated development workflows.*