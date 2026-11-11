# Day 5: Testing Principles + DevTools Basics 

## 1. The seven testing principles
"First, testing shows the presence of defects, not their absence. Second,
exhaustive testing is impossible, so we choose tests by risk. Third, early testing
saves time and money. Fourth, defects cluster together in a few modules. Fifth,
beware of the pesticide paradox: repeating the same tests stops finding new bugs.
Sixth, testing is context dependent. Seventh, the absence-of-defects fallacy:
fixing every bug does not help if the system doesn't meet user needs."

## 2. Why is exhaustive testing impossible?
"There are too many combinations of inputs, paths, browsers and devices. A flight
search alone has thousands of route, date and passenger combinations. So I use
risk-based selection and techniques like boundary value analysis."

## 3. What is the pesticide paradox?
"If the same tests are run repeatedly, they stop finding new defects. I would
review and update the test suite regularly, add new cases and use exploratory
testing to look beyond the script."

## 4. What does defect clustering mean?
"A small number of modules usually hold most of the defects. For example, if the
payment module has had many defects, I would test it more heavily."

## 5. What is the absence-of-defects fallacy?
"Even a system with no defects fails if it doesn't meet the users' needs. An
appointment page that works perfectly but doesn't support what patients actually
need is still a failure. This is why validation matters."

## 6. What is the test pyramid?
"The test pyramid says to have many fast unit tests at the bottom, a moderate
number of API tests in the middle and a few UI tests at the top. UI tests are slow
and fragile, so I automate at the lower levels where possible."

## 7. What is shift-left testing?
"Shift-left means starting testing activities earlier, such as reviewing
requirements, writing test cases while the feature is built and running tests on
every code change. It finds defects when they are cheaper to fix."

## 8. How do testers use Chrome DevTools?
"I use the Elements tab to inspect the page structure and attributes, the Console
tab to see JavaScript errors and the Network tab to see requests, status codes
and response times. It gives evidence for my bug reports."

## 9. Explain HTTP status codes
"2xx means success, 3xx means redirect, 4xx means a client-side problem and 5xx
means a server-side problem. Common ones: 200 OK, 201 Created, 400 Bad Request,
401 Unauthorized, 403 Forbidden, 404 Not Found, 500 Internal Server Error and 503
Service Unavailable."

## 10. 401 vs 403
"401 means the user is not authenticated, for example not logged in. 403 means
the user is logged in but not allowed to access that resource."

## 11. 404 vs 500
"404 means the requested resource was not found. 500 means the server failed while
processing a valid request, which is likely a server-side bug."

## One-line answers
- Testing shows bugs exist, never that none exist.
- Exhaustive testing is impossible, so test by risk.
- Same tests again and again stop finding bugs: pesticide paradox.
- Test pyramid: many unit, some API, few UI.
- 2xx success, 3xx redirect, 4xx client problem, 5xx server problem.

## Match the scenario to the principle

| No | Scenario | Principle | Why |
|---|---|---|---|
| 1 | The team says "all 200 test cases passed, so there are no bugs". | Testing shows the presence of defects | Testing can reveal bugs, but passing all test cases never proves that no defects exist. |
| 2 | A tester tries to test every possible combination of route, date, passenger count and payment method. | Exhaustive testing is impossible | Testing every possible combination is impractical, so testers prioritize using risk-based testing and techniques like Boundary Value Analysis. |
| 3 | Most of this month's defects came from the payment module. | Defect clustering | A large share of defects often comes from a small number of modules or areas of the application. |
| 4 | A regression suite has passed for six months, but a user finds a new bug. | Pesticide paradox | Repeating the same test cases may eventually stop finding new defects, so testers should regularly update and add test cases. |
| 5 | A booking page has zero known bugs, but customers want to pay by UPI and it isn't supported. | Absence-of-errors fallacy | Finding and fixing bugs is not enough if the software does not satisfy user needs and expectations. |
| 6 | A requirement gap is found in a review before any code is written. | Early testing saves time and money | Reviewing requirements early helps identify gaps before development, reducing the cost and effort of fixing them later. |

