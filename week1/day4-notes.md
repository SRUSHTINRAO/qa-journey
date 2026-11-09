# Day 4: Types of Testing

## 1. What is exploratory testing?
"Exploratory testing means learning the application, designing tests and running
them at the same time, instead of following a pre-written script. It is useful when
requirements are thin or changing, or when I want to find issues nobody scripted.
I keep it structured with a charter, a time-box and session notes."

## 2. What is a test charter?
"A charter is a one-line mission for an exploratory session. For example: explore
the login form with invalid inputs to discover how errors are handled. I time-box
it, usually thirty to ninety minutes, and take notes while testing."

## 3. Exploratory vs ad hoc testing
"Ad hoc testing is random and unrecorded. Exploratory testing has a charter, a
time-box and notes, so the findings are traceable and repeatable in intent."

## 4. Scripted vs exploratory
"In scripted testing, tests are designed before execution and documented in detail.
In exploratory testing, they are designed during execution. Scripted tests suit
regression, and exploratory tests suit finding unexpected issues. Good teams use both."

## 5. What is compatibility testing?
"Compatibility testing checks that the application works across different
browsers, browser versions, operating systems, devices and screen sizes. For a
travel site, I would check that the search button is visible and works on Chrome
on a laptop and Safari on a phone. Teams use a compatibility matrix based on what
their users actually use."

## 6. Simulated vs real devices
"Chrome's responsive mode simulates a screen size but does not behave exactly like
a real device. For important releases I would test on real devices or a device
cloud, and I would be clear about what I actually tested."

## 7. What is usability testing?
"Usability testing checks how easily real users can reach their goals: can they
find things, understand labels, read error messages and recover from mistakes.
Functional testing asks whether the button works. Usability testing asks whether
the user can find it and understand it."

## 8. Performance testing types
"Load testing checks expected load. Stress testing pushes beyond the limit to see
how the system breaks and recovers. Spike testing applies a sudden jump in users.
Endurance testing runs normal load for a long time to find problems like memory
leaks. Scalability testing checks whether added resources increase capacity. I
look at response time, throughput and error rate."

## 9. Black box, white box, grey box
"Black box testing is done without code knowledge, based on inputs and expected
outputs, mainly by QA. White box testing uses knowledge of the code to test paths
and branches, mainly by developers. Grey box testing uses partial knowledge, for
example checking the database after booking in the UI."

## 10. Static vs dynamic testing
"Static testing checks work products without running code, like reviewing
requirements, test cases or code. Dynamic testing runs the software. Static
testing is how verification is usually done, and dynamic testing is validation."

## One-line answers
- Exploratory = learn, design and test together, with a charter and notes.
- Compatibility = different browsers, OS and devices.
- Usability = can users find and understand it easily?
- Load, stress, spike, endurance, scalability = performance types.
- Black = no code. Grey = partial. White = full.
- Static = no running. Dynamic = running.

## Exploratory session on the-internet.herokuapp.com
- Charter: Explore the Checkboxes page using mouse clicks, keyboard interaction, repeated clicks, browser refresh and navigation to discover whether the checkboxes behave consistently and maintain their expected states.
- Environment: Browser and version: Google Chrome 156.0.8078.81, Computer: Mac, Date: 09-11-2026 (9 November 2026), Page tested: https://the-internet.herokuapp.com/checkboxes
- Time-box: 30 minutes (the notes below cover the first 23 minutes)

