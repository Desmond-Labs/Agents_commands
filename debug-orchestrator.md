# /debug-orchestrator - Enhanced Debugging Command with Arguments

Intelligently debug issues using our systematic 4-phase anti-loop methodology with enhanced argument parsing and specialized debugging modes.

## Usage Patterns

```bash
# Basic debugging
/debug-orchestrator "JavaScript function returning NaN instead of expected result"

# Error-specific debugging  
/debug-orchestrator --type=error --message="TypeError: Cannot read property 'length' of undefined" --file="src/utils/helper.js"

# Performance debugging
/debug-orchestrator --type=performance --issue="API response times increased by 300%" --baseline="< 200ms"

# CI/CD debugging
/debug-orchestrator --type=cicd --workflow="build-and-test" --failure="Tests failing on main branch"

# Configuration debugging
/debug-orchestrator --type=config --component="database connection" --environment="production"

# Integration debugging
/debug-orchestrator --type=integration --service="external API" --symptom="intermittent 500 errors"

# Quick mode (skip evidence gathering if recent analysis exists)
/debug-orchestrator --quick "Build failing after dependency update"

# Comprehensive mode (extra validation phases)
/debug-orchestrator --comprehensive --type=security "Potential XSS vulnerability in user input handling"
```

## 🎯 Intelligent Orchestration

**Automatic Mode Detection:** Analyzes arguments to determine optimal debugging approach:
- **Error Mode:** For specific error messages, stack traces, exceptions
- **Performance Mode:** For slowdowns, timeouts, resource issues  
- **Integration Mode:** For API failures, service communication problems
- **CI/CD Mode:** For build failures, deployment issues, workflow problems
- **Configuration Mode:** For environment, settings, dependency conflicts
- **Security Mode:** For vulnerabilities, permission issues, data exposure

**Dynamic Phase Execution:** Adapts the 4-phase process based on issue type and available context.

## 🔧 Enhanced Argument Processing

**Issue Classification:** Automatically categorizes the debugging request:
```markdown
Based on arguments provided:
- Issue Type: [error|performance|integration|cicd|config|security|general]
- Complexity: [simple|moderate|complex]
- Urgency: [low|medium|high|critical]
- Scope: [single-file|module|system-wide|infrastructure]
```

**Context Enrichment:** Expands minimal arguments into comprehensive debugging context:
- Extracts file paths, error messages, stack traces
- Identifies relevant system components
- Suggests additional investigation areas
- Prepares targeted questioning for evidence gathering

## 📋 Systematic Execution Protocol

### Phase 1: Enhanced Evidence Gathering
```
🔍 **PHASE 1: INTELLIGENT EVIDENCE GATHERING**

Use debugger-evidence-gatherer agent with enhanced context:
- Issue Type: [detected type]
- Key Arguments: [parsed arguments]
- Investigation Focus: [targeted areas based on arguments]
- Priority Evidence: [what to look for first]
```

**Enhanced Evidence Targeting:**
- **Error Mode:** Focus on stack traces, reproduction steps, recent changes
- **Performance Mode:** Profile execution, measure baselines, identify bottlenecks  
- **Integration Mode:** Test endpoints, verify configurations, check network
- **CI/CD Mode:** Analyze workflow logs, check environment differences
- **Configuration Mode:** Validate settings, verify dependencies, check env vars
- **Security Mode:** Scan for vulnerabilities, check permissions, validate inputs

**Phase 1 Summary Template:**
```markdown
## 📋 PHASE 1 SUMMARY - EVIDENCE GATHERING
**Status:** ✅ COMPLETED / ⚠️ PARTIAL / ❌ FAILED
**Duration:** [time taken]
**Evidence Quality:** [Comprehensive/Good/Limited/Insufficient]

### Key Findings Discovered
- **Error Analysis:** [specific error details, stack traces, reproduction steps]
- **System State:** [environment, versions, resource status, network state]
- **Code Context:** [affected files, recent changes, dependency analysis]
- **Pattern Recognition:** [error frequency, related issues, log patterns]

### Investigation Actions Taken
- [x] Reproduced error scenario: [result]
- [x] Analyzed system environment: [findings]
- [x] Reviewed recent changes: [changes found]
- [x] Examined relevant code files: [files analyzed]
- [x] Checked dependencies and configuration: [status]

### Evidence-Based Hypotheses Formed
1. **[Hypothesis 1]** - Likelihood: [High/Medium/Low]
   - Supporting Evidence: [specific evidence]
   - Focus Area: [where to investigate]

2. **[Hypothesis 2]** - Likelihood: [High/Medium/Low] 
   - Supporting Evidence: [specific evidence]
   - Focus Area: [where to investigate]

3. **[Hypothesis 3]** - Likelihood: [High/Medium/Low]
   - Supporting Evidence: [specific evidence] 
   - Focus Area: [where to investigate]

### Handoff to Phase 2
**Primary Investigation Target:** [most promising area based on evidence]
**Recommended Testing Order:** [hypothesis priority order]
**Critical Evidence to Validate:** [key evidence that needs confirmation]
**Risk Factors Identified:** [potential risks or complications]
```

