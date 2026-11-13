# Day 7: Week 1 Revision

## One-page cheat sheet

### Key pairs 
| Pair | Difference in one line |
|---|---|
| QA vs QC | QA prevents defects through process. QC detects defects in the product. |
| Verification vs validation | Verification: are we building it right (review, no running). Validation: are we building the right thing (run it). |
| Smoke vs sanity | Smoke: is the new build testable? Sanity: does this specific fix work? |
| Retesting vs regression | Retesting: the failed test again. Regression: other tests still pass. |
| Functional vs non-functional | What it does vs how well it does it. |
| Scenario vs test case | What to test (one line) vs how to test it (detailed). |
| Acceptance criteria vs Definition of Done | Per story vs for every story. |
| Black vs white vs grey box | No code knowledge, full code knowledge, partial. |
| Static vs dynamic | Without running the code vs by running it. |
| 401 vs 403 | Not logged in vs logged in but not allowed. |
| 404 vs 500 | Resource not found vs server failed on a valid request. |

### Lists to know
- SDLC: requirement, design, development, testing, deployment, maintenance.
- STLC: requirement analysis, test planning, test case development, test environment setup, test execution, test closure.
- V-model pairs: requirements with UAT, system design with system testing, architecture design with integration testing, module design with unit testing.
- Test levels: unit, integration, system, UAT.
- Scrum events: sprint planning, daily scrum, sprint review, sprint retrospective.
- Performance types: load, stress, spike, endurance, scalability.
- Execution statuses: Pass, Fail, Blocked, Not run.
- Seven principles: defects shown not absence, exhaustive testing impossible, early testing, defect clustering, pesticide paradox, context dependent, absence-of-defects fallacy.
- Status code families: 2xx success, 3xx redirect, 4xx client problem, 5xx server problem.
- DevTools tabs: Elements (structure), Console (errors), Network (requests and status codes).

## 12 speak-it-aloud answers

### 1. SDLC vs STLC
"SDLC is the whole process of building software: requirement, design, development,
testing, deployment and maintenance. STLC is the testing journey inside it, with
six phases: requirement analysis, test planning, test case development, test
environment setup, test execution and test closure. Each STLC phase has entry and
exit criteria."

### 2. QA vs QC
"QA is process-focused and preventive, for example defining reviews and standards.
QC is product-focused and detective, like checking the built feature against the
requirements. Testing is part of QC."

### 3. Verification vs validation
"Verification asks whether we are building the product right and is done without
running code, like reviewing a requirement document for missing rules. Validation
asks whether we are building the right product and is done by running the
software, like booking a flight on the running site."

### 4. Smoke vs sanity
"Smoke testing is a quick, wide check on a new build to decide whether it is
stable enough to test. If it fails, the build is rejected. Sanity testing is a
narrow, focused check after a small change or fix to confirm that change works."

### 5. Retesting vs regression
"Retesting re-runs the exact failed test after a fix to confirm the bug is gone.
Regression re-runs other, previously passing tests to confirm nothing else broke.
I retest first, then run regression, and regression is a good candidate for
automation."

### 6. Types of testing overview
"Functional testing checks what the system does, and non-functional checks how well,
such as performance, usability, security and compatibility. By level there is unit,
integration, system and UAT. By approach there is black, white and grey box, and
static and dynamic. Exploratory testing is learning and testing at the same time
with a charter and notes."

### 7. Where QA fits in a Scrum sprint
"QA is part of the team from sprint planning. In planning I check stories are
testable and estimate testing effort. During the sprint I write test cases, test
stories as they are ready, log bugs, retest fixes and run regression. In the
retrospective I share process problems, like stories reaching testing too late."

### 8. The seven principles, in my own words
"Testing shows bugs exist but never that none exist. We cannot test everything, so
we test by risk. Testing early is cheaper. Defects cluster in a few modules. The
same tests repeated stop finding new bugs. Testing depends on context. And a
bug-free system still fails if it does not meet user needs."

### 9. Scenario vs test case
"A test scenario says what to test in one line. A test case says how, with an ID,
preconditions, steps, test data, expected result, actual result and status. One
scenario can produce many test cases."

### 10. What is the test pyramid?
"Many fast unit tests at the bottom, a moderate number of API tests in the middle
and a few UI tests at the top. UI tests are slow and break when the screen
changes, so I push checks to lower levels where possible."

### 11. How I use DevTools as a tester
"Elements to inspect attributes like id and data-test, which I will use as
locators in automation. Console to see JavaScript errors. Network to see requests,
methods, status codes and response times, which gives evidence for bug reports."

### 12. Walk me through how you tested an e-commerce site
"I tested SauceDemo. I wrote assumptions first because there was no requirements
document. I wrote fifteen scenarios covering login, sorting, cart, checkout and
logout, then executed them with the standard user and all passed. Then I tried the
special test users and found two issues with problem_user: product images that did
not match names, and a sorting dropdown that did not respond. I reproduced both
twice and saved screenshots. I did not log a possible slow page load for another
user because I had not measured it reliably."

## My 10 own interview questions

