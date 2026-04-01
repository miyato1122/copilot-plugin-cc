# /copilot:review

Run a code review on your current changes using GitHub Copilot CLI.

## Usage

```
/copilot:review [options] [focus]
```

## Options

- `--base <ref>` — Compare against a branch or commit (e.g., `--base main`). Defaults to uncommitted changes.
- `--wait` — Wait for completion and show results inline (default behavior).

## Examples

```
/copilot:review
/copilot:review --base main
/copilot:review focus on error handling and edge cases
/copilot:review --base main look for security issues
```

## What it does

1. Checks that `gh` CLI is installed and authenticated.
2. Determines the review target:
   - With `--base <ref>`: reviews the diff between current branch and `<ref>` using `git diff <ref>`
   - Without `--base`: reviews uncommitted changes using `git diff HEAD`
3. Pipes the diff into `gh copilot` with the `/review` command and any focus text provided.
4. Displays the Copilot review feedback inline.

## Instructions

When this command is invoked:

1. **Check prerequisites**: Run `gh --version` to confirm `gh` is installed. If not, tell the user to install GitHub CLI from https://cli.github.com and run `gh auth login`.

2. **Check Copilot CLI**: Run `gh extension list` and check for `github/gh-copilot`. If missing, tell the user to run:
   ```
   gh extension install github/gh-copilot
   ```

3. **Determine diff target**:
   - If `--base <ref>` is provided, run: `git diff <ref>`
   - Otherwise, run: `git diff HEAD`
   - If the diff is empty, inform the user there are no changes to review.

4. **Run the review**: Pass the diff to Copilot CLI for review. Use the Bash tool to run:
   ```
   git diff [<ref>|HEAD] | gh copilot suggest -t shell "/review <focus>"
   ```
   Or if no focus text, simply:
   ```
   git diff [<ref>|HEAD] | gh copilot suggest -t shell "/review"
   ```
   Note: Since `gh copilot` is interactive, run it with the diff piped in and capture stdout.

5. **Display results**: Show the Copilot review output clearly to the user. Summarize key findings and highlight any actionable suggestions.

6. **Handle errors**: If `gh copilot` returns an error or requires interactive input that cannot be satisfied non-interactively, inform the user and suggest running `gh copilot` directly in the terminal with:
   ```
   git diff HEAD | gh copilot suggest -t shell "/review"
   ```
