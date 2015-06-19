**Android Release Notes**

### 

2.3.0a (v116)
============

**Features:**

- /

**Bugs:**

- Fixed orders not getting through

### 

2.3.0 (v116)
============

**Features:**

- New Product: Acrylic Trays

- New Product: Art Poster

- New Product: Beach Towel

- New Product: Cloth napkins

- New Product: Duvet Covers

- New Product: Giclee Art Prints

- New Product: Glass Cutting Board

- New Product: Mugs

- New Product: Ottoman

- New Product: Pillow Shams

- New Product: Placemats

- New Product: Posters

- New Product: Puzzle Tin

- New Product: Stone Coaster

- New Product: Tabletop Canvas Wraps

- New Product: Wall Clings

- Product Details screen now shows "Price" instead of "Starting at" for products which have the same price for all variants

- If an invalid Promo Code is entered, previously entered valid Promo Code (if any) is used

- Added `PhotobucketPhotoSource.setDefaultAlbumId(String defaultAlbumId)` method

- Dropbox photo source now uses OAuth 2.0 access tokens when downloading images

- Added `PIOConfig.setAvailableProducts(List<ProductType> availableProducts)` method which allows users to customize product availability in SDK

- Refactored Options screens for all products

**Bugs:**

- Fixed a crash caused by bad data returned from server

- Refactored products to use new Custom Steps mechanism

- Removed legacy activities

- Removed incorrect estimated arrival dates from Order Review and Order Completed screens

- Images are now being rotated correctly, according to EXIF attributes

- Fixed applying coupon code when shipping method is changed

- Improved bitmaps caching

- Improved Dropbox thumbnails quality

- Removed 'Change Background' button for products which don't support background color

- Metal Prints - Fixed image alignment on Options screen

- Fixed an issue with the wrong product being displayed on Customization screen

- Fixed cut-off selectors on some Option screens

