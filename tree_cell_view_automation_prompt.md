# Tree View and Cell View Testing Prompt for Claude Sonnet 4.5

## Primary Objective
You are tasked with performing a **COMPLETE and EXHAUSTIVE** automated test of the Cytoscape Web Tree View and Cell View features using the test checklist provided. This is a comprehensive quality assurance task focused specifically on cell map network visualization modes.

---

## 🚨 CRITICAL EXECUTION REQUIREMENT - READ FIRST 🚨

### STOPPING CONDITION - You Are NOT Allowed to Complete Until all conditions below (1 through 4) are satisfied.

⚠️ **BEFORE using `attempt_completion`, you MUST verify ALL of these conditions (1 through 4):**

1. ✅ **ALL 29 tests have been executed** (No legitimate skips - all tests are executable)
2. ✅ **Section 5 (Cleanup) has been completed** as the final step
3. ✅ **The final test report has been generated and saved** to `./test_results/reports/`
4. ✅ **You have explicitly counted and verified** that all 29 tests are complete

**If you attempt completion before executing all 29 tests, you have FAILED the task.**

### Expected Execution Time

- **Full test suite execution time:** 30-45 minutes
- **This is ACCEPTABLE and EXPECTED**
- **This is NOT "too long" or "inefficient"**
- If you complete in less than 25 minutes, you likely skipped tests
- If you need up to 60 minutes for thorough execution, that's also acceptable

**QUALITY AND COMPLETENESS ARE THE ONLY SUCCESS METRICS.**

---

## Test Overview

### Feature Focus
These tests focus on **Tree View** and **Cell View** - special visualization modes available only for cell map networks (like Multi-Scale Integrated Cell (MuSIC) v1).

- **Tree View**: Hierarchical tree structure showing parent-child relationships of cellular components
- **Cell View**: Circle packing visualization with nested circles representing cellular compartments

### Test Count
- **Total tests: 29** (all directly testable)
- **Legitimate skips: 0** (all tests can be executed)
- **Required execution: 29 tests**

---

## Critical Requirements

### 1. COMPLETE CHECKLIST EXECUTION (MANDATORY)
- **YOU MUST RUN THE ENTIRE CHECKLIST** from start to finish
- **DO NOT skip any test items**
- **Time constraints are NOT a valid reason to skip tests**
- **DO NOT abbreviate or summarize test execution**
- Every test marked as 🔧 TESTABLE **MUST BE EXECUTED**
- The checklist contains 29 tests; you must execute ALL 29

### 2. MCP Server Usage
- Use the **chrome-devtools-mcp** server exclusively for all browser interactions
- Available MCP tools include:
  - `take_snapshot` - Capture page structure and element UIDs (use frequently)
  - `click` - Interact with elements using their UID
  - `fill` - Fill form fields using their UID
  - `take_screenshot` - **USE ONLY ON TEST FAILURES** to document errors (exceptions: tests 0.4, 1.1, 2.1)
  - `navigate_page` - Navigate to URLs
  - `wait_for` - Wait for specific text to appear
  - `evaluate_script` - Execute JavaScript for verification
  - `handle_dialog` - Handle browser dialogs

### 3. Screenshot Policy (IMPORTANT)
**Default: NO screenshots unless test fails**
- Use `take_snapshot` frequently for element identification and state verification
- Use `take_screenshot` ONLY when:
  - A test FAILS (to document the error state)
  - Explicitly required (tests 0.4, 1.1, 2.1 - initial state documentation)
- Do NOT take screenshots for passing tests
- This reduces execution time and token usage significantly

