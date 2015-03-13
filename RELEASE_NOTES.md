##Android Release Notes

2.0.4 (v116)
============

**Features:**

-   Split `PIO.start(Context, PIOConfig)` into `PIO.setConfig(Context, PIOConfig)` and `PIO.start(Context)`

**Bugs:**

-   /

### 

2.0.3 (v116)
============

**Features:**

*   /

**Bugs:**

* Throw Pillows - On Color Options screen, for a moment, Step 4 appears on the screen

### 

2.0.2 (v116)
============

**Features:**

* Optimizing \*book products

**Bugs:**

* Customization screen - Parts of images are missing

* Choose Options screen - "Step 1,2,3,4" text should be bold

### 

2.0.1 (v116)
============

**Features:** /

**Bugs:**

* App has crashed - Acrylic Prints

* App has crashed - Coasters

### 

2.0.0 (v116)
============

**Features:**

* Return structured data when closing SDK

* Throw Pillows - Use the same look for back side of pillow

* Ability to change shipment options

* Added option on Shopping Review screen to offer expedited/overnight shipping options

* Updated PayPal SDK

* Created method PIO.closeWidgetFromShoppingCart()

* Split PIO class into PIO and PIOConfig classes (updated docs accordingly)

* Created internal SDK properties

* Improved activity navigation

* Caching of Photobucket images so the SDK doesn't make a new API call every time

* Added Google Analytics

* Ability to choose available payment options

* Dialog layout differences between Android and iOS

* Method for setting default products screen (set Featured screen or All Products screen to be first load)

* Removing “Add More” from cart Via method

* Jump to screen

* New Photo Image Source for Passed in Images

* Set passed in image to be first in row for all photo sources

* Add in ability for app to pass in URL for Photo

* Default country by location

* Change Layout from customize screen

* Created method to hide help button in Customize Product screen

* Improved handling of API calls

* Added caching of API calls

**Bugs:**

* Use passed image as thumb for one photo template" doesn't work

* Unselected image from Select Images Screen remains selected on the Customization screen list view

* App has crashed - Image Editor screen

* App has crashed - Throw Pillows

* Prints product image is stretched horizontally

* Images are downloaded and re-uploaded on client when image urls are passed to setImages

* Throw Pillows - On the Back side of pillow doesn't load images automatically on the layout

* Select Images Screen - Selected photos disappearing when user puts phone to sleep

* Logging in another photo source causing deselecting previously selected photo

* App has crashed - Minibooks

* Magnetgram - Unable to select more than one image on Select Image screen

* Changeble Country and currency toggle button doesn't work correctly

* Select Address screen - App has crashed

* Select Address screen - Add Title on Pop up

* Thick Prints - missing blue border on "Duplicate to Fill Order" button (added icon which should be changed)

* Customization screen with list view - Page Number is not correct

* Image Editor screen - User is able to reduce image outside of the layout

* Image Editor screen - Zoom out does not work

* Price for item is too long and is using 2 lines

* Crash in production java.lang.NullPointerException

* Error uploading product photos for high-image count products

* App has crashed after leaving PrintIO SDK

* Putting phone to sleep causing some issues

* Removed image from Customization screen remains selected on the Select Images Screen

* App has crashed - Adding Preselected Source on SDK Example

* Country Code is always applied on admin panel, for not supported countries, as USA

* Book products - Add More Images does not work correctly

* Remove dialog for "Add More Photos" when images are preselected

* "Cannot use Recycled Bitmap" crashes still happens in app
