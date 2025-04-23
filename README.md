# BCU-Contoso-Timetable-API-
Contoso-Timetable-API
BCU Contoso Timetable API Test Results Documentation
Functional Test Results
Project: BCU Contoso Timetable API
Test Status: Passed & Failed Results (Some Tests Failed Due to Date Format Issues)
Summary of Test Results:
Total Tests Run: 2000
Passed Tests: 1600
Failed Tests: 400 (Due to date format issues)
Skipped Tests: 0
Total Duration: 1 minute 58 seconds
Average Response Time: 61 ms
Failed Tests Details:
1. PUT Update Student Name
• Issue: The enrollmentDate field did not pass the format validation.
• Expected Result: The enrollmentDate should be in ISO 8601 format.
• Actual Result:
o Expected: 2024-08-31T17:32:25.316Z
o Received: 2024-08-31T17:32:25.3161066
• Test Status: Failed
Steps to Reproduce:
1. Perform a PUT request to update the student name (e.g., PUT
/updateStudentName).
2. Inspect the enrollmentDate field in the response.
3. The field should return in ISO 8601 format but fails validation.
Passed Tests Details:
1. GET Fetch Courses from Page
• Expected Result: The response should return status 200 and contain the
expected keys.
• Actual Result: Passed – The response is correct.
2. GET Get Course Details by ID 1
• Expected Result: The response should return status 200 and contain the
expected keys.
• Actual Result: Passed – The response is correct.
3. PUT Update Course Name by ID
• Expected Result: The course name should be updated successfully.
• Actual Result: Passed – The course name was updated.
4. GET Fetch Events from Page
• Expected Result: The response should return status 200 and contain the
expected keys.
• Actual Result: Passed – The response is correct.
Next Steps:
1. Fix Date Format Issue: The primary issue is with the incorrect format of
enrollmentDate. It should follow the ISO 8601 format.
2. Rerun Tests: After fixing the date format, rerun the tests to ensure the issue is
resolved.
Positive Test Results Summary
Project: BCU Contoso Timetable API
Test Date: April 21, 2025
Tester Name: Waleola Samuel Mayowa
Objective: Validate the correct behavior of the API with valid input, ensuring all
expected outcomes match the API specifications.
Test Scenarios & Results:
1. Fetch Courses from Page 1
• Request: GET https://localhost:51106/course/page/1
• Expected Result: The response should return 50 courses with details like id,
name, description, code, startDate, etc., and status 200 OK.
• Test Result: Passed
2. Fetch Courses from Page 2
• Request: GET https://localhost:51106/course/page/2
• Expected Result: The response should return 50 courses with details, and
status 200 OK.
• Test Result: Passed
3. Get Course Details by ID 1
• Request: GET https://localhost:57399/course/1
• Expected Result: The response should return course details including name,
description, startDate, endDate, and enrolledStudents.
• Test Result: Passed
BCU Contoso Timetable API - Error Handling Test Results
Test Summary:
• Project: BCU Contoso Timetable API
• Test Status: Passed & Failed Results (Error Handling for Missing and Invalid
Fields)
• Test Date: April 21, 2025
• Tester Name: Waleola Samuel Mayowa
• Objective: Validate the correct handling of errors by the API for missing, invalid,
or malformed data.
Test Scenarios & Results:
1. Missing Required Field (PUT Update Student Name)
• Request: PUT https://localhost:51947/student/1/name?newName=
• Expected Result: API should return status 400 Bad Request.
• Test Result: Passed – The system returned 400 Bad Request with the correct
error message.
2. Invalid Data Format (PUT Update Event Date)
• Request: PUT https://localhost:51947/event/2/name?newName=jack
• Expected Result: API should return status 400 Bad Request for invalid data
format.
• Test Result: Passed – The system returned 400 Bad Request when invalid data
was supplied.
BCU Contoso Timetable API - Integration Test Results
Test Summary:
• Project: BCU Contoso Timetable API
• Test Date: April 21, 2025
• Tester Name: Waleola Samuel Mayowa
• Objective: Validate the integration of different endpoints to ensure proper flow
of data between the front-end and back-end systems.
Test Scenarios & Results:
1. GET Fetch Courses from Page 1 and Page 2
• Request: GET https://localhost:51106/course/page/1
• Expected Result: The response should return status 200 OK and a list of
courses.
• Test Result: Passed – Correct data returned for both pages with proper
pagination.
2. PUT Update Course Name by ID
• Request: PUT
https://localhost:57399/course/1/name?newName=updatedCourse
• Expected Result: The course name should be updated successfully.
• Test Result: Passed
BCU Contoso Timetable API - SQL Injection Testing Report
Test Summary:
• Project: BCU Contoso Timetable API
• Test Date: April 21, 2025
• Tester Name: Waleola Samuel Mayowa
• Objective: Test API endpoints for vulnerabilities against SQL injection attacks.
Test Scenarios & Results:
1. SQL Injection on Course Details Fetch
• Request: GET https://localhost:51106/course/1' OR '1'='1
• Expected Result: The system should reject the SQL injection attempt.
• Test Result: Passed – The system correctly rejected the SQL injection.
2. SQL Injection on Event Details Fetch
• Request: GET https://localhost:51106/event/1' OR '1'='1
• Expected Result: The system should reject the SQL injection attempt.
• Test Result: Passed
BCU Contoso Timetable API - Cross-Site Scripting (XSS) Testing Report
Test Summary:
• Project: BCU Contoso Timetable API
• Test Date: April 21, 2025
• Tester Name: Waleola Samuel Mayowa
• Objective: Test the API for vulnerabilities to Cross-Site Scripting (XSS) attacks.
Test Scenarios & Results:
1. XSS Injection in Course Name
• Request: GET https://localhost:51106/course/1?name=alert('XSS')
• Expected Result: The input should be sanitized and displayed as plain text.
• Test Result: Passed – The system correctly handled the XSS attempt.
BCU Contoso Timetable API - Maximum String Length Testing Report
Test Summary:
• Project: BCU Contoso Timetable API
• Test Date: April 21, 2025
• Tester Name: Waleola Samuel Mayowa
• Objective: Verify how the API handles strings at or beyond the maximum length
expected.
Test Scenarios & Results:
1. Maximum String Length - 100 Characters
• Request: PUT https://localhost:51106/student/1/name?newName=<100-
characters-long-string>
• Expected Result: The string should be processed correctly without issues.
• Test Result: Passed
2. String Length Exceeding Limit - 101 Characters
• Request: PUT https://localhost:51106/student/1/name?newName=<101-
characters-long-string>
• Expected Result: The request should be rejected with a validation error.
• Test Result: Failed – The request caused the system to time out without
validation.
Manual UI Testing Report
Test Summary:
• Test Name: UI Testing for Students Timetable Page
• Test Date: [Date of Testing]
• Tester Name: [Your Name]
• Objective: Verify the correct display of student data and functionality of UI
elements.
Test Scope:
• Page Tested: Students Timetable Page
• Data Verified:
o Enrollment Date
o Student Name, Email, Address
o Button functionality
Test Steps:
1. Open the Students Timetable page.
2. Verified the correct display of student data.
3. Checked if the "View" button works properly.
4. Cross-verified UI data with backend API.
Test Results:
• Enrollment Date: Passed – Date format is correct.
• Data Accuracy: Passed – All data (name, email, address) is correct.
• Button Functionality: Passed – "View" button works as expected.
Issues Found:
• No issues found during testing.
Recommendations:
• No changes are needed.