### 3. Test Execution Order (CRITICAL)
Execute tests in this **STRICT ORDER**:
1. **Section 0: Setup** - Load U2OS cell map network from NDEx (enables Tree/Cell View)
2. **Section 1: Tree View Complete** - Full Tree View testing (display, zoom, tables, node selection, sub-network viewer)
3. **Section 2: Cell View Complete** - Full Cell View testing (display, zoom, tables, node selection, sub-network viewer)
4. **Section 3: SUB NETWORK VIEWER Filters** - Test filter panel, toggles, gear icon settings, integrated interactions filter
5. **Section 4: Controls** - Test share buttons in both views
6. **Section 5: Cleanup** - MUST run last to reset application state

**DO NOT deviate from this order.** U2OS network must be loaded before Tree/Cell View features become available.

---

## Mandatory Test Completion Checklist

**Before using `attempt_completion`, you MUST verify ALL of these are checked:**

- [ ] Section 0: Setup (4 tests) - COMPLETED
- [ ] Section 1: Tree View Complete (8 tests) - COMPLETED
- [ ] Section 2: Cell View Complete (8 tests) - COMPLETED
- [ ] Section 3: SUB NETWORK VIEWER Filters (5 tests) - COMPLETED
- [ ] Section 4: Controls (2 tests) - COMPLETED
- [ ] Section 5: Cleanup (2 tests) - COMPLETED AS FINAL STEP
- [ ] Final Report Generated and Saved - COMPLETED

**Total Tests Required: 29 (all tests are executable)**

**If ANY checkbox above is unchecked, you MUST continue testing.**

---

## BEFORE ATTEMPTING COMPLETION - Self-Check Questions

Ask yourself these questions. If ANY answer is "NO", DO NOT use attempt_completion:

1. ✅ Have I executed ALL 29 tests? (Count them explicitly)
2. ✅ Did I execute Section 5 (Cleanup) as the LAST step?
3. ✅ Have I generated the final comprehensive report?
4. ✅ Can I provide proof (screenshots, test count) that all tests were executed?
5. ✅ Does my report show results for ALL sections: 0, 1, 2, 3, 4, 5?
6. ✅ Do I have screenshots for failures and exceptions (tests 0.4, 1.1, 2.1)?

**If you cannot answer YES to all questions above, continue testing.**

---

## Test Count Verification

Your test execution is ONLY successful if you can verify:

1. ✅ Executed exactly **29 tests** (no skips)
2. ✅ Report shows results for sections: **0, 1, 2, 3, 4, 5**
3. ✅ Section 5 (Cleanup) documented as the **LAST** test executed
4. ✅ Have screenshots for failures and documented exceptions
5. ✅ Final report includes detailed results for **all 29 tests**

**Count your executed tests. If the number is not 29, you have NOT completed the task.**

---

## Detailed Instructions

### A. Initialization Phase
1. Load the checklist from: `tree_cell_view_test_checklist.json`
2. Review the complete test structure and prerequisites
3. Verify test data files exist in the specified locations (if needed)
4. Create test results directory structure:
   - `./test_results/`
   - `./test_results/logs/`
   - `./test_results/screenshots/`
   - `./test_results/reports/`

### B. Test Execution Phase

#### For EACH test section (0 through 5):
1. **Read the section metadata**:
   - Description
   - Priority level
   - Prerequisites
   - Special notes

2. **For EACH test within the section**:
   
   a. **Execute each step in the test**:
      - Follow the `steps` array in order
      - Use `take_snapshot` before most actions to identify element UIDs
      - Use the MCP tools with the correct parameters
      - Capture screenshots at key verification points
      - Save screenshots with naming convention: `tree_cell_view_test_{section_id}_{test_id}_{step_description}.png`
   
   b. **Verification**:
      - Verify each test's success conditions
      - Document pass/fail status
      - Capture error details if test fails
      - **DO NOT SKIP verification steps**
   
   c. **Error Handling**:
      - If a test fails, document the failure details
      - Continue with remaining tests (do not abort entire run)
      - Note any blocking failures that prevent subsequent tests

3. **Session Management**:
   - Maintain browser session throughout test execution
   - Keep MuSIC network loaded until cleanup section
   - Do not close browser between tests unless specified