| No | Question | My answer |
|---|---|---|
| 1 | Why is software testing necessary even when developers have already checked their code? | Developers mainly focus on building the functionality, whereas testers look at the software from the user's perspective. Testing helps identify defects, check whether requirements are satisfied and build confidence before releasing the software. |
| 2 | What happens if a requirement is unclear before development starts? | If requirements are unclear, developers and testers may understand the expected functionality differently. This can lead to incorrect implementation and defects later. As a tester, I would clarify the requirement with the team before preparing test cases. |
| 3 | What are entry and exit criteria in STLC? | Entry criteria are the conditions that must be satisfied before starting a testing phase. Exit criteria are the conditions that must be fulfilled before completing that phase. For example, test execution can begin when the build and test environment are ready. |
| 4 | What is the difference between acceptance criteria and test cases? | Acceptance criteria describe the conditions a feature must satisfy to be accepted by the product owner or customer. Test cases are detailed steps prepared by testers to verify whether those conditions are met. Multiple test cases can be created from one acceptance criterion. |
| 5 | Why is integration testing important? | Integration testing checks whether different modules or components work correctly when connected. Even if individual modules pass unit testing, problems can occur when they exchange data. For example, I would check whether the shopping cart correctly receives product details from the product page. |
| 6 | What is exploratory testing, and when would you use it? | Exploratory testing means learning about the application and testing it simultaneously without depending entirely on predefined test cases. I would use it when exploring a new application or when requirements are limited. I would maintain a test charter and record my observations. |
| 7 | Why should we test an application on different browsers and devices? | An application may behave differently across browsers, operating systems and screen sizes. Compatibility testing helps identify these differences. For example, a checkout button might work in Chrome but become misaligned or unresponsive in Safari. |
| 8 | What is defect clustering, and how does it help a tester? | Defect clustering means that most defects are often concentrated in a small number of modules. It helps testers identify high-risk areas and focus more testing effort on those modules. For example, if the payment module has repeatedly produced defects, I would give it additional attention. |
| 9 | How would you decide which test cases should be automated? | I would prioritise repetitive test cases that are executed frequently, such as login, checkout and regression tests. I would also consider how stable the feature is and how much time automation can save. Tests that require subjective human judgement, such as usability, are better suited to manual testing.  I would automate a test case only after it is stable and has passed manually. |
| 10 | What information should a good bug report contain? | A good bug report should contain a clear title, environment details, preconditions, steps to reproduce, expected result, actual result and severity. I would also attach screenshots or other evidence wherever possible. This helps developers understand and reproduce the issue easily.  priority is also recorded. Severity is how serious the impact is, and priority is how soon it should be fixed. I learn the difference in Week 2. |

## Week 1 reflection

### Three things I can now explain well
1. Software testing fundamentals: I can explain SDLC, STLC, QA, QC, verification and validation, along with how testing fits into the software development process.
2. Types and levels of testing: I understand functional and non-functional testing, smoke and sanity testing, retesting and regression testing, and the four testing levels. I can also explain different testing approaches with examples.
3. Practical testing and bug reporting: I can write test scenarios, execute test cases, identify defects and document them with reproducible steps and evidence. I have also learned the basics of using browser DevTools.

### Two topics I am still unsure about
1. Performance testing: I understand load, stress, spike, endurance and scalability testing theoretically, but I need more practical examples to understand when each type is used.
2. API testing and HTTP status codes: I understand the basic status code families and how to inspect network requests, but I need more hands-on practice with API requests, responses and status codes.

### What I will do about them in Week 2
I will revise performance testing using real-world examples and practise identifying the correct performance testing type for different situations. I will also learn API testing fundamentals using Postman, practise sending GET and POST requests, inspect responses and understand common HTTP status codes.

 Postman and API testing are planned for Week 3. In Week 2 I will revise HTTP status codes in a short slot and practise performance testing examples.

## Speaking log

| Question I answered aloud | Time taken | Where I got stuck | What I will improve |
|---|---|---|---|
| Explain the difference between SDLC and STLC. | 45 seconds | Remembering all six STLC phases in order. | Practise explaining the phases without looking at notes.  tip: say "analyse, plan, write, set up, run, close" to remember the order. |
| What is the difference between smoke and sanity testing? | 35 seconds | Finding a clear real-world example for sanity testing. | Practise with examples from login and checkout features.  example: after a fix to the cart price, I test that fix and a few nearby checks, not the whole site. |
| Explain the four levels of testing. | 50 seconds | Differentiating integration testing from system testing. | Understand the purpose of each level with practical examples.  integration tests modules together, system tests the whole application end to end. |
| What are the seven principles of software testing? | 1 minute | Remembering the pesticide paradox and absence-of-defects fallacy. | Revise the principles using simple examples.  example: my 15 SauceDemo scenarios all passed, but repeating them won't find new bugs (pesticide paradox). A site with no bugs that lacks UPI payment still fails users (absence-of-defects fallacy). |
| How would you report a defect? | 45 seconds | Remembering all the information required in a bug report. | Practise writing bug reports with steps, expected results, actual results and screenshots. |
| Walk me through how you tested SauceDemo. | 1 minute 30 seconds | Explaining the two defects clearly without getting confused. | Practise narrating my testing process confidently and in chronological order.  order: assumptions, 15 scenarios, results with standard_user, then problem_user issues, and what I did not log. |