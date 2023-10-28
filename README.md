# Aalto University
# E-commerce platform "Karadazzi Deliveries"

Second Flutter project for the course **"CS-E4270 - Device-Agnostic Design D"**, held at Aalto University, A.Y. 2022/2023 (Period I).

The project consists in implementing the frontend of an online web store. In this application, the user can "purchase" food from the Bulgarian cuisine at really convenient prices, by choosing dishes among five categories of products: breakfast, salads, appetizers, grill and soups.<br />The data is fetched from a `data.json` file, which contains all the information about the categories and products from the shop.

**Faculty**: Mika P. Nieminen, Arto Hellas

**Deployed online version**: https://alex-atanassov.github.io/dad-2022-project-2/

<div display="inline-block">
<img src="https://github.com/alex-atanassov/dad-2022-project-2/assets/79805163/7b6978e9-01a9-4dda-8f7c-e4033e6b40fc" width=78.7% />
<img src="https://github.com/alex-atanassov/dad-2022-project-2/assets/79805163/9b0f99a0-b06f-4d61-910f-f7a3ea9d4b5c" width=19.5% />
</div>

## Functionality

All the required features from the project handout have been implemented. The subsections below will explain each one in more detail.

### Landing page

When the user enters the website, the first screen he will see is the **`Landing page`**. This landing page contains an overview of all the 5 categories, and also features a section called "Products of the day", which displays 5 *random* products (exactly one product per category), chosen randomly at each reload.

### Categories and products

By selecting one category from the landing page, the user is brought to a **`Listing screen`**, which contains both the pages that in the specifications are referred to as **`Category Listing page`** and **`Category page`**.

Although the `Landing page` already contained a sort of category listing of its own, the `Category Listing page` on the left column of the screen allows to switch between categories easily, without the need to go back to the previous screen: when the user presses on a category, the respective card will change color from white to light red to indicate the current selection, and the right side of the screen (the `Category page`) displays all and only the products of that same category.

Clicking on a product card, either from the `Landing page` or from the `Category page`, brings the user to the respective **`Product page`**, on a separate screen. This page displays all the information concerning the selected product - including price, image and description -, and offers the possibility to add the product to the `Shopping cart`. After clicking "Add to cart", the application displays a snackbar with the message "Item added to cart". 

### Shopping cart, profile settings and search functionality

These three functionalities are all contained in the AppBar on the top of the screen, and can be accessed from any screen of the application, as IconButtons. Each of these three buttons provide a tooltip message when hovered, for more intuitiveness. The AppBar contains, from left to right:

- The shortcut to go back to the home page, accessed by clicking on the text "KARADAZZI".

- (Only shown on larger screen widths) A dynamic welcome message, which displays "Welcome!" if no username has been set, or "Hi, Alessandro!" otherwise (where "Alessandro" is replaced by your username).

- The **`Shopping cart`** icon, which displays the number of items saved in the cart, and opens the `Checkout screen` when clicked. (Note, the shopping cart is not persisted, but only saved as state throughout the duration of a user session).

- The **`Profile settings`** icon, which opens a Drawer on the right side with all the user settings. The settings feature a section to register Username and Delivery Address, and a section to manage the payment methods. In this latter section, the user can add a new payment card by filling the respective form with Card Owner and Card Number, or delete existing cards by interacting with the cards displayed on the bottom; to remove a card, swipe the ListTile to the right, or click on the trash bin icon.

- The **`Search`** icon, which opens a search bar, in which the user can research both categories and products.<br />The suggestions are not shown when the input is empty, but only when the user starts typing. Suggestions are based on a simple substring check, i.e., suggestions are all those categories and products which name has the user input as substring (not necessarily does the substring need to start from index 0 to match an item as suggestion).<br />Suggested categories and products are shown in separate lists, and in the case of products, the suggestions are sorted in alphabetical order.<br />Clicking on a suggestion brings to respective category or product page, as normal.

### Enhanced shopping cart and checkout functionality

Clicking on the cart icon from the AppBar brings to a separate **`Checkout screen`**, which displays the list of items in the shopping cart on one side, and the checkout details in the other.

The cart products are displayed as one card per item, which can be removed from the cart by either pressing the trailing trash icon, or by swiping the item to the left (this latter option is not available on a wider screen, where the items are displayed in a 2-column grid instead of a list).

The screen also displays the total price of the shopping cart, which changes in real time whenever the contents of the cart also change.

The checkout options include a dropdown where the user can select a credit card for payment. If the user does not select an option or if no address has been registered already, the "Confirm payment" button will stay disabled; an additional button "Add payment option" provides a shortcut to add the missing details for the payment. 

Once the user confirms the purchase, he is brought to the **`Confirmation screen`**, which displays a "Thank you" message, the button to go back to the home page, and the final list of items bought. The shopping cart is also going to be emptied after the purchase.