### C. Mandatory Progress Reporting

**After EVERY test section completion, you MUST:**

1. Update your progress counter: "Completed X of 29 required tests"
2. List remaining sections to execute
3. Confirm continuation to next section

**Example Progress Update:**
```
╔════════════════════════════════════════════╗
║ PROGRESS: 20/29 tests complete (69%)      ║
║ SECTIONS DONE: 0, 1, 2                    ║
║ SECTIONS REMAINING: 3, 4, 5               ║
║ NEXT: Section 3 - SUB NETWORK VIEWER Filters ║
╚════════════════════════════════════════════╝
```

This prevents premature stopping by making incomplete work visible.

### D. Special Test Handling

#### Setup Tests (Section 0 - CRITICAL)
```
Test 0.2 & 0.3: Load U2OS cell map network from NDEx
- Network: "U2OS Multi-scale Integrated Cell Map"
- Source: Data > Open Network(s) from NDEx...
- UUID: c380c4be-ae09-11f0-a218-005056ae3c32
- Node count: 276
- Edge count: 298
- Search by UUID in NDEx dialog
- MUST succeed for Tree/Cell View tabs to appear
- Verify TREE VIEW and CELL VIEW tabs are visible

CRITICAL: Tree View and Cell View ONLY appear for cell map networks
```

#### View Mode Tests
```
Tree View Complete (Section 1 - 8 tests):
- Display hierarchical tree structure
- Test zoom controls (fit button)
- Select Mitochondrion node using text search
- Verify NODES table filters to 1 row (Mitochondrion selected)
- Verify EDGES table still shows all 298 edges
- Verify SUB NETWORK VIEWER displays Mitochondrion subsystem
- Select the first gene in the Sub Network Viewer and confirm the label matches between grid and mini network
- Clear all selections and confirm no nodes remain selected

Cell View Complete (Section 2 - 8 tests):
- Same sequence as Tree View but within Cell View (circle packing)
- Includes verifying zoom controls, node search, table states, Sub Network Viewer sync, and selection clearing
```

Sub Network Viewer selection workflow (applies to automated Tests 1.7 and 2.9):
- After switching to the Sub Network Viewer tab, press the mini-network `fit` button so the canvas has focus.
- Trigger the scripted click on the first NODES row (leftmost cell) to highlight it.
- Use the `SELECT NODES` button beneath the NODES tab header to push the selection into the mini network.
- Verify via script that the grid row label matches the selected node label in the mini network rendering.

### E. Reporting Requirements

#### During Test Execution:
- Log each test start with timestamp
- Log each step within each test
- Capture screenshots at verification points
- Log pass/fail status for each test
- Record error messages and stack traces for failures
- Update progress counter after each section

#### Final Report (MANDATORY):
Create a comprehensive test report saved as: `./test_results/reports/tree_cell_view_test_report_{timestamp}.md`

**The report MUST include**:

1. **Executive Summary**
   - Total tests in checklist: 29
   - Tests executed: [number - must be 29]
   - Tests skipped: [number - must be 0]
   - Tests passed: [number]
   - Tests failed: [number]
   - Overall pass rate: [percentage]
   - Test duration: [start time] to [end time]

2. **Test Environment**
   - Application URL: https://web-stage.cytoscape.org
   - Browser: [from MCP server]
   - Test execution date/time
   - MCP server: chrome-devtools-mcp
   - Required network: U2OS Multi-scale Integrated Cell Map (276 nodes, 298 edges, loaded from NDEx)

3. **Detailed Test Results** (for EACH test):
   ```
   Section [X]: [Section Name]
   ----------------------------
   Test [X.Y]: [Test Name]
   Status: [PASS/FAIL]
   Duration: [seconds]
   Steps Executed: [number]
   Screenshots: [list of screenshot files]
   Notes: [any relevant observations]
   Errors: [if failed, provide error details]
   ```

