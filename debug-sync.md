---
description: Sync debugging logs to Google Drive for backup and sharing
allowed-tools: Bash(find:*), Bash(tar:*), Bash(curl:*), Bash(cp:*), Bash(rsync:*)
---

# Google Drive Sync for Debugging Logs

Syncs local debugging logs to the Google Drive folder for backup and team access.

## Usage
```
/debug-sync [action] [options]
```

Actions:
- `backup`: Create backup archive of all logs
- `sync`: Sync recent logs to Google Drive (requires Google Drive client)
- `status`: Check sync status and log space usage

## Sync Implementation

```bash
echo "=== DEBUGGING LOGS GOOGLE DRIVE SYNC ==="
echo "Timestamp: $(date -Iseconds)"

LOCAL_LOGS="/Users/omarbadran/.claude/logs"
GDRIVE_FOLDER_ID="1Bb9WlouQpaPjMKTkZB_bUwQheYRu8zCE"
GDRIVE_LOCAL_PATH="$HOME/Google Drive/Shared drives/Claude Code Knowledge/debugging-logs"

# Parse action
ACTION="${1:-status}"

case "$ACTION" in
    "backup")
        echo "Creating backup archive of debugging logs..."
        
        # Create timestamped backup
        BACKUP_NAME="debugging-logs-backup-$(date +%Y%m%d-%H%M%S).tar.gz"
        BACKUP_PATH="/tmp/$BACKUP_NAME"
        
        cd "$LOCAL_LOGS" || exit 1
        tar -czf "$BACKUP_PATH" \
            debugging-sessions/ \
            performance-analytics/ \
            analysis-reports/ \
            logging-config.json
        
        echo "Backup created: $BACKUP_PATH"
        echo "Size: $(du -h $BACKUP_PATH | cut -f1)"
        
        # Try to copy to Google Drive if available
        if [ -d "$GDRIVE_LOCAL_PATH" ]; then
            echo "Copying backup to Google Drive..."
            cp "$BACKUP_PATH" "$GDRIVE_LOCAL_PATH/"
            echo "Backup copied to Google Drive!"
        else
            echo "Google Drive not found at: $GDRIVE_LOCAL_PATH"
            echo "Manual upload required to: https://drive.google.com/drive/folders/$GDRIVE_FOLDER_ID"
        fi
        ;;
        
    "sync")
        echo "Syncing logs to Google Drive..."
        
        if [ -d "$GDRIVE_LOCAL_PATH" ]; then
            # Ensure target directory exists
            mkdir -p "$GDRIVE_LOCAL_PATH/debugging-sessions"
            mkdir -p "$GDRIVE_LOCAL_PATH/performance-analytics" 
            mkdir -p "$GDRIVE_LOCAL_PATH/analysis-reports"
            
            # Sync each directory
            echo "Syncing debugging sessions..."
            rsync -av --update "$LOCAL_LOGS/debugging-sessions/" "$GDRIVE_LOCAL_PATH/debugging-sessions/"
            
            echo "Syncing performance analytics..."
            rsync -av --update "$LOCAL_LOGS/performance-analytics/" "$GDRIVE_LOCAL_PATH/performance-analytics/"
            
            echo "Syncing analysis reports..."
            rsync -av --update "$LOCAL_LOGS/analysis-reports/" "$GDRIVE_LOCAL_PATH/analysis-reports/"
            
            echo "Syncing configuration..."
            cp "$LOCAL_LOGS/logging-config.json" "$GDRIVE_LOCAL_PATH/"
            
            echo "Sync complete!"
        else
            echo "ERROR: Google Drive path not found: $GDRIVE_LOCAL_PATH"
            echo "Please ensure Google Drive is mounted and the shared drive is accessible"
            echo "Alternative: Use 'backup' action to create an archive for manual upload"
        fi
        ;;
        
    "status")
        echo "Checking debugging logs status..."
        
        # Local storage usage
        echo ""
        echo "=== LOCAL STORAGE ==="
        if [ -d "$LOCAL_LOGS" ]; then
            echo "Location: $LOCAL_LOGS"
            echo "Total size: $(du -sh $LOCAL_LOGS | cut -f1)"
            
            echo ""
            echo "Directory breakdown:"
            if [ -d "$LOCAL_LOGS/debugging-sessions" ]; then
                session_count=$(find "$LOCAL_LOGS/debugging-sessions" -maxdepth 1 -type d -name "20*" | wc -l)
                session_size=$(du -sh "$LOCAL_LOGS/debugging-sessions" 2>/dev/null | cut -f1)
                echo "  Sessions: $session_count sessions, $session_size"
            fi
            
            if [ -d "$LOCAL_LOGS/performance-analytics" ]; then
                analytics_count=$(find "$LOCAL_LOGS/performance-analytics" -name "*.json" | wc -l)
                analytics_size=$(du -sh "$LOCAL_LOGS/performance-analytics" 2>/dev/null | cut -f1)
                echo "  Analytics: $analytics_count reports, $analytics_size"
            fi
            
            if [ -d "$LOCAL_LOGS/analysis-reports" ]; then
                reports_count=$(find "$LOCAL_LOGS/analysis-reports" -name "*.md" | wc -l)
                reports_size=$(du -sh "$LOCAL_LOGS/analysis-reports" 2>/dev/null | cut -f1)
                echo "  Reports: $reports_count reports, $reports_size"
            fi
        else
            echo "No local logs directory found at: $LOCAL_LOGS"
        fi
        
        # Google Drive status
        echo ""
        echo "=== GOOGLE DRIVE STATUS ==="
        if [ -d "$GDRIVE_LOCAL_PATH" ]; then
            echo "Status: ✅ Connected"
            echo "Path: $GDRIVE_LOCAL_PATH"
            echo "Size: $(du -sh $GDRIVE_LOCAL_PATH 2>/dev/null | cut -f1)"
            
            # Check sync status
            echo ""
            echo "Sync status:"
            
            # Compare file counts
            if [ -d "$LOCAL_LOGS/debugging-sessions" ] && [ -d "$GDRIVE_LOCAL_PATH/debugging-sessions" ]; then
                local_sessions=$(find "$LOCAL_LOGS/debugging-sessions" -name "*.json" | wc -l)
                gdrive_sessions=$(find "$GDRIVE_LOCAL_PATH/debugging-sessions" -name "*.json" | wc -l)
                echo "  Sessions: Local=$local_sessions, GDrive=$gdrive_sessions"
            fi
            
            if [ -d "$LOCAL_LOGS/performance-analytics" ] && [ -d "$GDRIVE_LOCAL_PATH/performance-analytics" ]; then
                local_analytics=$(find "$LOCAL_LOGS/performance-analytics" -name "*.json" | wc -l)
                gdrive_analytics=$(find "$GDRIVE_LOCAL_PATH/performance-analytics" -name "*.json" | wc -l)
                echo "  Analytics: Local=$local_analytics, GDrive=$gdrive_analytics"
            fi
        else
            echo "Status: ❌ Not connected"
            echo "Expected path: $GDRIVE_LOCAL_PATH"
            echo "Setup required: Mount Google Drive or configure sync"
        fi
        
        # Recent activity
        echo ""
        echo "=== RECENT ACTIVITY ==="
        if [ -d "$LOCAL_LOGS/debugging-sessions" ]; then
            echo "Recent debugging sessions:"
            find "$LOCAL_LOGS/debugging-sessions" -maxdepth 1 -type d -name "20*" -mtime -7 | sort -r | head -5 | while read session_dir; do
                session_id=$(basename "$session_dir")
                session_date=$(echo "$session_id" | cut -d'_' -f1)
                echo "  - $session_id ($(date -j -f %Y-%m-%d $session_date +%B\ %d 2>/dev/null || echo $session_date))"
            done
        fi
        
        echo ""
        echo "=== RECOMMENDATIONS ==="
        
        # Storage recommendations
        if [ -d "$LOCAL_LOGS" ]; then
            log_size_mb=$(du -sm "$LOCAL_LOGS" | cut -f1)
            if [ "$log_size_mb" -gt 100 ]; then
                echo "⚠️  Large log directory ($log_size_mb MB) - consider archiving old sessions"
            fi
            
            # Check for old sessions
            old_sessions=$(find "$LOCAL_LOGS/debugging-sessions" -maxdepth 1 -type d -mtime +30 -name "20*" | wc -l)
            if [ "$old_sessions" -gt 0 ]; then
                echo "📦 $old_sessions sessions older than 30 days - consider archiving"
            fi
        fi
        
        # Sync recommendations
        if [ ! -d "$GDRIVE_LOCAL_PATH" ]; then
            echo "🔗 Set up Google Drive sync for automatic backup"
            echo "   1. Install Google Drive for Desktop"
            echo "   2. Add 'Claude Code Knowledge' shared drive"
            echo "   3. Run '/debug-sync sync' to initialize"
        fi
        ;;
        
    *)
        echo "Unknown action: $ACTION"
        echo "Available actions: backup, sync, status"
        exit 1
        ;;
esac

echo ""
echo "=== SYNC COMPLETE ==="
```

