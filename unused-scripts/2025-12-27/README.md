# Unused Scripts - Archived 2025-12-27

## Status Update

Initial audit identified 13 "unused" scripts, but re-analysis found that **11 of them are actively used**
via barrel file imports (tasks.ts, reviews.ts, recurring.ts).

**Actually removed from omnifocus-mcp:** 2 scripts
**Archived but still in use:** 11 scripts (kept in archive for historical reference)

## Scripts Actually Removed

| Script | Category | Notes |
|--------|----------|-------|
| `cache/warm-projects-cache-with-stats.ts` | Cache | Superseded by `warm-projects-cache.ts` |
| `projects/update-project.ts` | Projects | Never connected to any tool |

## Scripts Archived But Still In Use

These scripts were initially thought unused but are imported through barrel files:

| Script | Used By |
|--------|---------|
| `tasks/complete-task.ts` | ManageTaskTool via tasks.ts |
| `tasks/complete-tasks-bulk.ts` | ManageTaskTool via tasks.ts |
| `tasks/delete-task.ts` | ManageTaskTool via tasks.ts |
| `tasks/delete-tasks-bulk.ts` | ManageTaskTool via tasks.ts |
| `tasks/todays-agenda.ts` | QueryTasksTool via tasks.ts |
| `tasks/list-tasks-ast.ts` | QueryTasksTool, ManageTaskTool via tasks.ts |
| `system/get-version.ts` | version-detection.ts |
| `recurring/get-recurring-patterns.ts` | RecurringTasksTool via recurring.ts |
| `reviews/mark-project-reviewed.ts` | ManageReviewsTool via reviews.ts |
| `reviews/projects-for-review.ts` | ManageReviewsTool via reviews.ts |
| `reviews/set-review-schedule.ts` | ManageReviewsTool via reviews.ts |

## Lesson Learned

When auditing for unused code, must trace through barrel file re-exports, not just direct imports.
The pattern `grep -r "from.*scriptname" src/tools` misses indirect imports via barrel files.
