## Claude's Response

[Submit valid credentials (a correctly formatted email and a password meeting complexity rules) and verify the user is redirected to /dashboard.
Submit valid credentials and verify the POST request is sent to /api/v1/auth/login with the correct email and password values in the request body.
Submit a valid email with an incorrect password and verify the inline error message "Invalid email or password." appears below the form.
Submit an unregistered email address with any password and verify the inline error message "Invalid email or password." appears below the form.
Submit with the Email field empty and the Password field populated, and verify the server returns an error resulting in the "Invalid email or password." message (since there is no client-side validation on Email).
Submit with the Password field empty and the Email field populated, and verify the form handles the empty submission (server-side behavior applies, as the Password field has no client-side minimum-length enforcement noted for blocking submission).
Enter a password of exactly 8 characters (boundary minimum) meeting complexity rules and verify a successful login redirects to /dashboard.
Enter a password of exactly 64 characters (boundary maximum) meeting complexity rules and verify a successful login redirects to /dashboard.
Enter a password of 65 characters and verify the server rejects it and the "Invalid email or password." error appears (no client-side character cap is specified, so this tests server enforcement).
Enter a password of 8+ characters containing only letters (no numbers) and verify the server rejects it due to complexity rules, displaying "Invalid email or password."
Enter a password of 8+ characters containing only numbers (no letters) and verify the server rejects it due to complexity rules, displaying "Invalid email or password."
Confirm the "Sign In" button is enabled when both fields are empty (per spec: "enabled at all times") and that clicking it still submits the POST request.
Click the "Forgot Password?" link and verify a "Coming soon" message is displayed.
Submit incorrect credentials 5 times from the same IP address and verify the 6th attempt within the 15-minute window is rate-limited (e.g., a distinct server error or block response is returned).
After being rate-limited, wait the full 15-minute window and verify that a subsequent login attempt from the same IP is accepted again (rate limit resets correctly).


Note on out-of-scope dependencies: All 15 scenarios above are grounded in elements and behaviors explicitly defined in the spec. No scenarios were flagged. One nuance worth noting: Scenario 9 (65-character password) and Scenario 6 (empty password submission) assume no client-side blocking exists beyond what the spec states — the spec only mentions the server enforces rules, so these are valid server-side tests. If a future version adds client-side length enforcement or a "required field" HTML attribute to the Password input, those scenarios would shift from server tests to client tests.Paste Claude's full response here]

## ChatGPT's Response

Verify that a valid email and valid password between 8 and 64 characters with at least one letter and one number submits successfully and redirects the user to /dashboard.

2. Verify that clicking Sign In sends a POST request to /api/v1/auth/login with the entered Email and Password values.

3. Verify that the Sign In button remains enabled when both Email and Password are empty.

4. Verify that submitting an empty Email and empty Password shows the inline error message: "Invalid email or password."

5. Verify that the Email field accepts a normal email string such as user@test.com without client-side validation blocking the input.

6. Verify that the Email field accepts an invalid email string such as not-an-email, submits it, and relies on the server to reject it.

7. Verify that a password with exactly 8 characters, including at least one letter and one number, can be submitted.

8. Verify that a password with exactly 64 characters, including at least one letter and one number, can be submitted.

9. Verify that a password shorter than 8 characters fails login.

10. Verify that a password longer than 64 characters fails login.

11. Verify that a password containing only letters fails because the server requires at least one number.

12. Verify that a password containing only numbers fails because the server requires at least one letter.

13. Verify that incorrect credentials show one inline error message below the form with the exact text "Invalid email or password."

14. Verify that after 5 failed login attempts from the same IP within 15 minutes, additional failed attempts are rate-limited.

15. Verify that clicking Forgot Password? shows a "Coming soon" message.

Note: I did not include scenarios for Remember Me, social login, two-factor authentication, CAPTCHA, password visibility toggle, or biometric login because they are explicitly out of scope.aste ChatGPT's full response here]

## Gemini's Response

[## Manual Test Scenarios
 1. Verify that entering a valid email format, a valid password (8–64 characters with at least one letter and one number), and clicking "Sign In" successfully authenticates and redirects the user to /dashboard.
 2. Verify that clicking the "Forgot Password?" link displays a "Coming soon" message.
 3. Verify that entering an invalid email format (e.g., missing "@" or domain) and valid password triggers the inline error "Invalid email or password." below the form after clicking "Sign In".
 4. Verify that entering a valid email but a password shorter than 8 characters triggers the inline error "Invalid email or password." below the form upon submission.
 5. Verify that entering a valid email but a password longer than 64 characters triggers the inline error "Invalid email or password." below the form upon submission.
 6. Verify that entering a valid email and a password exactly 8 characters long (including at least one letter and one number) allows a successful login and redirect.
 7. Verify that entering a valid email and a password exactly 64 characters long (including at least one letter and one number) allows a successful login and redirect.
 8. Verify that entering a valid email and an 8–64 character password containing only letters (no numbers) triggers the inline error "Invalid email or password." below the form.
 9. Verify that entering a valid email and an 8–64 character password containing only numbers (no letters) triggers the inline error "Invalid email or password." below the form.
 10. Verify that leaving the "Email" input blank and entering a valid password triggers the inline error "Invalid email or password." below the form upon submission.
 11. Verify that entering a valid email and leaving the "Password" input blank triggers the inline error "Invalid email or password." below the form upon submission.
 12. Verify that the "Sign In" button remains enabled and clickable even when both the "Email" and "Password" inputs are completely empty.
 13. Verify that making 5 consecutive failed login attempts within 15 minutes from the same IP address triggers the rate-limiting behavior on the 6th attempt.
 14. Verify that a 6th login attempt from a different IP address is allowed and successfully processes even if a previous IP address has been rate-limited.
 15. This scenario would apply only if a [Show/Hide Password toggle icon] existed: verify that clicking the toggle reveals the plain text of the password input.
### Out-of-Scope Elements Note
Scenario 15 was explicitly flagged because it depends on a password visibility toggle, a UI element that is not present in this specification and is explicitly listed as out of scope. All other 14 scenarios strictly adhere to the exact UI elements ("Email" input, "Password" input, "Sign In" button, and "Forgot Password?" link) and behavioral constraints provided in BedrockShop Login Form v1.0.Paste Gemini's full response here]

Summary
Claude’s Response Evaluation

VALID. This scenario fits the spec because successful login should redirect the user to /dashboard.
VALID. This checks that the Sign In action submits a POST request to /api/v1/auth/login with the entered credentials.
VALID. This is a useful failure test because incorrect credentials should show the inline error message.
VALID. This is a useful negative test because an unregistered email should fail login and show the same error.
VALID. This fits the spec because the Email field accepts any string and server-side behavior should handle invalid or missing email values.
VALID. This fits the spec because the Password field accepts strings, and the server enforces password rules.
VALID. This is a boundary test for the minimum valid password length of 8 characters.
VALID. This is a boundary test for the maximum valid password length of 64 characters.
VALID. This is a negative boundary test for a password longer than the allowed maximum.
VALID. This tests the server complexity rule requiring at least one number.
VALID. This tests the server complexity rule requiring at least one letter.
VALID. This fits the spec because the Sign In button is enabled at all times.
VALID. This fits the spec because clicking Forgot Password? should show a “Coming soon” message.
VALID. This tests the rate limit rule of 5 failed attempts per 15 minutes per IP address.
VALID. This is a useful edge case because it checks whether the rate limit resets after the 15-minute window.

Claude Totals:
VALID: 15
HALLUCINATED: 0
GENERIC: 0
DUPLICATE: 0

ChatGPT’s Response Evaluation

VALID. This fits the success behavior because valid credentials should redirect the user to /dashboard.
VALID. This checks that clicking Sign In sends a POST request to /api/v1/auth/login with the Email and Password values.
VALID. This fits the spec because the Sign In button is enabled at all times.
VALID. This is a useful negative test for submitting empty fields and expecting the inline error message.
VALID. This fits the spec because the Email field accepts any string and has no client-side validation.
VALID. This checks that invalid email format is accepted by the field but rejected by the server.
VALID. This is a boundary test for the minimum valid password length of 8 characters.
VALID. This is a boundary test for the maximum valid password length of 64 characters.
VALID. This is a negative boundary test for passwords shorter than 8 characters.
VALID. This is a negative boundary test for passwords longer than 64 characters.
VALID. This tests the password complexity rule requiring at least one number.
VALID. This tests the password complexity rule requiring at least one letter.
VALID. This checks the exact inline error message shown after failed login.
VALID. This tests the rate limit rule after 5 failed attempts within 15 minutes from the same IP.
VALID. This fits the spec because the Forgot Password? link should show a “Coming soon” message.

ChatGPT Totals:
VALID: 15
HALLUCINATED: 0
GENERIC: 0
DUPLICATE: 0

Gemini’s Response Evaluation

VALID. This fits the success behavior because valid credentials should redirect the user to /dashboard.
VALID. This fits the spec because clicking Forgot Password? should display a “Coming soon” message.
VALID. This checks server-side validation for invalid email format and the correct inline error message.
VALID. This checks that a password shorter than 8 characters fails.
VALID. This checks that a password longer than 64 characters fails.
VALID. This is a boundary test for the minimum valid password length of 8 characters.
VALID. This is a boundary test for the maximum valid password length of 64 characters.
VALID. This tests the password complexity rule requiring at least one number.
VALID. This tests the password complexity rule requiring at least one letter.
VALID. This checks login behavior when the Email input is blank.
VALID. This checks login behavior when the Password input is blank.
VALID. This fits the spec because the Sign In button remains enabled at all times.
VALID. This tests the rate limit rule after 5 failed login attempts within 15 minutes from the same IP address.
VALID. This fits the “per IP address” rule because it checks that rate limiting applies to one IP and does not automatically block a different IP.
HALLUCINATED. This scenario references a Show/Hide Password toggle icon, which does not exist in the spec and is explicitly listed as not in scope, even though Gemini correctly flagged it as conditional.

Gemini Totals:
VALID: 14
HALLUCINATED: 1
GENERIC: 0
DUPLICATE: 0

Summary

Claude and ChatGPT produced the most VALID scenarios, with 15 valid scenarios each. Gemini produced 14 valid scenarios and 1 hallucinated scenario. Gemini hallucinated the most because it included a password visibility toggle, which is specifically listed as not in scope. However, Gemini was also the most likely to flag its own out-of-scope suggestion because it wrote that the scenario would apply only if the Show/Hide Password toggle existed. Claude and ChatGPT had some very similar scenarios, especially around valid login, password boundaries, failed login errors, and rate limiting, but they were not identical word-for-word. This shows that AI tools often pattern-match the same obvious test ideas when the feature spec is very constrained. One thing I learned is that AI can produce useful test coverage, but I still need to compare every scenario against the spec because even confident-sounding suggestions can include features that do not exist.