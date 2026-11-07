# Day 2: STLC, Agile/Scrum, QA in a Sprint

## 1. What is STLC?
"STLC is the Software Testing Life Cycle. It is the sequence of testing activities
inside the overall SDLC. It has six phases: requirement analysis, test planning,
test case development, test environment setup, test execution and test closure."

## 2. Entry and exit criteria
"Entry criteria are the conditions that must be met before a phase can start.
Exit criteria are the conditions that must be met before a phase is considered
complete. For example, test execution can start only when test cases are ready,
the environment is ready and the build has passed a smoke check. It ends when
planned tests are run and defects are retested."

## 3. STLC with a hospital example
"In requirement analysis I would read the appointment booking requirement and ask
whether a doctor on leave can be booked. In planning I would decide the scope and
browsers. Then I write cases like booking an available slot and booking a taken
slot. I set up a test environment with dummy patient data, never real data. During
execution I run the cases and log defects. At closure I share a summary report
and lessons learned."

## 4. What is Agile and Scrum?
"Agile means building software in small increments with frequent feedback instead
of planning everything upfront. Scrum is a framework for Agile with three roles,
the Product Owner, the Scrum Master and the Developers, which includes testers.
Work happens in time-boxed sprints, usually one to two weeks."

## 5. Scrum events
"Sprint planning decides what we build and how. The daily scrum is a 15-minute
sync. The sprint review shows finished work to stakeholders. The retrospective
looks at how we worked and what to improve."

## 6. User story and acceptance criteria
"A user story is a short requirement from the user's view: As a patient, I want to
book an appointment online so that I don't have to call the hospital. Acceptance
criteria are the specific conditions for that story to be accepted, like only
available slots are shown. As a tester I convert acceptance criteria into test cases."

## 7. Definition of Done vs acceptance criteria
"Acceptance criteria belong to one story. The Definition of Done is a team-wide
checklist that applies to every story, for example code reviewed, tests passed
and no open critical defects."

## 8. Where does QA fit in a sprint?
"QA is part of the team from sprint planning. In planning I check stories are
testable and estimate testing effort. During the sprint I write test cases, test
stories as soon as they are ready, log bugs, retest fixes and run regression. At
the review I support the demo, and in the retrospective I share process issues,
like stories arriving for testing too late."

## 9. What is a three amigos meeting?
"It is a short discussion before development between the business person, a
developer and a tester. The tester asks what-if questions, which finds gaps in
requirements early."

## One-line answers
- STLC = the testing journey inside SDLC.
- Entry = needed to start. Exit = needed to finish.
- In Scrum, testers are part of the Developers.
- Acceptance criteria = per story. Definition of Done = for all stories.

## STLC for hospital appointment booking
- Requirement analysis: Understand the appointment booking requirements, including doctor selection, available time slots, patient details and appointment cancellation and ask questions about unclear points, for example whether a doctor on leave can be booked and list what is testable.
- Test planning: Decide what needs to be tested, who will test it, which tools are required and how much time testing will take.
- Test case development: Write test cases for booking appointments, selecting unavailable slots, entering incorrect details and cancelling appointments.
- Environment setup: Prepare the hospital booking application, test database and test patient accounts.
- Test execution: Run the test cases, compare actual results with expected results and report any bugs found.
- Test closure: Prepare a test summary report, check whether major bugs are resolved and document the testing results.

Entry and exit criteria for two respective phases:
- Phase: Requirement analysis
  - Entry: The hospital appointment booking requirements are available for review.
  - Exit: All requirements are understood, reviewed and clarified with the development team.
- Phase: Test execution
  - Entry: Test cases are ready, the testing environment is available and the application is ready for testing.
  - Exit: All planned test cases are executed, critical bugs are resolved and test results are documented.

## User story, acceptance criteria and Definition of Done
Feature: flight search on a travel site

- User story: As a traveller, I want to search for flights by entering my source, destination and travel date, so that I can find suitable flights for my journey.
- Acceptance criteria:
  1. The user should be able to enter a source and destination
  2. The user should be able to select a valid travel date
  3. The website should display available flights based on the entered details
  4. If no flights are available, the website should display an appropriate message
  5. A past travel date is not accepted and an error message is shown
- Definition of Done:
  1. All required flight search features are developed and working
  2. All test cases are executed successfully
  3. Critical and high priority bugs are fixed
  4. The feature is reviewed and approved by the team before release
  5. The code is reviewed, and the story meets its acceptance criteria 

## Exercise 3: My 2-week sprint QA plan
Day                QA activity 
1          Understand the requirements and discuss the feature with the development team and estimate testing effort and check the stories are testable 
2-3        Prepare test scenarios and write detailed test cases 
3-7        Execute test cases and report bugs to developers 
7-8        Retest fixed bugs and perform regression testing 
9          Perform final testing and check whether all acceptance criteria are satisfied and run a smoke check on the release build 
10         Prepare the test summary report and share the testing results with the team 