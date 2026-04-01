# /copilot:setup

Check whether GitHub Copilot CLI is installed and ready to use.

## Usage

```
/copilot:setup
```

## Instructions

When this command is invoked:

1. **Check `gh` CLI**:
   - Run `gh --version`
   - If not found: tell the user to install GitHub CLI from https://cli.github.com

2. **Check authentication**:
   - Run `gh auth status`
   - If not authenticated: tell the user to run `gh auth login`

3. **Check Copilot extension**:
   - Run `gh extension list`
   - Look for `github/gh-copilot` in the output
   - If missing: tell the user to run:
     ```
     gh extension install github/gh-copilot
     ```

4. **Verify Copilot CLI works**:
   - Run `gh copilot --version`
   - Confirm version is displayed

5. **Report status**: Show a clear summary of each check with ✅ or ❌, and next steps if anything is missing.

### Example output

```
✅ gh CLI installed (2.x.x)
✅ Authenticated as your-username
✅ gh-copilot extension installed (1.x.x)

GitHub Copilot CLI is ready. Run /copilot:review to review your changes.
```
