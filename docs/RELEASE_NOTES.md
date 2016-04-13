**Android Release Notes**

3.2.7 (v120)
============

**Features:**

- Improved Analytics

- Added option for testing SDK in Live environment without placing actual orders. Refer to [docs](SDK_REFERENCE.md#-set-testing-mode-for-order-placing)

- Added option to use all available `Products` and `Product Variants` with default pricing. Refer to [docs](SDK_REFERENCE.md#-set-all-products-and-variants)

**Bugs:**

- Handled expired promo coupons

- Fixed coupon savings when items are deleted on `Shipping Review` Screen

- Fixed currency conversion when changing shipping country

- Fixed overlay images for some products in `Products` V2 Screen

- Fixed hanging Progress Dialog when handling large cached data

###

3.2.2 (v120)
============

**Features:**

-

**Bugs:**

- Fixed backwards compatibility with v3.1.28

- Fixed wrong format when exporting Multi-Item products to server; Fixed compatibility with Vendor API

###

3.2.1 (v120)
============

**Features:**

-

**Bugs:**

- Fixed an issue with list-type products

###

3.2.0 (v120)
============

**New products:**
`SCARVES`
`STICKERS`
`JERSEY_BLANKETS`
`LAPTOP_COVERS`
`PET_BANDANA`
`PET_BOWLS`
`APRONS`
`FLOORMATS`
`YOGA_MATS`
`BEER_MUGS`
`CURTAIN_SHEERS`
`FLIP_FLOPS`
`BODY_PILLOWS`
`BATH_TOWELS`
`ACCESSORY_POUCHES`
`WASH_CLOTHS`
`INFANT_CLOTHING`
`SWEATSHIRTS`
`HOODIES`
`YOUTH_APPAREL`
`TODDLER_CLOTHING`
`LEGGINGS`
`PREMIUM_COASTERS`
`LEATHER_GALLERY_WRAPS`
`FRAMED_LEATHER_GALLERY_WRAPS`
`OUTDOOR_CANVAS_WRAPS`
`NOTEBOOKS`
`NOTEPADS`
`MAGNETS`
`STICKERS`
`WATER_BOTTLES`
`TAPESTRIES`
`FOLDED_CARDS`

**Features:**

- Payment options now default to Gooten's, if not specified

- Side Menu redesigned

- Search moved to title bar

- `Shopping Cart` icon added to `Select Country` and `Select Currency` screens

- `Keep Shopping` button moved to title bar when necessary

- Added support for transparency on specific products

- Added `Estimated International Arrival` to `Product Details` screen

- Added a method to manually set featured products in `Products` screen. Refer to [docs](SDK_REFERENCE.md#-set-featured-products-in-hero)

- Added a method to add an image and link to featured product section in `Products` screen. Refer to [docs](SDK_REFERENCE.md#-set-promo-image-with-link-in-hero)

- Customizable `Make It` button

- Customizable `Cancel` button in `Product Options` screen

- Customizable indicator for Photo Count for Photo Albums in `Select Images` screen

- Customizable `Keep Shopping` button

- Customizable `Remove Item` button in `Shopping Cart` screen

- Customizable prices display in `Product Details V2` screen

- Customizable `Add Address` screen

- Customizable screen titles

- Screen titles automatically shrink to fit available space

- Facebook SDK updated

- Optimized SDK storage usage

- Image cache is cleared every 24h

**Bugs:**

- Fixed wrong price being displayed in `Add Address` and `Select Address` screens when coupons are applied

- Fixed a bug when user is able to select more than maximum allowed photos for a given product

- Fixed a crash when using `SingleOptionStepStrategy.SKIP` strategy

- Fixed a crash for `Puzzles` products

- Fixed missing `Use Same Look` dialog for some products

- Prevented opening of multiple `Shopping Cart` items at the same time

- Prevented opening of multiple screens from menu at the same time

- Prevented opening of multiple payment options at the same time

- Fixed a bug with transparent `Phone Cases`

- Fixed a crash when going back from `Checkout` screen on some devices

- Fixed overlapping product descriptions in `Shopping Cart` screen

- Fixed image loading on Android Emulator (AVD)

- Fixed missing page selection dropdown for `Flat Cards` product

- Fixed "default text" warning not shown for `Folded Cards` product

- Fixed a crash when Facebook Page Url is not set

- Fixed non-transparent search icon

###

3.1.28 (v119)
=============

**Features:**

- Ability to contact our Customer Support when an order fails two times

- Added checkout progress indicator. Refer to [docs](SDK_REFERENCE.md#-show-checkout-progress-below-the-title-bar-in-shopping-cart)

- Product Description is now expandable in `Product Details` V2 Screen

- Product price is displayed in Title Bar during checkout

- Added a method to hide `Remove Item` button from `Shopping Cart` Screen. Refer to [docs](SDK_REFERENCE.md#-set-delete-mode-for-shopping-cart)

- Removed list view from `Products` V2 Screen

- Removed `Featured Products` button from Side Menu

- Added shopping cart summary to `Shopping Cart` screen

- Overlays are automatically resized to the required size

- Added fallback strategy when desirable `Options` Screen layout does not match API data

**Bugs:**

- Fixed segmentation fault in `Customize List` Screen

- Fixed minor issues in `Options` Screen

- Fixed crash in `Payment Method` Screen

- Fixed layout names for `Flat Cards` product

- Fixed crash on `Mousepads` product

- Fixed missing `Photo Arrangement` dialog when device is put to sleep on `Customize Product` Screen

- Fixed Billing Address when using PayPal payment method

- Fixed a NullPointerException reported by Keepy (github issue #151)

- Fixed a crash caused by missing overlays on some products

- Fixed missing authorization screen when app is brought back from background

###

3.1.21 (v118)
=============

**IMPORTANT NOTE TO PARTNERS**: We have made changes to Framed Canvas’ and T-shirts products. These products will not behave as intended if enabled in the production version of your admin panel for iOS and Android clients. A work around is to disable these products in your admin panel. This will ensure a better user experience.  

**Features:**

- Added an exception when SDK is invoked without specifying any Payment methods

- Added ability to make a purchase when a coupon brings order total to $0

- Added ability to enter Billing Address when making purchases

- Removed 5-character limit when entering Zip codes

- Added confirmation dialog when logging out of photo sources

- Customizable user flow for `Options` screen. Refer to [docs](SDK_REFERENCE.md#-set-strategy-for-steps-with-single-option)

- V2 screens can be used without passed-in image

- Vendor logo can now be displayed in V1 screens

- `Cancel` button in `Options` screen is now customizable. Refer to [docs](SDK_REFERENCE.md#-set-cancel-button-visibility)

- Resolution warning thresholds reduced from 0.5 to 0.33

- Updated `Google Photos` icon

- Added new options for some products

- Added crash reporting

**Bugs:**

- Fixed a bug which occurred when some images were passed in, but `Preselected` photo source was not selected

- Fixed a bug which occurred when country was changed from within a category

- Fixed a crash when dialog is shown while the app is in the background

- Fixed a crash on image preview in V2 `Product Details` screen

- Fixed image alignment in MINIBOOKS product

- Fixed `Add more photos` button visibility when `PIOConfig.setShowPhotosInCustomize()` is set to `false`

- Fixed transparency issues in MINIBOOKS product

- Fixed a crash in WALL_CALENDARS product when using auto-populate option

- Fixed bad overlays and bad/missing icons for some products

- Fixed text being cut off on some labels

###

3.1.7 (v118)
============

**Features:**

- Redesigned `Products` screen

- All products enabled in `Products` screen V2

- PayPal disabled when order total is zero

- Added 'Auto Populate' feature for Wall Calendars and Ottomans

- Added new layout step strategy: `SKIP_FOR_SINGLE_PASSED_IMAGE` (refer to [this method](SDK_REFERENCE.md#-set-strategy-for-choose-layout-step-on-product-options-screen))

**Bugs:**

- Fixed a crash caused by setting `PIOConfig.setShowOptionsInCustomize()` to `false`

- Fixed loading of large overlay images

- Fixed a crash on Mementos product

- Fixed image manipulations being lost when screen turned off/on in List-type products

- Adjusted promo text in V2 `Product Details` screen

- Changed price container color

- Added missing icons for some product options

- Fixed 'Decrease text size' button

- Fixed a crash when replacing photos in Layflat Photobooks

- Buttons in `Customize Product` screen are now closed when tapping outside

###

3.1.0 (v118)
============

**Features:**

- Add text to product design

- New Product: Layflat Photobooks

- New Product: Flat Cards

- New Product: Mementos

- New Product: Adjustable Strap Tote

- New Product: Bandana

- New Product: Dopp Kits

- New Product: Fabric By The Yard

- New Product: Framed Canvas

- New Product: Hand Towels

- Warning when selected photos are too small to be printed on selected product

- New Shopping Cart layout

- New Screen: `Past Orders`

- New Screen: `Order Details`

- New Screen: `Order Status`

- `What's New` Dialog added

- Merged all product options into single page

- Added method for showing 'Cancel' button on Options Screen (`PIOConfig.setCancelOptionsButtonVisibility(boolean isVisible)`)

- Added method for setting Retail Price discount percent (`Product Details` screen)

- Added method to enable Template filtering based on passed photos count (`PIOConfig.setLayoutStepStrategy(LayoutStepStrategy strategy)`)

**Bugs:**

- Fixed a crash caused by Facebook ID not being set in PIOConfig

- Fixed overlapping Gear icon and Back button on `Order Completed` screen

- Fixed an issue which caused a crash on some devices when too many photos are selected

- Autoresize subtotal text in `Shopping Cart` screen

###

3.0.27 (v117)
============

**Features:**

- /

**Bugs:**

- Removed dependency on FacebookSDK when Facebook is not being used as a Photo Source

- Fixed updating of prices for Shopping Cart items

###

3.0.24 (v117)
============

**Features:**

- Updated design of `Product Details V2` screen

- Added a method to remove logo from `Order Completed` screen

**Bugs:**

- /

###

3.0.18 (v117)
============

**Features:**

- Added `Product Details V2` screen

- `Create It` button renamed `Make It`

**Bugs:**

- Fixed Unicode support in API calls

###

3.0.13 (v117)
============

**Features:**

- Added `Products V2` screen

**Bugs:**

- Fixed `Products` screen sometimes showing list instead of grid

- Fixed duplicating items in Shopping Cart

###

3.0.4 (v117)
============

**Features:**

- Order Number on Order Completed screen can be selected and copied

**Bugs:**

- Fixed Address validation issues

- Fixed `setProductSkuFromApp()` method

- Fixed deletion of items on Shipment Review screen

###

3.0.0 (v117)
============

**API Changes:**

- Please refer to [Migration Guide](MIGRATION_GUIDE.md)

**Features:**

- Reduced SDK size by half

- Updated Facebook SDK to latest version (4.2.0)

- Added support for new Products format

- Added new customization steps for some products

- Added Discount Amount and Coupon Code to Order Completed callback

- Added full-screen image preview on Product Details screen

- Added fourth customizable font type (Normal, Light, Bold, *Title*)

- Added a method to clear all saved Shipping Addresses

- Turned off Google Analytics in Staging mode

**Bugs:**

- Fixed Credit Card number validation - All card types are now supported

- Fixed image rotation according to EXIF attributes

- Fixed a crash which occured when using 'jump to Shopping Cart' and the Shopping Cart is empty

- Fixed negative values in Shopping Cart

- Some tweaks to Customize Product screen

- Fixed issues with applying promo coupons

- Fixed missing thumbnails in Shopping Cart for some products

- Fixed memory issues on some devices when creating multi-item products

- Fixed Products search in Side Menu

- Fixed an issue when loading Facebook albums with lots of photos

- Fixed a crash when paying using PayPal and order total is $0

- Stability & code improvements

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
