# Day 3: Types of Testing

## 1. Functional vs non-functional testing
"Functional testing checks what the system does against the requirements, for
example a patient can book an available slot. Non-functional testing checks how
well it does it, like speed, security, usability and compatibility. A booking
feature that works but takes thirty seconds to respond still fails the user."

## 2. Types of non-functional testing
"Performance checks speed and stability under load. Usability checks how easy it
is for real users. Security checks protection of data and access. Compatibility
checks different browsers and devices. Reliability checks that it keeps working
without failure."

## 3. Smoke testing
"Smoke testing is a quick check on a new build to confirm the most critical
functions work and the build is stable enough to test further. It is wide and
shallow. If smoke fails, the build goes back to the developers. For a hospital
app, I would check login, doctor search, booking and the confirmation screen."

## 4. Sanity testing
"Sanity testing is a narrow, focused check after a small change or bug fix to
confirm the change works and has not obviously broken related areas. For example,
after a fix for booking an already taken slot, I would test that exact scenario
plus cancelling and rebooking."

## 5. Smoke vs sanity
"Smoke is done on a new build and is wide and shallow, to decide whether the
build is testable. Sanity is done after a minor change and is narrow and deep, to
verify the change. Some teams use these terms slightly differently, so I confirm
the definition with the team."

## 6. Regression testing
"Regression testing means re-running existing tests after a change to make sure
previously working features did not break. Because it is repeated every sprint
and grows over time, it is a strong candidate for automation."

## 7. Retesting vs regression
"Retesting means re-running the exact failed test after a fix to confirm that bug
is fixed. Regression testing means running other, previously passing tests to
confirm nothing else broke. I retest first, then run regression."

## 8. Integration testing
"Integration testing checks that modules work together, for example the booking
module sending data to billing and the payment status coming back correctly.
Bugs here are often about data passing between modules."

## 9. System testing
"System testing checks the complete, integrated application end to end against
the requirements, in a production-like test environment. It is done by the QA
team. For example: register, book an appointment, pay and receive a confirmation."

## 10. UAT
"User acceptance testing is the final check by business users or the client that
the system meets their needs before go-live. Alpha testing is done by internal
users and beta testing by a small group of real external users."

Added: System testing checks against the specified requirements in a
production-like test environment. UAT checks against real business needs, usually
in a staging or UAT environment, and ends with a sign-off.

## 11. Do test types overlap?
"Yes. One check can belong to several types. Logging in with valid credentials is
functional, can be part of smoke testing and is also part of system testing. I
explain why I chose a label."

## One-line answers
- Functional = what it does. Non-functional = how well.
- Smoke = is the build testable? Sanity = does the fix work?
- Retesting = the failed test again. Regression = everything else still works.
- Unit, integration, system, UAT = code, modules, whole app, business sign-off.

## Testing 10 Observations on SauceDemo

**Website:** https://www.saucedemo.com

**Added:** Username for the first run: not recorded. Re-checked on 08 Nov 2026 with standard_user.

| No. | Check I performed | Result I saw | Testing type(s) and why |
|---|---|---|---|
| 1 | Logged in using valid login credentials. | Successfully redirected to the products page. | Functional testing – verifies that login works correctly. |
| 2 | Selected Price (low to high) from the sorting dropdown. | Products appeared in the incorrect order. Sauce Labs Onesie ($47.69) appeared before Sauce Labs Bike Light ($25.06). Added: when re-checked with standard_user, sorting was correct, so this was not reproducible in the standard flow. | Functional testing – checks whether sorting works correctly. |
| 3 | Clicked Add to Cart for a product. | Button changed to Remove, cart count increased to 1, and product appeared in the cart. I also noticed a price difference between the product page and cart. Added: when re-checked with standard_user, the product page and cart prices were the same. | Functional testing – verifies the add-to-cart feature. |
| 4 | Clicked Remove for the added product. | Button changed back to Add to Cart, cart count became 0, and product disappeared from the cart. | Functional testing – verifies product removal. |
| 5 | Opened the shopping cart after adding a product. | Cart page opened and displayed the product name and quantity. I noticed a price difference from the product page. Added: same re-check, prices matched for standard_user. | Functional and UI testing – checks cart navigation and product display. |
| 6 | Clicked Checkout without entering customer details. | Error message appeared: "Error: First Name is required". | Negative and functional testing – checks mandatory field validation. |
| 7 | Entered valid customer details and clicked Continue. | Successfully redirected to the checkout overview page. | Positive and functional testing – verifies valid customer details. |
| 8 | Checked the order summary and total calculation. | Item total was $29.99, tax was $2.40, and final total was $32.39. The calculation was correct. | Calculation and UI testing – checks order details and total calculation. |
| 9 | Clicked Finish to complete the purchase. | Confirmation page appeared with "Checkout: Complete!" and confirmed that the order was dispatched. | Functional testing – verifies successful checkout. |
| 10 | Checked the website in iPhone 14 mobile responsive mode. | Product names, Add to Cart buttons, and cart icon were visible. The page fitted the screen without awkward horizontal scrolling. Added: this is Chrome's simulation of the device, not a real iPhone 14. | Compatibility testing – checks the website on a mobile screen. |

### Usability Observation

Adding products, locating the shopping cart, and proceeding to checkout were easy and identifiable.

**Testing type:** Usability testing – checks whether users can understand and navigate the application easily.

### Additional Findings

- First run : sorting looked incorrect and the cart price looked different from the product page.
- Re-check with standard_user: sorting is correct and prices match, so neither issue reproduces in the standard flow.
- Lesson: I record the username, browser and steps every time I test. A finding I cannot reproduce is not reported as a bug until I can.

## Exercise 2: Smoke checklist for saucedemo.com (8 items)

1. Check whether the login page loads successfully.
2. Check whether a user can log in using valid credentials.
3. Check whether the products page displays the available products.
4. Check whether the Add to Cart button works.
5. Check whether the shopping cart displays the added products.
6. Check whether a user can remove products from the cart.
7. Check whether the checkout page opens successfully.
8. Check whether a user can complete an order and see the confirmation message.

Precondition: the build is deployed and the site opens. Expected result for every item: the step completes with no error message.

**Rule I follow:** If any item fails, I will stop further testing, record the failure with screenshots and steps to reproduce it, report it to the developer or team lead, and wait for the issue to be fixed before continuing the smoke test. Added: the build is marked rejected until a fixed build arrives.