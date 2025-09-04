# /debug-production - Production Issue Emergency Response

Systematically debug critical production issues with enhanced safety protocols and emergency response procedures.

## Usage

```bash
# Critical production error
/debug-production --critical "500 errors spiking on checkout API - 95% error rate"

# Performance degradation
/debug-production --performance "Database response times increased 10x in last hour"

# Service outage
/debug-production --outage "User authentication service completely down"

# Data integrity issue
/debug-production --data "Users reporting missing order history"

# Security incident
/debug-production --security "Unusual API access patterns detected"

# Silent failure
/debug-production --silent "Background job processing stopped without errors"
```

## 🚨 Production Safety Protocols

### Critical Issue Triage (First 60 seconds)
```
🚨 **PRODUCTION TRIAGE PROTOCOL**

IMMEDIATE ASSESSMENT:
1. System stability check
2. Impact assessment (users affected, data at risk)
3. Emergency containment decision
4. Escalation and communication protocols
5. Safety checkpoint before any changes
```

**Production Triage Summary:**
```markdown
## 🚨 PRODUCTION TRIAGE SUMMARY
**Status:** ✅ COMPLETED / ⚠️ ESCALATION NEEDED / 🔴 EMERGENCY CONTAINMENT
**Duration:** [time taken for triage]
**Severity Classification:** [🔴 CRITICAL / 🟡 HIGH / 🟢 MEDIUM]

### Impact Assessment
- **Users Affected:** [number/percentage of users impacted]
- **Services Down:** [list of affected services/systems]
- **Data at Risk:** [any data integrity/loss concerns]
- **Business Impact:** [revenue/operations impact level]
- **SLA Status:** [SLA violation level and timeline]

### System Stability Check
- **Core Services:** [status of critical system components]
- **Resource Utilization:** [CPU/memory/disk status]
- **External Dependencies:** [third-party service status]
- **Error Rate:** [current error rates vs baseline]

### Emergency Response Decision
**Response Level:** [🔴 Emergency / 🟡 Urgent / 🟢 Standard]
**Containment Actions:** [immediate containment steps taken]
**Communication Plan:** [stakeholder notification strategy]
**Team Escalation:** [who was notified and when]

### Safety Checkpoint
**Database Safety:** ✅ SAFE / ⚠️ CAUTION REQUIRED / 🔴 AT RISK
**Service Stability:** ✅ STABLE / ⚠️ DEGRADED / 🔴 UNSTABLE
**Rollback Readiness:** ✅ READY / ⚠️ PARTIAL / ❌ NOT AVAILABLE
```

### Emergency Response Levels

**🔴 CRITICAL (System Down/Data Loss Risk)**
- Immediate emergency containment
- Skip normal evidence gathering - focus on restoration
- Document actions for post-incident analysis
- Implement fastest safe fix available

**🟡 HIGH (Performance/Functionality Impacted)**  
- Rapid but systematic approach
- Shortened evidence gathering phase
- Conservative fix implementation
- Enhanced monitoring during resolution

**🟢 MEDIUM (Monitoring Alerts/Minor Issues)**
- Full systematic debugging process
- Standard safety protocols
- Comprehensive validation before deployment

## 📋 Production-Specific Execution Protocol

### Phase 1: Production Evidence Gathering
```
🔍 **PHASE 1: PRODUCTION EVIDENCE GATHERING**

Use debugger-evidence-gatherer with production constraints:

PRODUCTION SAFETY RULES:
- NO write operations without explicit approval
- NO production database modifications during investigation
- NO service restarts without impact assessment
- READ-ONLY evidence gathering mode

ENHANCED MONITORING:
- Real-time metrics and alerting
- User impact measurement
- Performance baseline comparison
- External dependency status check
```

**Production Evidence Priorities:**
1. **System Health:** Current resource usage, service status, dependency health
2. **Error Patterns:** Log analysis, error rates, failure distribution
3. **Recent Changes:** Deployments, configuration changes, infrastructure updates
4. **User Impact:** Affected user percentage, business impact, SLA violations
5. **External Factors:** Third-party service issues, network problems, DDoS attacks

