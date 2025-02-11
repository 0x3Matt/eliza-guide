# Cursor Development Prompts Guide

## Overview
This document serves as the master reference for maintaining project documentation across three core files:
1. file-tree.md (Project structure and relationships)
2. dev-notes.md (Technical implementation details)
3. task-log.md (Task tracking and progress)

### Document Purpose
- Provide standardized prompts for documentation maintenance
- Ensure consistency across all project documentation
- Guide task tracking and progress updates
- Maintain project structure integrity
- Facilitate proper cross-referencing

### Contents

1. File-Specific Prompts
   - file-tree.md Prompts
     * Update Instructions
     * Reference Guide
   - dev-notes.md Prompts
     * Update Instructions
     * Reference Guide
   - task-log.md Prompts
     * Update Instructions
     * Reference Guide

2. Common Task Management Prompts
   - Update Progress and Move Forward
     * For dev-notes.md
     * For task-log.md
     * For file-tree.md
   - Task Completion Verification
     * For dev-notes.md
     * For task-log.md
     * For file-tree.md
   - Task Review and Next Steps
     * For dev-notes.md
     * For task-log.md
     * For file-tree.md

### Usage Guidelines
1. Documentation Updates
   - Always update all three files in sync
   - Follow the specified order of updates
   * Maintain cross-references
   * Preserve historical information

2. Task Management
   - Use consistent status indicators
   * Track dependencies accurately
   * Document progress regularly
   * Maintain task relationships

3. Integration Process
   * Follow pre-task review steps
   * Complete during-task documentation
   * Perform post-task updates
   * Verify documentation consistency

### Document Organization
Each section provides:
- Detailed step-by-step instructions
* Specific items to check/update
* Cross-referencing requirements
* Documentation guidelines
* Best practices

---

## file-tree.md 

Prompt 1: Updating file-tree.md
Update Instructions for file-tree.md (/src/pattern_pro/dev/file-tree.md):

1. File Tree Maintenance:
   - After creating new files/directories: Add entries under appropriate sections
   - After modifying files: Update size, line counts, and feature descriptions
   - After removing files: Remove entries and update dependency relationships
   - Maintain alphabetical ordering within each directory section

2. Component Analysis:
   - Update "Total Project Statistics" at the top
   - Add new components to "File Categories" section
   - Update "Directory Structure Overview" with new paths
   - Modify "Component Relationships" diagram if dependencies change
   - Update "File Dependencies Matrix" with new relationships

3. Detailed Summaries:
   For each new/modified file, document:
   - Purpose
   - Features
   - Dependencies
   - Size/Line Count
   - Usage
   - Relationships with other components

4. Integration Requirements:
   - Cross-reference with dev-notes.md (/src/pattern_pro/dev/dev-notes.md)
   - Sync with task-log.md (root directory)
   - Update after each completed task
   - Maintain consistency with project documentation

5. Workflow Process:
   a. Before task:
      - Review file-tree.md for component relationships
      - Check dependencies and existing implementations
   b. After task:
      - Update file-tree.md with changes
      - Update dev-notes.md with implementation details
      - Update task-log.md with completion status
   c. Commit changes to all three files together

Remember: This document serves as the master reference for project structure and relationships. Keep it accurate and up-to-date for all development workflows.




Prompt 2: Using file-tree.md as Reference


Reference Guide for file-tree.md (/src/pattern_pro/dev/file-tree.md):

1. Project Navigation:
   - Use this document as your primary map of the codebase
   - Understand component relationships before making changes
   - Reference dependency matrices for impact analysis
   - Follow established patterns for new implementations

2. Development Workflow:
   a. Task Initialization:
      - Check file-tree.md for:
        * Relevant components and their locations
        * Existing implementations
        * Dependencies and relationships
        * Required interfaces
   
   b. Implementation:
      - Follow patterns from similar components
      - Maintain consistent structure
      - Adhere to documented dependencies
      - Use established naming conventions

   c. Task Completion:
      - Update file-tree.md with changes
      - Sync with dev-notes.md
      - Update task-log.md
      - Verify all relationships are current

