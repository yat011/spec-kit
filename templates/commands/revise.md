---
description: Revise feature specifications based on new requirements or changes
scripts:
  sh: scripts/bash/check-task-prerequisites.sh --json
  ps: scripts/powershell/check-task-prerequisites.ps1 -Json
---

Given the revision requirements provided as an argument, do this:

1. Run `{SCRIPT}` from repo root and parse FEATURE_DIR and AVAILABLE_DOCS list. All paths must be absolute.

2. Load current specifications:
   - Read plan.md to understand current implementation approach
   - IF REQUIRED: Read data-model.md for current entities
   - IF REQUIRED: Read contracts/ for current API endpoints
   - IF REQUIRED: Read research.md for technical decisions
   - IF REQUIRED: Read quickstart.md for test scenarios
   - IF EXISTS: Read tasks.md for current task breakdown

3. Analyze revision requirements:
   - Parse the user input to understand what needs to be revised
   - Identify which documents will be affected by the changes
   - Determine if changes are:
     * Feature additions (new functionality)
     * Modifications (changes to existing features)
     * Refactoring (structural changes)
     * Bug fixes or corrections

4. Update plan.md:
   - Revise implementation approach if needed
   - Update tech stack if new libraries are required
   - Modify architecture decisions based on changes
   - Keep existing content that remains valid
   - Append changelog: `<!-- Revised: {date} - {brief description of changes} -->`

5. Update all related documents:
   - data-model.md: Update entities, relationships, or schemas
   - contracts/: Modify or add API endpoints
   - research.md: Document new technical decisions
   - quickstart.md: Update test scenarios if needed
   - Each update should preserve existing valid content

6. Update tasks.md:
   - Add new tasks for new features (marked with [NEW])
   - Modify existing incomplete tasks if requirements changed
   - Mark obsolete tasks as [DEPRECATED] but keep for history
   - Reorder tasks if dependencies changed
   - Update parallel execution guidance
   - Maintain task numbering sequence

7. Append changelog to each modified file:
   - Format: `<!-- Revised: YYYY-MM-DD - {one-line description} -->`
   - Place at the end of each file
   - Keep it concise but informative

Revision requirements: {ARGS}

The revision should maintain project consistency while incorporating the requested changes. All updates should be immediately actionable.