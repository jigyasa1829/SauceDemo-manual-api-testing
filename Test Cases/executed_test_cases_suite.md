Test Case ID,Module,Scenario Description,Pre-conditions,Execution Steps,Expected Result,Type,Priority,Status
TC001,Login,Verify successful login with valid credentials,User is on login page,"1. Enter 'standard_user' in Username
2. Enter 'secret_sauce' in Password
3. Click Login button",User is redirected to /inventory.html and product catalog is visible,Smoke,High,Pass
TC002,Login,Verify login fails with invalid password,User is on login page,"1. Enter 'standard_user' in Username
2. Enter 'wrong_password' in Password
3. Click Login button",Error message displayed: 'Epic sadface: Username and password do not match any user in this service',Regression,High,Pass
TC003,Login,Verify login fails with invalid username,User is on login page,"1. Enter 'invalid_user' in Username
2. Enter 'secret_sauce' in Password
3. Click Login button",Error message displayed: 'Epic sadface: Username and password do not match any user in this service',Regression,High,Pass
TC004,Login,Verify login fails for locked out user,User is on login page,"1. Enter 'locked_out_user' in Username
2. Enter 'secret_sauce' in Password
3. Click Login button",Error message displayed: 'Epic sadface: Sorry, this user has been locked out.',Regression,High,Pass
TC005,Login,Verify validation error when username is empty,User is on login page,"1. Leave Username blank
2. Enter 'secret_sauce' in Password
3. Click Login button",Error message displayed: 'Epic sadface: Username is required',Regression,Medium,Pass
TC006,Login,Verify validation error when password is empty,User is on login page,"1. Enter 'standard_user' in Username
2. Leave Password blank
3. Click Login button",Error message displayed: 'Epic sadface: Password is required',Regression,Medium,Pass
TC007,Login,Verify validation error when both fields are empty,User is on login page,"1. Leave Username blank
2. Leave Password blank
3. Click Login button",Error message displayed: 'Epic sadface: Username is required',Regression,Medium,Pass
TC008,Login,Verify password field masks characters,User is on login page,1. Type characters into Password field,Password input characters are masked as dots/asterisks,Functional,Low,Pass
TC009,Login,Verify username field case sensitivity,User is on login page,"1. Enter 'STANDARD_USER' in Username
2. Enter 'secret_sauce' in Password
3. Click Login button",Login fails with authentication error message,Regression,Low,Pass
TC010,Login,Verify direct URL access restriction without authentication,User is not logged in,1. Navigate directly to https://www.saucedemo.com/inventory.html,Redirected back to login page with error: 'Epic sadface: You can only access /inventory.html when you are logged in.',Sanity,High,Pass
TC011,Login,Verify user can logout successfully via side menu,User is logged in on /inventory.html,"1. Click hamburger menu icon
2. Click 'Logout' link",User is redirected back to the login page (/index.html),Regression,High,Pass
TC012,Login,Verify back button behavior after logout,User logged out successfully,1. Click browser Back button,User is not granted access to /inventory.html and remains on login page,Regression,Medium,Pass
TC013,Products,Verify product catalog loads 6 default items,User is logged in on /inventory.html,1. Observe the main inventory grid,Exactly 6 product cards are rendered with image name price and add to cart button,Smoke,High,Pass
TC014,Products,Verify product sorting by Name (A to Z),User is logged in on /inventory.html,"1. Click sort dropdown
2. Select 'Name (A to Z)'",Products are sorted alphabetically by title in ascending order (A to Z),Regression,Medium,Pass
TC015,Products,Verify product sorting by Name (Z to A),User is logged in on /inventory.html,"1. Click sort dropdown
2. Select 'Name (Z to A)'",Products are sorted alphabetically by title in descending order (Z to A),Regression,Medium,Pass
TC016,Products,Verify product sorting by Price (low to high),User is logged in on /inventory.html,"1. Click sort dropdown
2. Select 'Price (low to high)'",Products are sorted by price in ascending order ($7.99 to $49.99),Regression,Medium,Pass
TC017,Products,Verify product sorting by Price (high to low),User is logged in on /inventory.html,"1. Click sort dropdown
2. Select 'Price (high to low)'",Products are sorted by price in descending order ($49.99 to $7.99),Regression,Medium,Pass
TC018,Products,Verify navigation to Product Detail page,User is logged in on /inventory.html,1. Click title 'Sauce Labs Backpack',Redirected to /inventory-item.html showing complete details image and price,Functional,Medium,Pass
TC019,Products,Verify Back to Products button from details page,User is on product details page,1. Click 'Back to products' button,User returns to /inventory.html catalog view,Functional,Low,Pass
TC020,Cart,Verify adding single item updates cart badge count,User is logged in on /inventory.html,"1. Click 'Add to cart' on Sauce Labs Backpack",Cart badge counter updates to '1'. Button changes to 'Remove',Smoke,High,Pass
TC021,Cart,Verify adding multiple items updates cart count,User is logged in on /inventory.html,"1. Click 'Add to cart' on Backpack
2. Click 'Add to cart' on Bike Light
3. Click 'Add to cart' on Bolt T-Shirt",Cart badge counter dynamically updates to '3',Regression,High,Pass
TC022,Cart,Verify removing item from inventory page updates badge,User has 1 item in cart,"1. Click 'Remove' on Sauce Labs Backpack",Cart badge counter disappears and button reverts to 'Add to cart',Regression,Medium,Pass
TC023,Cart,Verify removing item from cart page updates list,User added item and navigated to /cart.html,"1. Click 'Remove' next to item on cart page",Item is removed from list. Cart badge counter updates/disappears,Regression,Medium,Pass
TC024,Cart,Verify cart contents persist across page navigation,User added items to cart,"1. Navigate to Product Detail page
2. Click Cart icon",All previously added items remain present in the cart list,Regression,Medium,Pass
TC025,Cart,Verify Continue Shopping button functionality,User is on /cart.html page,1. Click 'Continue Shopping' button,User is redirected back to product inventory catalog page,Functional,Low,Pass
TC026,Checkout,Verify end-to-end checkout completion,User has items in cart,"1. Open Cart and click Checkout
2. Enter First Name Last Name Zip Code
3. Click Continue
4. Click Finish",Redirected to /checkout-complete.html with header 'Thank you for your order!',Smoke,High,Pass
TC027,Checkout,Verify validation error when First Name is blank,User is on Checkout Step 1,"1. Leave First Name blank
2. Enter Last Name and Zip Code
3. Click Continue",Error message displayed: 'Error: First Name is required',Regression,High,Pass
TC028,Checkout,Verify validation error when Last Name is blank,User is on Checkout Step 1,"1. Enter First Name
2. Leave Last Name blank
3. Enter Zip Code
4. Click Continue",Error message displayed: 'Error: Last Name is required',Regression,High,Pass
TC029,Checkout,Verify validation error when Zip Code is blank,User is on Checkout Step 1,"1. Enter First Name and Last Name
2. Leave Postal Code blank
3. Click Continue",Error message displayed: 'Error: Postal Code is required',Regression,High,Pass
TC030,Checkout,Verify total amount calculation in Checkout Overview,Items added to cart,"1. Proceed to /checkout-step-two.html",Item Subtotal + Tax matches the displayed Final Total exactly,Functional,High,Pass
TC031,Checkout,Verify Cancel button on Checkout Step 1,User is on Checkout Step 1,1. Click 'Cancel' button,User is returned to the Cart page (/cart.html),Functional,Low,Pass
TC032,Checkout,Verify cart resets after successful order completion,User completed an order,1. Click Cart icon after finishing order,Cart is empty and badge counter is cleared,Sanity,Medium,Pass
TC033,Checkout,Verify Back Home button on order confirmation page,User is on order confirmation page,1. Click 'Back Home' button,User is returned to main product inventory page (/inventory.html),Functional,Low,Pass