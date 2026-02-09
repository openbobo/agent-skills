# GitHub CLI Skills

## Essential Commands

### CI/CD Debugging
```bash
# View only FAILED steps (HUGELY useful!)
gh run view <run-id> --log-failed

# With repo
gh run view <id> --repo owner/repo --log-failed
```

### Structured API Output
```bash
# JSON output with jq filtering
gh issue list --json number,title --jq '.[] | "\(.number): \(.title)"'

# Extract specific fields
gh api repos/owner/repo/pulls/55 --jq '.title, .state, .user.login'

# List PRs with custom format
gh pr list --json number,title,state,author --jq '.[] | "\(.number) [\(.state)] \(.title) - @\(.author.login)"'
```

### Useful Flags
- `--repo owner/repo` - Target specific repo
- `--json` - Structured output
- `--jq '<filter>'` - Filter JSON output
- `--log-failed` - Only failed CI steps

## Examples

### Check CI Status
```bash
gh pr checks 55
gh run list --repo owner/repo
```

### Work with Issues
```bash
gh issue list --repo owner/repo --state open
gh issue view 123
gh issue create --title "Bug" --body "Description"
```

---

*From GitHub skill (SKILL.md) + self-improvement learning*
