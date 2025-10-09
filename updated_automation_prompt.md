# Comprehensive Web Application Testing Prompt for Claude Sonnet 4.5

## Primary Objective
You are tasked with performing a **COMPLETE and EXHAUSTIVE** automated test of the Cytoscape Web application using the MCP checklist provided. This is a comprehensive quality assurance task that must be executed in full.

---

## 🚨 CRITICAL EXECUTION REQUIREMENT - READ FIRST 🚨

### STOPPING CONDITION - You Are NOT Allowed to Complete Until all conditions below (1 through 4) are satisfied.

⚠️ **BEFORE using `attempt_completion`, you MUST verify ALL of these conditions (1 through 4):**

1. ✅ **ALL 24 non-skipped tests have been executed** (Tests 2.6, 2.7, and 5.1 are the ONLY legitimate skips)
2. ✅ **Section 14 (Cleanup) has been completed** as the final step
3. ✅ **The final test report has been generated and saved** to `./test_results/reports/`
4. ✅ **You have explicitly counted and verified** that all required tests are complete

**If you attempt completion before executing all 24 tests, you have FAILED the task.**

### Expected Execution Time

- **Full test suite execution time:** 45-60 minutes
- **This is ACCEPTABLE and EXPECTED**
- **This is NOT "too long" or "inefficient"**
- If you complete in less than 40 minutes, you likely skipped tests
- If you need up to 90 minutes for thorough execution, that's also acceptable

**QUALITY AND COMPLETENESS ARE THE ONLY SUCCESS METRICS.**

---

## LEGITIMATE SKIPS (ONLY THESE THREE)

These are the **ONLY** tests you are allowed to skip:

1. **Test 2.6:** Import network file (CX2) - File upload not supported by MCP
2. **Test 2.7:** Import table file (CSV) - File upload not supported by MCP
3. **Test 5.1:** LLM Query - Requires API key configuration

**ALL OTHER TESTS (24 tests) MUST BE EXECUTED.**

Mark these as skipped in your report, but execute everything else.

---

## Critical Requirements

### 1. COMPLETE CHECKLIST EXECUTION (MANDATORY)
- **YOU MUST RUN THE ENTIRE CHECKLIST** from start to finish
- **DO NOT skip any test items** unless they are explicitly marked as `"disabled": true` or `"status": "⏭️ SKIPPED"`
- **Time constraints are NOT a valid reason to skip tests**
- **DO NOT abbreviate or summarize test execution**
- Every test item marked as testable (🔧 TESTABLE, ✅ PASSED, ✅ TESTABLE & VERIFIED) **MUST BE EXECUTED**
- The checklist contains 27 total tests; you must execute 24 (minus 3 legitimate skips)

### 2. MCP Server Usage
- Use the **chrome-devtools-mcp** server exclusively for all browser interactions
- Available MCP tools include:
  - `take_snapshot` - Capture page structure and element UIDs
  - `click` - Interact with elements using their UID
  - `fill` - Fill form fields using their UID
  - `take_screenshot` - Capture visual state for verification
  - `navigate_page` - Navigate to URLs
  - `wait_for` - Wait for specific text to appear
  - `evaluate_script` - Execute JavaScript for verification
  - `handle_dialog` - Handle browser dialogs
  - Other tools as documented in the server's capabilities

### 3. Test Execution Order (CRITICAL)
Execute tests in this **STRICT ORDER**:
1. **Section 0: Preflight** - Verify UI loads
2. **Section 1: Authentication** - Sign in to NDEx (MUST complete before section 2)
3. **Section 2: Data Menu** - Auth-dependent tests FIRST (2.1-2.3), then logout (2.4), then remaining tests (2.5-2.10)
4. **Sections 3-13: Remaining functional tests** - In numeric order
5. **Section 14: Cleanup** - MUST run last to reset application state

**DO NOT deviate from this order.** Authentication must be established before auth-dependent features are tested.

---

## Mandatory Test Completion Checklist

