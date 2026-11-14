# Day 8: Equivalence Partitioning + Boundary Value Analysis 

## 1. Why do we need test design techniques?
"Exhaustive testing is impossible, so techniques help me choose a small, smart set
of tests that still find most defects. For a field accepting one to nine, the valid
values are few but the invalid values are endless."

## 2. What is equivalence partitioning?
"Equivalence partitioning splits all possible inputs into groups where the system
should behave the same way. I test one representative from each group. If one
value in a group works, the others should too. I include valid partitions and
invalid ones, including hidden ones like empty, letters, decimals and special
characters."

## 3. Example of equivalence partitioning
"For passengers one to nine, the partitions are below one, one to nine, above nine,
decimals, letters and empty. I pick zero, five, fifteen, two point five, abc and a
blank. That is six tests instead of thousands."

## 4. What is boundary value analysis?
"Bugs often hide at the edges of ranges, for example a developer writes greater
than instead of greater than or equal to. BVA tests values at and around each
boundary. With two-value BVA I test the boundary and the value just outside. With
three-value BVA I test just below, on and just above."

## 5. Example of boundary value analysis
"For one to nine, three-value BVA gives zero, one, two, eight, nine and ten. A mid
value like five would pass even if the lower boundary were coded wrongly."

## 6. EP vs BVA
"EP gives coverage across groups by testing one value per group. BVA targets the
edges of ranges, where defects cluster. I use both together: EP first, then BVA."

## 7. When does BVA work best?
"For ordered data such as numbers, dates, text lengths, amounts and times. For
example, a booking window of today to thirty days ahead has boundaries yesterday,
today, day thirty and day thirty-one."

## 8. What if the requirement is unclear at a boundary?
"I do not guess. I note a question for the business analyst or product owner, for
example whether booking for today is allowed late in the evening. BVA often exposes
unclear requirements, which is verification in action."

## One-line answers
- EP = one value per group. BVA = values at the edges.
- Test invalid partitions too, including empty, letters, decimals.
- 3-value BVA: below, on, above each boundary.
- Unclear boundary? Ask, do not assume.

# My exercises

## Exercise 1: Passenger count field
Requirement (assumed for practice): "Number of adult passengers: whole number from 1 to 9."

### Equivalence partitions
| Partition | Valid or invalid | My example value | Expected result |
|---|---|---|---|
| 1. Within the allowed range | Valid | 5 | Accepted |
| 2. Below minimum | Invalid | 0 | Rejected with a message |
| 3. Above maximum | Invalid | 10 | Rejected with a message |
| 4. Negative number | Invalid | -3 | Rejected with a message |
| 5. Decimal number | Invalid | 2.5 | Rejected with a message |
| 6. Non-numeric input | Invalid | "bca" | Rejected with a message |
| 7. Empty input | Invalid | (blank) | Rejected with a "required" message |

### Boundary values (3-value)
- Lower boundary (1): 0, 1, 2
- Upper boundary (9): 8, 9, 10

## Exercise 2: Hospital consultation fee by age
Requirement (made up for practice): "Patient age decides the consultation fee. Age 0 to 12 is Child. Age 13 to 59 is Adult. Age 60 and above is Senior."

### Equivalence partitions
| Partition | Valid or invalid | My example value | Expected result |
|---|---|---|---|
| 1. Child age | Valid | 6 | Child |
| 2. Adult age | Valid | 45 | Adult |
| 3. Senior age | Valid | 72 | Senior |
| 4. Alphabetic input | Invalid | "sru" | Rejected with message |
| 5. Negative age | Invalid | -45 | Rejected with message |
| 6. Empty input | Invalid | Empty | Validation message required |
| 7. Decimal number | Invalid | 4.5 | Ask BA whether decimals are allowed. Expected result is TBD, pending the BA's answer |
| 8. Very large age | Unclear | 200 | TBD, because the requirement has no maximum age |

### Boundary values (3-value) for each boundary
- Lower boundary (0): -1, 0, 1
- Child/Adult boundary (12/13): 12, 13, 14
- Adult/Senior boundary (59/60): 59, 60, 61

### Questions I would ask the business analyst (at least 2)
1. Are decimal ages such as 12.5 allowed, or should the system accept only whole numbers?
2. Is there a maximum permitted age?

## Exercise 3: Observe a real field
- Site and page: DemoQA – Automation Practice Form
- Field tested: Mobile
- Rule I read on the page: Mobile (10 Digits). This is the label on the page, not a full requirement, so I treated it as the rule for practice.
- Browser and version: Google Chrome Version 157.0.8103.79    Date: 14 November 2026

| Value tried | Partition or boundary it represents | Expected | Actual result I saw |
|---|---|---|---|
| 5463728190 | Valid Input | Accepted | Accepted; form submitted successfully; no popup. Re-checked on 14 November 2026 with all other fields filled: the confirmation window appeared. |
| 135246789 | Just below boundary | Rejected | Submission unsuccessful; red border appeared |
| 45321678910 | Just above boundary | Rejected | Accepted all 11 digits; form submitted; no error on either attempt. The confirmation window appeared and showed Mobile as screenshot: week2/day8-screenshots/day8-11-digit-mobile.png |
| Empty | Empty Input | Rejected | Submission unsuccessful; red border appeared |
| adjective | Alphabetic Input | Rejected | Letters accepted while typing; submission unsuccessful; red border appeared |
| 897634aghast | Alphanumeric Input | Rejected | Entire value accepted while typing; submission unsuccessful; red border appeared |

Observations or questions:
1. The field accepts 10 digits and allows successful submission.
2. The field also accepts 11 digits and allows successful submission, which contradicts the displayed requirement.
3. Empty input is rejected.
4. Alphabetic and alphanumeric values are rejected during submission.
5. Why does the application accept an 11-digit number when the requirement specifies 10 digits?
6. Re-checked with all other fields filled. 11 digits was accepted by the form, although the page says 10 digits. Logged as a practice defect on a demo site.