3. Cross-Reference Process:
   - file-tree.md: Project structure and relationships
   - dev-notes.md: Implementation details and progress
   - task-log.md: Task status and completion tracking

4. Document Integration:
   Before each task:
   1. Review file-tree.md → Understand structure
   2. Check dev-notes.md → Get context
   3. Consult task-log.md → Confirm requirements

   After each task:
   1. Update file-tree.md → Record changes
   2. Update dev-notes.md → Document implementation
   3. Update task-log.md → Mark progress

5. Key Sections to Reference:
   - Component Relationships: Understanding dependencies
   - File Dependencies Matrix: Impact analysis
   - Detailed Directory Summaries: Implementation patterns
   - Project Structure Summary: Architecture overview

Remember: These three documents work together to maintain project coherence:
- file-tree.md: Structure and relationships
- dev-notes.md: Implementation details
- task-log.md: Progress tracking

Always update all three after completing any task to maintain project integrity.




## dev-notes.md


### Prompts for dev-notes.md

### Prompt 1: Updating dev-notes.md
Location: C:\BYBIT-PRO\src\pattern_pro\dev\dev-notes.md

1. Document Structure Maintenance:
   a. Core Sections (Preserve Order):
      - Project Overview
      - System Specifications
      - ML Environment Setup
      - Project Structure
      - Task Status Legend
      - Current Project Status & Tasks
      - Implementation Timeline
      - Success Metrics
      - Dashboard Status
      - Testing Status
      - Recent Updates

2. Update Guidelines:
   a. Status Updates:
      - Use emoji indicators consistently:
        * 🔴 Not Started
        * 🟡 In Progress
        * 🟢 Completed
        * ⭕️ Blocked
        * 🔵 Testing
        * ✅ Verified
      - Update status without removing tasks
      - Add sub-tasks under existing tasks
      - Include completion dates for verified tasks

   b. Technical Details:
      - Add specific metrics (memory usage, processing times)
      - Include version numbers for dependencies
      - Document configuration changes
      - Record optimization results

   c. Implementation Notes:
      - Add new sections under appropriate categories
      - Include code snippets when relevant
      - Document dependencies and relationships
      - Note performance metrics and benchmarks

3. Integration Requirements:
   - Cross-reference with file-tree.md
   - Sync with task-log.md
   - Update after each task completion
   - Maintain technical accuracy

4. Workflow Process:
   a. Before Implementation:
      - Review relevant sections
      - Check dependencies
      - Verify system requirements
   
   b. During Implementation:
      - Document technical decisions
      - Record configuration changes
      - Note performance metrics
   
   c. After Implementation:
      - Update status indicators
      - Add implementation details
      - Record success metrics
      - Document any issues or solutions

Remember: This document serves as the technical implementation record and progress tracker.


### Prompt 2: Using dev-notes.md as Reference
Location: C:\BYBIT-PRO\src\pattern_pro\dev\dev-notes.md

1. Document Purpose:
   - Technical implementation details
   - System configuration records
   - Progress tracking
   - Performance metrics
   - Development decisions

2. Reference Workflow:
   a. Project Setup:
      - Check System Specifications
      - Review ML Environment Setup
      - Verify CUDA Configuration
      - Confirm Dependencies

   b. Implementation:
      - Reference Current Project Status
      - Check Task Dependencies
      - Review Success Metrics
      - Follow Implementation Timeline

   c. Testing:
      - Review Testing Status
      - Check Success Metrics
      - Verify Performance Benchmarks
      - Update Test Results

3. Section Usage:
   a. Technical Implementation:
      - Use ML Environment Setup for configuration
      - Reference System Specifications for requirements
      - Follow Project Structure for organization
      - Check Recent Updates for changes

   b. Progress Tracking:
      - Use Task Status Legend for updates
      - Reference Implementation Timeline
      - Check Current Project Status
      - Review Success Metrics

4. Integration Process:
   Before Task:
   1. Review dev-notes.md → Technical requirements
   2. Check file-tree.md → Structure
   3. Consult task-log.md → Task details

   After Task:
   1. Update dev-notes.md → Technical details
   2. Update file-tree.md → Structure changes
   3. Update task-log.md → Progress

