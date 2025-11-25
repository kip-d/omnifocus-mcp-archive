# Testing Prompts Archive

**Date Archived:** November 9, 2025
**Reason:** Consolidation to single unified testing prompt

## Why These Files Were Archived

The project had accumulated 11 different testing prompt files across multiple directories, creating:
- Confusion about which prompt to use
- Maintenance burden (updating multiple files with same information)
- Version drift (different prompts referenced different tool versions)
- Fragmented testing approaches

## Consolidation Strategy

All testing prompts were consolidated into a single comprehensive guide:
- **`TESTING_PROMPT.md`** (root directory)
- Combines best elements from all archived prompts
- Updated for v3.0.0 unified API (4 tools instead of 17)
- Includes both natural language and technical testing approaches
- Has built-in cleanup system using unique test identifiers

## What Was Preserved

From these archived files, we extracted and incorporated:

**From `TESTING_PROMPTS_COMPREHENSIVE_V3.md`:**
- Unique test identifier system (`@mcp-test-TIMESTAMP`)
- Automated cleanup protocol
- Known issues documentation

**From `TESTING_PROMPTS_NATURAL_CONVERSATION.md`:**
- Natural language test scenarios
- User-friendly conversation examples
- Real-world testing approach

**From `CLAUDE_DESKTOP_TEST_PROMPT.md`:**
- Error handling test cases
- Edge case scenarios
- Comprehensive coverage checklist

**From `TESTING_PROMPTS_LIGHTWEIGHT.md`:**
- Concise output format
- Token budget estimates

## Archived Files

### Root Directory
- `TESTING_INSTRUCTIONS.md` (172 lines)
  - Setup instructions for feature branch testing
  - Outdated: References `feature/three-tool-builder-api` branch
  - Status: Replaced by current TESTING_PROMPT.md

### Tests Directory
- `CLAUDE_DESKTOP_TEST_PROMPT.md`
  - Comprehensive test suite from v2.0.0
  - Outdated: References 15 legacy tools instead of 4 unified tools
  - Status: Test scenarios updated for unified API

### Docs Directory
- `TESTING_PROMPTS_COMPREHENSIVE_V3.md` (817 lines)
  - Most comprehensive testing guide
  - Mixed quality: Good cleanup strategy, inconsistent tool references
  - Status: Best elements incorporated into unified prompt

- `TESTING_PROMPTS_NATURAL_CONVERSATION.md` (191 lines)
  - User-friendly natural language testing approach
  - Status: Conversation style adopted in unified prompt

- `TESTING_PROMPTS_CLAUDE_DESKTOP.md` (270 lines)
  - Natural language test guide for v2.2.0
  - Status: Testing approach preserved, updated for v3.0.0

- `TESTING_PROMPTS_LIGHTWEIGHT.md` (277 lines)
  - Lightweight test suite with concise output
  - Status: Format and efficiency ideas incorporated

- `TESTING_PROMPTS_SESSION_1.md` (104 lines)
  - Early testing session template
  - Status: Superseded by comprehensive guide

- `TESTING_PROMPTS_SESSION_2.md` (125 lines)
  - Second iteration testing session
  - Status: Superseded by comprehensive guide

## Migration Notes

**If you need to reference old testing approaches:**
- These files remain accessible in this archive
- Git history preserved via `git mv` (use `git log --follow` to see history)
- Can be compared with current TESTING_PROMPT.md if needed

**For new testing:**
- Always use `/TESTING_PROMPT.md` (root directory)
- Report issues or suggest improvements to that single file
- Do not create new separate testing prompts

## Archive Maintenance

This archive is part of the main repository (not separate archive repo) because:
- Files are outdated but not incorrect
- Useful for historical reference
- May inform future testing approaches
- `.archive/` is git-ignored in main repo (but this consolidation is committed)

For truly obsolete or incorrect documentation, use the separate archive repository:
https://github.com/kip-d/omnifocus-mcp-archive
