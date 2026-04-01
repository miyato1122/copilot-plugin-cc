# copilot-plugin-cc

Use GitHub Copilot CLI from inside Claude Code to review code changes.

Inspired by [openai/codex-plugin-cc](https://github.com/openai/codex-plugin-cc).

## Commands

| Command | Description |
|---|---|
| `/copilot:review` | Review current uncommitted changes or a branch diff |
| `/copilot:setup` | Check that GitHub Copilot CLI is installed and authenticated |

## Requirements

- [GitHub CLI](https://cli.github.com) (`gh`)
- GitHub Copilot CLI extension: `gh extension install github/gh-copilot`
- GitHub Copilot Pro (or higher) plan

## Install

```
/plugin install copilot@your-username
```

Or locally with:

```
claude --plugin-dir ./copilot-plugin-cc
```

Then run:

```
/copilot:setup
```

## Usage

### `/copilot:review`

Review uncommitted changes:

```
/copilot:review
```

Review diff against a base branch:

```
/copilot:review --base main
```

Review with a specific focus:

```
/copilot:review --base main look for security issues
```

## Notes

Unlike `codex-plugin-cc`, this plugin does not support background execution since `gh copilot` is an interactive CLI. For long-running reviews, open a second Claude Code session.
