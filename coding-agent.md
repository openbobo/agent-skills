# Coding Agent Skills

## Process Tool
```bash
# Monitor progress
process action:log --sessionId <id>

# Check if done
process action:poll --sessionId <id>

# Send input to agent
process action:write --sessionId <id> --data "command"

# Send keystrokes
process action:send-keys --sessionId <id> --keys ["Enter"]

# Kill session
process action:kill --sessionId <id>
```

## Workdir Pattern
```bash
# Focus agent on specific directory
workdir:/path/to/project

# Prevents wandering into unrelated files
# Essential for "little box" isolation
```

## Codex CLI Modes
```bash
# Sandbox + auto-approve
codex --full-auto

# Fastest (bypass sandbox + approvals)
codex --yolo
codex --dangerously-bypass-approvals-and-sandbox
```

## Best Practices
1. Use `workdir:` to contain agents
2. Check process status with `action:log`
3. Use `action:poll` to wait for completion
4. Kill stuck processes with `action:kill`

---

*From coding-agent skill (SKILL.md)*
