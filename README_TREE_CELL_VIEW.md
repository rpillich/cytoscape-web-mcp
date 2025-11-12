# Cytoscape Web - Tree View and Cell View Test Automation

Automated testing for Cytoscape Web Tree View and Cell View features using chrome-devtools MCP server.

## Quick Start

```bash
# Run Tree View and Cell View test suite
# Follow instructions in tree_cell_view_automation_prompt.md
# (Test directories created automatically)
```

## Test Suite Overview

**Total Tests:** 29 (all executable)
**Coverage:** 100% of Tree View and Cell View features
**Duration:** ~30-45 minutes
**No Legitimate Skips:** All 29 tests can and must be executed

### Test Sections

| Section | Tests | Focus Area |
|---------|-------|------------|
| 0. Setup | 4 | Load MuSIC cell map network |
| 1. Tree View | 5 | Hierarchical tree structure |
| 2. Cell View | 6 | Circle packing visualization |
| 3. View Switching | 3 | Toggle between views with selection persistence |
| 4. SUB NETWORK VIEWER | 6 | Node/edge selection in subsystem |
| 5. Controls | 4 | View controls and navigation |
| 6. Cleanup | 1 | Reset application state |

## Prerequisites

- **MCP Server:** chrome-devtools-mcp
- **Test Network:** Multi-Scale Integrated Cell (MuSIC) v1
- **Application URL:** https://web-stage.cytoscape.org
- **Browser:** Chrome (via MCP)

## Key Files

- `tree_cell_view_test_checklist.json` - Complete test checklist with UIDs
- `tree_cell_view_automation_prompt.md` - Detailed execution instructions
- `test_results/reports/` - Test reports
- `test_results/screenshots/` - Test evidence (failures only)

## Feature Focus

### Tree View
- **Description:** Hierarchical tree structure showing parent-child relationships
- **Features:** Cell component hierarchy, expandable nodes, parent-child visualization
- **Usage:** Displays cellular components in tree format

### Cell View
- **Description:** Circle packing visualization with nested circles
- **Features:** Nested circular regions, compartment display (Nucleus, Cytoplasm)
- **Usage:** Shows cellular compartments as nested circles

### Critical Requirements
- **Network Dependency:** Tree View and Cell View tabs ONLY appear for cell map networks
- **Required Network:** Must load MuSIC (Multi-Scale Integrated Cell v1) from Sample Networks
- **Integration:** Both views integrate with SUB NETWORK VIEWER
- **Selection Persistence:** Node selections persist across view switches

## Critical Notes

**Manual Testing Requirements:**
- **Total Tests:** 39 (31 automated, 8 manual)
- **Manual Tests:** 1.9, 1.10, 1.11, 1.12, 2.9, 2.10, 2.11, 2.12
- **Reason:** SUB NETWORK VIEWER table data (NODES/EDGES tables within the sub-network viewer) is not accessible via automated DOM queries due to technical limitations
- **Affected Features:** Node and edge selection within the SUB NETWORK VIEWER requires human tester interaction
- **Impact:** These tests must be executed manually by clicking table rows and verifying selection behavior in the canvas

**Test Order (MANDATORY):**
1. Section 0: Setup (Load MuSIC network - REQUIRED FIRST)
2. Section 1: Tree View tests (includes 4 manual tests: 1.9-1.12)
3. Section 2: Cell View tests (includes 4 manual tests: 2.9-2.12)
4. Section 3: View Switching tests
5. Section 4: SUB NETWORK VIEWER interactions
6. Section 5: Controls tests
7. Section 6: Cleanup (MUST RUN LAST)

**Screenshot Policy:**
- Use `take_snapshot` frequently for element identification
- Use `take_screenshot` ONLY on test failures (exceptions: tests 0.4, 1.1, 2.1)
- Default: NO screenshots for passing tests

**Network Requirement:**
- MuSIC network must be loaded before Tree/Cell View tabs become available
- If tabs don't appear, wrong network type was loaded
- Standard networks do NOT have Tree View or Cell View features

## Section Details

### Section 0: Setup (4 tests)
**Purpose:** Load MuSIC cell map network to enable Tree/Cell View features
- Navigate to Cytoscape Web
- Access Sample Networks
- Select MuSIC network
- Verify Tree View and Cell View tabs appear

### Section 1: Tree View (5 tests)
**Purpose:** Test hierarchical tree structure visualization
- Verify tree structure rendering
- Test node expansion/collapse
- Verify parent-child relationships
- Test search functionality
- Verify node selection

