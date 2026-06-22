Bedrock Bug Report Template (v3.2)
Title:
Contact form shows successful submission but provides no persistent confirmation or email when valid form is submitted.
Environment:
macOS 14.2.1 Sonoma
Chrome 121.0.6167.85
Bedrock Demo App build 11.4.2
Tested on 2026-04-15 between 14:22 and 14:28 EST
User state: Not logged in / anonymous user
Network: Corporate WiFi, no VPN
URL: https://bedrock-demo.example.com
Preconditions:
User is on the Bedrock Demo App contact form.
User is not logged in.
Contact form fields are visible: Name, Email, Subject, Message, and Submit button.
User has valid test data ready.
Steps to Reproduce:
Open https://bedrock-demo.example.com.
Navigate to the contact form.
Enter Test User in the Name field.
Enter test@example.com in the Email field.
Enter Hello in the Subject field.
Enter This is a test. in the Message field.
Click Submit.
Observe the form behavior after submission.
Wait 60 seconds.
Check the inbox for test@example.com.
Open the browser Network tab and check the POST request to /api/contact.
Expected Result:
After submitting a valid contact form, the user should see a persistent confirmation message stating that the submission was received. If the app is expected to send a confirmation email, the user should receive that email at the submitted address.
Actual Result:
The form clears all fields immediately. A green checkmark appears for about half a second and then disappears. No confirmation message remains on the screen. The page does not redirect. No confirmation email arrives after 60 seconds. The Network tab shows the POST request to /api/contact returned 200 OK with response body {"status": "queued"}.
Severity:
Medium.
The form appears to submit successfully, but the user receives no lasting confirmation on screen and no confirmation email. This can cause confusion and may lead users to submit the form multiple times because they cannot confirm whether their message was actually received.
Reproducibility:
Always reproducible.
Tested 3 times with valid contact form data, including a second attempt with a different valid email address. The same behavior occurred every time.
Evidence:
In a real ticket, I would attach:
Screenshot of the completed contact form before clicking Submit.
Screen recording showing the form clearing and the green checkmark disappearing.
Screenshot of the page after submission showing no persistent confirmation message.
Screenshot of the Network tab showing POST /api/contact returned 200 OK.
Screenshot of the response body: {"status": "queued"}.
Screenshot or note showing no confirmation email received after 60 seconds.