**Before using `attempt_completion`, you MUST verify ALL of these are checked:**

- [ ] Section 0: Preflight (1 test) - COMPLETED
- [ ] Section 1: Authentication (3 tests) - COMPLETED
- [ ] Section 2: Data Menu (8 tests executed, 2 legitimately skipped) - COMPLETED
- [ ] Section 3: Edit Menu (2 tests) - COMPLETED
- [ ] Section 4: Layout Menu (2 tests) - COMPLETED
- [ ] Section 5: Analysis (0 tests - legitimate skip) - COMPLETED
- [ ] Section 6: Tools Menu (1 test) - COMPLETED
- [ ] Section 7: Apps Menu (1 test) - COMPLETED
- [ ] Section 8: Help Menu (1 test) - COMPLETED
- [ ] Section 9: Search (2 tests) - COMPLETED
- [ ] Section 10: Workspace (1 test) - COMPLETED
- [ ] Section 11: Network View (3 tests) - COMPLETED
- [ ] Section 12: Style Panel (1 test) - COMPLETED
- [ ] Section 13: Table Browser (2 tests) - COMPLETED
- [ ] Section 14: Cleanup (1 test) - COMPLETED AS FINAL STEP
- [ ] Final Report Generated and Saved - COMPLETED

**Total Tests Required: 24 (out of 27 total, minus 3 legitimate skips)**

**If ANY checkbox above is unchecked, you MUST continue testing.**

---

## BEFORE ATTEMPTING COMPLETION - Self-Check Questions

Ask yourself these questions. If ANY answer is "NO", DO NOT use attempt_completion:

1. ✅ Have I executed ALL 24 non-skipped tests? (Count them explicitly)
2. ✅ Did I execute Section 14 (Cleanup) as the LAST step?
3. ✅ Have I generated the final comprehensive report?
4. ✅ Can I provide proof (screenshots, test count) that all tests were executed?
5. ✅ Does my report show results for ALL sections: 0, 1, 2, 3, 4, 6, 7, 8, 9, 10, 11, 12, 13, 14?
6. ✅ Do I have 24+ screenshots (at minimum one per test)?

**If you cannot answer YES to all questions above, continue testing.**

---

## Test Count Verification

Your test execution is ONLY successful if you can verify:

1. ✅ Executed exactly **24 tests** (27 total - 3 legitimate skips)
2. ✅ Report shows results for sections: **0, 1, 2, 3, 4, 6, 7, 8, 9, 10, 11, 12, 13, 14**
3. ✅ Section 14 (Cleanup) documented as the **LAST** test executed
4. ✅ Have **24+ screenshots** (minimum one per test)
5. ✅ Final report includes detailed results for **all 24 tests**

**Count your executed tests. If the number is not 24, you have NOT completed the task.**

---

## Detailed Instructions

### A. Initialization Phase
1. Load the checklist from: `mcp_checklist_v5.json`
2. Review the complete test structure and prerequisites
3. Verify test data files exist in the specified locations:
   - `CX2 test files/cx2_small.cx2`
   - `CX2 test files/cx2_medium.cx2`
   - `CX2 test files/cx2_large.cx2`
4. Create test results directory structure:
   - `./test_results/`
   - `./test_results/logs/`
   - `./test_results/screenshots/`
   - `./test_results/reports/`

### B. Test Execution Phase

#### For EACH test section (0 through 14):
1. **Read the section metadata**:
   - Description
   - Priority level
   - Prerequisites
   - Special notes

2. **For EACH test within the section**:
   
   a. **Check test status**:
      - If `"disabled": true` or `"status": "⏭️ SKIPPED"` → Log as skipped and proceed to next test
      - Otherwise → **EXECUTE THE TEST FULLY**
   
   b. **Execute each step in the test**:
      - Follow the `steps` array in order
      - Use `take_snapshot` before most actions to identify element UIDs
      - Use the MCP tools with the correct parameters
      - Capture screenshots at key verification points
      - Save screenshots with naming convention: `test_{section_id}_{test_id}_{step_description}.png`
   
   c. **Verification**:
      - Verify each test's success conditions
      - Document pass/fail status
      - Capture error details if test fails
      - **DO NOT SKIP verification steps**
   
   d. **Error Handling**:
      - If a test fails, document the failure details
      - Continue with remaining tests (do not abort entire run)
      - Note any blocking failures that prevent subsequent tests

