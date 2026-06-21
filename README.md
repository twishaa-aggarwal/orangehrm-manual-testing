# 🧪 Manual Testing Project – OrangeHRM Web Application

> A structured manual testing project covering functional, boundary, negative, and security test scenarios on the OrangeHRM demo HR application.

---

## 📌 Project Overview

| Field | Details |
| **Application** | OrangeHRM – Open Source HR Management Software |
| **Application URL** | https://opensource-demo.orangehrmlive.com |
| **Test Type** | Manual Testing |
| **Modules Tested** | Login, Employee Management (PIM), Leave Management |
| **Total Test Cases** | 46 |
| **Total Bugs Found** | 1 (High Severity) |
| **Prepared By** | Twisha Aggarwal |
| **Tools Used** | MS Excel, Chrome DevTools, GitHub |

---

## 🗂️ Repository Structure

```
orangehrm-manual-testing/
│
├── OrangeHRM_Manual_Testing_TwishaAggarwal.xlsx   # Test cases, bug report & summary dashboard
└── README.md                                       # Project documentation
```

---

## 📋 Test Coverage Summary

| Module | Test Cases | Pass | Fail |
|---|---|---|---|
| Login | 17 | 16 | 1 |
| Employee Management (PIM) | 15 | 15 | 0 |
| Leave Management | 14 | 14 | 0 |
| **Total** | **46** | **45** | **1** |

---

## 🔍 What Was Tested

### 1. Login Module (17 Test Cases)
- Valid and invalid credentials
- Empty and whitespace-only fields
- Password masking and copy-paste behaviour
- Maximum character boundary testing
- SQL Injection attempt (`' OR '1'='1'`)
- Forgot password link navigation
- Logout functionality
- **Session expiry after logout** ← Bug found here
- Login button hover UI validation
- Case sensitivity of username

### 2. Employee Management / PIM (15 Test Cases)
- Add employee with valid and invalid data
- Mandatory field validation on create and edit
- Duplicate Employee ID and duplicate username detection
- Search by full name and partial name
- Edit employee details
- Single and bulk delete
- Post-delete verification in search
- Profile photo upload (valid and invalid file types)

### 3. Leave Management (14 Test Cases)
- Apply leave with valid future dates
- Date validation (From Date after To Date)
- Missing Leave Type validation
- Leave application on past dates, weekends, and public holidays
- Zero leave balance restriction
- Same-day leave application
- Negative/zero value in duration field
- Edit pending leave before approval
- Cancel a pending leave request
- View leave entitlements and leave list

---

## 🐛 Bug Report

### BUG_001 – Session Not Invalidated After Logout

| Field | Details |
|---|---|
| **Bug ID** | BUG_001 |
| **Related Test Case** | TC_LGN_17 |
| **Module** | Login |
| **Severity** | High |
| **Priority** | High |
| **Status** | Open |
| **Bug Type** | Security – Session Management |

**Summary:**
After a user logs out, the browser Back button restores the authenticated session without requiring re-authentication — indicating server-side session invalidation is not implemented.

**Steps to Reproduce:**
1. Navigate to `https://opensource-demo.orangehrmlive.com`
2. Login with Username: `Admin` / Password: `admin123`
3. Verify you land on the Dashboard
4. Click the user avatar (top right) → Click **Logout**
5. Confirm you are redirected to the Login page
6. Press the browser **Back button** (`Alt + ←`)
7. Observe the page that loads

**Expected Result:**
User remains on the Login page. Dashboard is not accessible without re-authentication.

**Actual Result:**
The Dashboard loads successfully without requiring credentials. The session was not invalidated server-side on logout.

**Impact:**
On shared or public computers, any person with access to the browser after logout can access the account without credentials — a session management security vulnerability.

---

## 📊 Test Deliverables

The Excel workbook (`OrangeHRM_Manual_Testing_TwishaAggarwal.xlsx`) contains three sheets:

| Sheet | Contents |
|---|---|
| **Summary Dashboard** | Project info, tester details, module-wise pass/fail metrics |
| **Test Cases** | 46 test cases with TC ID, module, steps, test data, expected result, actual result, status, severity |
| **Bug Reports** | Detailed bug log with reproduction steps, severity, priority, and status |

---

## 🧠 Concepts & Techniques Applied

- **STLC** (Software Testing Life Cycle) — followed end-to-end from test planning to defect reporting
- **Black Box Testing** — tested functionality without knowledge of internal code
- **Boundary Value Analysis** — tested edge values for input fields (max characters, zero duration)
- **Negative Testing** — invalid inputs, wrong credentials, missing mandatory fields
- **Security Testing** — SQL injection, XSS payload injection, session management validation
- **Defect Life Cycle** — bugs logged with severity, priority, status, and reproduction steps

---

## 🛠️ How to Use This Repository

1. Download `OrangeHRM_Manual_Testing_TwishaAggarwal.xlsx`
2. Open the **Summary Dashboard** sheet for a quick overview
3. Go to **Test Cases** sheet to review all 46 test scenarios
4. Go to **Bug Reports** sheet to view the identified defect

---

## 👩‍💻 Author

**Twisha Aggarwal**
B.Tech Computer Science Engineering – 3rd Year
📧 twishaaggarwal96@gmail.com
🔗 [GitHub](https://github.com/twishaa-aggarwal)
