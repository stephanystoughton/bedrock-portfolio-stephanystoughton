Bedrock Bug Report Template (v3.2)

Title

Contact form shows no persistent confirmation message or email after successful submission.

Environment

macOS 14.2.1 Sonoma
Chrome 121.0.6167.85
Bedrock Demo App build 11.4.2
Tested on 2026-04-15 between 14:22 and 14:28 EST
Anonymous user (not logged in)
Corporate WiFi, no VPN
URL: https://bedrock-demo.example.com

Preconditions

User is on the Bedrock Demo App contact form page.
User is not logged in.
Contact form fields (Name, Email, Subject, Message) are visible and editable.
Inbox for test@example.com is accessible for verification.

Steps to Reproduce

Open https://bedrock-demo.example.com.
Open the Contact form.
Enter “Test User” in the Name field.
Enter “test@example.com” in the Email field.
Enter “Hello” in the Subject field.
Enter “This is a test.” in the Message field.
Click the Submit button.
Wait 60 seconds.
Check the inbox for test@example.com.
Open Chrome DevTools and review the Network tab entry for the POST request to /api/contact.

Expected Result

A persistent confirmation message should remain visible on the page indicating that the contact form submission was received successfully.
A confirmation email should be delivered to the submitted email address.

Actual Result

The form clears all fields immediately after submission. A green checkmark appears for approximately half a second and then disappears. No confirmation message remains visible on the page. The page does not redirect. No confirmation email arrives after waiting 60 seconds. The Network tab shows a POST request to /api/contact returning HTTP 200 OK with the response body:

{“status”:“queued”}

Severity

Medium

The submission appears successful, but users receive no lasting confirmation that their message was received. This can cause confusion and lead to duplicate submissions, although the application remains usable and no data loss is visible.

Reproducibility

Always (3/3 attempts)

The issue occurred on three consecutive tests, including one test using a different valid email address.

Evidence

The following evidence would be attached in a real defect ticket:

Screenshot of the completed contact form before submission.
Screen recording showing:
Form submission
Green checkmark appearing briefly
Confirmation indicator disappearing
Screenshot of the page after submission showing no persistent confirmation message.
Screenshot of Chrome DevTools Network tab showing POST /api/contact returned HTTP 200 OK.
Screenshot of the response body:
    {“status”:“queued”}
Screenshot of the email inbox showing no confirmation email received after 60 seconds.

⸻

Reflection

Claude identified several areas where my report could be more precise. I agreed with the feedback on the title, preconditions, expected result, and severity because those sections could be written more clearly and with less ambiguity. I updated the title to make it shorter, improved the preconditions, and separated the expected result into clear outcomes for both the on-screen confirmation and the email confirmation. I partially accepted the severity feedback by adding more justification for the Medium rating, but I did not reference an internal Bedrock severity scale because that information was not provided in the scenario. I rejected the suggestion about attaching actual screenshots because the exercise explicitly states that attachments are not available and asks only for a description of the evidence that would be included in a real ticket.