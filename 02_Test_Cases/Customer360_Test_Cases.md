
# Customer 360 — Test Cases

## 1. Project Overview

**Project:** FinServe Customer 360  
**Application Type:** Fictional Banking Application  
**Testing Type:** Functional, Integration, Data Validation, Negative, Regression  
**Artifact Type:** Synthetic Portfolio Artifact

FinServe Customer 360 is a fictional banking application that provides authorized users with a consolidated view of customer information received from multiple internal source systems.

The purpose of this test suite is to demonstrate a structured approach to test case design for a customer data platform.

---

## 2. Testing Scope

The test cases cover:

- Customer search
- Customer profile validation
- Customer status
- Account information
- Business-rule validation
- Data validation
- Negative testing
- Integration testing
- Regression testing
- Boundary-value testing

---

## 3. Test Case Format

| Field | Description |
|---|---|
| Test Case ID | Unique identifier |
| Scenario | Functionality being validated |
| Preconditions | Conditions required before execution |
| Test Data | Data required for execution |
| Steps | High-level execution steps |
| Expected Result | Expected system behavior |
| Priority | Business/testing priority |

---

# 4. Customer Search Test Cases

## TC-C360-001 — Search Customer Using Valid Customer ID

**Scenario:** Verify that a customer can be searched using a valid Customer ID.

**Preconditions:**
- User is authenticated.
- User has permission to access Customer 360.
- Valid customer record exists.

**Test Data:** Customer ID = CUST10001

**Steps:**
1. Open Customer 360.
2. Enter a valid Customer ID.
3. Select Search.
4. Review the search result.

**Expected Result:**
- Matching customer record is displayed.
- Customer ID is displayed correctly.
- No unrelated customer record is returned.

**Priority:** High

---

## TC-C360-002 — Search Customer Using Invalid Customer ID

**Scenario:** Verify system behavior when an invalid Customer ID is entered.

**Preconditions:**
- User is logged in.

**Test Data:** Customer ID = INVALID999

**Steps:**
1. Open Customer 360.
2. Enter an invalid Customer ID.
3. Select Search.

**Expected Result:**
- No customer record is displayed.
- Appropriate "Customer not found" or equivalent message is displayed.
- Application remains stable.

**Priority:** High

---

## TC-C360-003 — Search Customer Using Blank Customer ID

**Scenario:** Verify validation when the Customer ID field is blank.

**Steps:**
1. Open Customer 360.
2. Leave Customer ID blank.
3. Select Search.

**Expected Result:**
- Search is not executed.
- Appropriate validation message is displayed.

**Priority:** Medium

---

## TC-C360-004 — Search Customer Using Boundary-Length Customer ID

**Scenario:** Validate Customer ID field boundary conditions.

**Steps:**
1. Enter a Customer ID containing the minimum supported length.
2. Search for the customer.
3. Repeat using the maximum supported length.
4. Repeat using a value exceeding the maximum length.

**Expected Result:**
- Supported boundary values are accepted.
- Values exceeding the defined limit are rejected or appropriately validated.

**Priority:** Medium

---

## TC-C360-005 — Search Customer Using Unsupported Characters

**Scenario:** Verify handling of special characters in Customer ID.

**Test Data:** `CUST@#$%`

**Steps:**
1. Enter the value.
2. Select Search.

**Expected Result:**
- Invalid input is rejected or validated.
- Application does not crash.
- Appropriate validation message is displayed.

**Priority:** Medium

---

## TC-C360-006 — Verify Search Result Accuracy

**Scenario:** Verify that returned customer information corresponds to the requested customer.

**Steps:**
1. Search using a valid Customer ID.
2. Review Customer ID, name, date of birth and status.
3. Compare displayed information against the expected test data.

**Expected Result:**
- All displayed customer attributes correspond to the requested customer.
- No cross-customer data is displayed.

**Priority:** Critical

---

# 5. Customer Profile Test Cases

## TC-C360-007 — Verify Customer Name

**Scenario:** Verify customer name displayed in the profile.

**Steps:**
1. Search for a valid customer.
2. Open the customer profile.
3. Review the customer name.