## Setup Instructions

### Google Drive Integration Setup

1. **Install Google Drive for Desktop**
   - Download from: https://www.google.com/drive/download/
   - Sign in with your account

2. **Access Shared Drive**
   - Ensure you have access to the shared drive containing folder ID: `1Bb9WlouQpaPjMKTkZB_bUwQheYRu8zCE`
   - The folder should appear in `~/Google Drive/Shared drives/`

3. **Create debugging-logs folder**
   - Navigate to the shared drive
   - Create a `debugging-logs` folder if it doesn't exist

4. **Run initial sync**
   ```bash
   /debug-sync sync
   ```

### Manual Backup Option

If automatic sync isn't available:
```bash
# Create backup archive
/debug-sync backup

# Manual upload to Google Drive
# 1. Go to https://drive.google.com/drive/folders/1Bb9WlouQpaPjMKTkZB_bUwQheYRu8zCE
# 2. Upload the generated .tar.gz file
```

### Automated Sync (Optional)

Add to crontab for automatic daily sync:
```bash
# Run daily at 2 AM
0 2 * * * /usr/local/bin/claude /debug-sync sync
```

## Security Notes

- Local logs contain debugging session data
- Ensure Google Drive access is properly secured
- Consider encrypting sensitive debugging logs
- Review retention policies for compliance

## Troubleshooting

### Common Issues

1. **Google Drive not mounted**
   - Restart Google Drive for Desktop
   - Check shared drive access permissions

2. **Permission denied**
   - Verify write access to Google Drive folder
   - Check local file permissions

3. **Large backup files**
   - Use compression for archives
   - Consider selective sync for recent data only

Example status output:
```
=== LOCAL STORAGE ===
Location: /Users/omarbadran/.claude/logs
Total size: 45MB
  Sessions: 12 sessions, 32MB
  Analytics: 8 reports, 5MB
  Reports: 15 reports, 8MB

=== GOOGLE DRIVE STATUS ===
Status: ✅ Connected
Path: /Users/omarbadran/Google Drive/Shared drives/Claude Code Knowledge/debugging-logs
Size: 42MB
Sync status:
  Sessions: Local=145, GDrive=140
  Analytics: Local=8, GDrive=8
```