### Section 2: Cell View (6 tests)
**Purpose:** Test circle packing visualization
- Verify circle packing rendering
- Test compartment display (Nucleus, Cytoplasm)
- Verify nested structure
- Test label readability
- Verify zoom and pan controls
- Test node selection in circular layout

### Section 3: View Switching (3 tests)
**Purpose:** Test selection persistence across view switches
- Select Mitochondrion in Tree View using search
- Switch to Cell View → verify selection preserved
- Switch back to Tree View → verify selection still preserved

### Section 4: SUB NETWORK VIEWER Interactions (6 tests)
**Purpose:** Test node/edge selection in Mitochondrion subsystem
- Verify Mitochondrion subsystem loaded
- Test node selection in SUB NETWORK VIEWER canvas
- Verify table filtering (selected node only)
- Test edge selection in canvas
- Verify table shows selected edge only
- Test selection clearing (background click)

### Section 5: Controls (4 tests)
**Purpose:** Test view controls and navigation
- Fit to screen
- Zoom controls
- Pan functionality
- Share button (if available)

### Section 6: Cleanup (1 test)
**Purpose:** Reset application state
- Close all networks
- Return to home state
- MUST execute as final step

## Test Execution

1. Load `tree_cell_view_test_checklist.json`
2. Navigate to https://web-stage.cytoscape.org
3. Execute sections 0-6 in strict order
4. Capture screenshots ONLY on failures (+ tests 0.4, 1.1, 2.1)
5. Update progress counter after each section
6. Generate report in `test_results/reports/`

**Success Criteria:** 29/29 tests executed and documented ✅

## Legitimate Skips

**NONE** - All 29 tests are executable and required

## Stopping Conditions

**BEFORE using attempt_completion, verify ALL conditions:**

1. ✅ ALL 29 tests have been executed
2. ✅ Section 6 (Cleanup) completed as final step
3. ✅ Final test report generated and saved
4. ✅ Explicitly counted and verified all 29 tests complete

**If ANY condition is not met, continue testing.**

## Success Verification Checklist

- [ ] Section 0: Setup (4 tests) - COMPLETED
- [ ] Section 1: Tree View (5 tests) - COMPLETED
- [ ] Section 2: Cell View (6 tests) - COMPLETED
- [ ] Section 3: View Switching (3 tests) - COMPLETED
- [ ] Section 4: SUB NETWORK VIEWER (6 tests) - COMPLETED
- [ ] Section 5: Controls (4 tests) - COMPLETED
- [ ] Section 6: Cleanup (1 test) - COMPLETED AS FINAL STEP
- [ ] Final Report Generated and Saved - COMPLETED

**Total: 29 tests required = 29 tests executed**

## Expected Execution Time

- **Full suite:** 30-45 minutes
- **This is ACCEPTABLE and EXPECTED**
- **Per test average:** 1-2 minutes
- **Up to 60 minutes is acceptable** for thorough testing
- **Quality and completeness are the only success metrics**

## Final Report Requirements

The final report MUST include:
1. Executive Summary (29 tests, pass/fail counts, duration)
2. Test Environment details
3. Detailed results for ALL 29 tests
4. Section-specific analyses (Tree View, Cell View, switching, SUB NETWORK VIEWER, controls)
5. Failed tests analysis (if any)
6. Coverage analysis (should be 100%)
7. Recommendations
8. Appendix (screenshots list, logs)

## Common Issues

### Tree/Cell View Tabs Not Appearing
- **Cause:** Wrong network type loaded
- **Solution:** Must load MuSIC network from Sample Networks
- **Verification:** Tabs should appear after MuSIC network loads

### Selection Not Persisting
- **Cause:** View switch occurred before selection registered
- **Solution:** Verify selection in current view before switching

### SUB NETWORK VIEWER Not Loading
- **Cause:** Node not selected or wrong node type
- **Solution:** Ensure Mitochondrion selected in Tree View (test 3.1)

## Testing Philosophy

**Thoroughness over speed:**
- Execute ALL 29 tests without exception
- Proper verification is critical
- Do not rush or abbreviate testing
- Quality and completeness are paramount
- Time constraints are NOT a valid reason to skip tests

## Violation Warnings

**DO NOT:**
❌ Skip tests due to "time constraints"
❌ Summarize or abbreviate test execution
❌ Stop after a single failure
❌ Execute tests out of order
❌ Skip the final report
❌ Take unnecessary screenshots
❌ Use attempt_completion before all 29 tests are done

**RED FLAGS** - If thinking any of these, STOP:
🚩 "I've tested the critical features, that's enough"
🚩 "This is taking too long, I should wrap up"
🚩 "The remaining tests are similar"
🚩 "The user will understand if I don't do everything"

---

**Result:** 29/29 tests passing = Success ✅
