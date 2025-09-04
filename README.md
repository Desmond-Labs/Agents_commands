# ORBIT Agents & Commands Collection

A curated collection of specialized AI agents and slash commands designed to enhance Claude Code with advanced debugging capabilities and workflow automation for the ORBIT image processing platform.

## 🎯 Overview

This repository contains sophisticated agent definitions and slash commands that extend Claude Code's capabilities with specialized debugging workflows and ORBIT-specific automation. Each agent is designed with specific expertise areas and integrates seamlessly with Claude Code's task execution framework.

## 🤖 Specialized Debugging Agents

The repository includes a comprehensive 4-phase debugging system with integrated logging and token tracking:

### Phase 1: Evidence Gathering
**`debugger-evidence-gatherer`**
- **Purpose**: Forensic debugging specialist for comprehensive system investigation
- **Features**: 
  - Must be used FIRST before any debugging attempts
  - Never makes code changes - only investigates and documents
  - Integrates GitHub Actions and CI/CD pipeline analysis
  - Includes comprehensive error analysis and system state investigation
  - Built-in logging integration with session tracking

### Phase 2: Root Cause Analysis  
**`debugger-root-cause-analyst`**
- **Purpose**: Scientific root cause analysis using systematic hypothesis testing
- **Features**:
  - Uses scientific method to identify actual root causes vs symptoms
  - Systematic hypothesis testing with evidence validation
  - Never makes code changes - only analyzes and concludes
  - Cross-hypothesis validation and evidence chain construction
  - Confidence scoring and quality metrics

### Phase 3: Surgical Implementation
**`debugger-solution-surgeon`**
- **Purpose**: Precision fix implementation with minimal system impact
- **Features**:
  - Makes minimal, targeted fixes based on confirmed root cause analysis
  - Never fixes unrelated issues or makes "while I'm here" improvements
  - Includes pre-surgery safety protocols and rollback procedures
  - Surgical precision with change tracking and validation
  - Implementation quality metrics and risk assessment

### Phase 4: Comprehensive Validation
**`debugger-validator`**
- **Purpose**: Final gatekeeper ensuring complete solution validation
- **Features**:
  - Comprehensive testing of root cause resolution
  - Regression testing and edge case validation
  - Performance and security impact assessment
  - Integration and compatibility testing
  - Final quality assurance with detailed analytics

## 🚀 ORBIT Workflow Agents

### Frontend Architecture
**`orbit-frontend-architect`**
- **Purpose**: ORBIT frontend UX specialist implementing organic intuitionist design
- **Features**:
  - Cosmic design system compliance (Deep Navy, Orbit Blue, Orbit Teal)
  - Organic intuitionist UX methodology
  - Frank Lloyd Wright inspired architecture principles
  - ORBIT brand identity integration
  - Component design with 8px border radius and elevated dark surfaces

### Workflow Processing
**`orbit-workflow-processor`**
- **Purpose**: Complete ORBIT image processing workflow automation
- **Features**:
  - End-to-end order processing from pending to complete
  - AI image analysis with Google Gemini integration
  - Metadata embedding and XMP packet creation
  - Storage verification and database reconciliation
  - Email notifications and cleanup procedures

## 🛠 Key Features

### Integrated Logging System
All debugging agents include comprehensive logging integration:
```bash
# Initialize logging session
/debug-log [agent-name] start "Session description"

# Log key findings
/debug-log [agent-name] log "Detailed findings with evidence"

# Complete session with metrics
/debug-log [agent-name] complete "Session summary with confidence scores"
```

### Token Tracking & Analytics
- Comprehensive token usage estimation
- Cost optimization recommendations
- Performance metrics and efficiency tracking
- Session analytics and continuous improvement insights

### Anti-Loop Prevention
- Systematic 4-phase process prevents debugging loops
- Evidence-based decision making
- Hypothesis testing rigor
- Validation completeness requirements

## 📋 Usage Guidelines

### For Debugging Workflows
1. **Always start with `debugger-evidence-gatherer`** - Never skip evidence collection
2. **Follow the 4-phase sequence** - Each phase builds on the previous
3. **Use logging integration** - Track progress and maintain audit trails
4. **Complete each phase fully** - Don't skip to solutions without proper analysis

### For ORBIT Development
1. **Use `orbit-frontend-architect`** for all UI/UX work
2. **Use `orbit-workflow-processor`** for order processing automation
3. **Maintain cosmic brand compliance** - Follow the established design system
4. **Integrate with existing ecosystem** - Ensure seamless user experience

## 🎨 ORBIT Design System

### Color Palette
- **Deep Navy**: `#1A233F` (backgrounds)
- **Orbit Blue**: `#4A77C3` (primary elements)  
- **Orbit Teal**: `#48C9B0` (highlights)

### Visual Elements
- Orbital paths and constellation patterns
- Star fields and scanning grids
- Geometric sans-serif typography
- 150% line height for readability
- 8px border radius standard
- Subtle gradients on elevated surfaces

## 🏗 Architecture Principles

### Organic Intuitionist Design
- Essence-first design approach
- Iterative reductionism while preserving depth
- Holistic integration within ORBIT ecosystem
- Deep contextual understanding of user needs

### Debugging Methodology
- Forensic investigation before solutions
- Scientific hypothesis testing
- Surgical precision in implementations
- Comprehensive validation and quality assurance

## 🔧 Integration with Claude Code

These agents are designed to work seamlessly with Claude Code's task execution framework:

- Each agent includes detailed prompts and behavioral guidelines
- Integrated with Claude Code's tool ecosystem
- Built-in progress tracking and quality metrics
- Designed for autonomous task execution

## 📊 Quality Metrics

### Debugging Success Criteria
- Root cause identification accuracy
- Solution implementation precision  
- Validation thoroughness
- Regression prevention effectiveness

### ORBIT Development Standards
- Brand compliance adherence
- User experience quality scores
- Performance impact measurements
- Integration success metrics

## 🤝 Contributing

When adding new agents or commands:

1. Follow the established naming conventions
2. Include comprehensive documentation
3. Implement logging integration where applicable
4. Maintain consistency with existing agent patterns
5. Ensure compatibility with Claude Code framework

## 📝 License

Part of the ORBIT ecosystem by Desmond Labs.

---

**ORBIT by Desmond Labs** — Advancing AI-powered image analysis through sophisticated workflow automation and cosmic design principles.