5. Key Information:
   - System requirements and configurations
   - Implementation details and decisions
   - Performance metrics and benchmarks
   - Testing results and coverage
   - Recent updates and changes

Remember: This document provides technical context and implementation details for the entire project.


## task-log.md


### Prompts for task-log.md

### Prompt 1: Updating task-log.md
Location: C:\BYBIT-PRO\task-log.md

1. Document Structure Maintenance:
   a. Core Sections:
      - Project Structure (Tree)
      - Task Status Legend
      - Core Infrastructure Tasks
      - Component-specific Tasks
      - Integration Tasks
      - Testing Tasks

2. Task Management:
   a. Status Updates:
      - Use consistent emoji indicators:
        * 🔴 Not Started
        * 🟡 In Progress
        * 🟢 Completed
        * ⭕️ Blocked
        * 🔵 Testing
        * ✅ Verified
      - Preserve task history
      - Add sub-tasks as needed
      - Include completion dates

   b. Task Organization:
      - Group related tasks
      - Maintain hierarchy
      - Add dependencies
      - Track blockers

   c. Progress Tracking:
      - Update status without deletion
      - Add new tasks at appropriate level
      - Note blocked tasks and reasons
      - Track completion metrics

3. Integration Requirements:
   - Cross-reference with file-tree.md
   - Sync with dev-notes.md
   - Update after each task change
   - Maintain task relationships

4. Workflow Process:
   a. Task Creation:
      - Add under appropriate category
      - Include sub-tasks
      - Note dependencies
      - Set priority

   b. Status Updates:
      - Update emoji indicators
      - Add progress notes
      - Note blockers
      - Track completion

   c. Task Completion:
      - Update status to verified
      - Add completion notes
      - Update related tasks
      - Note any follow-ups

Remember: This document tracks all project tasks and their current status.

### Prompt 2: Using task-log.md as Reference
Location: C:\BYBIT-PRO\task-log.md

1. Document Purpose:
   - Task tracking and management
   - Progress monitoring
   - Dependency tracking
   - Project structure reference

2. Reference Workflow:
   a. Task Planning:
      - Review Project Structure
      - Check existing tasks
      - Identify dependencies
      - Note blocked items

   b. Implementation:
      - Follow task hierarchy
      - Check sub-tasks
      - Monitor dependencies
      - Track progress

   c. Progress Updates:
      - Update task status
      - Note completion
      - Check blocked tasks
      - Update dependencies

3. Section Usage:
   a. Project Management:
      - Use Project Structure for context
      - Reference Task Status Legend
      - Follow task categories
      - Check dependencies

   b. Task Execution:
      - Follow task hierarchy
      - Complete sub-tasks
      - Update status
      - Note progress

4. Integration Process:
   Before Task:
   1. Review task-log.md → Task details
   2. Check file-tree.md → Implementation
   3. Consult dev-notes.md → Technical info

   After Task:
   1. Update task-log.md → Progress
   2. Update file-tree.md → Structure
   3. Update dev-notes.md → Details

5. Key Information:
   - Project structure and organization
   - Task status and progress
   - Dependencies and blockers
   - Implementation order
   - Completion tracking

Remember: This document guides task execution and tracks overall project progress.

# Other Tasks

## Common Task Management Prompts

### 1. Update Progress and Move Forward

#### For dev-notes.md:
```
Review and Update Instructions for dev-notes.md:

1. Locate Current Task:
   - Check "Current Project Status & Tasks" section
   - Find task with 🟡 (In Progress) status
   - Review sub-tasks and dependencies

2. Update Implementation Details:
   - Add technical decisions made
   - Record configuration changes
   - Document performance metrics
   - Note any issues encountered

3. Update Status:
   - Change emoji indicators appropriately
   - Add completion date if verified
   - Update sub-task status
   - Note any blockers

4. Add to Recent Updates:
   - Document key changes
   - Include version numbers
   - Note important decisions
   - Record optimization results

5. Update Success Metrics:
   - Record current values
   - Compare with targets
   - Note improvements
   - Add new metrics if needed

6. Cross-reference:
   - Check file-tree.md for structural changes
   - Verify task-log.md synchronization
   - Update related documentation
```

