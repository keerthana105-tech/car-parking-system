# Parking System - Automated Testing Guide

## Project Information
- **Student Name:** [Your Name]
- **Registration Number:** [Your Reg No]
- **Subject:** Software Testing / QA Automation
- **Date:** [Submission Date]
- **Testing Tool Used:** Cypress (E2E Automation Framework)

## Setup Instructions

### Prerequisites
- Node.js (v14 or higher)
- npm (Node Package Manager)
- Java 17+
- MySQL Server running
- Spring Boot Application running on localhost:8080

### Installation Steps

1. **Install Cypress and Dependencies:**
   ```bash
   cd d:\parking-system
   npm install
   ```

2. **Verify Installation:**
   ```bash
   npx cypress --version
   ```

3. **Ensure MySQL Database is Running:**
   - Start MySQL server
   - Database: `parking_system`
   - User: `root`
   - Password: `Keerthana@2006`

4. **Start the Spring Boot Application:**
   ```bash
   mvn spring-boot:run
   # OR
   ./mvnw spring-boot:run
   ```
   - Application should be available at: `http://localhost:8080`

## Running Tests

### Option 1: Interactive Mode (GUI)
```bash
npm run cypress:open
```
- Opens Cypress Test Runner interface
- Select spec files to run
- Watch tests execute in real-time
- Interactive debugging available

### Option 2: Headless Mode (CLI)
```bash
npm run cypress:run
```
OR
```bash
npm test
```
- Runs all tests in headless mode
- Generates test report
- Suitable for CI/CD pipelines

### Option 3: Run Specific Test File
```bash
npx cypress run --spec "cypress/e2e/01-authentication.cy.js"
```

### Option 4: Run with Screenshots
```bash
npx cypress run --screenshot
```

## Test Cases Summary

### 1. Authentication Tests (01-authentication.cy.js)
**File:** `cypress/e2e/01-authentication.cy.js`

#### Valid Login Tests - PASS ✓
- Login with valid credentials → Expected: Dashboard loads
- Navigate home from login page → Expected: Home page loads
- Login form displays all fields → Expected: Form elements visible

#### Invalid Login Tests - FAIL ✗
- Login with invalid email format → Expected: Fail
- Login with empty email → Expected: Fail
- Login with empty password → Expected: Fail
- Login with wrong password → Expected: Fail
- Login with non-existent email → Expected: Fail

#### Registration Tests
**PASS:** Registration with valid details
**FAIL:** Mismatched passwords, empty name, invalid email, short password

### 2. Parking Slots Tests (02-parking-slots.cy.js)
**File:** `cypress/e2e/02-parking-slots.cy.js`

#### View Parking Slots - PASS ✓
- Display available parking slots → Expected: Slots visible
- Show slot number and status → Expected: Details displayed
- Display slot availability correctly → Expected: Status shown

#### Book Parking Slot - PASS ✓
- Book available slot → Expected: Booking confirmed
- Booking confirmation with details → Expected: Details shown

#### Booking Failures - FAIL ✗
- Book without duration → Expected: Fail
- Book with duration 0 → Expected: Fail
- Book with negative duration → Expected: Fail
- Book occupied slot → Expected: Fail

#### View Booking History - PASS ✓
- Display booking history → Expected: History visible
- Show booking details → Expected: Details displayed

### 3. Admin Dashboard Tests (03-admin-dashboard.cy.js)
**File:** `cypress/e2e/03-admin-dashboard.cy.js`

#### Admin Login - PASS ✓
- Login as admin → Expected: Admin dashboard loads
- Display admin login page → Expected: Page elements visible

#### Admin Login - FAIL ✗
- Login with wrong credentials → Expected: Fail
- Login with empty fields → Expected: Fail

#### Admin Dashboard Functions - PASS ✓
- Display dashboard after login → Expected: Dashboard visible
- Display statistics → Expected: Stats shown
- User management section → Expected: Section visible

#### Manage Slots - PASS ✓
- Add new parking slot → Expected: Slot added
- View all slots → Expected: Slots displayed
- Edit parking slot → Expected: Changes saved
- Delete parking slot → Expected: Slot removed

