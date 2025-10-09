# Cytoscape Web - MCP Test Automation

Automated testing for Cytoscape Web using chrome-devtools MCP server.

## Quick Start

```bash
# Ensure test directories exist
mkdir -p test_results/{logs,screenshots,reports}

# Run comprehensive test suite
# Follow instructions in updated_automation_prompt.md
```

## Test Suite Overview

**Total Tests:** 27 (24 executable, 3 skipped)
**Coverage:** 100% of executable tests
**Duration:** ~40 minutes

### Test Sections

| Section | Tests | Skips |
|---------|-------|-------|
| 0. Preflight | 1 | - |
| 1. Authentication | 3 | - |
| 2. Data Menu | 10 | 2 (file upload) |
| 3. Edit | 2 | - |
| 4. Layout | 2 | - |
| 5. Analysis | 1 | 1 (API key) |
| 6. Tools | 1 | - |
| 7. Apps | 1 | - |
| 8. Help | 1 | - |
| 9. Search | 2 | - |
| 10. Workspace | 1 | - |
| 11. Network View | 3 | - |
| 12. Style | 1 | - |
| 13. Table Browser | 2 | - |
| 14. Cleanup | 1 | - |

## Prerequisites

- **MCP Server:** chrome-devtools-mcp
- **Test Account:** ndextutorials / ndextutorials
- **Cytoscape Desktop:** Running on port 1234 (for integration tests)
- **Test Data:** CX2 files in `CX2 test files/`, CSV files in `test_data/`

## Key Files

- `mcp_checklist_v5.json` - Complete test checklist with UIDs
- `updated_automation_prompt.md` - Execution instructions
- `test_results/reports/` - Test reports
- `test_results/screenshots/` - Test evidence

## Critical Notes

**Authentication Order:** Section 1 (login) → Section 2.1-2.3 (auth tests) → Section 2.4 (logout) → remaining tests

**Test 11.1b Button:** THIRD button in network view controls (unlabeled, no icon). Tooltip: "Open a copy of the current network in Cytoscape Desktop."

**Final Step:** Section 14 cleanup MUST run last

## Legitimate Skips

- **2.6, 2.7:** File upload (MCP limitation)
- **5.1:** LLM Query (requires API key)

## Test Execution

1. Load `mcp_checklist_v5.json`
2. Navigate to https://web-stage.cytoscape.org
3. Execute sections 0-14 in order
4. Capture screenshots for all tests
5. Generate report in `test_results/reports/`

**Result:** 24/24 tests passing = Success ✅