#### For task-log.md:
```
Review and Update Instructions for task-log.md:

1. Locate Task Entry:
   - Find current component section
   - Identify active task
   - Review sub-tasks
   - Check dependencies

2. Update Task Status:
   - Update emoji indicators
   - Add completion notes
   - Update sub-tasks
   - Note completion date

3. Task Dependencies:
   - Update dependent tasks
   - Note any new blockers
   - Update prerequisite status
   - Check integration points

4. Next Tasks:
   - Identify next task
   - Check prerequisites
   - Note dependencies
   - Verify resources

5. Cross-reference:
   - Update related tasks
   - Check component dependencies
   - Verify integration tasks
   - Update testing tasks
```

#### For file-tree.md:
```
Review and Update Instructions for file-tree.md:

1. Update Statistics:
   - Recount directories
   - Update file counts
   - Recalculate total size
   - Update file types

2. Structure Changes:
   - Add new files/directories
   - Update file sizes
   - Update line counts
   - Modify relationships

3. Dependencies:
   - Update direct dependencies
   - Check indirect dependencies
   - Verify component relationships
   - Update dependency matrix

4. Documentation:
   - Update component descriptions
   - Modify feature lists
   - Update usage notes
   - Verify relationships
```

### 2. Task Completion Verification

#### For dev-notes.md:
```
Verification Instructions for dev-notes.md:

1. Check Implementation Details:
   - Verify all technical requirements met
   - Confirm configuration changes
   - Check performance metrics
   - Review success criteria

2. Status Verification:
   - Confirm all sub-tasks completed
   - Verify dependencies resolved
   - Check integration points
   - Review testing results

3. Documentation Review:
   - Verify technical documentation
   - Check configuration records
   - Confirm performance metrics
   - Review recent updates
```

#### For task-log.md:
```
Verification Instructions for task-log.md:

1. Task Status Check:
   - Verify task completion
   - Check sub-task status
   - Confirm dependencies met
   - Review blockers resolved

2. Integration Verification:
   - Check related tasks
   - Verify component integration
   - Confirm testing status
   - Review follow-up tasks

3. Documentation:
   - Add completion notes
   - Update related tasks
   - Note follow-up items
   - Record completion date
```

#### For file-tree.md:
```
Verification Instructions for file-tree.md:

1. Structure Verification:
   - Confirm file additions
   - Verify size updates
   - Check relationship changes
   - Validate dependencies

2. Documentation Check:
   - Verify component descriptions
   - Check feature lists
   - Confirm relationships
   - Review usage notes
```

### 3. Task Review and Next Steps

#### For dev-notes.md:
```
Review and Planning Instructions for dev-notes.md:

1. Current Status Review:
   - Check implementation progress
   - Review technical decisions
   - Verify configurations
   - Check performance metrics

2. Next Task Preparation:
   - Identify next priority
   - Review requirements
   - Check dependencies
   - Verify resources

3. Documentation Update:
   - Record current status
   - Note pending items
   - Update timeline
   - Plan next steps
```

#### For task-log.md:
```
Review and Planning Instructions for task-log.md:

1. Current Task Review:
   - Check completion status
   - Verify dependencies
   - Review blockers
   - Check integration status

2. Next Task Selection:
   - Identify next priority
   - Check prerequisites
   - Review dependencies
   - Verify resources

3. Task Planning:
   - Break down next task
   - Set sub-tasks
   - Note dependencies
   - Plan integration
```

#### For file-tree.md:
```
Review and Planning Instructions for file-tree.md:

1. Structure Review:
   - Check recent changes
   - Verify relationships
   - Review dependencies
   - Check component status

2. Next Task Impact:
   - Identify affected components
   - Review dependencies
   - Plan structural changes
   - Note integration points

3. Documentation Planning:
   - Plan updates needed
   - Note affected sections
   - Prepare relationship changes
   - Review dependencies
```

