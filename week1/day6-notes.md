# Day 6: Mini Manual-Testing Project

## 1. Test scenario vs test case
"A test scenario says what to test, in one line, for example: verify that a
patient can book an available appointment slot. A test case says how to test it,
with an ID, preconditions, steps, test data, expected result, actual result and
status. One scenario can produce many test cases."

## 2. What are the execution statuses?
"Pass means the actual result matches the expected result. Fail means it does not,
and I log a defect. Blocked means I cannot run the test because something else is
broken. Not run means it has not been executed yet."

## 3. Where do expected results come from?
"From the requirements. When there is no requirements document, I use common
sense about how similar software behaves and I write my assumption down so others
can check it."

## 4. What makes a good bug report?
"A specific title, numbered steps to reproduce, the expected result, the actual
result, the environment such as browser, user and date, and evidence such as a
screenshot or console message. I reproduce the problem once before reporting it."

## 5. Defect vs observation
"A defect breaks a requirement or reasonable behaviour. An observation is
something I noticed that may deserve a question or suggestion, but it does not
break a requirement."

## 6. How did you decide what to test first?
"I started with the critical flow: login, product list, cart and checkout,
because a failure there blocks everything else. Then I covered negative cases,
validations and calculations."

## 7. What would you test first with only 30 minutes?
"The smoke checklist: can I log in, add a product, reach checkout and complete an
order. If any of those fail, the build is rejected and further testing is
pointless."

## 8. Typical flows in my target domains
"Healthcare: register patient, search doctor, book appointment, consultation,
billing, prescription and lab reports, with patient data protected and fake test
data used. Travel: search, select a flight, passenger details, payment,
confirmation and cancellation or refund."

## One-line answers
- Scenario = what. Test case = how.
- Pass, Fail, Blocked, Not run.
- Always record username, browser and date with results.
- Reproduce before reporting.
- Critical flow first.

# Project: SauceDemo manual testing

## Environment
- Website: https://www.saucedemo.com
- Browser and version: Google Chrome Version 157.0.8103.51
- Computer: Mac
- Date: 12 November 2026
- Main user for execution: standard_user

## Assumptions (no requirements document exists, so I wrote these)
1. The website should display an appropriate error message when a mandatory field is left empty.
2. The website should prevent login with incorrect credentials and display a suitable error message.
3. When a user adds a product to the shopping cart, the cart should correctly reflect the selected product and its quantity.

## 15 test scenarios with execution results
| ID | Scenario | Steps | Expected result | Actual result | Status |
|---|---|---|---|---|---|
| TS01 | Login with valid credentials | 1. Open SauceDemo 2. Enter standard_user 3. Enter secret_sauce 4. Click Login | User is redirected to the Products page. | User successfully logged in and the Products page displayed the available products | Pass |
| TS02 | Login with incorrect password | 1. Open site 2. Enter standard_user 3. Enter an incorrect password 4. Click Login | Error message is displayed stating that the username or password does not match. | Error message displayed: "Epic sadface: Username and password do not match any user in this service" | Pass |
| TS03 | Login with empty username | 1. Open site 2. Leave username empty 3. Enter secret_sauce 4. Click Login | Error message indicates that the username is required. | Error message displayed: "Epic sadface: Username is required" | Pass |
| TS04 | Login with empty password | 1. Open site 2. Enter standard_user 3. Leave password empty 4. Click Login | Error message indicates that the password is required. | Error message displayed: "Epic sadface: Password is required" | Pass |
| TS05 | Login with locked-out user | 1. Open site 2. Enter locked_out_user 3. Enter secret_sauce 4. Click Login | Error message indicates that the user has been locked out. | Error message displayed: "Epic sadface: Sorry, this user has been locked out" | Pass |
| TS06 | Verify product sorting options | 1. Login 2. Open the sorting dropdown 3. Select Price Low to High 4. Select Price High to Low 5. Verify product order | Products are displayed in the selected price order. | Products were correctly arranged from lowest to highest price and highest to lowest price when the respective sorting options were selected. | Pass |
| TS07 | View product details | 1. Login 2. Open the Products page 3. Click a product name 4. View its details | Product details page displays the correct product name, description, price and image. | Sauce Labs Backpack details page opened successfully. Product name, description, price and image were displayed. | Pass |
| TS08 | Add product to cart | 1. Login 2. Select a product 3. Click Add to cart 4. Open the cart | Selected product appears in the shopping cart. | Sauce Labs Backpack was successfully added to the cart. Cart badge displayed 1, and the product appeared in the cart with its details. | Pass |
| TS09 | Remove product from cart | 1. Add a product to cart 2. Open the cart 3. Click Remove | Selected product is removed from the cart. | Sauce Labs Backpack was successfully removed from the cart. The cart badge disappeared after removal. | Pass |
| TS10 | Verify cart badge count | 1. Login 2. Add one product 3. Add another product 4. Observe the cart badge | Cart badge displays the correct number of added products. | After adding Sauce Labs Backpack and Sauce Labs Bike Light, the cart badge correctly displayed 2. | Pass |
| TS11 | Verify cart persistence during navigation | 1. Add a product to cart 2. Navigate to another page 3. Return to the cart | Previously added product remains in the cart. | Both previously added products remained in the cart after navigating to the Products page and returning to the Cart page. | Pass |
| TS12 | Verify mandatory checkout fields | 1. Add a product 2. Open cart and click Checkout 3. Leave First Name empty and continue 4. Repeat with Last Name empty 5. Repeat with Postal Code empty | Appropriate validation error appears for each missing mandatory field. | When First Name, Last Name and Postal Code were individually left empty, the website displayed the respective validation errors: "First Name is required", "Last Name is required" and "Postal Code is required". | Pass |
| TS13 | Verify checkout details and total calculation | 1. Add a product 2. Proceed to Checkout 3. Enter First Name, Last Name and Postal Code 4. Click Continue 5. Verify item price, subtotal, tax and total | Checkout overview displays the correct item price, subtotal, tax and final total. | Checkout Overview displayed both selected products with correct prices. Item Total, Tax and final Total were calculated and displayed correctly. | Pass |
| TS14 | Complete an order and verify confirmation | 1. Proceed to checkout overview 2. Click Finish 3. Observe the confirmation page | Order is completed and an order confirmation message is displayed. | Checkout Complete page appeared with the message "Thank you for your order!" and order dispatch confirmation. | Pass |
| TS15 | Logout from the application | 1. Login with valid credentials 2. Open the navigation menu 3. Click Logout | User is redirected to the login page. | User successfully logged out and was redirected to the SauceDemo login page, where the username and password fields were visible. | Pass |

