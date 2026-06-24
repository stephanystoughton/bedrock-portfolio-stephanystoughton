# SESSION REPORT

Charter: Investigate the login, product browsing, cart, and checkout flow as the problem_user account, focusing on functional differences from the standard_user account.

Tester: Stephany Holt
Date: June 24, 2026
Timebox: 60 minutes (actual: 60 minutes)
Target: https://www.saucedemo.com
Account(s) used: standard_user, problem_user

## TEST IDEAS EXECUTED:

1. Logged in with the standard_user account to understand expected behavior.
2. Logged in with the problem_user account and compared results.
3. Tested product browsing and navigation.
4. Added products to the cart.
5. Removed products from the cart.
6. Started the checkout process.
7. Refreshed pages during shopping actions.
8. Compared product images and product names.
9. Tested cart persistence.
10. Reviewed checkout overview information.

## BUGS FOUND:

- bug-report-1.md: Incorrect product images displayed for problem_user.

## ISSUES OBSERVED (not yet filed):

Some product images displayed by problem_user did not match the product names. This behavior could confuse customers and lead to incorrect purchasing decisions.

## TEST DATA USED:

Accounts:
- standard_user
- problem_user

Products:
- Sauce Labs Backpack
- Sauce Labs Bike Light
- Sauce Labs Bolt T-Shirt
- Sauce Labs Onesie

Checkout data:
- First Name: Test
- Last Name: User
- ZIP Code: 33543

## COVERAGE NOTES:

- Tested thoroughly: Login, browsing, cart actions, image validation, checkout start.
- Barely touched: Mobile testing, browser compatibility, performance testing, error_user account.

## SUMMARY:

The session identified a defect involving incorrect product images while using the problem_user account. The standard_user account behaved as expected. Future sessions should focus on checkout defects and performance-related issues using the other specialized accounts.