### Phase 2: Contextual Root Cause Analysis
```
🧠 **PHASE 2: CONTEXTUAL ROOT CAUSE ANALYSIS**

Use debugger-root-cause-analyst agent with argument-informed hypotheses:
- Primary Focus Area: [based on issue type]
- Argument-Derived Hypotheses: [theories from initial arguments]
- Systematic Testing Protocol: [tailored to issue type]
```

**Phase 2 Summary Template:**
```markdown
## 🧠 PHASE 2 SUMMARY - ROOT CAUSE ANALYSIS
**Status:** ✅ COMPLETED / ⚠️ PARTIAL / ❌ FAILED
**Duration:** [time taken]
**Analysis Confidence:** [High/Medium/Low]

### Hypotheses Testing Results
**[Hypothesis 1 Name]** - [CONFIRMED/DISPROVEN/INCONCLUSIVE]
- **Testing Method:** [how it was tested]
- **Evidence Found:** [supporting or contradicting evidence]
- **Conclusion:** [why confirmed/disproven]

**[Hypothesis 2 Name]** - [CONFIRMED/DISPROVEN/INCONCLUSIVE]
- **Testing Method:** [how it was tested]
- **Evidence Found:** [supporting or contradicting evidence]
- **Conclusion:** [why confirmed/disproven]

**[Hypothesis 3 Name]** - [CONFIRMED/DISPROVEN/INCONCLUSIVE]
- **Testing Method:** [how it was tested]
- **Evidence Found:** [supporting or contradicting evidence]
- **Conclusion:** [why confirmed/disproven]

### Root Cause Identification
**Confirmed Root Cause:** [the verified underlying problem]
**Confidence Level:** [High/Medium/Low] - [reasoning for confidence]

### Evidence Chain Validation
1. **Root Cause:** [verified underlying issue]
2. **Leads to:** [intermediate effect] ← [evidence supporting connection]
3. **Results in:** [immediate symptom] ← [evidence supporting connection]
4. **Manifests as:** [observable error] ← [evidence supporting connection]

### Impact Assessment
- **System Components Affected:** [list of affected areas]
- **Risk Level:** [Low/Medium/High/Critical]
- **Potential Side Effects:** [other issues this could cause]

### Handoff to Phase 3
**Fix Strategy:** [recommended approach]
**Implementation Scope:** [minimal/targeted/system-wide]
**Risk Considerations:** [what to be careful about]
**Success Criteria:** [how to know the fix worked]
```

### Phase 3: Surgical Solution Implementation
```
⚡ **PHASE 3: SURGICAL SOLUTION IMPLEMENTATION**

Use debugger-solution-surgeon agent with solution constraints:
- Solution Scope: [minimal|targeted|system-wide based on analysis]
- Risk Assessment: [based on issue type and system impact]
- Implementation Strategy: [informed by argument context]
```

**Phase 3 Summary Template:**
```markdown
## ⚡ PHASE 3 SUMMARY - SOLUTION IMPLEMENTATION
**Status:** ✅ COMPLETED / ⚠️ PARTIAL / ❌ FAILED
**Duration:** [time taken]
**Implementation Risk:** [Low/Medium/High]

### Pre-Implementation Safety
- **Backup Created:** ✅/❌ [backup method/location]
- **Rollback Plan:** [specific rollback procedure]
- **Safety Checkpoints:** [restoration points created]

### Solution Applied
**Root Cause Addressed:** [specific underlying issue fixed]
**Fix Strategy Used:** [minimal/targeted/system-wide approach]
**Implementation Method:** [how the fix was applied]

### Exact Changes Made
**Files Modified:** 
- [filename]: [specific changes - before → after]
- [filename]: [specific changes - before → after]

**Configuration Changes:**
- [config item]: [old value → new value]
- [config item]: [old value → new value]

**Dependencies Updated:**
- [package]: [old version → new version]
- [package]: [old version → new version]

### Changes NOT Made
- [deliberate non-changes and reasoning]
- [areas left untouched and why]

### Immediate Validation Results
**Original Error Status:** ✅ RESOLVED / ❌ STILL PRESENT / ⚠️ PARTIALLY RESOLVED
**Quick Smoke Tests:** 
- [test 1]: ✅ PASSED / ❌ FAILED
- [test 2]: ✅ PASSED / ❌ FAILED
- [test 3]: ✅ PASSED / ❌ FAILED

### Risk Assessment Update
**New Risks Introduced:** [any new risks or side effects]
**Mitigation Steps:** [steps taken to reduce risk]
**Monitoring Required:** [what to watch for]

### Handoff to Phase 4
**Validation Focus Areas:** [specific areas needing thorough testing]
**Success Criteria:** [what constitutes successful resolution]
**Regression Test Scope:** [areas to test for unintended impacts]
**Performance Baseline:** [expected performance characteristics]
```

