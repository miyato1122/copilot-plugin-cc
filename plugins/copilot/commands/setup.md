# /copilot:setup

Check whether GitHub Copilot CLI is installed and ready to use.

## Usage

```
/copilot:setup
```

## Instructions

When this command is invoked:

1. **Check `copilot` CLI**:
   - Run `copilot --version`
   - If not found: tell the user to install GitHub Copilot CLI from https://docs.github.com/copilot/how-tos/copilot-cli

2. **Check authentication**:
   - Run `copilot -p "ping" -s` and confirm it returns a response
   - If not authenticated: tell the user to run `copilot login`

3. **Report status**: Show a clear summary of each check with ✅ or ❌, and next steps if anything is missing.

### Example output

```
✅ copilot CLI installed (1.x.x)
✅ Authenticated

GitHub Copilot CLI is ready. Run /copilot:review to review your changes.
```
