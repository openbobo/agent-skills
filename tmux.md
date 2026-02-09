# tmux Skills for OpenClaw

## Socket Management
```bash
# Default socket: /tmp/openclaw-tmux-sockets/openclaw.sock
# Override: export CLAWDBOT_TMUX_SOCKET_DIR=/path/to/sockets
```

## Critical: Python REPL
```bash
# MUST set this for send-keys to work with Python
PYTHON_BASIC_REPL=1
```

## Capturing Output
```bash
# Join wrapped lines for cleaner parsing
capture-pane -p -J

# Get all output
capture-pane -p
```

## Detecting Completion
Look for shell prompts in output:
- `❯` (often used by starship/oh-my-zsh)
- `$` (standard bash)

## Helper Scripts
```bash
# wait-for-text.sh - Poll pane for regex patterns
./wait-for-text.sh -t 60 -i 2 "❯"  # Wait 60s, check every 2s for prompt

# find-sessions.sh - List sessions on socket
./find-sessions.sh
```

## Safe send-keys Pattern
```bash
tmux send-keys -t target -l -- "$cmd"
# -l flag prevents special character interpretation
# -- separates arguments from command string
```

## Parallel Agent Orchestration
```bash
# Create isolated sessions on same socket
tmux new-session -d -s agent1 -n main
tmux new-session -d -s agent2 -n main

# Send commands
tmux send-keys -t agent1:main "cd /project && npm run dev" Enter

# Monitor for completion
watch -n 2 "tmux capture-pane -p -t agent1:main | tail -1"
```

## Platform Support
- ✅ macOS (darwin)
- ✅ Linux
- ❌ Windows native (use WSL with tmux inside WSL)

---

*From tmux skill (SKILL.md) + self-improvement learning*