**Phase 1 Production Summary:**
```markdown
## 🔍 PHASE 1 PRODUCTION SUMMARY - EVIDENCE GATHERING
**Status:** ✅ COMPLETED / ⚠️ PARTIAL / ❌ FAILED
**Duration:** [time taken]
**Safety Compliance:** ✅ ALL RULES FOLLOWED / ⚠️ MINOR VIOLATIONS / ❌ SAFETY BREACH

### Production System Health Analysis
- **Service Status:** [status of all critical production services]
- **Resource Utilization:** [CPU: X%, Memory: X%, Disk: X%, Network: X%]
- **Database Performance:** [query times, connections, locks]
- **External Dependencies:** [third-party service status and response times]
- **Load Balancer Health:** [distribution and health checks]

### Error Pattern Analysis
- **Error Rate:** [current vs baseline error rates]
- **Error Distribution:** [geographic, service, user segment patterns]
- **Log Analysis:** [key error messages and stack traces found]
- **Alert History:** [timeline of alerts and escalations]

### Production Change Timeline
- **Recent Deployments:** [deployments in last 24-48 hours]
- **Configuration Changes:** [env vars, feature flags, infrastructure]
- **Infrastructure Updates:** [server changes, scaling events, maintenance]
- **Third-party Changes:** [external service updates affecting us]

### User Impact Assessment
- **Affected Users:** [number/percentage and demographics]
- **Business Metrics:** [revenue impact, conversion rates, key KPIs]
- **SLA Impact:** [current SLA compliance status]
- **Customer Complaints:** [support ticket volume and severity]

### Safety Compliance Report
- **Read-Only Mode:** ✅ MAINTAINED / ❌ VIOLATED
- **No DB Modifications:** ✅ CONFIRMED / ❌ ACCIDENTAL CHANGES
- **No Service Restarts:** ✅ CONFIRMED / ❌ UNAUTHORIZED RESTARTS
- **Approval Gates:** ✅ ALL FOLLOWED / ⚠️ BYPASSED WITH REASON

### Production Evidence Quality
**Evidence Sufficiency:** [Comprehensive/Adequate/Limited/Insufficient]
**Monitoring Coverage:** [areas well covered vs blind spots]
**Data Reliability:** [confidence level in gathered data]

### Production-Specific Hypotheses
1. **[Production Hypothesis 1]** - Likelihood: [High/Medium/Low]
   - **Production Evidence:** [specific production metrics/logs]
   - **Impact Scope:** [which services/users affected]
   - **Rollback Risk:** [risk level if hypothesis is wrong]

2. **[Production Hypothesis 2]** - Likelihood: [High/Medium/Low]
   - **Production Evidence:** [specific production metrics/logs]
   - **Impact Scope:** [which services/users affected]
   - **Deployment Risk:** [risk level for potential fixes]

### Handoff to Production Phase 2
**Critical Production Factors:** [production-specific considerations]
**Deployment Constraints:** [production deployment limitations]
**Rollback Readiness:** [current rollback capability status]
**Stakeholder Communication:** [who needs updates and frequency]
```

### Phase 2: Production Root Cause Analysis
```
🧠 **PHASE 2: PRODUCTION ROOT CAUSE ANALYSIS**

Use debugger-root-cause-analyst with production focus:

ANALYSIS CONSTRAINTS:
- Consider production environment limitations
- Factor in external dependencies
- Account for scale and load differences
- Evaluate deployment and rollback risks

HYPOTHESIS PRIORITIZATION:
1. Recent changes (deployments, config, infrastructure)
2. External dependency failures
3. Resource exhaustion (memory, CPU, disk, network)
4. Database performance degradation
5. Security incidents or attacks
```

**Phase 2 Production Summary:**
```markdown
## 🧠 PHASE 2 PRODUCTION SUMMARY - ROOT CAUSE ANALYSIS
**Status:** ✅ COMPLETED / ⚠️ PARTIAL / ❌ FAILED
**Duration:** [time taken]
**Production Risk Assessment:** [Low/Medium/High/Critical]

### Production Hypothesis Testing Results
**Hypothesis 1:** [CONFIRMED/DISPROVEN] - [production-specific evidence]
**Hypothesis 2:** [CONFIRMED/DISPROVEN] - [production-specific evidence]

### Confirmed Production Root Cause
**Root Cause:** [verified production issue]
**Production Impact:** [current user/business impact]
**Deployment Risk:** [risk of fixing in production]
**Rollback Capability:** [current rollback options]

### Production Implementation Strategy
**Approach:** [emergency/urgent/standard fix]
**Deployment Method:** [blue-green/canary/hotfix/maintenance window]
**Approval Required:** [stakeholders who must approve]
**Monitoring Plan:** [how to monitor during deployment]
```

### Phase 3: Production Solution Implementation
```
⚡ **PHASE 3: PRODUCTION SOLUTION IMPLEMENTATION**

Use debugger-solution-surgeon with production safety protocols:

PRODUCTION DEPLOYMENT SAFETY:
- Blue-green deployment if available
- Canary releases for non-critical fixes
- Feature flags for instant rollback capability
- Database migration safety checks
- Performance impact validation

CHANGE APPROVAL PROCESS:
- Document change rationale and risk assessment
- Get approval for production modifications
- Implement monitoring for new deployments
- Prepare rollback procedures before deployment
```

**Phase 3 Production Summary:**
```markdown
## ⚡ PHASE 3 PRODUCTION SUMMARY - SOLUTION IMPLEMENTATION
**Status:** ✅ DEPLOYED / ⚠️ PARTIAL / ❌ FAILED
**Duration:** [time taken]
**Deployment Method:** [method used]

### Production Safety Compliance
**Approvals Obtained:** ✅ All required / ⚠️ Some pending / ❌ Bypassed
**Rollback Prepared:** ✅ Ready / ⚠️ Partial / ❌ Not available
**Monitoring Active:** ✅ Full coverage / ⚠️ Basic / ❌ Limited

### Production Changes Applied
**Change Type:** [code/config/infrastructure/emergency]
**Scope:** [services/databases/infrastructure affected]
**Risk Level:** [low/medium/high implemented risk]

### Immediate Production Impact
**User Impact:** [improvement/no change/degradation]
**Error Rates:** [before vs after deployment]
**Performance:** [response time changes]
**Stability:** [system stability status]
```

