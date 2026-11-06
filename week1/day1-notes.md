# Day 1: Testing Fundamentals 

## 1. What is software testing?
"Software testing is checking whether the software does what it is supposed to do,
does not do what it should not do, and is usable. Its goals are to find defects,
build confidence, support decisions and prevent defects. Testing can show that
bugs exist, but it cannot prove that there are none."

## 2. What is SDLC?
"SDLC is the Software Development Life Cycle: requirement, design, development,
testing, deployment and maintenance. Teams follow it to build software in an
organised way."

## 3. Waterfall vs V-Model vs Agile
"In Waterfall, each phase finishes before the next starts, so testing happens
late. The V-Model pairs each development phase with a test phase, for example
requirements with UAT and module design with unit testing. In Agile, we build
and test in short sprints with regular feedback. I would prefer Agile because
issues are found early."

Why "V": the left side goes down through the development phases (requirements,
system design, architecture design, module design) and the right side goes up
through the matching test phases (UAT, system testing, integration testing,
unit testing).

## 4. QA vs QC
"QA is process-focused and preventive: defining standards, reviews and audits.
QC is product-focused and detective: checking the actual product for defects.
Testing is a part of QC. For example, QA defines a review process, and QC
checks the built feature."

## 5. Verification vs Validation
"Verification asks: are we building the product right? It is static, like
reviewing requirements or code. Validation asks: are we building the right
product? It is dynamic, like running the software. In a hospital app, reviewing
the requirement document is verification, and booking an appointment on the
running app is validation."

Travel example: Verification = reviewing the requirement document to confirm it
lists every required passenger field (name, email, passport number) and the rule
for each, before any code is written. Validation = booking a flight on the
running site: search, select, pay and receive a confirmation.

## 6. Why is early testing cheaper?
"A defect found in a requirement review costs a conversation. The same defect
found after release needs redesign, recoding, retesting and redeployment."

## One-line answers
- Testing cannot prove software is bug free.
- QA prevents, QC detects.
- Verification = review. Validation = run.


## My exercise: Hospital appointment booking

- Requirement: The list of doctors and their available dates and time have to be displayed first and then the user should select the required date and time and once booked the appointment date, respective doctor and time with booking status should be seen on the screen.
- Design: Create a simple interface where patients can search for doctors, view available dates and time and confirm appointments.
- Development: Develop the appointment booking feature and connect it to the hospital database to store patient and appointment details.
- Testing: Check whether patients can successfully book, reschedule and cancel appointments without errors.
- Deployment: Make the appointment booking feature available to patients on the hospital website or application.
- Maintenance: Fix reported issues, improve the booking process and update doctor availability whenever needed.

### What a tester can do
- In requirements: Check whether all necessary features are mentioned, whether patients can cancel or reschedule appointments and whether the requirements are clear and complete.
- Gap found: the requirement describes only booking, but the testing phase includes cancel and reschedule. I would raise this with the business analyst.
- In design: Check whether the booking page is easy to understand, whether all required fields are included and whether error messages and confirmation screens are properly designed.
- In testing: Check whether appointments are booked successfully, whether unavailable time slots can be selected and whether incorrect patient details are handled properly.