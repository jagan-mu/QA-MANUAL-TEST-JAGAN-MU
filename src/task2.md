# Scenario
You are testing the login functionality of a web application. The login page contains:
- Username field
- Password field  
- Login button
- An error message displayed for invalid login attempts
- A "Remember Me" checkbox
- A "Forgot Password" link

# Task
Write 5-10 test cases for the login functionality, covering both positive and negative scenarios.

Use the following template for each test case:

## Test Case Template
- **Test Case ID:** A unique identifier for the test case
- **Title:** A brief description of the test case
- **Pre-conditions:** Any setup required before running the test
- **Test Steps:** Step-by-step instructions to execute the test
- **Expected Result:** The expected outcome for the test
- **Actual Result:** Leave this blank (to be filled during actual execution)
- **Priority:** Assign a priority (High/Medium/Low)
- **Remarks:** Any additional comments

# Solution
TODO: Your solution goes below
<!-- <Write your solution here> -->

<Login Functionality Test Cases

Test Case 1

Test Case ID: TC-LOGIN-001
Title: Successful login with valid credentials
Pre-conditions: User has a registered account with valid credentials; user is on the login page
Test Steps:

Navigate to the login page
Enter a valid username in the username field
Enter the correct password in the password field
Click the Login button


Expected Result: User is authenticated and redirected to the dashboard/home page; no error messages are displayed
Actual Result:
Priority: High
Remarks: This is the core happy-path scenario; must pass before other tests are meaningful


Test Case 2

Test Case ID: TC-LOGIN-002
Title: Login fails with an incorrect password
Pre-conditions: User has a registered account; user is on the login page
Test Steps:

Navigate to the login page
Enter a valid username in the username field
Enter an incorrect password in the password field
Click the Login button


Expected Result: Login is rejected; an appropriate error message is displayed (e.g., "Invalid username or password"); user remains on the login page
Actual Result:
Priority: High
Remarks: Error message should not reveal which field is incorrect to prevent user enumeration attacks


Test Case 3

Test Case ID: TC-LOGIN-003
Title: Login fails when username does not exist
Pre-conditions: User is on the login page
Test Steps:

Navigate to the login page
Enter a username that is not registered in the system
Enter any password
Click the Login button


Expected Result: Login is rejected; a generic error message is displayed (e.g., "Invalid username or password"); user remains on the login page
Actual Result:
Priority: High
Remarks: The error message should be identical to TC-LOGIN-002 to avoid leaking whether a username exists


Test Case 4

Test Case ID: TC-LOGIN-004
Title: Login fails when both username and password fields are empty
Pre-conditions: User is on the login page
Test Steps:

Navigate to the login page
Leave both the username and password fields empty
Click the Login button


Expected Result: Form submission is blocked; a validation error is displayed for both required fields (e.g., "Username is required", "Password is required")
Actual Result:
Priority: High
Remarks: Validation may be client-side or server-side; test both; no network request should fire on empty submission


Test Case 5

Test Case ID: TC-LOGIN-005
Title: Login fails when only the username is provided
Pre-conditions: User is on the login page
Test Steps:

Navigate to the login page
Enter a valid username in the username field
Leave the password field empty
Click the Login button


Expected Result: Form submission is blocked; a validation error is shown specifically for the password field
Actual Result:
Priority: Medium
Remarks: Counterpart test TC-LOGIN-006 should verify the reverse (password only, no username)


Test Case 6

Test Case ID: TC-LOGIN-006
Title: "Remember Me" persists the session after browser restart
Pre-conditions: User has valid credentials; user is on the login page; browser cookies are cleared
Test Steps:

Navigate to the login page
Enter valid credentials
Check the "Remember Me" checkbox
Click the Login button
Verify successful login
Close the browser completely and reopen it
Navigate back to the application URL


Expected Result: User is still logged in without being prompted to enter credentials again
Actual Result:
Priority: Medium
Remarks: Also verify the negative case — logging in without "Remember Me" should not persist the session after the browser is closed


Test Case 7

Test Case ID: TC-LOGIN-007
Title: "Forgot Password" link navigates to the password reset page
Pre-conditions: User is on the login page
Test Steps:

Navigate to the login page
Click the "Forgot Password" link


Expected Result: User is redirected to the password reset page; a field to enter a registered email/username is displayed
Actual Result:
Priority: Medium
Remarks: Verify the link is keyboard-accessible and has a proper href attribute (not #)


Test Case 8

Test Case ID: TC-LOGIN-008
Title: Account is locked after multiple consecutive failed login attempts
Pre-conditions: User has a registered account; user is on the login page
Test Steps:

Navigate to the login page
Enter a valid username and an incorrect password
Click the Login button
Repeat steps 2–3 until the maximum allowed attempts are reached (e.g., 5 times)


Expected Result: After exceeding the threshold, the account is temporarily locked; an appropriate message is displayed (e.g., "Your account has been locked. Please try again later or reset your password.")
Actual Result:
Priority: High
Remarks: Verify that the lockout also triggers a notification email to the registered user; lockout duration/policy should match security requirements


Test Case 9

Test Case ID: TC-LOGIN-009
Title: Password field masks input characters
Pre-conditions: User is on the login page
Test Steps:

Navigate to the login page
Click on the password field
Type any characters into the password field


Expected Result: Each typed character is masked (displayed as ● or *); the actual characters are not visible in the UI
Actual Result:
Priority: High
Remarks: If a "show/hide password" toggle exists, verify it works correctly and re-masks on toggle-off


Test Case 10

Test Case ID: TC-LOGIN-010
Title: Login form is protected against SQL injection
Pre-conditions: User is on the login page
Test Steps:

Navigate to the login page
Enter a SQL injection payload in the username field (e.g., ' OR '1'='1)
Enter any value in the password field
Click the Login button


Expected Result: Login is rejected; a generic error message is displayed; the application does not expose database errors or grant unauthorised access
Actual Result:
Priority: High
Remarks: Repeat with the payload in the password field as well; extend to XSS payloads (e.g., <script>alert(1)</script>) as a separate security test case>