**Expected Result:**
- Customer name is displayed correctly.
- Name matches the expected test data.

**Priority:** High

---

## TC-C360-008 — Verify Customer Date of Birth

**Scenario:** Verify Date of Birth displayed in the customer profile.

**Steps:**
1. Search for a valid customer.
2. Open the profile.
3. Review Date of Birth.

**Expected Result:**
- Date of Birth is displayed correctly.
- Date format follows the defined application standard.

**Priority:** High

---

## TC-C360-009 — Verify Customer Address

**Scenario:** Verify customer address information.

**Steps:**
1. Search for a valid customer.
2. Open customer profile.
3. Review address fields.

**Expected Result:**
- Address information is displayed correctly.
- No unrelated customer's address is displayed.

**Priority:** Medium

---

## TC-C360-010 — Verify Contact Information

**Scenario:** Verify phone number and email information.

**Steps:**
1. Search for a valid customer.
2. Open profile.
3. Review contact information.

**Expected Result:**
- Contact details correspond to the selected customer.
- Data is displayed according to defined formatting rules.

**Priority:** High

---

## TC-C360-011 — Verify Mandatory Customer Attributes

**Scenario:** Verify mandatory customer fields.

**Steps:**
1. Open a customer profile.
2. Review mandatory fields.
3. Check for missing values.

**Expected Result:**
- Mandatory customer attributes contain valid values where required.
- Missing mandatory data is appropriately identified.

**Priority:** High

---

## TC-C360-012 — Verify Profile Data Consistency

**Scenario:** Verify that the same customer attributes remain consistent across relevant sections.

**Steps:**
1. Search for a customer.
2. Note Customer ID and name.
3. Navigate between profile and account sections.
4. Compare displayed customer information.

**Expected Result:**
- Customer information remains consistent across sections.

**Priority:** Critical

---

# 6. Customer Status Test Cases

## TC-C360-013 — Verify Active Customer Status

**Scenario:** Verify display of an active customer.

**Test Data:** Customer status = Active

**Steps:**
1. Search for the customer.
2. Open the customer profile.
3. Review status.

**Expected Result:**
- Status is displayed as Active.
- Status corresponds to the expected test data.

**Priority:** High

---

## TC-C360-014 — Verify Inactive Customer Status

**Scenario:** Verify display of an inactive customer.

**Test Data:** Customer status = Inactive

**Steps:**
1. Search for the customer.
2. Review customer status.

**Expected Result:**
- Status is displayed correctly as Inactive.
- Any applicable business restrictions are correctly represented.

**Priority:** High

---

## TC-C360-015 — Verify Suspended Customer Status

**Scenario:** Verify handling of a suspended customer.

**Test Data:** Customer status = Suspended

**Expected Result:**
- Suspended status is displayed correctly.
- Applicable restrictions or warnings are displayed according to business rules.

**Priority:** Critical

---

## TC-C360-016 — Verify Status Change

**Scenario:** Verify that a changed customer status is reflected correctly.

**Steps:**
1. Identify a customer with a known status.
2. Simulate/update status through the approved test process.
3. Refresh or reload Customer 360.
4. Review status.

**Expected Result:**
- Updated status is displayed correctly.
- Previous status is not incorrectly displayed as current status.

**Priority:** High

---

## TC-C360-017 — Verify Unsupported Status Value

**Scenario:** Verify handling of an unsupported customer status.

**Test Data:** Status = UNKNOWN

**Expected Result:**
- Unsupported status is rejected or handled according to validation rules.
- Application remains stable.

**Priority:** Medium

---

# 7. Account Information Test Cases

## TC-C360-018 — Verify Customer Account List

**Scenario:** Verify accounts associated with a customer.

**Steps:**
1. Search for a valid customer.
2. Open Account Information.
3. Review listed accounts.

**Expected Result:**
- Accounts belonging to the selected customer are displayed.
- No unrelated account is displayed.

**Priority:** Critical

---

## TC-C360-019 — Verify Account Number

**Scenario:** Verify account number display.

**Steps:**
1. Open a customer profile.
2. Navigate to Account Information.
3. Review account number.

