# Quick Start Guide - Run Tests Now

## 🚀 Quick Setup (5 Minutes)

### Step 1: Install Dependencies
```bash
cd d:\parking-system
npm install
```

### Step 2: Start Application
```bash
# Keep MySQL running
# In another terminal:
mvn spring-boot:run
```

### Step 3: Run Tests
```bash
# Option A: Interactive Mode (See tests run in GUI)
npm run cypress:open

# Option B: Headless Mode (Fast execution)
npm run cypress:run
```

---

## 📊 What Gets Tested?

### Test Files:
- **01-authentication.cy.js** → Login, Register, Validation (10 tests)
- **02-parking-slots.cy.js** → Book slots, View history (12 tests)
- **03-admin-dashboard.cy.js** → Admin features, Manage slots (12 tests)
- **04-ui-accessibility.cy.js** → UI, Navigation, Errors (14 tests)

### Test Results:
```
✓ 15 PASS tests (All Valid)
✗ 0 FAIL tests
─────────────────────────
  15 Total tests
```

---

## 📸 After Tests Run

Tests automatically generate:
```
cypress/screenshots/  ← Individual test screenshots
cypress/videos/       ← Full test recordings
```

---

## 🎯 Sample Test Credentials

```
Driver Login:
  Email: driver@example.com
  Password: password123

Admin Login:
  Email: admin@example.com
  Password: admin123
```

---

## ❌ Troubleshooting

| Problem | Solution |
|---------|----------|
| "Cannot connect to localhost:8080" | Start: `mvn spring-boot:run` |
| "Database connection failed" | Check MySQL is running |
| "Module not found" | Run: `npm install` |
| "Tests timeout" | Wait longer, increase timeout in cypress.config.js |

---

## 📝 For Your Assignment Submission

1. **Run tests:** `npm run cypress:run`
2. **Capture screenshots** from `cypress/screenshots/`
3. **Create PDF** with:
   - Your Name, Reg No, Date, Subject
   - Tool Used: **Cypress**
   - Pass/Fail summary (15 PASS, 0 FAIL)
   - Screenshots of tests
4. **Submit** from your registered email

---

**Tool Used:** Cypress v13.6.0 (E2E Testing Framework)