### Phase 4: Comprehensive Validation
```
✅ **PHASE 4: COMPREHENSIVE VALIDATION**

Use debugger-validator agent with enhanced validation criteria:
- Validation Focus: [tailored to issue type]
- Success Metrics: [defined by initial arguments and analysis]
- Regression Testing: [scope based on changes made]
```

**Phase 4 Summary Template:**
```markdown
## ✅ PHASE 4 SUMMARY - COMPREHENSIVE VALIDATION
**Status:** ✅ VALIDATION PASSED / ⚠️ ISSUES FOUND / ❌ VALIDATION FAILED
**Duration:** [time taken]
**Overall Confidence:** [High/Medium/Low]

### Root Cause Resolution Verification
**Original Issue Status:** ✅ FULLY RESOLVED / ⚠️ PARTIALLY RESOLVED / ❌ NOT RESOLVED
**Resolution Evidence:**
- **Reproduction Test:** [original error scenario now passes/fails]
- **Root Cause Verification:** [underlying cause confirmed eliminated]
- **Symptom Elimination:** [all related symptoms resolved]

### Comprehensive Testing Results
**Test Suite Results:**
- **Unit Tests:** ✅ [X/X passed] / ❌ [X failures]
- **Integration Tests:** ✅ [X/X passed] / ❌ [X failures]
- **End-to-End Tests:** ✅ [X/X passed] / ❌ [X failures]
- **Manual Testing:** ✅ [scenarios tested] / ❌ [issues found]

### Regression Analysis
**Related Functionality Status:** ✅ ALL WORKING / ⚠️ MINOR ISSUES / ❌ MAJOR PROBLEMS
**Specific Areas Tested:**
- [functionality 1]: ✅ Working / ⚠️ Minor issue / ❌ Broken
- [functionality 2]: ✅ Working / ⚠️ Minor issue / ❌ Broken
- [functionality 3]: ✅ Working / ⚠️ Minor issue / ❌ Broken

### Performance Impact Assessment
**Performance Status:** ✅ NO IMPACT / ⚠️ MINOR IMPACT / ❌ SIGNIFICANT IMPACT
- **Response Time:** [baseline vs current]
- **Resource Usage:** [memory, CPU impact]
- **Throughput:** [requests/operations per second]

### Security & Safety Validation
**Security Status:** ✅ NO CONCERNS / ⚠️ MINOR CONCERNS / ❌ SECURITY ISSUES
- **Data Integrity:** [status of data handling]
- **Access Control:** [authentication/authorization status]
- **Vulnerability Assessment:** [any new security risks]

### Edge Case Testing
**Edge Case Status:** ✅ ALL HANDLED / ⚠️ SOME ISSUES / ❌ MAJOR GAPS
**Scenarios Tested:**
- [edge case 1]: ✅ Handled / ❌ Issue found
- [edge case 2]: ✅ Handled / ❌ Issue found
- [boundary condition]: ✅ Handled / ❌ Issue found

### Issues Discovered
**Critical Issues:** [any show-stopping problems found]
**Minor Issues:** [small problems that need attention]
**Future Improvements:** [opportunities for enhancement]

### Final Debugging Assessment
**Debugging Success Level:** ✅ COMPLETE SUCCESS / ⚠️ PARTIAL SUCCESS / ❌ FAILED

#### ✅ If Complete Success:
- Original issue fully resolved
- No regressions introduced
- All tests passing
- Performance maintained
- System stable

**Recommendation:** DEBUGGING COMPLETE - Issue resolved successfully

#### ⚠️ If Partial Success:
**Remaining Issues:** [list of outstanding problems]
**Required Actions:** [what still needs to be done]
**Priority Level:** [High/Medium/Low]

**Recommendation:** Address remaining issues or accept current state

#### ❌ If Failed:
**Primary Failure Reason:** [why validation failed]
**Rollback Recommendation:** [should changes be reverted]
**Next Steps:** [return to which phase for re-analysis]

**Recommendation:** ROLLBACK and restart debugging process

### Post-Resolution Actions
**Monitoring Setup:** [alerts/dashboards configured]
**Documentation Updated:** [docs/runbooks modified]
**Team Notification:** [stakeholders informed]
**Lessons Learned:** [key insights for future debugging]

### Session Completion Report
**Total Debugging Time:** [start to finish duration]
**Phases Completed:** [successful phases]
**Key Success Factors:** [what worked well]
**Areas for Improvement:** [process improvements identified]
```

