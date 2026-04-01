# copilot-plugin-cc【unofficial】

Use GitHub Copilot CLI from inside Claude Code to review code changes.

Inspired by [openai/codex-plugin-cc](https://github.com/openai/codex-plugin-cc).

## Commands

| Command | Description |
|---|---|
| `/copilot:review` | Review current uncommitted changes or a branch diff |
| `/copilot:setup` | Check that GitHub Copilot CLI is installed and authenticated |

## Requirements

- [GitHub Copilot CLI](https://docs.github.com/copilot/how-tos/copilot-cli) (`copilot`)
- GitHub Copilot Pro (or higher) plan

## Install

Add the marketplace in Claude Code:

```
/plugin marketplace add miyato1122/copilot-plugin-cc
```

Install the plugin:

```
/plugin install copilot@miyato1122
```

Reload plugins:

```
/reload-plugins
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

This plugin uses the standalone `copilot` CLI (`copilot -p`) for non-interactive execution, which requires GitHub Copilot CLI v1.0 or later.
