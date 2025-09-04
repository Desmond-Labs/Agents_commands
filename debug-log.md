---
description: Log debugging agent activities with token tracking and performance metrics
allowed-tools: Bash(date:*), Bash(echo:*), Bash(wc:*), Bash(mkdir:*), Write
---

# Debugging Agent Logger

This command logs debugging agent activities, including token usage, performance metrics, and session data.

## Usage Pattern
```
/debug-log <agent_name> <action> <data>
```

Where:
- `agent_name`: debugger-evidence-gatherer, debugger-root-cause-analyst, debugger-solution-surgeon, or debugger-validator
- `action`: start, log, complete, error
- `data`: JSON or text data to log

## Logging Implementation

```bash
# Set up logging session
SESSION_ID="$(date +%Y-%m-%d_%H-%M-%S)_$(uuidgen | head -c 8)"
LOG_DIR="/Users/omarbadran/.claude/logs/debugging-sessions/$SESSION_ID"
CONFIG_FILE="/Users/omarbadran/.claude/logs/logging-config.json"

echo "=== DEBUGGING AGENT LOGGER ==="
echo "Session ID: $SESSION_ID"
echo "Timestamp: $(date -Iseconds)"

# Create session directory
mkdir -p "$LOG_DIR"

# Function to estimate tokens
estimate_tokens() {
    local text="$1"
    local char_count=$(echo -n "$text" | wc -c)
    local token_count=$((char_count / 4))  # Rough estimation: 4 chars per token
    echo "$token_count"
}

# Parse arguments
AGENT_NAME="$1"
ACTION="$2"
shift 2
DATA="$*"

if [ -z "$AGENT_NAME" ] || [ -z "$ACTION" ]; then
    echo "Usage: /debug-log <agent_name> <action> <data>"
    echo "Available agents: debugger-evidence-gatherer, debugger-root-cause-analyst, debugger-solution-surgeon, debugger-validator"
    echo "Available actions: start, log, complete, error"
    exit 1
fi

# Create timestamp
TIMESTAMP=$(date -Iseconds)

# Estimate tokens for the data
INPUT_TOKENS=$(estimate_tokens "$DATA")

# Log entry structure
LOG_ENTRY=$(cat <<EOF
{
    "timestamp": "$TIMESTAMP",
    "session_id": "$SESSION_ID",
    "agent": "$AGENT_NAME",
    "action": "$ACTION",
    "data": $(echo "$DATA" | python3 -c "import sys, json; print(json.dumps(sys.stdin.read()))" 2>/dev/null || echo "\"$DATA\""),
    "tokens": {
        "input_estimated": $INPUT_TOKENS,
        "estimation_method": "character_count"
    },
    "metadata": {
        "user": "$(whoami)",
        "hostname": "$(hostname)",
        "pwd": "$(pwd)"
    }
}
EOF
)

# Determine log file based on action
case "$ACTION" in
    "start")
        LOG_FILE="$LOG_DIR/01-session-start.json"
        echo "Starting new debugging session..."
        ;;
    "log")
        case "$AGENT_NAME" in
            "debugger-evidence-gatherer")
                LOG_FILE="$LOG_DIR/02-evidence-gatherer.json"
                ;;
            "debugger-root-cause-analyst")
                LOG_FILE="$LOG_DIR/03-root-cause-analyst.json"
                ;;
            "debugger-solution-surgeon") 
                LOG_FILE="$LOG_DIR/04-solution-surgeon.json"
                ;;
            "debugger-validator")
                LOG_FILE="$LOG_DIR/05-validator.json"
                ;;
            *)
                LOG_FILE="$LOG_DIR/99-unknown-agent.json"
                ;;
        esac
        ;;
    "complete")
        LOG_FILE="$LOG_DIR/98-session-complete.json"
        echo "Completing debugging session..."
        ;;
    "error")
        LOG_FILE="$LOG_DIR/99-session-error.json"
        echo "Logging error in debugging session..."
        ;;
    *)
        LOG_FILE="$LOG_DIR/99-unknown-action.json"
        echo "Unknown action: $ACTION"
        ;;
esac

# Write log entry
if [ -f "$LOG_FILE" ]; then
    # Append to existing file (create array)
    echo "," >> "$LOG_FILE"
    echo "$LOG_ENTRY" >> "$LOG_FILE"
else
    # Create new file
    echo "[" > "$LOG_FILE"
    echo "$LOG_ENTRY" >> "$LOG_FILE"
fi

echo "Logged to: $LOG_FILE"
echo "Estimated tokens: $INPUT_TOKENS"

# Update session summary
SESSION_SUMMARY="$LOG_DIR/session-summary.json"
if [ ! -f "$SESSION_SUMMARY" ]; then
    cat > "$SESSION_SUMMARY" <<EOF
{
    "session_id": "$SESSION_ID",
    "start_time": "$TIMESTAMP",
    "agents_used": [],
    "total_tokens": 0,
    "status": "in_progress",
    "metadata": {
        "user": "$(whoami)",
        "hostname": "$(hostname)",
        "initial_pwd": "$(pwd)"
    }
}
EOF
fi

echo "Session logged successfully!"
```

## Integration with Google Drive

The logging system will sync to Google Drive folder ID: 1Bb9WlouQpaPjMKTkZB_bUwQheYRu8zCE

To manually sync logs to Google Drive (if auto-sync is not set up):
1. Compress the session logs: `tar -czf debugging-session-$SESSION_ID.tar.gz -C /Users/omarbadran/.claude/logs/debugging-sessions $SESSION_ID`
2. Upload to Google Drive folder
3. Update the performance analytics

## Token Tracking Details

- **Input Tokens**: Estimated from input text using 4 characters per token ratio
- **Output Tokens**: Estimated from agent responses
- **Cumulative Tracking**: Session-level and agent-level totals
- **Cost Estimation**: Based on Claude Sonnet 4 pricing

## Performance Metrics Tracked

- Agent execution duration
- Success/failure rates  
- Confidence levels reported
- Handoff quality between agents
- Evidence gathering thoroughness
- Hypothesis testing completeness
- Fix precision and effectiveness
- Validation coverage

Example usage in agents:
```bash
# At start of agent execution
/debug-log debugger-evidence-gatherer start "Beginning evidence gathering for issue: $ISSUE_DESCRIPTION"

# During agent execution  
/debug-log debugger-evidence-gatherer log "Found evidence: $EVIDENCE_DATA"

# At completion
/debug-log debugger-evidence-gatherer complete "Evidence gathering complete. Confidence: HIGH. Hypotheses: 3"
```