### Responsiveness

The application features 4 different layouts per screen, using 3 different width thresholds of 600, 900 and 1200 pixels.

The 4 layouts have been tested on the following devices and orientations:

1) **Desktop**: all layouts;
2) **Tablet**: Width 900-1199 (Landscape) and Width 600-899 (Portrait);
3) **Mobile**: Width 600-899 (Landscape) and Width below 600 (Portrait);


From widest to narrowest layout, the following elements are responsive to the resizing.

- `Landing screen`: Categories and "Products of the day" are shown in 5, 3, 2 or 1 column.

- `Listing screen`: 
    - *Width over 1200*: the categories are shown as a list on the left side, while the products are shown in a 3-column grid on the right;
    - *Width 900-1199*: the categories are still shown as a list, and the products are shown in one column, just like the categories;
    - *Width 600-899*: the categories list is replaced by a dropdown on the top, from which the category can be still changed, while the products are shown again in 3 columns;
    - *Width below 600*: the categories dropdown is still present, and the products are in one column.

- `Product screen`: 
    - *Width over 1200*: the content is in two columns - the left column contains the image, the right one has the price, "Add to cart" button and description; the "Back" button is centered on the bottom of the page;
    - *Width 900-1199*: still in two columns, but the price and "Add" button are moved up in the center (just below the title), and aligned horizontally; the "Back" button is now on the left column, below the image;
    - *Width 600-899*: all the content is now on one column, with the exception of the price and "Add button", which are still aligned horizontally;
    - *Width below 600*: now also the price and button are aligned vertically.

- `Checkout screen`: 
    - *Width over 1200*: the content is in two columns - the left column contains a 2-column grid of the cart items, and the right columns has the checkout details and options;
    - *Width 900-1199*: the overall content is still in two columns, but the grid of cart items is now a 1-column list;
    - *Width 600-899*: the two sections (cart and checkout) are now aligned in one column, but the cart items are again in 2 columns;
    - *Width below 600*: now the cart items are again in a 1-column ListView.

- `Confirmation screen`: The list of purchased products is displayed in respectively 4, 3, 2 and 1 column.

## Challenges

Compared to the first project, this second project has been by far more demanding, in terms of complexity, but also of quantity of the requirements.

- Not only was the required number of features much higher, but the specifications were in general more "broad", in the sense that I had to "invent" more specifications for myself, in order to bring a finished product. For instance, I had to decide the contents of my website, and I had to invent the checkout options (which, since unspecified in the handout, I simplified to a set of cards with only card owner and card number). Although many would see this as an advantage because it leaves more freedom for the implementation choices, I would rather see this as a challenge, because I needed to take more time in the ideation phase.
    - Related to this, unlike last time, the project handout did not contain any "Get started" section, which provided useful guidelines when you are overwhelmed by many requirements, and have to decide in which order to implement them in a time-efficient way.<br />

- Responsiveness has been - once again - a major challenge, this time with more breakpoints and more screens to adapt. In general, when it comes to responsiveness, one challenge was the ideation of the layouts, the other was to achieve them as intended, without bugs, with Flutter.<br />
The hardest part was how to get rid of the many overflows and unbounded sizes accidentally created by the many Rows, Columns, grids and lists present in the project. Despite the previous assignments had addressed all of these problems, it is hard to remember every rule and best practice for a responsive layout, meaning that there is always going to be a lot of trial and error in the process.

- On some occasions, I felt like the course material was not enough to implement some advanced features, so I spent more efforts researching new, unexplored Flutter components. For instance, I felt like having a whole page only for the profile settings was unnecessary, so I decided to explore Drawers for this purpose. Also, to reduce the scrolling on mobile, in the listing page I wanted to collapse the listed categories in one single Dropdown; this same component would be later used also for choosing the payment option.

## Learning outcomes

- Once again, generally speaking, learning how to use Flutter has been a major learning outcome for me. This language is going to strengthen my technical competencies in the development of UIs, without having to be specialized on one type of device, or OS. My expectation is that the knowledge of languages like this one allow for more versatility as a developer: I could either do web development, mobile development, TV development or others... applying the same knowledge.

- Similarly to last time, with this project I consolidated what I learned during the past assignments: this time, the focus was on SharedPreferences, input handling, dismissibles and - again - layout building; I got to train myself on these important aspects of Flutter.

- Following one of the challenges, I went beyond the course material and explored a few new Flutter components, discovered either from the Flutter documentation, or from StackOverflow. I used components such as Drawers, Dropdowns, Snackbars and SearchDelegates, which I do not recall to have seen during the course; I also discovered new properties from already known components, such as the tooltip for the IconButtons, which are a really simple, yet useful feature to add more interaction feedback and intuitiveness.