**Expected Result:**
- Account number is correct.
- Account number follows defined formatting or masking rules.

**Priority:** Critical

---

## TC-C360-020 — Verify Account Status

**Scenario:** Verify account status.

**Test Data:** Active / Closed / Suspended

**Expected Result:**
- Account status is displayed correctly.
- Status corresponds to the expected test data.

**Priority:** High

---

## TC-C360-021 — Verify Multiple Accounts

**Scenario:** Verify customer with multiple accounts.

**Steps:**
1. Search for a customer having multiple accounts.
2. Review the account list.
3. Compare against expected test data.

**Expected Result:**
- All eligible accounts are displayed.
- Accounts are not duplicated.
- No unrelated account is displayed.

**Priority:** High

---

## TC-C360-022 — Verify Customer With No Active Accounts

**Scenario:** Verify customer having no active accounts.

**Expected Result:**
- Customer profile remains accessible.
- Account section displays an appropriate empty-state message.
- Application does not fail.

**Priority:** Medium

---

# 8. Data Validation Test Cases

## TC-C360-023 — Verify Customer ID Data Accuracy

**Scenario:** Validate Customer ID received from the source system.

**Steps:**
1. Identify expected Customer ID in synthetic source data.
2. Search for the customer in Customer 360.
3. Compare the displayed Customer ID.

**Expected Result:**
- Customer ID matches the expected source value.

**Priority:** Critical

---

## TC-C360-024 — Verify Customer Name Data Accuracy

**Scenario:** Validate customer name between source and Customer 360.

**Expected Result:**
- Customer name matches expected source data.
- No unintended truncation or transformation occurs.

**Priority:** High

---

## TC-C360-025 — Verify Date Format

**Scenario:** Verify consistent date formatting.

**Steps:**
1. Open customer profile.
2. Review date fields.
3. Compare against expected format.

**Expected Result:**
- Date is displayed using the defined format.
- Invalid or malformed dates are not displayed as valid dates.

**Priority:** Medium

---

## TC-C360-026 — Verify Null or Missing Optional Data

**Scenario:** Verify handling of missing optional customer information.

**Expected Result:**
- Optional missing fields are displayed appropriately.
- Application does not display misleading or unrelated data.

**Priority:** Medium

---

## TC-C360-027 — Verify Duplicate Customer Records

**Scenario:** Verify handling of duplicate customer records.

**Steps:**
1. Search using a Customer ID associated with synthetic duplicate test data.
2. Review returned records.

**Expected Result:**
- Duplicate handling follows the defined business rule.
- Records are not incorrectly merged or lost.

**Priority:** High

---

# 9. Negative Test Cases

## TC-C360-028 — Verify Session Without Authentication

**Scenario:** Verify unauthorized access to Customer 360.

**Steps:**
1. Attempt to access Customer 360 without authentication.

**Expected Result:**
- User is redirected to authentication or access is denied.
- Customer information is not exposed.

**Priority:** Critical

---

## TC-C360-029 — Verify Unauthorized User Access

**Scenario:** Verify access control for a user without Customer 360 permission.

**Steps:**
1. Log in using a synthetic unauthorized test user.
2. Attempt to access Customer 360.

**Expected Result:**
- Access is denied according to authorization rules.
- Customer information is not displayed.

**Priority:** Critical

---

## TC-C360-030 — Verify Invalid Search Input

**Scenario:** Verify handling of invalid search input.

**Test Data:** Special characters / unsupported format / excessive length

**Expected Result:**
- Input is validated.
- No unexpected application error occurs.

**Priority:** High

---

## TC-C360-031 — Verify Search With Leading and Trailing Spaces

**Scenario:** Verify handling of spaces around Customer ID.

**Test Data:** `  CUST10001  `

**Expected Result:**
- System either trims spaces according to requirements or displays an appropriate validation message.
- Search behavior is consistent.

**Priority:** Medium

---

## TC-C360-032 — Verify Repeated Search Requests

**Scenario:** Verify application behavior when multiple searches are performed sequentially.

**Steps:**
1. Search for Customer A.
2. Search for Customer B.
3. Search again for Customer A.