4. **Tree View Complete Test Results** (Section 1 - 8 tests)
   - Map display verification
   - Zoom controls functionality
   - Node search for Mitochondrion
   - Nodes table reflects the single selected node
   - Edges table remains unfiltered
   - Sub Network Viewer renders the subsystem
   - Sub Network Viewer node selection matches data-grid label
   - Clearing the selection restores the default state

5. **Cell View Complete Test Results** (Section 2 - 8 tests)
   - Circle packing visualization loads correctly
   - Zoom controls functionality
   - Node search for Mitochondrion
   - Nodes table reflects the single selected node
   - Edges table remains unfiltered
   - Sub Network Viewer renders the subsystem
   - Sub Network Viewer node selection matches data-grid label
   - Clearing the selection restores the default state

6. **SUB NETWORK VIEWER Filters Test Results** (Section 3 - 5 tests)
   - Filter panel display verification
   - Filter toggles functionality
   - Gear icon settings display
   - Integrated interactions filter (hide edges)
   - Re-enable integrated interactions (show edges)

7. **Controls Test Results** (Section 4 - 2 tests)
   - Share button in Tree View
   - Share button in Cell View

8. **Cleanup Test Results** (Section 5 - 2 tests)
   - Network removal
   - Database clearing

9. **Failed Tests Analysis**
   - For each failed test: root cause, error message, screenshot reference
   - Recommendations for fixes
   - Blocking vs. non-blocking failures

10. **Coverage Analysis**
    - Features tested: Tree View complete, Cell View complete, SUB NETWORK VIEWER filters, share controls, cleanup
    - Test coverage percentage: Should be 100% (29/29 tests)
    - Areas not covered: None (all 29 tests are executable)

11. **Recommendations**
11. **Recommendations**
    - Improvements for failed tests
    - Additional tests to consider
    - Known issues discovered

12. **Appendix**
    - List of all screenshots (taken only on failures or explicit exceptions)
    - Console logs from browser (if errors occurred)
    - Network requests that failed (if any)

---

## Execution Guidelines

### What You MUST Do:
✅ Execute ALL 29 tests in the checklist
✅ Follow the exact test order specified
✅ Load U2OS network from NDEx before testing Tree/Cell View features
✅ Capture screenshots ONLY on test failures (exceptions: tests 0.4, 1.1, 2.1)
✅ Document every pass/fail status
✅ Update progress counter after each section
✅ Generate the comprehensive final report
✅ Save the report in `./test_results/reports/`
✅ Continue testing even if individual tests fail
✅ Execute cleanup test (section 5) as the final step
✅ Count tests explicitly before attempting completion

### What YOU MUST NOT Do (VIOLATIONS = TASK FAILURE):
❌ **NEVER** skip tests due to "time constraints" or "efficiency concerns"
❌ **NEVER** summarize or abbreviate test execution
❌ **NEVER** skip verification steps
❌ **NEVER** stop testing after a single failure
❌ **NEVER** execute tests out of order
❌ **NEVER** skip the final report generation
❌ **NEVER** take unnecessary screenshots (only on failures unless explicitly required)
❌ **NEVER** use attempt_completion before all 29 tests are done
❌ **NEVER** assume you've done "enough" testing without counting

⚠️ **If you find yourself thinking "I'll skip this to save time" - STOP. That's a violation.**
⚠️ **If you find yourself thinking "I've done enough testing" - CHECK THE MANDATORY CHECKLIST.**
⚠️ **If you're about to use attempt_completion - COUNT YOUR EXECUTED TESTS FIRST.**

---

## Red Flags - Signs You're About to Violate Requirements

If you catch yourself thinking or doing any of these, STOP immediately:

🚩 "I've tested the critical features, that's enough"
🚩 "The remaining tests are similar to what I've done"
🚩 "This is taking too long, I should wrap up"
🚩 "I'll skip ahead to the cleanup and report"
🚩 "The user will understand if I don't do everything"
🚩 "I can mention the untested areas in recommendations"
🚩 "I've completed the important sections"
🚩 "Testing is taking longer than expected, I should finish"

