# /copilot:review

Run a code review on your current changes using GitHub Copilot CLI.

## Usage

```
/copilot:review [options] [focus]
```

## Options

- `--base <ref>` — Compare against a branch or commit (e.g., `--base main`). Defaults to uncommitted changes.

## Examples

```
/copilot:review
/copilot:review --base main
/copilot:review focus on error handling and edge cases
/copilot:review --base main look for security issues
```

## What it does

1. Determines the review target:
   - With `--base <ref>`: reviews the diff between current branch and `<ref>` using `git diff <ref>`
   - Without `--base`: reviews uncommitted changes using `git diff HEAD` (includes both staged and unstaged)
2. Passes the diff to `copilot -p` for review.
3. Displays the Copilot review feedback inline.

## Instructions

When this command is invoked:

1. **Determine diff target**:
   - If `--base <ref>` is provided, run: `git diff <ref>`
   - Otherwise, run: `git diff HEAD` (covers both staged and unstaged changes)
   - If the diff is empty, inform the user there are no changes to review.

2. **Run the review**: Capture the diff and pass it to `copilot` for review. Use the Bash tool to run:
   ```
   DIFF=$(git diff HEAD) && copilot -p "$(printf 'Review the following code diff and provide feedback. Focus: <focus>\n\n%s' "$DIFF")" -s
   ```
   Or if no focus text:
   ```
   DIFF=$(git diff HEAD) && copilot -p "$(printf 'Review the following code diff and provide feedback:\n\n%s' "$DIFF")" -s
   ```
   For `--base <ref>`:
   ```
   DIFF=$(git diff <ref>) && copilot -p "$(printf 'Review the following code diff and provide feedback:\n\n%s' "$DIFF")" -s
   ```

3. **Display results**: Show the Copilot review output clearly to the user. Summarize key findings and highlight any actionable suggestions.

4. **Handle errors**: If `copilot` returns an error, inform the user and suggest running it directly in the terminal:
   ```
   DIFF=$(git diff HEAD) && copilot -p "$(printf 'Review this diff:\n\n%s' "$DIFF")" -s
   ```
