# BUG REPORT

## 1. Title

Incorrect product images are displayed for problem_user

## 2. Environment

Website: https://www.saucedemo.com
Browser: Chrome
Device: MacBook
Account: problem_user

## 3. Preconditions

User is on the Sauce Demo login page.

## 4. Steps to Reproduce

1. Open https://www.saucedemo.com
2. Login as problem_user
3. Enter password secret_sauce
4. Click Login
5. Observe product images on the inventory page

## 5. Expected Result

Each product should display the correct image associated with the product name.

## 6. Actual Result

Several products display images that do not match their product names.

## 7. Severity

Medium

## 8. Priority

Medium

## 9. Notes / Evidence

The issue was observed using problem_user but not standard_user.