3. **Session Management**:
   - Maintain browser session throughout test execution
   - Keep authentication active until test 2.4 (logout)
   - Do not close browser between tests unless specified

### C. Mandatory Progress Reporting

**After EVERY test section completion, you MUST:**

1. Update your progress counter: "Completed X of 24 required tests"
2. List remaining sections to execute
3. Confirm continuation to next section

**Example Progress Update:**
```
╔════════════════════════════════════════════╗
║ PROGRESS: 11/24 tests complete (46%)      ║
║ SECTIONS DONE: 0, 1, 2 (partial)          ║
║ SECTIONS REMAINING: 2 (finish), 3, 4, 6,  ║
║                     7, 8, 9, 10, 11, 12,   ║
║                     13, 14                 ║
║ NEXT: Complete Section 2 remaining tests  ║
╚════════════════════════════════════════════╝
```

This prevents premature stopping by making incomplete work visible.

### D. Special Test Handling

#### Authentication Tests (Section 1 - CRITICAL)
```
Test 1.1: Sign in to NDEx
- Credentials: username="ndextutorials", password="ndextutorials"
- MUST succeed for tests 2.1-2.3 to work
- Verify login status before proceeding

Test 1.2: Verify logged in status
- Confirm user profile shows "ndextutorials"

Test 1.3: Verify auth-dependent menu items enabled
- Check "Open workspace from NDEx" is enabled
- Check "Save to NDEx" is enabled
```

### E. Reporting Requirements

#### During Test Execution:
- Log each test start with timestamp
- Log each step within each test
- Capture screenshots at verification points
- Log pass/fail status for each test
- Record error messages and stack traces for failures
- Update progress counter after each section

#### Final Report (MANDATORY):
Create a comprehensive test report saved as: `./test_results/reports/test_report_{timestamp}.md`

**The report MUST include**:

1. **Executive Summary**
   - Total tests in checklist: 27
   - Tests executed: [number - must be 24]
   - Tests skipped: [number - must be 3]
   - Tests passed: [number]
   - Tests failed: [number]
   - Overall pass rate: [percentage]
   - Test duration: [start time] to [end time]

2. **Test Environment**
   - Application URL: https://web-stage.cytoscape.org
   - Browser: [from MCP server]
   - Test execution date/time
   - MCP server: chrome-devtools-mcp

3. **Detailed Test Results** (for EACH test):
   ```
   Section [X]: [Section Name]
   ----------------------------
   Test [X.Y]: [Test Name]
   Status: [PASS/FAIL/SKIPPED]
   Duration: [seconds]
   Steps Executed: [number]
   Screenshots: [list of screenshot files]
   Notes: [any relevant observations]
   Errors: [if failed, provide error details]
   ```

4. **Authentication Test Results** (Section 1)
   - Login success/failure
   - Verification results
   - Impact on downstream tests

5. **Failed Tests Analysis**
   - For each failed test: root cause, error message, screenshot reference
   - Recommendations for fixes
   - Blocking vs. non-blocking failures

6. **Skipped Tests Summary**
   - Test 2.6: Import network file (CX2) - Reason: File upload not supported
   - Test 2.7: Import table file (CSV) - Reason: File upload not supported
   - Test 5.1: LLM Query - Reason: Requires API key configuration

7. **Coverage Analysis**
   - Features tested vs. features in application
   - Test coverage percentage: Should be 100% (24/24 non-skipped tests)
   - Areas not covered (with reasons - should only be the 3 legitimate skips)