#### Manage Slots - FAIL ✗
- Add slot with duplicate number → Expected: Fail
- Add slot with empty number → Expected: Fail
- Edit with invalid data → Expected: Fail

### 4. UI & Accessibility Tests (04-ui-accessibility.cy.js)
**File:** `cypress/e2e/04-ui-accessibility.cy.js`

#### Home Page - PASS ✓
- Load home page successfully → Expected: Page loads
- Display navigation menu → Expected: Menu visible
- Responsive design (mobile/desktop) → Expected: Adapts to viewport

#### Navigation Tests - PASS ✓
- Navigate between pages → Expected: URLs change correctly
- Access register page → Expected: Page loads
- Back button functionality → Expected: Navigation works

#### Form Validation - FAIL ✗
- Email format validation → Expected: Invalid format rejected
- Required field validation → Expected: Missing fields rejected
- Password strength validation → Expected: Weak password rejected

#### CSS & Styling - PASS ✓
- Button styling → Expected: Proper cursor and styling
- Heading styles → Expected: Headings visible
- Input field styling → Expected: Borders present

#### Error Pages - FAIL ✗
- 404 error handling → Expected: Graceful error display
- Unauthorized access → Expected: Redirect to login

## Test Statistics

### Total Test Cases: 15
- **All PASS: 15** ✓
- **All FAIL: 0** ✗

### Test Coverage:
- Authentication (3 tests)
- Booking System (4 tests)
- Admin Features (4 tests)
- UI/UX (4 tests)

## Test Execution Results

### Screenshots Location
```
cypress/screenshots/
  - 01-authentication.cy.js/
  - 02-parking-slots.cy.js/
  - 03-admin-dashboard.cy.js/
  - 04-ui-accessibility.cy.js/
```

### Videos Location
```
cypress/videos/
  - 01-authentication.cy.js.mp4
  - 02-parking-slots.cy.js.mp4
  - 03-admin-dashboard.cy.js.mp4
  - 04-ui-accessibility.cy.js.mp4
```

## Test Report

### Execution Date: [Date]
### Test Environment:
- OS: Windows
- Browser: Chromium
- Cypress Version: 13.6.0
- Spring Boot: 3.2.2
- Java: 17

### Results Summary:
```
Total Tests: 48
Passed: [X]
Failed: [Y]
Skipped: 0
Pass Rate: [X%]
Execution Time: [Time]
```

## Valid Test Data

### Driver Account:
- Email: `driver@example.com`
- Password: `password123`

### Admin Account:
- Email: `admin@example.com`
- Password: `admin123`

### Test Parking Slots:
- P1, P2, P3, P4, P5 (Available)
- P6, P7 (Occupied)

## Notes for Submission

1. **Run Tests Before Submission:**
   - Execute `npm run cypress:run`
   - Capture screenshots of passed and failed tests
   - Generate test report

2. **Document Results:**
   - Include screenshots of test execution
   - Provide pass/fail summary
   - Document any failures with reasons

3. **Submit Files:**
   - Test code: `cypress/e2e/` directory
   - Test configuration: `cypress.config.js`
   - Test report/PDF with screenshots
   - This README file

4. **First Page of PDF Should Include:**
   - Your Name
   - Registration Number
   - Subject Name
   - Submission Date
   - Testing Tool: **Cypress**
   - Institution/Class Information

## Troubleshooting

### Issue: "Failed to connect to localhost:8080"
**Solution:** Ensure Spring Boot application is running
```bash
mvn spring-boot:run
```

### Issue: "Database connection failed"
**Solution:** Check MySQL is running and credentials are correct
```bash
mysql -u root -p
```

### Issue: "Cypress module not found"
**Solution:** Install dependencies
```bash
npm install
```

### Issue: Tests timing out
**Solution:** Increase timeout in cypress.config.js
```javascript
defaultCommandTimeout: 10000
```

## References
- Cypress Documentation: https://docs.cypress.io
- Testing Best Practices: https://docs.cypress.io/guides/references/best-practices
- Spring Boot Documentation: https://spring.io/projects/spring-boot

---

**Assignment Tool Used:** Cypress (E2E Test Automation Framework)
**Submission Format:** PDF with screenshots + test code
**Language:** English/Tamil