| Time | What I tried | What I saw | Bug / question / idea |
|---|---|---|---|
| 0–2 min | Opened the Checkboxes page and inspected both checkboxes. | First checkbox was unchecked; second was checked. | Initial states identified. |
| 2–5 min | Clicked each checkbox individually and selected both. | Both checkboxes responded correctly. | No issue observed. |
| 5–8 min | Selected both checkboxes and refreshed the page. | First checkbox became unchecked and second remained checked. | Checkbox selections do not persist after refresh. no requirement says they should persist, so this is an observation or question, not a bug. |
| 8–11 min | Clicked each checkbox five times. | Every click alternated between checked and unchecked. | Repeated clicking works correctly. |
| 11–14 min | Changed checkbox states, clicked Back and then Forward. | Back returned to the examples list. Forward returned to the checkbox page with the state observed before leaving. | Browser history navigation works. question: Forward kept the state, but a refresh reset it. Why the difference? |
| 14–17 min | Changed checkbox states, refreshed and revisited the page using its URL. | The page returned to its original state: first unchecked, second checked. | State is not retained across a fresh page load. |
| 17–20 min | Resized the Chrome window. | The page remained usable down to 50% magnification. | No layout issue observed in the tested range. 50% refers to browser zoom, not window width. |
| 20–23 min | Used Tab and Space to interact with both checkboxes. | Both checkboxes could be accessed and toggled using the keyboard. | Keyboard interaction works. |

**Debrief:**

**What I covered:**
- Tested the initial state of both checkboxes and their selection and deselection behaviour.
- Checked repeated clicking, refreshing, browser Back and Forward navigation, and revisiting the page.
- Tested browser resizing and keyboard interaction using Tab and Space.

**What I found:**
- Both checkboxes responded correctly to mouse clicks and keyboard input.
- Checkbox states returned to their original values after refreshing or revisiting the page.
- Browser navigation worked as expected, and no visible layout issues were noticed during resizing.

**What I would test next:**
- Test the same checkbox functionality in Safari.
- Check keyboard focus visibility and accessibility.
- Explore the behaviour at smaller screen sizes and different zoom levels.
- Safari and responsive sizes were covered in the compatibility check below, so next I would test keyboard focus visibility, rapid double-clicks, and another page such as Dropdown.

## Compatibility check on one page
**Page tested:** https://the-internet.herokuapp.com/checkboxes

| Browser / screen | What I checked | Result I saw | Note |
|---|---|---|---|
| Chrome, full window | Checkbox visibility, text readability and clicking functionality. | Both checkboxes were visible up to 200% zoom. Text was readable and both checkboxes responded correctly. | No issue observed. |
| Safari, full window | Checkbox visibility, text readability and clicking functionality. | Both checkboxes were visible, text was readable and both responded correctly. | No issue observed. |
| Chrome responsive mode, phone width | Visibility, readability, clicking functionality and horizontal scrolling. | Both checkboxes were visible, text was readable, both were clickable and there was no overlapping or horizontal scrolling. | Simulated mobile testing. |
| Chrome responsive mode, tablet width | Visibility, readability, clicking functionality and horizontal scrolling. | Both checkboxes were visible but appeared slightly small. Text was readable, although it might be difficult for older users with poor eyesight. Both checkboxes were clickable, with no overlapping or horizontal scrolling. | Simulated tablet testing. usability observation, not a defect, since no size requirement exists for this page. |

Safari version  27.0.1 . Phone preset used iphon16. Tablet preset used surface pro 10.

## Classify the scenarios
| No | Scenario | Black / grey / white box | Static / dynamic | Why |
|---|---|---|---|---|
| 1 | A tester reviews the appointment booking requirement document for missing rules | Black box | Static | The tester reviews the requirements without executing the application or examining source code. box types mainly describe how tests are designed and run, so for a document review "static" is the label that matters. |
| 2 | A developer writes tests for each branch of the refund-calculation code | White box | Dynamic | The developer uses knowledge of internal code and branches. Dynamic testing applies when those tests are executed. |
| 3 | A tester books a flight on the site as a customer would | Black box | Dynamic | The tester interacts with the application as an external user without accessing internal code. |
| 4 | A tester books an appointment, then queries the database to confirm the record was saved | Grey box | Dynamic | The tester interacts with the application and uses partial internal knowledge through database access. |
| 5 | A team does a walkthrough of the test cases before execution | Black box | Static | The team reviews test cases without executing the application. same note as row 1: "static" is the label that matters. |
| 6 | A tester enters a past date in the flight search and checks the message | Black box | Dynamic | The tester enters input and observes the application's response without accessing internal code. |