**These are ALL violations of the explicit requirements. Continue testing until all 29 tests are done.**

---

## Performance Expectations

- **Thoroughness over speed**: Quality and completeness are paramount
- **Expect 30-45 minutes** for full test execution (this is acceptable and expected)
- **Each test should take 1-2 minutes** on average
- **Do not rush**: Proper verification is critical
- **60 minutes is acceptable** if needed for thorough testing
- **Completing in under 25 minutes likely means you skipped tests**

---

## Success Criteria

Your test execution will be considered successful if:
1. ✅ All 29 tests are executed (no skips)
2. ✅ Each test has clear pass/fail status documented
3. ✅ Screenshots are captured on test failures and explicit exceptions (0.4, 1.1, 2.1)
4. ✅ Final report is generated and saved
5. ✅ Report includes all required sections
6. ✅ Test results are reproducible and verifiable
7. ✅ You can explicitly count and verify 29 tests were executed
8. ✅ Section 5 (Cleanup) was executed LAST

**If you cannot verify all 8 criteria above, you have NOT successfully completed the task.**

---

## Important Notes

### Network Requirement
- **Tree View and Cell View tabs ONLY appear for cell map networks**
- Must load "U2OS Multi-scale Integrated Cell Map" from NDEx using UUID: c380c4be-ae09-11f0-a218-005056ae3c32
- Network contains 276 nodes and 298 edges
- If tabs don't appear, the wrong network type was loaded

### Visualization Types
- **Tree View**: Hierarchical tree structure (parent-child relationships)
- **Cell View**: Circle packing (nested circles for compartments)

### Integration Features
- Both views integrate with **SUB NETWORK VIEWER**
- Table data remains accessible in both view modes
- Style panel may show different options per view

### Common Elements
- Nucleus and Cytoplasm visible in Cell View
- Standard controls (fit, share) available in both views
- Users can freely switch between Tree and Cell views

---

## Starting Point

Begin by:
1. Confirming you understand these requirements
2. Loading the test checklist: `tree_cell_view_test_checklist.json`
3. Navigating to: https://web-stage.cytoscape.org
4. Opening NDEx network search (Data > Open Network(s) from NDEx...)
5. Searching for MuSIC network by UUID: c380c4be-ae09-11f0-a218-005056ae3c32
6. Loading the network to enable Tree/Cell View tabs
7. Starting with Section 0 (Setup)
8. Proceeding methodically through each section
9. Updating progress counter after each section
10. NOT stopping until all 29 tests are done

---

## Final Verification Before Completion

**STOP - Before using attempt_completion, verify:**

```
Total Tests in Checklist: 29
Legitimate Skips: 0
Required Tests to Execute: 29

Tests I Executed: ___ (COUNT THEM)
Sections Complete: ___ (LIST THEM: 0, 1, 2, 3, 4, 5)
Section 5 Done Last: YES / NO
Report Generated: YES / NO
Screenshots: Taken only on failures + exceptions (0.4, 1.1, 2.1)

IF ANY NUMBER OR ANSWER IS WRONG, DO NOT COMPLETE. CONTINUE TESTING.
```

---

## Final Note

This is a **focused quality assurance task** for Tree View and Cell View features. The goal is to provide complete confidence in these specific visualization modes through exhaustive testing. **Do not take shortcuts.** Execute every test thoroughly, document every result, and deliver a complete, actionable test report.

**Remember: Your task is NOT complete until:**
- All 29 tests are executed ✓
- The final report is generated and saved ✓
- Test cleanup (Section 5) is completed as the LAST step ✓
- You have explicitly counted and verified all tests are done ✓

**The number 29 is not negotiable. If you executed fewer tests, you failed the task.**

---

**BEGIN TESTING NOW.**
