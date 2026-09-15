# SauceDemo – Manual Testing Project

End-to-end manual testing of **SauceDemo** (https://www.saucedemo.com), a demo e-commerce web application. This repository contains the complete set of QA deliverables produced for one full test cycle: test planning, scenario and test case design, requirement traceability, execution results, defect logging, and supporting evidence.

---

## Project Overview

| | |
|---|---|
| **Application Under Test** | SauceDemo (Swag Labs) |
| **URL** | https://www.saucedemo.com |
| **Testing Type** | Manual – Functional, Negative, UI, Regression, End-to-End |
| **Test Design Techniques** | Equivalence Partitioning, Boundary Value Analysis |
| **Environment** | Windows 11 (64-bit), Google Chrome (latest stable) |
| **Tools** | Microsoft Excel (test artefacts), Snipping Tool (evidence) |
| **Prepared By** | Subham – QA Engineer |
| **Test Cycle** | Cycle 1 – Manual Test Execution |

---

## Scope

**In scope**

- Login – valid and invalid credentials, account lockout, error messaging
- Product Listing (Inventory) – product data display, cart badge, navigation menu
- Product Details – navigation, add/remove to cart, data consistency
- Sorting – Name (A–Z, Z–A) and Price (low–high, high–low)
- Shopping Cart – add, remove, quantity display, navigation, persistence
- Checkout – mandatory field validation, order overview, tax and total calculation
- Order Confirmation – completion message, cart reset, return-to-home flow
- Session handling – logout and browser back-button behaviour
- UI consistency across special demo user profiles

**Out of scope**

- Performance and load testing (beyond observation with `performance_glitch_user`)
- Security penetration testing, API testing, and database validation
- Cross-browser and mobile responsiveness testing
- Payment gateway integration (checkout is a simulated flow)

---

## Repository Structure

```
SauceDemo_Manual_Project/
├── README.md
├── Test_Plan.xlsx                  # Scope, strategy, environment, entry/exit criteria, risks
├── Test_Scenarios.xlsx             # 18 high-level test scenarios mapped to requirements
├── Test_Cases.xlsx                 # 45 detailed test cases with steps, data and results
├── RTM.xlsx                        # Requirement Traceability Matrix (14 requirements)
├── Test_Execution_Report.xlsx      # Execution log and module-wise pass/fail summary
├── Defect_Report.xlsx              # Logged defects with severity, priority and status
└── Screenshots/                    # Execution and defect evidence
```

---

## Test Deliverables

| Document | Description |
|---|---|
| **Test_Plan.xlsx** | Objective, scope, test strategy, environment, entry and exit criteria, deliverables, risks and schedule. |
| **Test_Scenarios.xlsx** | 18 scenarios across Login, Product Listing, Product Details, Sorting, Cart, Checkout, Order Confirmation, Session and UI modules, each mapped to a requirement ID with priority. |
| **Test_Cases.xlsx** | 45 test cases with preconditions, step-by-step actions, test data, expected results, actual results, status and linked defect IDs. |
| **RTM.xlsx** | Forward and backward traceability from 14 requirements to scenarios and test cases, with coverage status. |
| **Test_Execution_Report.xlsx** | Execution log per test case plus module-wise breakdown of pass/fail counts. |
| **Defect_Report.xlsx** | Defect log with summary, reproduction steps, expected vs actual result, severity, priority, status, environment and screenshot reference. |

---

## Test Data

All accounts use the password `secret_sauce`.

| Username | Purpose |
|---|---|
| `standard_user` | Primary account for positive and end-to-end flows |
| `locked_out_user` | Account lockout verification |
| `problem_user` | Image and UI defect verification |
| `performance_glitch_user` | Page-load delay observation |
| `error_user` | Cart action error verification |
| `visual_user` | Layout and alignment verification |

---

## Execution Summary

| Metric | Value |
|---|---|
| Total test cases | 45 |
| Passed | 40 |
| Failed | 5 |
| Blocked / Not executed | 0 |
| Pass rate | 88.9% |
| Defects logged | 5 |

**Module-wise results**

| Module | Total | Passed | Failed |
|---|---|---|---|
| Login | 6 | 6 | 0 |
| Product Listing | 7 | 5 | 2 |
| Product Details | 4 | 4 | 0 |
| Sorting | 5 | 5 | 0 |
| Cart | 6 | 5 | 1 |
| Checkout | 8 | 7 | 1 |
| Order Confirmation | 3 | 3 | 0 |
| End-to-End | 3 | 2 | 1 |
| Session / Logout | 3 | 3 | 0 |

---

## Defect Summary

| Defect ID | Module | Summary | Severity | Priority | Status |
|---|---|---|---|---|---|
| DEF-001 | Product Listing | All products display the same incorrect image for `problem_user` | Medium | P2 | Open |
| DEF-002 | Performance | Products page takes ~5+ seconds to load after login for `performance_glitch_user` | Low | P3 | Open (by design – demo data) |
| DEF-003 | Checkout | Zip/Postal Code field accepts special characters with no format validation | Low | P4 | Open (demo app limitation) |
| DEF-004 | Cart | `Remove` button on the Cart page behaves inconsistently for `error_user` | High | P2 | Open |
| DEF-005 | Product Listing (UI) | Product images inconsistently sized and aligned for `visual_user` | Medium | P3 | Open |

Severity distribution: 1 High, 2 Medium, 2 Low.

---

## Requirement Coverage

| Coverage status | Count |
|---|---|
| Total requirements | 14 |
| Fully covered | 11 |
| Partially covered (open defects) | 3 |

Partially covered requirements are REQ-08 (cart operations), REQ-12 (end-to-end purchase journey) and REQ-14 (UI rendering consistency), each blocked by an open defect rather than by missing test coverage.

---

## Testing Approach

1. **Smoke testing** – verified login, add to cart and checkout were stable before deeper testing.
2. **Functional testing** – validated each feature against expected business rules.
3. **Negative testing** – invalid credentials, blank mandatory fields, invalid input classes.
4. **Boundary Value Analysis and Equivalence Partitioning** – applied to login and checkout form fields.
5. **UI testing** – layout, labels, alignment and image rendering, including special demo profiles.
6. **Regression testing** – re-verified unaffected areas after repeated sessions and state resets.
7. **End-to-end testing** – complete purchase journey from login through order confirmation.

---

## Key Observations

- The core purchase journey (login → product listing → cart → checkout → order confirmation) is stable for `standard_user`, with all High priority path test cases passing.
- Checkout total calculations (item total, tax, grand total) were verified as accurate.
- Session handling is enforced correctly; browser back navigation after logout does not restore an authenticated session.
- All logged defects are reproducible only under specific demo user profiles or relate to known limitations of the demo application, and are documented accordingly.

---

## How to Use This Repository

1. Start with **Test_Plan.xlsx** for scope, strategy and environment details.
2. Review **Test_Scenarios.xlsx** for high-level coverage, then **Test_Cases.xlsx** for step-level detail.
3. Use **RTM.xlsx** to confirm requirement-to-test-case traceability.
4. Refer to **Test_Execution_Report.xlsx** for results and **Defect_Report.xlsx** for logged issues.
5. Supporting evidence for passed cases and defects is available in the **Screenshots/** folder.

---

## Author

**Subham** — QA Engineer
Manual Testing | Test Design | Defect Reporting | Requirement Traceability
