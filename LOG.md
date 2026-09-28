# Debug log

Your notes. One entry per bug you fixed, using the template below.

This file is read as carefully as your code. A correct fix you cannot
explain counts for little; a bug you could not fix but investigated
honestly still counts for something.

Delete the example before you submit.







## CC-01 — "The search suggestions are behind everything"

**Reproduced:** When typing in the search box, the suggestions appear behind other elements on the page.

**Cause:** The z-index of .search-wrap was set to 1, z-index of .cat-tabs was set to 40, causing the suggestions to be hidden behind other elements.

**Fix:**: Updated the z-index of .search-wrap to 100 in style.css to ensure it appears above other elements.

**Checked:** Search suggestions now appear correctly above other elements when typing in the search box.

**Time:** 5 minutes

## CC-02 — "Can't read anything in dark mode"

**Reproduced:** Switched the site to dark mode and observed that the dish names and prices were almost invisible against the dark background.

**Cause:** The text color for class .dish-body was set to a dark color (#2b2118) which does not contrast well with the dark background in dark mode.

**Fix:**: Added a new CSS rule for dark mode that changes the text color of .dish-body to a lighter color (#f2e8df) when the data-theme attribute is set to "dark".

**Checked:** Dish names and prices are now clearly visible in dark mode.

**Time:** 2 minutes

## CC-03 — "The menu is wider than my phone"

**Reproduced:** On a phone, the menu required horizontal scrolling to view all dishes, and the "Add to Cart" buttons were cut off.

**Cause:** The .dish-card container did not have a responsive width set, causing it to exceed the viewport width on smaller screens.

**Fix:**: Added min-width: 0; to the .dish-card class in style.css to ensure it does not exceed the viewport width on smaller screens.

**Checked:** The menu now fits within the viewport on phones, and the "Add to Cart" buttons are fully visible without horizontal scrolling.

**Time:** 5 minute

## CC-04 — "The buttons don't work on my tablet"

**Reproduced:** On a tablet, the "Add to Cart" and "Save" buttons did not respond to clicks, while they worked fine on a laptop and a phone.

**Cause:** The .dish-card container had a after pseudo-element that was covering the buttons, preventing click events from reaching them. (only for screen size between 761px and 900px)

**Fix:**: Commented out the CSS rules for the after pseudo-element on .dish-card and .img-wrap in style.css for screen sizes between 761px and 900px.

**Checked:** The buttons now respond correctly to clicks on the tablet.

**Time:** 5 minutes

## CC-05 — "The category bar scrolls away on my phone"

**Reproduced:** On smaller screens, the category and filter bar scrolls away instead of staying visible at the top while scrolling through the menu dishes.

**Cause:** The .filter was in .view and the .view was scrollable, causing the filter bar to scroll away with the rest of the content.

**Fix:**: Put .filter div in header instead of .view, so it stays fixed at the top while scrolling through the menu dishes. (Also increased z-index of .site-nav to 99999 to ensure it stays above other elements).

**Checked:** The category and filter bar now stay visible at the top while scrolling through the menu dishes.

**Time:** 5 minutes

## CC-06 — "I ordered more than they had"

**Reproduced:** The counter says only 5 hakka noodels were left but it let me order 10

**Cause:** setQty function in state.js was not checking the stock of the dish before allowing the quantity to be updated in the cart.

**Fix:**: Added a check in setQty function to ensure that the quantity being added to the cart does not exceed the available stock of the dish. If it does, it returns an error message indicating the maximum available stock.

**Checked:** The cart now correctly prevents adding more items than are available in stock, and displays an appropriate error message when attempting to do so.

**Time:** 15 minutes 

# CC-07: Cancelling makes it worse

**Reproduced:** Ordered 2 hakka noodles, then cancelled the order. The stock counter still says 3 left instead of 5.

**Cause:** Release stock function decreased stock instead of increasing it when an order is cancelled. The stock was being updated incorrectly in the backend logic.

**Fix:**: Updated the release stock function in validation.js to correctly increase the stock of the dish when an order is cancelled. Also updated the frontend to reflect the correct stock after cancellation.

**Checked:** The stock now correctly reflects the available quantity after an order is cancelled.

**Time:** 15 minutes 

# CC-08: An old coupon still works

**Reproduced:** Applied the coupon code "FRESHERS24" which was 2024's offer and expired, but it still gave a discount on the order.

**Cause:** The coupon's expiration date was not being checked properly in the applyCoupon function. 

**Fix:**: Updated the applyCoupon function to check the expiration date of the coupon before applying it. If the coupon has expired, it will return an error message.

**Checked:** The coupon code "FRESHERS24" now correctly returns an error message indicating that the coupon has expired and does not apply any discount to the order.

**Time:** 10 minutes 

### CC-09: "The menu shows more dishes than it should"

**Reproduced:** The menu is displaying more dishes than it should (it is repeating all dishes).

**Cause:** The paginate function in search.js was returning the entire list of dishes instead of just the paginated items. The items property in the returned object was set to the entire list instead of the sliced list.

**Fix:**: Updated the paginate function in search.js to return only the sliced list of items for the current page, instead of the entire list.

**Checked:** The menu now correctly displays only the dishes for the current page.

**Time:** 5 minutes

### CC-10: "Sorting by price is backwards"

**Reproduced:** When sorting dishes by price, the order is reversed from what is expected.

**Cause:** The SORTERS object in search.js had the sorting functions for price-asc and price-desc reversed, causing the dishes to be sorted in the opposite order.

**Fix:**: Updated the SORTERS object in search.js to correctly sort dishes by price in ascending order for price-asc and descending order for price-desc.

**Checked:** The menu now correctly sorts dishes by price in ascending order.

**Time:** 2 minutes



## Could not fix

Fixed every issue above


## Extra credit

Anything not on the bug log: a problem you found yourself, a test you
wrote, or a fix you are unsure about. Same format, plus one line on how
you noticed it.