Remember: Always update all three files in sync to maintain project coherence and documentation accuracy. The order of updates should be:
1. file-tree.md for structural changes
2. dev-notes.md for technical details
3. task-log.md for progress tracking

Each file serves a specific purpose:
- file-tree.md: Structure and relationships
- dev-notes.md: Technical implementation details
- task-log.md: Task progress and management

## Task History and Documentation Management

### Task Completion Documentation
```markdown
Instructions for maintaining comprehensive task history:

1. Task Summary Requirements:
   - Use markdown formatting
   - Include relevant emojis
   - Document file paths and changes
   - Note terminal commands
   - Explain project impact

2. Location of Documentation:
   - Primary: dev-notes.md
   - Cross-reference: task-log.md
   - Structure updates: file-tree.md

3. Required Summary Sections:
   a. Task Overview
      - Task name/description
      - Date completed
      - Files modified/created
      - Brief change summary

   b. Implementation Details
      - Technical changes made
      - Configuration updates
      - Performance metrics
      - Dependencies modified

   c. Testing & Commands
      - Test results
      - Terminal commands used
      - Monitoring commands
      - Debugging commands

   d. Project Impact
      - Purpose of changes
      - Project benefits
      - Module improvements
      - Framework contributions

   e. Next Steps
      - Follow-up tasks
      - Unblocked dependencies
      - Required updates
      - Future improvements

4. Documentation Process:
   a. During Task:
      - Record all commands used
      - Note configuration changes
      - Document technical decisions
      - Track performance metrics

   b. After Completion:
      - Write comprehensive summary
      - Update all three core files
      - Cross-reference changes
      - Verify documentation accuracy

5. Historical Record Format:
```markdown
## Task Completion Summary - [Date]

### Task Overview
🎯 Task: [Task Name]
📂 Files Modified:
- `path/to/file` - [Brief edit summary]

### Implementation Details
✨ Changes Made:
[Detailed changes]

🔧 Technical Details:
[Technical specifications]

### Testing & Commands
✅ Tests:
[Test results]

🖥️ Terminal Commands:
```bash
[Relevant commands]
```

### Project Impact
🎯 Purpose:
[Task significance]

📈 Improvements:
[Specific improvements]

### Next Steps
➡️ Follow-up Tasks:
[Next tasks]
```

6. Example Documentation:
```markdown
## Task Completion Summary - 2024-01-15

### Task Overview
🎯 Task: Implement Database Connection Pool
📂 Files Modified:
- `src/db/connection.py` - Added connection pooling
- `config/db_config.json` - Updated pool settings

### Implementation Details
✨ Changes Made:
- Implemented SQLAlchemy connection pool
- Added connection retry logic
- Optimized query performance
- Added connection monitoring

🔧 Technical Details:
- Pool size: 10
- Timeout: 30s
- Retry attempts: 3
- Query cache: 1000 entries

### Testing & Commands
✅ Tests:
- Connection stability: 100%
- Query performance: 45ms avg
- Pool efficiency: 95%

🖥️ Terminal Commands:
```bash
# Start database service
python src/db/service.py --pool-size 10

# Run connection tests
pytest tests/db/test_connection.py -v

# Monitor pool status
python tools/monitor.py --service db
```

### Project Impact
🎯 Purpose:
- Improves database reliability
- Reduces connection overhead
- Enables high-throughput operations

📈 Improvements:
- 60% reduction in connection time
- 45% improvement in query speed
- 99.99% connection reliability

### Next Steps
➡️ Follow-up Tasks:
1. Implement query optimization
2. Add performance monitoring
3. Set up automated failover
```

7. Documentation Best Practices:
   - Keep summaries comprehensive
   - Include all relevant details
   - Maintain consistent formatting
   - Use clear, descriptive language
   - Include specific metrics
   - Document all commands
   - Explain project impact
   - Note dependencies

8. Historical Record Maintenance:
   - Keep all task summaries
   - Maintain chronological order
   - Update cross-references
   - Preserve command history
   - Document configuration changes
   - Track performance evolution

Remember: Comprehensive task documentation is crucial for:
- Project history tracking
- Knowledge transfer
- Troubleshooting
- Performance monitoring
- Process improvement
- Team collaboration
```