## 🎛️ Advanced Debugging Modes

### Quick Mode (`--quick`)
- Skips evidence gathering if recent analysis exists for similar issue
- Uses cached context from previous debugging sessions
- Faster turnaround for recurring or well-understood issues

### Comprehensive Mode (`--comprehensive`)
- Adds extra validation phases
- Extended regression testing
- Security and performance impact analysis
- Documentation and prevention recommendations

### Continuous Mode (`--continuous`)
- Sets up monitoring for the fixed issue
- Schedules follow-up validation
- Creates alerts for regression detection

## 🚨 Emergency Response Protocols

### Critical Issues (`--critical`)
```markdown
🚨 CRITICAL ISSUE DETECTED - EMERGENCY PROTOCOL

1. **Immediate Triage (60 seconds)**
   - Assess system stability
   - Implement emergency containment if needed
   - Document current state

2. **Rapid Evidence Gathering (5 minutes)**
   - Focus on critical system state
   - Capture essential logs and metrics
   - Identify immediate risks

3. **Emergency Fix Protocol**
   - Implement minimal safe fix
   - Verify system stability
   - Plan comprehensive fix for later

4. **Crisis Communication**
   - Document emergency actions taken
   - Prepare status communication
   - Schedule follow-up comprehensive analysis
```

## 🔄 Intelligent Orchestration Logic

**Argument Processing Pipeline:**
1. **Parse Arguments:** Extract structured information from natural language or flags
2. **Classify Issue:** Determine issue type, complexity, and urgency
3. **Enrich Context:** Add relevant system context and debugging hints
4. **Plan Execution:** Customize 4-phase approach based on classification
5. **Execute Phases:** Run agents with enhanced, targeted instructions
6. **Adapt Dynamically:** Modify approach based on intermediate findings

**Smart Handoffs:** Each phase receives enhanced context:
```markdown
Agent Handoff Package:
- Original Arguments: [user input]
- Parsed Context: [structured information]
- Issue Classification: [type, complexity, urgency]
- Previous Phase Results: [findings and recommendations]
- Specialized Instructions: [tailored to issue type]
```

## 📊 Debug Session Management

**Session Tracking:** Maintains context across related debugging attempts:
- Links related debugging sessions
- Tracks hypothesis evolution
- Maintains solution history
- Prevents debugging loops

**Learning Integration:** Improves future debugging based on past sessions:
- Pattern recognition for similar issues
- Solution template suggestions
- Risk assessment based on historical data

## 🎯 Execution

**Processing Arguments:** `$ARGUMENTS`

**Intelligent Classification and Orchestration:**
1. Parse and classify the debugging request
2. Enrich context with system knowledge
3. Plan optimized 4-phase execution
4. Execute phases with enhanced targeting
5. Provide comprehensive results and recommendations

**Execute the enhanced 4-phase debugging methodology now with intelligent orchestration based on provided arguments.**

---

## Example Argument Patterns

**Error Pattern:** `/debug-orchestrator "TypeError: Cannot read property 'map' of undefined in ProductList component"`
- Auto-detects: React component error, array handling issue
- Focus: Component props, data flow, state management

**Performance Pattern:** `/debug-orchestrator --type=performance "Database queries taking >5 seconds"`  
- Auto-detects: Database performance issue
- Focus: Query optimization, indexing, connection pooling

**CI/CD Pattern:** `/debug-orchestrator --type=cicd "Build failing on deploy step with exit code 1"`
- Auto-detects: Deployment pipeline issue
- Focus: Build logs, environment differences, dependency issues

**Integration Pattern:** `/debug-orchestrator --type=integration "External API returning 429 errors"`
- Auto-detects: Rate limiting or service communication issue
- Focus: API configuration, retry logic, authentication

Start systematic debugging with enhanced orchestration for: **$ARGUMENTS**