- Product specifics are now displayed in shopping cart instead of the SKU string which could be misleading because of imperial/metric measurements (github issue #136)

- Fixed imperial/metric units on Option screens

- Fixed increasing MaxPhotos count for Throw Pillows

- Fixed photos counter when Photo Sources are disabled

- Fixed a crash when adding more photos on Customization screen

- Fixed status bar hiding on Customization screen

- Fixed product names cut off on Order Complete screen

- Fixed a crash when starting the SDK without an Internet connection

- Fixed "Confirming Order Information" dialog staying visible forever after phone was put to sleep

- Fixed swipe in Address List

### 

2.1.13 (v116)
============

**Features:**

- /

**Bugs:**

- Fixed bug which caused application to occasionally crash when recycled bitmaps are drawn

- Fixed authorisation on Facebook photo source

- Fixed bug when images where not visible on Admin panel for orders which contained photos from Dropbox photo source

- Fixed pre-filling State field on Add Address screen when state is selected from dropdown

### 

2.1.12 (v116)
============

**Features:**

- Added instructions for customizing "How It Works" section of the SDK

- Applied coupon codes are now stored when user leaves the SDK

**Bugs:**

- New fix for display issues on Customize screen [*github issue \#130*](https://github.com/printdotio/printio-android-sdk/issues/130)

- Fixed a bug with serialization of PhotoSource objects

- Fixed handling of invalid Build Options

- Fixed broken Choose Options screen for some products [*github issue \#125*](https://github.com/printdotio/printio-android-sdk/issues/125)

- Fixed Choose Options selection box alignment [*github issue \#129*](https://github.com/printdotio/printio-android-sdk/issues/129) 

### 

2.1.9a (v116)
============

**Features:**

- Added Custom Photosources feature

- Added Select All button to Select Photos screen

- Android devices are now shown first in Phone Cases

- Added methods to get ProductType enum from Product ID (`ProductType.getProductType(int id)` and `ProductType.getProductType(int id, boolean isLive)`)

- Passed promo code is now automatically applied

- Photos count is now displayed for Photobucket folders

**Bugs:**

- Fixed display issues on Customize screen [*github issue \#130*](https://github.com/printdotio/printio-android-sdk/issues/130)

- Fixed a bug where photo manipulations were lost in sigle-photo layouts when app was put to background

- Removed invalid placeholders

### 

2.1.8 (v116)
============

**Features:**

- Switched to ProductType enum instead of raw Product ID values from PublicConstants.ProductIds

- Moved PIOConfig enums to separate package (print.io.piopublic)

**Bugs:**

- Fixed an issue with absolute-value promo coupons and negative total values

- Minor layout tweaks

### 

2.1.7 (v116)
============

**Features:**

- Added support for Final coordinates (new product format) 

**Bugs:**

- /

### 

2.1.6 (v116)
============

**Features:**

- /

**Bugs:**

- Fixed an issue with Customize view which caused it to measure its dimensions incorrectly

- Fixed infinite loading dialog when screen is turned off during loading on Customize screen

### 

2.1.5 (v116)
============

**Features:**

- /

**Bugs:**

- New interface for CANVAS_POSTERS

### 

2.1.4 (v116)
============

**Features:**

- /

**Bugs:**

- Fixed product upload for PRINTS, PROFESSIONAL_PRINTS, METAL_MAGNETS [*github issue \#127*](https://github.com/printdotio/printio-android-sdk/issues/127)

- Fixed crash when reading PIOConfig from persistence

### 

2.1.3 (v116)
============

**Features:**

- /

**Bugs:**

- Fixed some products crashing on certain devices

- Increased RestClient timeouts

- Fixed crash in Framed Prints reported by Photobucket

- Fixed Customization screen sometimes not drawing correctly

### 

2.1.2 (v116)
============

**Features:**

- /

**Bugs:**

- Customization screen waits until product design is loaded before displaying product

- Hidden keyboard on Add Address screen when Save Address button is clicked

- Removed unnecessary help text for Canvas Wraps

### 

2.1.1 (v116)
============

**Features:**

-  Display exact price instead of "starting at $x" on Product Details screen for products which have the same price for all Product Variants

**Bugs**

- Added missing prices for some products

### 

2.1.0 (v116)
============

**Features:**

- /

**Bugs:**

- Fixed shipping address autocomplete issue [*github issue \#123*](https://github.com/printdotio/printio-android-sdk/issues/123)

- Product Details screen - Changed "Create It" button color to Secondary color (green) to match iOS

### 

2.0.7 (v116)
============

**Features:**

- /

**Bugs:**

- Fixed a bug with drawing background layer for products without solid background color in Customization screen

- Canvas Wraps, Framed Prints and similar products - Customization Step 2 - Moved items closer to the couch on the bottom of the screen for more accurate preview; Increased spacing between items

- Wall Calendars - Added years next to months in drop down menu on Customization screen

- Wall Calendars - Show calendar names instead of "1 Photo" in Step 1

- Wall Calendars - Bigger images in Step 1

- Wall Calendar - Fixed a crash that ocurred when quickly tapping next button

- Professional Prints and Prints - Added missing preview images in Options screen

- Canvas Minis - Removed couch image from Customization Step 1

- Fixed a crash in Framed Prints reported by Photobucket

- Fixed "Price of Professional Prints not visible on All Products view"

- Fixed various minor layout issues (selectors, borders, margins)

### 

2.0.6 (v116)
============

**Features:**

- /

**Bugs:**

- Canvas Wraps - Bigger images in Step 1

- Fixed "Change Country" icon to be the same size as the rest of the icons in Side Menu

- Dog Beds - Fixed some layout issues (sizes on Choose Options screen are now displayed in one row and some of preview items were cut off)

- Wall Calendar - Fixed missing count on Shopping Cart icon when adding more photos from Customization screen

### 

2.0.5 (v116)
============

**Features:**

- New Product: Dog Beds

- New Product: Canvas Posters

- New Product: Canvas Minis

- New Product: Pro Prints

- New Product: Rugs

- New Product: Tote Bags

- New Product: Wall Calendars

**Bugs:**

- Fixed a glitch when drawing product in Customization screen caused by low number precision

- Fixed missing symbol in Choose Currency button in Side Menu

### 

2.0.4 (v116)
============

**Features:**

- Split `PIO.start(Context, PIOConfig)` method into `PIO.setConfig(Context, PIOConfig)` and `PIO.start(Context)`

**Bugs:**

- /

### 

2.0.3 (v116)
============

**Features:**

- /

**Bugs:**

- Throw Pillows - Hidden unneeded "Step 4" from Color Options screen

### 

2.0.2 (v116)
============

**Features:**

- Optimized book products; Removed paging

**Bugs:**

- Fixed "Parts of images are missing" in Customization screen

- "Step 1,2,3,4" text is now bold in Choose Options screen

### 

2.0.1 (v116)
============

**Features:** /

**Bugs:**

- Fixed a crash in Acrylic Prints

- Fixed a crash in Coasters

### 

2.0.0 (v116)
============

**Features:**

- Return structured data when closing SDK

- Throw Pillows - Use the same look for front and back side of the pillow

- Ability to change shipment options on Shopping Review screen

- Updated PayPal SDK to v2.7.1

- Added method closeWidgetFromShoppingCart()

- Split PIO class into PIO and PIOConfig classes

- Improved activity navigation

- Caching of Photobucket images so the SDK doesn't make a new API call every time

- Added Google Analytics tracking

- Added a method to choose available payment options

- Fixed some differences in Dialogs layouts between Android and iOS

- Added method for selecting default products list screen: Featured Products (large items) or All Products (small items)

- Added method to remove "Add More" button from Shopping Cart screen [*github issue \#84*](https://github.com/printdotio/printio-ios-sdk/issues/84)

- Added Jump to screen method

- Images passed in using setImageUris() now shown as a separate Photosource (Preselected)

- Set passed in image to be first in row for all photo sources

- Added ability to pass URLs to Preselected Photosource

- Select default country based on location

- Change Layout from customize screen

- Added method to hide help button in Customize Product screen

- Improved handling of API calls

- Added caching of API calls

- Removed product prices from navigation bar

**Bugs:**

- Fixed "Use passed image as thumb for one photo template"

- Removed images from book products list view screen when images are unselected on Select Images screen

- Fixed a crash in Image Editor screen

- Fixed a crash in Throw Pillows

- Fixed aspect ratio for product images [*github issue \#75*](https://github.com/printdotio/printio-android-sdk/issues/75)

- Images not re-uploaded when image urls are passed to SDK using setImages()

- Throw Pillows - Automatically load images on the back side of the pillow

- Fixed disappearing selected photos in Select Images screen when phone goes to sleep

- Fixed "Logging in another photo source causing deselecting previously selected photo"

- Fixed a crash in Minibooks

- Fixed "Unable to select more than one image on Select Image screen" for Magnetgram

- Fixed Changeable Country and Currency toggle buttons in PrintIO SDK Example app

- Fixed a crash in Select Address screen

- Added title on pop up in Select Address screen

- Thick Prints - added missing blue border on "Duplicate to Fill Order" button

- Book products - screen with list view - Fixed page numbers

- Image Editor screen - Fixed minimum zoom level - locked to product size

- Image Editor screen - Fixed zoom out

- Fixed "Price for item is too long and is using 2 lines" [*github issue \#100*](https://github.com/printdotio/printio-android-sdk/issues/100)

- Fixed a crash in production (java.lang.NullPointerException) [*github issue \#119*](https://github.com/printdotio/printio-android-sdk/issues/119)

- Fixed uploading product photos for high-image count products [*github issue \#120*](https://github.com/printdotio/printio-android-sdk/issues/120)

- Fixed a crash when leaving PrintIO SDK

- Fixed some issues when putting phone to sleep

- Deselected image from Select Images screen when image is removed from Customization screen

- Fixed a crash when adding Preselected Photosource in PrintIO SDK Example app

- Fixed app to use selected Country Code (always was US)

- Book products - Fixed "Add More Images" behaviour

- Removed "Add More Photos" dialog when images are preselected

- "Cannot use Recycled Bitmap" crashes happen less frequently