| Results summary | Count |
|---|---|
| Total | 15 |
| Pass | 15 |
| Fail | 0 |
| Blocked | 0 |
| Not run | 0 |

 all 15 scenarios passed with standard_user. That does not prove the site has no defects (testing shows the presence of defects, not their absence). The two issues below came from the special test user problem_user.

## Smoke suite (which scenarios would I include and why)
A smoke test suite contains a small set of important test cases used to check whether the application's main functionalities are working correctly.

I would include the following scenarios:
- TS01 – Login with valid credentials: To verify that users can successfully log in.
- TS02 – Login with incorrect password: To verify that the application handles invalid login attempts correctly.
- TS06 – Product sorting options: To check whether products can be sorted correctly by price.
- TS08 – Add product to cart: To verify that users can successfully add products to their cart.
- TS09 – Remove product from cart: To check whether users can remove products from their cart.
- TS12 – Checkout mandatory fields: To verify that required checkout fields display appropriate validation messages.
- TS13 – Checkout details and total calculation: To ensure product prices, item totals, tax and final amount are calculated correctly.
- TS14 – Complete order and confirmation: To verify that users can complete an order and receive an order confirmation.

 reflection: this list has 8 of 15 scenarios, which is more than half. A smoke suite should be small and take a few minutes. A tighter suite for this app would be TS01, TS07, TS08, TS09, TS13 and TS14, which are the critical flow of login, products, cart, checkout and confirmation. TS02, TS06 and TS12 are important, but they stay in the full functional suite. If a smoke scenario fails, I stop testing and reject the build.

## Issue log (2 issues)
 I logged two issues because I could reproduce both and capture evidence. 

### Issue 1
- Title: Product images do not match product names for problem_user.
- Type: Practice defect (special test user).
- Steps to reproduce:
  1. Open SauceDemo in an Incognito window.
  2. Login using problem_user and secret_sauce.
  3. Navigate to the Products page.
  4. Compare product images with their names.
- Expected result: Each product should display its corresponding image.
- Actual result: Product images do not match their respective product names.
- Environment: Chrome 157.0.8103.51, Mac, 12 November 2026, user: problem_user.
- Reproduced a second time? Yes
- Evidence: Screenshot: week1/day6-screenshots/issue1-problem-user-image-mismatch.png

### Issue 2
- Title: Product sorting dropdown does not respond for problem_user
- Type: Practice defect (special test user)
- Steps to reproduce:
  1. Open SauceDemo in an Incognito window.
  2. Login using problem_user and secret_sauce.
  3. Open the Products page.
  4. Open the sorting dropdown.
  5. Select Price (low to high).
- Expected result: Sorting option should be selected and products should be arranged in ascending price order.
- Actual result: The sorting option does not get selected.  with standard_user the same steps work correctly (checked on Day 3).
- Environment: Chrome 157.0.8103.51, Mac, 12 November 2026, user: problem_user.
- Reproduced a second time? Yes
- Evidence: Screenshot: week1/day6-screenshots/issue2-problem-user-sorting.png