### Phase 4: Production Validation
```
✅ **PHASE 4: PRODUCTION VALIDATION**

Use debugger-validator with production monitoring:

COMPREHENSIVE PRODUCTION VALIDATION:
- Real-time monitoring during fix deployment
- User impact measurement and verification
- Performance baseline restoration confirmation
- SLA compliance verification
- Long-term stability monitoring setup

POST-INCIDENT REQUIREMENTS:
- Incident timeline documentation
- Root cause and resolution summary
- Prevention measures identification
- Monitoring and alerting improvements
- Team communication and lessons learned
```

**Phase 4 Production Summary:**
```markdown
## ✅ PHASE 4 PRODUCTION SUMMARY - VALIDATION
**Status:** ✅ VALIDATION PASSED / ⚠️ ISSUES FOUND / ❌ VALIDATION FAILED
**Duration:** [time taken]
**Production Stability:** [stable/degraded/unstable]

### Production Issue Resolution
**Original Issue:** ✅ RESOLVED / ⚠️ PARTIALLY RESOLVED / ❌ NOT RESOLVED
**User Impact:** [% improvement in user experience]
**SLA Compliance:** [back in compliance/still violated]
**Business Metrics:** [revenue/conversion impact]

### Production System Health
**Error Rates:** [baseline restored/improved/still elevated]
**Performance:** [response times vs baseline]
**Resource Usage:** [CPU/memory/disk utilization]
**External Dependencies:** [third-party service integration status]

### Post-Incident Actions Required
**Monitoring Updates:** [new alerts/dashboards needed]
**Documentation:** [runbooks/procedures to update]
**Team Communication:** [stakeholder notifications sent]
**Follow-up Tasks:** [prevention measures to implement]

### Final Production Assessment
**Incident Resolution:** ✅ COMPLETE / ⚠️ PARTIAL / ❌ ESCALATION NEEDED
**Production Readiness:** [ready for normal operations/needs monitoring/requires follow-up]
**Lessons Learned:** [key insights for future incidents]
```

## 🛡️ Production Safety Features

### Emergency Rollback Protocol
```bash
🔄 EMERGENCY ROLLBACK INITIATED

If any phase fails or introduces new issues:
1. Immediate rollback to last known good state
2. Re-establish service stability
3. Document failure mode for post-incident analysis
4. Escalate to senior engineering team
5. Consider alternative resolution approaches
```

### Change Approval Gates
- **Critical Changes:** Require senior engineer approval
- **Database Changes:** Require DBA review
- **Infrastructure Changes:** Require DevOps approval
- **Security Changes:** Require security team review

### Communication Protocol
```markdown
🗣️ PRODUCTION INCIDENT COMMUNICATION

STAKEHOLDER UPDATES:
- Engineering team: Technical details and progress
- Product team: User impact and resolution timeline  
- Management: Business impact and recovery status
- Customer support: User-facing communication guidance

UPDATE FREQUENCY:
- Critical issues: Every 15 minutes
- High impact: Every 30 minutes
- Medium impact: Every hour or major milestone
```

## 📊 Production Monitoring Integration

### Real-Time Metrics Dashboard
- Error rates and response times
- Resource utilization (CPU, memory, disk)
- Database performance metrics
- User session impact
- Business metric impact

### Automated Alerts
- Service health degradation
- Performance threshold violations
- Error rate spikes
- Resource exhaustion warnings
- SLA violation risks

## 🎯 Post-Incident Requirements

### Incident Documentation
```markdown
# PRODUCTION INCIDENT REPORT

## Incident Summary
- **Start Time:** [timestamp]
- **Resolution Time:** [timestamp]  
- **Duration:** [total time]
- **Severity:** [Critical/High/Medium]
- **User Impact:** [percentage and description]

## Root Cause Analysis
- **Primary Cause:** [identified root cause]
- **Contributing Factors:** [additional factors]
- **Evidence Chain:** [how cause led to symptoms]

## Resolution Implementation
- **Solution Applied:** [specific fix implemented]
- **Deployment Method:** [how fix was deployed]
- **Validation Results:** [confirmation of resolution]

## Prevention Measures
- **Monitoring Improvements:** [new alerts/dashboards]
- **Process Improvements:** [workflow changes]
- **Technical Improvements:** [architectural changes]
- **Training Needs:** [team skill gaps identified]

## Lessons Learned
- **What Worked Well:** [effective parts of response]
- **Areas for Improvement:** [response weaknesses]
- **Action Items:** [specific follow-up tasks]
```

---

**Execute production debugging with safety protocols for:** `$ARGUMENTS`

**Production Safety Mode: ENABLED**
**Emergency Protocols: ACTIVE**
**Communication: STAKEHOLDER NOTIFICATIONS READY**