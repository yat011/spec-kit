---
description: Execute the implementation tasks defined in tasks.md for the current feature
scripts:
  sh: scripts/bash/check-task-prerequisites.sh --json
  ps: scripts/powershell/check-task-prerequisites.ps1 -Json
---

Given the implementation scope provided as an argument (or "all" for complete implementation), do this:

1. Run `{SCRIPT}` from repo root and parse FEATURE_DIR and AVAILABLE_DOCS list. All paths must be absolute.

2. Load and validate tasks.md:
   - Read FEATURE_DIR/tasks.md
   - Parse all task sections (Setup, Tests, Core, Integration, Polish)
   - Identify task dependencies and parallel execution markers [P]
   - Build execution order based on dependencies

3. Determine implementation scope:
   - If ARGS is "all": Execute all pending tasks
   - If ARGS contains task IDs (T001, T002): Execute specific tasks
   - If ARGS contains section name: Execute all tasks in that section
   - If ARGS contains keywords: Execute matching tasks

4. Pre-implementation checks:
   - Verify all prerequisite tasks are completed
   - Check that required files and directories exist
   - Confirm tech stack dependencies are installed
   - Review plan.md for implementation guidelines

5. Task execution rules:
   - Update task status in tasks.md as you progress:
     * Mark as [IN PROGRESS] when starting
     * Mark as [COMPLETED] when done
     * Mark as [BLOCKED] if dependencies fail
   - Create actual code files as specified in each task
   - Follow the tech stack defined in plan.md

Implementation scope: {ARGS}

Execute tasks systematically, ensuring each implementation matches the specifications in plan.md and related design documents. Prioritize test-driven development where tests are defined.