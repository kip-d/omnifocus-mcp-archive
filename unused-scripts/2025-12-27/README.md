# Unused Scripts - Archived 2025-12-27

These scripts were removed from omnifocus-mcp v3.0.0 because they are not imported by any tools.

## Context

With the v3.0.0 unified API consolidation, many backend scripts became orphaned as tools were
consolidated into the 4 unified MCP tools (omnifocus_read, omnifocus_write, omnifocus_analyze, system).

Some scripts were superseded by newer implementations:
- `list-tasks-ast.ts` - Replaced by AST-based query system in contracts/
- `warm-projects-cache-with-stats.ts` - Replaced by `warm-projects-cache.ts`
- Various task scripts - Functionality consolidated into ManageTaskTool

Some scripts were never connected to the MCP interface:
- Review scripts (`mark-project-reviewed.ts`, `projects-for-review.ts`, `set-review-schedule.ts`)
- These contain valid OmniJS code but were never routed through a tool

## Scripts Archived

| Script | Category | Notes |
|--------|----------|-------|
| `tasks/delete-task.ts` | Tasks | Superseded by ManageTaskTool |
| `tasks/list-tasks-ast.ts` | Tasks | Replaced by AST query system |
| `tasks/complete-task.ts` | Tasks | Superseded by ManageTaskTool |
| `tasks/delete-tasks-bulk.ts` | Tasks | Bulk delete via batch operations |
| `tasks/todays-agenda.ts` | Tasks | Today mode in QueryTasksTool |
| `tasks/complete-tasks-bulk.ts` | Tasks | Bulk complete via batch operations |
| `cache/warm-projects-cache-with-stats.ts` | Cache | Superseded by simpler version |
| `projects/update-project.ts` | Projects | Via ManageTaskTool with target:project |
| `system/get-version.ts` | System | Moved to utils/version.ts |
| `recurring/get-recurring-patterns.ts` | Recurring | Never routed to tool |
| `reviews/mark-project-reviewed.ts` | Reviews | Never routed to tool |
| `reviews/projects-for-review.ts` | Reviews | Never routed to tool |
| `reviews/set-review-schedule.ts` | Reviews | Never routed to tool |

## Potential Future Use

The review scripts could be valuable if review management is added to the MCP server.
The OmniJS code is functional and could be connected to a new ReviewTool.
