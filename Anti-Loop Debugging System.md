# 🔄 Anti-Loop Debugging System - Full Orchestration

I need you to systematically debug this issue using our 4-phase anti-loop debugging methodology. **Automatically progress through all phases** - don't wait for me to prompt each step.

## 🎯 Your Orchestration Mission

Execute all 4 phases sequentially and automatically:

1. **🔍 Evidence Gathering** → 2. **🧠 Root Cause Analysis** → 3. **⚡ Surgical Implementation** → 4. **✅ Comprehensive Validation**

## 📋 Phase Execution Protocol

### Phase 1: Evidence Gathering (REQUIRED FIRST)
```
Use the debugger-evidence-gatherer agent to investigate [ERROR/ISSUE] completely before attempting any fixes.
```

**Wait for complete evidence report before proceeding.**

**Phase 1 Success Criteria:**
- ✅ Complete error reproduction documented
- ✅ System context captured
- ✅ Code context analyzed
- ✅ Hypotheses formed with evidence
- ✅ Evidence report provided

**Once Phase 1 completes, AUTOMATICALLY continue to Phase 2.**

### Phase 2: Root Cause Analysis (AUTOMATIC)
```
Use the debugger-root-cause-analyst agent to systematically test the hypotheses from the evidence report.
```

**Phase 2 Success Criteria:**
- ✅ Hypotheses tested systematically
- ✅ Root cause identified with high confidence
- ✅ Evidence chain validated
- ✅ Fix strategy recommended

**Once Phase 2 completes, AUTOMATICALLY continue to Phase 3.**

### Phase 3: Surgical Implementation (AUTOMATIC)
```
Use the debugger-solution-surgeon agent to implement the minimal fix for the confirmed root cause.
```

**Phase 3 Success Criteria:**
- ✅ Minimal change applied
- ✅ Only root cause addressed
- ✅ Safety checkpoint created
- ✅ Immediate validation passed
- ✅ Changes documented

**Once Phase 3 completes, AUTOMATICALLY continue to Phase 4.**

### Phase 4: Comprehensive Validation (AUTOMATIC - FINAL)
```
Use the debugger-validator agent to comprehensively validate the debugging solution.
```

**Phase 4 Success Criteria:**
- ✅ Original error eliminated
- ✅ No regressions introduced
- ✅ Edge cases validated
- ✅ Performance acceptable
- ✅ Final validation report provided

## 🔄 Orchestration Rules

### Execution Flow
1. **Start with Phase 1** - NEVER skip evidence gathering
2. **Wait for completion** - Each phase must fully complete before proceeding
3. **Automatic progression** - Move to next phase without waiting for user prompts
4. **No phase skipping** - All 4 phases are mandatory
5. **Clear handoffs** - Each agent should provide output for the next

### Error Handling
- **If any phase fails**: Stop and report which phase failed and why
- **If validation fails**: Return to Phase 1 with new evidence gathering
- **If loop detected**: Force restart from Phase 1

### Communication Protocol
- **Start each phase** with clear announcement: "🔍 **PHASE 1: EVIDENCE GATHERING**"
- **End each phase** with clear completion status and handoff
- **Provide progress updates** throughout the process
- **Final summary** with complete debugging outcome

## 🎯 Expected User Experience

**User provides:** Single debugging request
**Claude Code delivers:** Complete end-to-end debugging solution through all 4 phases

### Example Flow:
```
User: "My JavaScript function is returning NaN instead of the expected average"

Claude Code Response:
🔍 PHASE 1: EVIDENCE GATHERING
[Uses debugger-evidence-gatherer agent - completes full investigation]

🧠 PHASE 2: ROOT CAUSE ANALYSIS  
[Uses debugger-root-cause-analyst agent - identifies array bounds issue]

⚡ PHASE 3: SURGICAL IMPLEMENTATION
[Uses debugger-solution-surgeon agent - fixes <= to < in loop]

✅ PHASE 4: COMPREHENSIVE VALIDATION
[Uses debugger-validator agent - confirms fix works, no regressions]

🎯 DEBUGGING COMPLETE: Issue resolved with minimal surgical fix
```

## 🚫 Anti-Patterns to Avoid

- **DON'T** jump straight to solutions
- **DON'T** skip any phases
- **DON'T** wait for user prompts between phases
- **DON'T** make assumptions without evidence
- **DON'T** fix multiple issues simultaneously
- **DON'T** proceed if any phase reports failure

## ✅ Success Indicators

- All 4 phases executed in sequence
- Each agent completed its specific methodology
- Clear handoffs between phases
- Original issue completely resolved
- No new issues introduced
- Complete documentation provided

## 🔧 Customization Notes

- **For urgent issues**: Still follow all phases but note time constraints
- **For complex issues**: May need multiple cycles, restart from Phase 1 with new evidence
- **For partial failures**: Validate what works, identify what needs more work

---

**Execute this debugging methodology now. Start with Phase 1 and progress automatically through all phases until the issue is completely resolved.**

# Issue to debug: 
#$ARGUMENTS