## DevTools investigation

Browser and version: Google Chrome 157.0.8103.39    Date: 11-11-2026

### Elements tab (saucedemo.com login page)

| Item inspected | Attributes I saw (id, name, class, etc.) | Why this matters to a tester |
|---|---|---|
| Username field | class="input_error form_input", placeholder="Username", aria-label="Username", data-test="username", id="user-name", autocorrect="off", autocapitalize="none", type="text", value="", name="user-name" | Helps identify the field, create automation locators, verify placeholder text, check accessibility and validate text input. |
| Password field | class="input_error form_input", placeholder="Password", aria-label="Password", data-test="password", id="password", autocorrect="off", autocapitalize="none", type="password", value="", name="password" | Helps identify the field, verify password masking, validate password input, create automation locators and check accessibility. |
| Login button | class="submit-button btn_action", data-test="login-button", id="login-button", type="submit", value="Login", name="login-button" | Helps identify the button, verify visibility and clickability, validate form submission and create automation locators. |
 in Week 4, id and data-test attributes are usually the most stable locators, because they change less often than class names or page layout.

### Network tab (the-internet.herokuapp.com/status_codes)

| Link clicked | Request URL | Method | Status code | What it means |
|---|---|---|---|---|
| 200 | https://the-internet.herokuapp.com/status_codes/200 | GET | 200 OK | The server successfully processed the request and returned the requested page. |
| 301 | https://the-internet.herokuapp.com/status_codes/301 | GET | 301 Moved Permanently | The requested resource has permanently moved to another URL. |
| 404 | https://the-internet.herokuapp.com/status_codes/404 | GET | 404 Not Found | The server could not find the requested resource. |
| 500 | https://the-internet.herokuapp.com/status_codes/500 | GET | 500 Internal Server Error | The server encountered an unexpected problem while processing the request. |
 this practice page returns these codes on purpose, so they are learning examples, not defects.

### Console tab (the-internet.herokuapp.com/javascript_error)

- What I saw in the Console:
  - `Uncaught TypeError: Cannot read properties of undefined (reading 'xyz')`
  - `at loadError (javascript_error:8:52)`
  - `at onload (javascript_error:12:30)`
- Was the page's visible content affected? The page displays a message stating that it has a JavaScript error in the onload event. The rest of the page appears mostly blank.
- Would I report it as a bug? Why or why not? I would not report this as an unexpected application bug because this website intentionally generates a JavaScript error for testing and learning purposes. However, if the same error occurred unexpectedly in a real application, I would report it because it could affect page functionality.
- on a real application I would copy the error message, file name and line number and attach a screenshot. A console error can exist even when the page looks fine, so I would still check what feature it might affect.

## Test pyramid for hospital appointment booking

- Unit tests (two examples):
  1. Check whether the system correctly calculates the available appointment slots for a doctor based on their working hours.
  2. Check whether the system rejects a booking date that is in the past.

- API tests (two examples):
  1. Send a request to book an appointment and check whether the API returns a successful response with the correct appointment details.
  2. Send a booking request for an already occupied time slot and check whether the API rejects the request with an appropriate error message.

- UI tests (two examples):
  1. Open the appointment booking page, select a doctor, choose an available date and time and check whether the patient can successfully book an appointment.
  2. Try submitting the booking form without entering required details and check whether the website displays validation messages.

- Which layer would I automate first, and why? I would automate unit tests first because they are faster to execute, easier to maintain and help identify errors in the application logic at an early stage. Fixing these problems before moving to API and UI testing can save time and effort.
- unit tests are normally written by developers. As a QA, I would automate API tests for the core booking flow first, then a small set of UI smoke and regression tests, because API tests are faster and more stable than UI tests and still check the real behaviour.