## Detailed Examples for Common Scenarios

### 1. Task Progress Documentation Examples

#### Example: Adding New Feature
```markdown
## Task Progress - 2024-01-15

### Current Implementation
🎯 Task: Implement Real-time Market Data Collection
📊 Progress: 75% Complete

#### Changes Made
- ✅ WebSocket connection manager
- ✅ Data validation layer
- 🟡 Performance optimization
- 🔴 Error recovery system

#### Technical Metrics
- Connection uptime: 99.95%
- Message throughput: 1000/sec
- Memory usage: 1.2GB
- Latency: 45ms avg

#### Next Steps
1. Complete performance optimization
2. Implement error recovery
3. Add monitoring system
```

#### Example: Bug Fix Documentation
```markdown
## Bug Fix Report - 2024-01-16

### Issue Details
🐛 Bug: Memory leak in WebSocket connection
📈 Impact: High (System crash after 48h)

#### Root Cause
- Connection pool not properly releasing
- Resource cleanup missing in error paths
- Async handlers not properly disposed

#### Solution Implementation
✅ Fixed:
- Added connection cleanup
- Implemented proper error handling
- Added resource monitoring
```

### 2. File Update Examples

#### file-tree.md Update Example
```markdown
Before:
```
src/
└── websocket/
    └── manager.py     (5KB)
```

After:
```
src/
└── websocket/
    ├── manager.py     (8KB) - Added connection pooling
    ├── monitor.py     (3KB) - New monitoring system
    └── config/
        └── pool.json  (1KB) - Connection pool settings
```

Changes:
- Added monitoring system
- Implemented connection pooling
- Created configuration structure
```

#### dev-notes.md Update Example
```markdown
## Implementation Notes - 2024-01-15

### WebSocket System Enhancement
✨ New Features:
- Connection pooling
  * Max pool size: 10
  * Timeout: 30s
  * Retry logic: Exponential backoff

🔧 Configuration:
```json
{
    "pool": {
        "maxSize": 10,
        "timeout": 30,
        "retryMax": 3
    }
}
```

📊 Performance Impact:
- Before: 500 msg/sec, 2GB memory
- After: 1000 msg/sec, 1.2GB memory
```

### 3. Command Documentation Examples

#### Development Commands
```bash
# Start development environment
python -m venv venv
source venv/bin/activate  # Linux/Mac
.\venv\Scripts\activate   # Windows

# Install dependencies
pip install -r requirements.txt

# Run development server
python src/main.py --env dev --debug

# Run specific tests
pytest tests/websocket/ -v -k "test_connection"
```

#### Deployment Commands
```bash
# Build production package
python setup.py build

# Deploy to staging
./deploy.sh --env staging

# Monitor production
python tools/monitor.py --service websocket --env prod
```

### 4. Cross-Reference Examples

#### Task Dependencies
```markdown
## Task: Implement Trading Engine

### Prerequisites
1. ✅ Market data collection
   - Required for: Price feeds
   - Status: Complete
   - Location: `src/market/collector.py`

2. 🟡 Order management
   - Required for: Trade execution
   - Status: In Progress
   - Location: `src/trading/orders.py`

3. 🔴 Risk management
   - Required for: Position sizing
   - Status: Not Started
   - Blocked by: Order management
```

### 5. Performance Documentation Examples

#### System Metrics
```markdown
## Performance Metrics - 2024-01-15

### Trading System
📊 Execution Performance:
- Order latency: 45ms (target: <100ms)
- Throughput: 100 orders/sec
- Success rate: 99.95%

### Market Data
📈 Data Processing:
- Message rate: 1000/sec
- Processing time: 0.5ms/msg
- Memory usage: 1.2GB

### Database
🔋 Connection Pool:
- Active connections: 8/10
- Query time: 5ms avg
- Cache hit rate: 95%
```