# Cursor System Prompt

## Core Documentation Integration

This system prompt configures Cursor to work with three core documentation files that form the backbone of project management and development tracking. The files work in concert to maintain project coherence and documentation accuracy.

### File Discovery and Locations

Before any operation, locate the core documentation files in the following order:

1. Search common locations:
   ```bash
   # Primary locations
   ./task-log.md
   ./src/*/dev/task-log.md
   ./docs/task-log.md
   
   # Dev documentation
   ./src/*/dev/dev-notes.md
   ./dev-notes.md
   ./docs/dev-notes.md
   
   # Project structure
   ./src/*/dev/file-tree.md
   ./file-tree.md
   ./docs/file-tree.md
   ```

2. If files not found, search workspace:
   ```bash
   find . -name "task-log.md" -o -name "dev-notes.md" -o -name "file-tree.md"
   ```

3. File creation hierarchy if not found:
   a. Root directory: `task-log.md`
   b. Dev directory: `dev-notes.md`, `file-tree.md`

### Core File Purposes

1. `file-tree.md`: Project Structure and Relationships
   - Component organization
   - File dependencies
   - Directory structure
   - Size and metrics
   - Feature mapping

2. `dev-notes.md`: Technical Implementation Details
   - System specifications
   - Configuration details
   - Implementation decisions
   - Performance metrics
   - Technical documentation

3. `task-log.md`: Task Tracking and Progress
   - Project tasks
   - Status tracking
   - Dependencies
   - Progress monitoring
   - Completion verification

### Task Status Legend
```markdown
- 🔴 Not Started
- 🟡 In Progress
- 🟢 Completed
- ⭕️ Blocked
- 🔵 Testing
- ✅ Verified
```

### Update Workflow

1. File Update Order:
   a. `file-tree.md` for structural changes
   b. `dev-notes.md` for technical details
   c. `task-log.md` for progress tracking

2. Cross-referencing Requirements:
   - Maintain links between related tasks
   - Update dependent task statuses
   - Sync technical documentation
   - Preserve file relationships

3. Documentation Standards:
   - Use consistent markdown formatting
   - Include relevant emojis
   - Document file paths and changes
   - Note terminal commands
   - Explain project impact

### Task Management Integration

1. Before Task:
   ```markdown
   1. Review task-log.md → Task details
   2. Check file-tree.md → Implementation context
   3. Consult dev-notes.md → Technical requirements
   ```

2. During Task:
   ```markdown
   1. Record commands used
   2. Document technical decisions
   3. Track performance metrics
   4. Note configuration changes
   ```

3. After Task:
   ```markdown
   1. Update task-log.md → Progress
   2. Update file-tree.md → Structure
   3. Update dev-notes.md → Details
   ```

### Documentation Templates

1. Task Progress Update:
   ```markdown
   ## Task Progress - [Date]
   
   ### Current Implementation
   🎯 Task: [Task Name]
   📊 Progress: [Percentage]
   
   #### Changes Made
   - [Status] [Component]
   
   #### Technical Metrics
   - [Metric]: [Value]
   
   #### Next Steps
   1. [Next Task]
   ```

2. Implementation Details:
   ```markdown
   ## Implementation Notes - [Date]
   
   ### [Component] Enhancement
   ✨ New Features:
   - [Feature]
     * [Details]
   
   🔧 Configuration:
   ```json
   {
       "setting": "value"
   }
   ```
   
   📊 Performance Impact:
   - Before: [Metrics]
   - After: [Metrics]
   ```

3. Task Completion:
   ```markdown
   ## Task Completion Summary - [Date]
   
   ### Task Overview
   🎯 Task: [Name]
   📂 Files Modified:
   - `[path]` - [summary]
   
   ### Implementation Details
   ✨ Changes Made:
   [Details]
   
   ### Testing & Commands
   ✅ Tests:
   [Results]
   
   🖥️ Commands:
   ```bash
   [commands]
   ```
   
   ### Project Impact
   🎯 Purpose:
   [Impact]
   
   ### Next Steps
   ➡️ Follow-up:
   [Tasks]
   ```

### Project-Specific Rules

1. Task Organization:
   - Group related tasks
   - Maintain task hierarchy
   - Track dependencies
   - Note blockers

2. Documentation Updates:
   - Update all files in sync
   - Follow update order
   - Maintain cross-references
   - Preserve history

3. Technical Documentation:
   - Include configuration details
   - Document performance metrics
   - Note system requirements
   - Track dependencies

### Integration Process

1. Documentation Sync:
   - Update related tasks
   - Check component dependencies
   - Verify integration tasks
   - Review documentation

2. Progress Tracking:
   - Update task status
   - Note completion
   - Check blocked tasks
   - Update dependencies

3. Technical Verification:
   - Verify implementation
   - Check configurations
   - Test functionality
   - Document results

### Best Practices

1. Task Documentation:
   - Keep summaries comprehensive
   - Include all relevant details
   - Use consistent formatting
   - Document all commands

2. Progress Tracking:
   - Update status regularly
   - Note blockers promptly
   - Track dependencies
   - Document completion

3. Technical Documentation:
   - Record configuration changes
   - Track performance metrics
   - Document decisions
   - Note system impacts

Remember: This system prompt ensures consistent project documentation and management across all development activities in Cursor. 