**Expected Result:**
- Correct information is displayed for each search.
- Previous customer's information is not retained incorrectly.

**Priority:** High

---

# 10. Integration Test Cases

## TC-C360-033 — Verify Source-to-Customer360 Data Flow

**Scenario:** Verify that customer information received from a source system is reflected in Customer 360.

**Steps:**
1. Prepare synthetic source customer data.
2. Process the data through the defined integration flow.
3. Search for the customer in Customer 360.
4. Compare selected attributes.

**Expected Result:**
- Expected customer data is available in Customer 360.
- Key attributes are accurately transferred.

**Priority:** Critical

---

## TC-C360-034 — Verify Handling of Missing Source Data

**Scenario:** Verify integration behavior when an expected source attribute is unavailable.

**Expected Result:**
- Missing data is handled according to defined rules.
- Valid attributes continue to be processed.
- Application remains stable.

**Priority:** High

---

## TC-C360-035 — Verify Source Data Update Propagation

**Scenario:** Verify that a source data update is reflected in Customer 360.

**Steps:**
1. Identify a customer.
2. Update a synthetic source attribute.
3. Execute the required processing flow.
4. Search for the customer in Customer 360.

**Expected Result:**
- Updated value is reflected after successful processing.
- Previous value is not incorrectly displayed as current.

**Priority:** Critical

---

## TC-C360-036 — Verify Integration Failure Handling

**Scenario:** Verify behavior when source-system processing fails.

**Expected Result:**
- Failure is handled gracefully.
- Incomplete data is not incorrectly presented as successfully processed data.
- Appropriate error/status information is available to authorized users or support processes.

**Priority:** High

---

# 11. Regression Test Cases

## TC-C360-037 — Regression of Customer Search

**Scenario:** Verify that customer search continues to work after application changes.

**Expected Result:**
- Valid customer searches continue to return correct results.
- Invalid searches continue to be handled correctly.

**Priority:** Critical

---

## TC-C360-038 — Regression of Customer Profile

**Scenario:** Verify customer profile after application enhancement.

**Expected Result:**
- Customer attributes remain available and accurate.
- Existing functionality is not negatively affected.

**Priority:** High

---

## TC-C360-039 — Regression of Account Information

**Scenario:** Verify account information after release.

**Expected Result:**
- Customer-account relationships remain correct.
- Account information is displayed correctly.

**Priority:** Critical

---

## TC-C360-040 — End-to-End Regression

**Scenario:** Verify the complete Customer 360 journey.

**Steps:**
1. Authenticate as an authorized user.
2. Search for a valid customer.
3. Open customer profile.
4. Review customer details.
5. Review customer status.
6. Review account information.
7. Navigate back to search.
8. Search for another customer.

**Expected Result:**
- Complete user journey works successfully.
- Customer data remains accurate throughout the journey.
- No regression is observed in core functionality.

**Priority:** Critical

---

# 12. Test Case Priority Classification

| Priority | Meaning |
|---|---|
| Critical | Failure could expose incorrect customer information, prevent core functionality, or significantly affect business operations |
| High | Important business functionality that should work correctly for release |
| Medium | Important supporting functionality with lower business impact |
| Low | Minor functionality or usability-related validation |

---

# 13. Test Design Techniques Demonstrated

The test suite demonstrates the use of:

- Positive testing
- Negative testing
- Boundary-value analysis
- Input validation
- Business-rule validation
- Data validation
- Integration testing
- End-to-end testing
- Regression testing
- Risk-based prioritization

---

# 14. QA Perspective

For a Customer 360 platform, the highest-risk areas are:

1. Customer identification accuracy
2. Customer-to-account relationship accuracy
3. Data consistency across integrated systems
4. Customer status accuracy
5. Prevention of cross-customer data exposure
6. Handling of incomplete or inconsistent source data
7. Regression of critical customer search and profile functionality

Testing should therefore prioritize data accuracy and customer information integrity in addition to functional behavior.

---

## Disclaimer

This is a **fictional/synthetic portfolio project** created for demonstration of QA analysis and test-case design skills.

It does not contain client names, proprietary requirements, confidential information, production data, customer information, internal screenshots, source code, or internal system details.
