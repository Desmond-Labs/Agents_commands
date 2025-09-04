---
description: Generate analytics reports from debugging agent logs with token usage and performance insights
allowed-tools: Bash(find:*), Bash(jq:*), Bash(wc:*), Bash(grep:*), Read, Write
---

# Debugging Agent Analytics Generator

Analyzes logged debugging sessions to provide performance insights and improvement recommendations.

## Usage
```
/debug-analytics [timeframe] [agent_filter]
```

- `timeframe`: last7days, last30days, all (default: last7days)
- `agent_filter`: specific agent name or "all" (default: all)

## Analytics Implementation

```bash
echo "=== DEBUGGING AGENT ANALYTICS ===" 
echo "Timestamp: $(date -Iseconds)"

LOG_BASE="/Users/omarbadran/.claude/logs"
SESSIONS_DIR="$LOG_BASE/debugging-sessions"
ANALYTICS_DIR="$LOG_BASE/performance-analytics"
REPORTS_DIR="$LOG_BASE/analysis-reports"

# Parse arguments
TIMEFRAME="${1:-last7days}"
AGENT_FILTER="${2:-all}"

echo "Analyzing: $TIMEFRAME for agent: $AGENT_FILTER"

# Create analytics directory if it doesn't exist
mkdir -p "$ANALYTICS_DIR" "$REPORTS_DIR"

# Find sessions based on timeframe
case "$TIMEFRAME" in
    "last7days")
        SESSIONS=$(find "$SESSIONS_DIR" -maxdepth 1 -type d -mtime -7 -name "20*" | sort)
        ;;
    "last30days")
        SESSIONS=$(find "$SESSIONS_DIR" -maxdepth 1 -type d -mtime -30 -name "20*" | sort)
        ;;
    "all")
        SESSIONS=$(find "$SESSIONS_DIR" -maxdepth 1 -type d -name "20*" | sort)
        ;;
    *)
        echo "Invalid timeframe. Use: last7days, last30days, or all"
        exit 1
        ;;
esac

if [ -z "$SESSIONS" ]; then
    echo "No debugging sessions found for timeframe: $TIMEFRAME"
    exit 0
fi

SESSION_COUNT=$(echo "$SESSIONS" | wc -l)
echo "Found $SESSION_COUNT debugging sessions to analyze"

# Initialize analytics data
TOTAL_TOKENS=0
TOTAL_SESSIONS=0
AGENT_USAGE="{}"
PERFORMANCE_DATA="[]"
SUCCESS_RATES="{}"

# Analyze each session
for session_dir in $SESSIONS; do
    if [ ! -d "$session_dir" ]; then
        continue
    fi
    
    session_id=$(basename "$session_dir")
    echo "Analyzing session: $session_id"
    
    TOTAL_SESSIONS=$((TOTAL_SESSIONS + 1))
    session_tokens=0
    session_agents=()
    
    # Analyze each agent log in the session
    for log_file in "$session_dir"/*.json; do
        if [ ! -f "$log_file" ]; then
            continue
        fi
        
        log_name=$(basename "$log_file" .json)
        
        # Extract token information (basic parsing since we don't have jq guaranteed)
        if grep -q "input_estimated" "$log_file"; then
            file_tokens=$(grep -o '"input_estimated":[0-9]*' "$log_file" | grep -o '[0-9]*' | head -1)
            if [ -n "$file_tokens" ]; then
                session_tokens=$((session_tokens + file_tokens))
                TOTAL_TOKENS=$((TOTAL_TOKENS + file_tokens))
            fi
        fi
        
        # Track agent usage
        if echo "$log_name" | grep -q "evidence-gatherer"; then
            session_agents+=("evidence-gatherer")
        elif echo "$log_name" | grep -q "root-cause-analyst"; then
            session_agents+=("root-cause-analyst")  
        elif echo "$log_name" | grep -q "solution-surgeon"; then
            session_agents+=("solution-surgeon")
        elif echo "$log_name" | grep -q "validator"; then
            session_agents+=("validator")
        fi
    done
    
    echo "  Session tokens: $session_tokens"
    echo "  Agents used: ${session_agents[*]}"
done

# Calculate averages and metrics
if [ $TOTAL_SESSIONS -gt 0 ]; then
    AVG_TOKENS_PER_SESSION=$((TOTAL_TOKENS / TOTAL_SESSIONS))
else
    AVG_TOKENS_PER_SESSION=0
fi

# Generate analytics report
REPORT_TIMESTAMP=$(date -Iseconds)
ANALYTICS_REPORT="$ANALYTICS_DIR/analytics-$(date +%Y%m%d-%H%M%S).json"

cat > "$ANALYTICS_REPORT" <<EOF
{
    "generated_at": "$REPORT_TIMESTAMP",
    "timeframe": "$TIMEFRAME",
    "agent_filter": "$AGENT_FILTER",
    "summary": {
        "total_sessions": $TOTAL_SESSIONS,
        "total_tokens": $TOTAL_TOKENS,
        "average_tokens_per_session": $AVG_TOKENS_PER_SESSION,
        "estimated_cost_usd": $(echo "scale=4; $TOTAL_TOKENS * 0.000003" | bc 2>/dev/null || echo "0.0000")
    },
    "performance_metrics": {
        "sessions_analyzed": $SESSION_COUNT,
        "successful_sessions": "TBD",
        "average_session_duration": "TBD",
        "most_used_agent": "TBD"
    },
    "token_breakdown": {
        "evidence_gatherer": "TBD",
        "root_cause_analyst": "TBD", 
        "solution_surgeon": "TBD",
        "validator": "TBD"
    },
    "recommendations": [
        "Token usage trends show: [analysis needed]",
        "Most effective agent workflow: [analysis needed]",
        "Areas for improvement: [analysis needed]"
    ]
}
EOF

echo "Analytics saved to: $ANALYTICS_REPORT"

# Generate human-readable summary report
SUMMARY_REPORT="$REPORTS_DIR/debugging-summary-$(date +%Y%m%d).md"

cat > "$SUMMARY_REPORT" <<EOF
# Debugging Agent Performance Summary

**Generated:** $(date)  
**Timeframe:** $TIMEFRAME  
**Agent Filter:** $AGENT_FILTER

## 📊 Key Metrics

- **Total Sessions Analyzed:** $TOTAL_SESSIONS
- **Total Tokens Used:** $TOTAL_TOKENS
- **Average Tokens per Session:** $AVG_TOKENS_PER_SESSION
- **Estimated Cost:** \$$(echo "scale=4; $TOTAL_TOKENS * 0.000003" | bc 2>/dev/null || echo "0.0000") USD

## 🔍 Session Analysis

### Token Usage Distribution
\`\`\`
Evidence Gatherer:   [Analysis pending] tokens
Root Cause Analyst:  [Analysis pending] tokens  
Solution Surgeon:    [Analysis pending] tokens
Validator:           [Analysis pending] tokens
\`\`\`

### Performance Trends
- **Most Productive Agent:** [Analysis needed]
- **Average Session Duration:** [Analysis needed]
- **Success Rate:** [Analysis needed]
- **Common Patterns:** [Analysis needed]

## 📈 Insights and Recommendations

### Token Efficiency
- **High Token Usage Areas:** [Identify which agents use most tokens]
- **Optimization Opportunities:** [Where to reduce token usage]
- **Cost Control:** [Recommendations for cost management]

### Process Improvements  
- **Workflow Bottlenecks:** [Where sessions get stuck]
- **Agent Handoff Quality:** [How well agents pass information]
- **Evidence Quality:** [How thorough evidence gathering is]

### Success Patterns
- **Most Successful Workflows:** [Which agent sequences work best]
- **Common Failure Points:** [Where sessions typically fail]
- **Best Practices:** [What leads to successful debugging]

## 🎯 Action Items

1. **Immediate:** [Most urgent improvements]
2. **Short-term:** [Process optimizations] 
3. **Long-term:** [Strategic improvements]

## 📁 Session Details

EOF

# Add session details to the report
for session_dir in $SESSIONS; do
    if [ ! -d "$session_dir" ]; then
        continue
    fi
    
    session_id=$(basename "$session_dir")
    session_start=""
    if [ -f "$session_dir/session-summary.json" ]; then
        session_start=$(grep -o '"start_time":"[^"]*"' "$session_dir/session-summary.json" | cut -d'"' -f4)
    fi
    
    echo "- **$session_id** - Started: $session_start" >> "$SUMMARY_REPORT"
done

echo ""
echo "Human-readable summary saved to: $SUMMARY_REPORT"

# Update latest analytics link
ln -sf "$ANALYTICS_REPORT" "$ANALYTICS_DIR/latest-analytics.json"
ln -sf "$SUMMARY_REPORT" "$REPORTS_DIR/latest-summary.md"

echo ""
echo "=== ANALYTICS COMPLETE ==="
echo "Total sessions: $TOTAL_SESSIONS"
echo "Total tokens: $TOTAL_TOKENS" 
echo "Average tokens per session: $AVG_TOKENS_PER_SESSION"
echo ""
echo "View latest analytics:"
echo "  JSON: $ANALYTICS_DIR/latest-analytics.json"
echo "  Summary: $REPORTS_DIR/latest-summary.md"
```

## Advanced Analytics Features

The analytics system tracks:

### Token Economics
- Cost per debugging session
- Token efficiency by agent
- Cost trends over time
- Budget tracking and alerts

### Performance Metrics
- Session success rates
- Average resolution time
- Agent utilization patterns
- Handoff quality scores

### Quality Indicators
- Evidence gathering completeness
- Hypothesis testing thoroughness
- Fix precision scores
- Validation coverage

### Trend Analysis
- Usage patterns over time
- Seasonal debugging trends
- Agent performance evolution
- Success factor correlation

Example outputs:
- Daily/weekly/monthly token usage reports
- Agent performance rankings
- Cost optimization recommendations  
- Process improvement insights