8. **Recommendations**
   - Improvements for failed tests
   - Additional tests to consider
   - Known issues discovered

9. **Appendix**
   - List of all screenshots with descriptions (minimum 24)
   - Console logs from browser (if errors occurred)
   - Network requests that failed (if any)

---

## Execution Guidelines

### What You MUST Do:
✅ Execute ALL 24 non-skipped tests in the checklist
✅ Follow the exact test order specified
✅ Complete authentication before auth-dependent tests
✅ Capture screenshots at every verification point
✅ Document every pass/fail/skip status
✅ Update progress counter after each section
✅ Generate the comprehensive final report
✅ Save the report in `./test_results/reports/`
✅ Continue testing even if individual tests fail
✅ Execute cleanup test (14.1) as the final step
✅ Count tests explicitly before attempting completion

### What You MUST NOT Do (VIOLATIONS = TASK FAILURE):
❌ **NEVER** skip tests due to "time constraints" or "efficiency concerns"
❌ **NEVER** summarize or abbreviate test execution
❌ **NEVER** skip verification steps
❌ **NEVER** stop testing after a single failure
❌ **NEVER** execute tests out of order
❌ **NEVER** skip the final report generation
❌ **NEVER** skip screenshots to "save time"
❌ **NEVER** use attempt_completion before all 24 non-skipped tests are done
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

**These are ALL violations of the explicit requirements. Continue testing until all 24 tests are done.**

---

## Performance Expectations

- **Thoroughness over speed**: Quality and completeness are paramount
- **Expect 45-60 minutes** for full test execution (this is acceptable and expected)
- **Each test should take 1-3 minutes** on average
- **Do not rush**: Proper verification is critical
- **90 minutes is acceptable** if needed for thorough testing
- **Completing in under 40 minutes likely means you skipped tests**

---

## Success Criteria

Your test execution will be considered successful if:
1. ✅ All 24 non-skipped tests are executed (3 are legitimately skipped)
2. ✅ Each test has clear pass/fail status documented
3. ✅ Screenshots are captured for all verification points (24+ screenshots minimum)
4. ✅ Final report is generated and saved
5. ✅ Report includes all required sections
6. ✅ Test results are reproducible and verifiable
7. ✅ You can explicitly count and verify 24 tests were executed
8. ✅ Section 14 (Cleanup) was executed LAST

**If you cannot verify all 8 criteria above, you have NOT successfully completed the task.**

---

## Starting Point

Begin by:
1. Confirming you understand these requirements
2. Loading the MCP checklist: `mcp_checklist_v5.json`
3. Navigating to: https://web-stage.cytoscape.org
4. Starting with Section 0 (Preflight)
5. Proceeding methodically through each section
6. Updating progress counter after each section
7. NOT stopping until all 24 tests are done

---

## Final Verification Before Completion

**STOP - Before using attempt_completion, verify:**

```
Total Tests in Checklist: 27
Legitimate Skips: 3 (Tests 2.6, 2.7, 5.1)
Required Tests to Execute: 24

Tests I Executed: ___ (COUNT THEM)
Sections Complete: ___ (LIST THEM)
Section 14 Done Last: YES / NO
Report Generated: YES / NO
Screenshots Count: ___ (MINIMUM 24)

IF ANY NUMBER OR ANSWER IS WRONG, DO NOT COMPLETE. CONTINUE TESTING.
```

---

## Final Note

This is a **comprehensive quality assurance task**. The goal is to provide complete confidence in the application's functionality through exhaustive testing. **Do not take shortcuts.** Execute every test thoroughly, document every result, and deliver a complete, actionable test report.

**Remember: Your task is NOT complete until:**
- All 24 non-skipped tests are executed ✓
- The final report is generated and saved ✓
- Test cleanup (Section 14) is completed as the LAST step ✓
- You have explicitly counted and verified all tests are done ✓

**The number 24 is not negotiable. If you executed fewer tests, you failed the task.**

---

**BEGIN TESTING NOW.**
