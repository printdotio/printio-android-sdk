Migrating to v3.1.25 from v3.1.21
========

Method `PIOConfig.setShowFeaturedProductsByDefault` was removed and all products are shown by default.
Enum value `SideMenuButton.FEATURED_PRODUCTS` was removed.  

Migrating to v3.1.21 from v3.1.7
========
**Changes in AndroidManifest.xml**
Activity declarations have been modified and new Activities were added.  
Please refer to [Project Setup](PROJECT_SETUP.md#3-activities)

Migrating to v3.1.0 from v3.0.24
========
**New feature - Text**

A new feature has been added in this version, which allows users to add text to products.  
In order for this feature to work, `fonts` folder needs to be added to the `assets` folder of the host app.  
The folder can be found in our [Example app](https://github.com/printdotio/printio-android-example/tree/master/PIOSDKPOConcept/assets)

**Changes in AndroidManifest.xml**

Following activity declarations should be added:
```xml
<activity android:name="print.io.ActivityProductOptions" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivitySelectPhotos" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityCustomizeList" android:screenOrientation="portrait" android:windowSoftInputMode="stateHidden" />
<activity android:name="print.io.ActivityOptionBackground" android:screenOrientation="portrait" android:windowSoftInputMode="stateHidden" />
```

The following activity declarations should be removed:
```xml
<activity android:name="print.io.ActivityProductPreview" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityCustomSteps" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityImageUpload" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityStickerBook" android:screenOrientation="portrait" android:windowSoftInputMode="stateHidden" />
<activity android:name="print.io.ActivityCaseColorStyle" android:screenOrientation="portrait" android:windowSoftInputMode="stateHidden" />
```

The following activity declaration:
```xml
<activity android:name="print.io.ActivityCustomizeProduct" android:screenOrientation="portrait" />
```
should be replaced by:
```xml
<activity android:name="print.io.ActivityCustomizeProduct" android:screenOrientation="portrait" android:windowSoftInputMode="adjustResize" />
```

The following activity declaration:
```xml
<activity android:name="print.io.ActivityCustomizePhotobook" android:screenOrientation="landscape" />
```
should be replaced by:
```xml
<activity android:name="print.io.ActivityCustomizePhotobook" android:screenOrientation="landscape" android:windowSoftInputMode="adjustResize" />
```

**Changes in `PIOConfig` class**

Medhod `PIOConfig.hideEditButtonInShoppingCart()` has been removed as well as the Edit button in the Shopping Cart.

Migrating to v3.0.24 from v3.0.13
========
**Changes in `PIOConfig` class**

Mechanism for showing vendor logo on screens has been changed. New method for showing logo on screens [`PIOConfig.setVendorLogoOnScreen`](SDK_REFERENCE.md#-show-vendor-logo-on-screens) has been added and previously defined method for removing logo from Payment and Order Completed screens `PIOConfig.removeLogoFromPaymentScreen` has been removed.

If you used `removeLogoFromPaymentScreen(true)` to remove logo from Payment screen in your SDK initialization code, then you should simply remove this method call, as logos are now hidden from all screens by default.

Otherwise, if your SDK was showing overridden logos, you should add the following code to your SDK initialization code:
```java
PIOConfig.setVendorLogoOnScreen(Screen.PAYMENT, R.drawable.icon_logo_payment_screen);
PIOConfig.setVendorLogoOnScreen(Screen.ORDER_COMPLETED, R.drawable.icon_logo);
```


Migrating to v3.0.13 from v3.0.4
========

**Changes in AndroidManifest.xml**

Following activity declarations should be added:
```xml
<activity android:name="print.io.ActivityProducts" android:screenOrientation="portrait" android:windowSoftInputMode="adjustResize"/>
<activity android:name="print.io.ActivityProductsV2" android:screenOrientation="portrait" android:windowSoftInputMode="adjustResize" />
<activity android:name="print.io.ActivityProductDetailsV2" android:screenOrientation="portrait" />
```

The following activity declaration should be removed:
```xml
<activity android:name="print.io.ActivityFeaturedProducts" android:screenOrientation="portrait" android:windowSoftInputMode="adjustResize"/>
```

**Changes in `Screen` enum**

Value `FEATURED_PRODUCTS` has been renamed `PRODUCTS`.

**Changes in `PIOConfig` class**

- Disabling screens

Mechanism for disabling screens has been changed.  
Since version v3.0.13, the correct way to disable screens is to pass a `List<Screen>` to the `setDisabledScreens()` method.

For example, instead of using:
```java
PIOConfig#setSkipProductDetails(true); 
// ... or PIOConfig#setPhotoSourcesDisabled(true)
```
you should now use:
```java
//import print.io.piopublic.Screen;

PIOConfig#setDisabledScreens(Arrays.asList(Screen.PRODUCT_DETAILS)));
// ... or PIOConfig#setDisabledScreens(Arrays.asList(Screen.PRODUCT_DETAILS, Screen.SELECT_PHOTOS)));
```

Note: Up until v3.0.13, disabling Product Options screen was done by passing SKU to the SDK.  
In order to be consistent, this way of disabling Product Options has been changed.  
As of v3.0.13, disabling Product Options is done the same way as for other screens.  
If Product Options screen is disabled, passed SKU will still be used to specify product variant or, if SKU was not passed, default SKU will be used.

- Jump to screen

Mechanism for jumping to screens has been changed.  
Since version v3.0.13, concept of screen flags has been removed, as well as `setJumpToScreenFlags(int)` and `setJumpToScreen(Screen, int)` methods.  

Instead of screen flags, a new method `setJumpToScreen(Screen, Screen)` for specifying "navigate-back screen" has been added.  

For example, if you want to launch the SDK at `Shopping Cart` screen, and go to `Products` screen when user navigates back, you would have to do the following:

```java
PIOConfig#setJumpToScreen(Screen.SHOPPING_CART, Screen.PRODUCTS);
```


Migrating to v3.0.4 from v3.0.0
========
**Changes in `PIOConfig` class**

Method `setCountryOnFeaturedProducts` has been removed and new method `showCountrySelectionOnScreen` for showing country selection bar on arbitrarily screens has been added.

For example,  instead of using
```java
PIOConfig#setCountryOnFeaturedProducts(true);
```
you should use 
```java
PIOConfig#showCountrySelectionOnScreen(Arrays.asList(Screen.FEATURED_PRODUCTS));
```


Migrating to v3.0.0 from v2.3.0
========
 ---
**Changes in AndroidManifest.xml**

Following activity declarations should be added:
```xml
<activity android:name="print.io.ActivityCustomizePhotobook" android:screenOrientation="landscape" />
<activity android:name="print.io.ActivityProductPreview" android:screenOrientation="portrait" />
```
Following activities are no longer used and should be removed:
```xml
<activity android:name="print.io.ActivityAnimatedHelp" android:screenOrientation="portrait" />
```

**API Changes**

Screen titles are now displayed using a separate font.  
Use the new method [`PIOConfig#setFontPathInAssetsTitle(String)`](SDK_REFERENCE.md#-set-custom-fonts-from-main-app-bundle) to set Title font.
To keep using the same fonts, use the same font for `setFontPathInAssetsNormal()` and `setFontPathInAssetsTitle()`.  

Method `PIOConfig#setSplashScreenEnabled(boolean isSplashScreenEnabled)` has been removed.  
Use [`PIOConfig#setSplashScreenTimeout(int splashScreenTimeout)`](SDK_REFERENCE.md#-splash-screen-settings) to enable or disable Splash Screen.  

Separate [colors](SDK_REFERENCE.md#-change-buttons-colors) for `Save To Cart` button have been added.  
To keep the design the same, set `Save To Cart` button colors to be the same as your secondary button colors.

A separate [text size](SDK_REFERENCE.md#-adjust-font-sizes) for `Create It` button has been added (`text_size_button_create_it`).
To keep the design the same, set `Create It` text size to be the same as the `text_size_normal` in your `dimens.xml`.  
Notice that there are two versions of `dimens.xml` file - `values/dimens.xml` for small screens and `values-sw330dp/dimens.xml` for normal screens.  

**Renamed Resources**
Resource `icon_arrow_back_2.png` has been renamed `icon_arrow_back.png`
[Set icon for back button](SDK_REFERENCE.md#-set-icon-for-back-button)  

Resources which define [primary and secondary buttons' colors](SDK_REFERENCE.md#-change-buttons-colors) have been renamed.  
res/colors.xml
```xml
<color name="green"> --> <color name="button_primary_default">
<color name="green_dark"> --> <color name="button_primary_pressed">

<color name="blue_light"> --> <color name="button_secondary_default">
<color name="blue_dark"> --> <color name="button_secondary_pressed">
```


Migrating to v2.3.0 from v2.1.13
========
 ---
**Changes in AndroidManifest.xml**
 
Update minSdkVersion and targetSdkVersion fields to following values:
```xml
<uses-sdk android:minSdkVersion="9" android:targetSdkVersion="19" />
```

Following activity declaration should be added:
```xml
<activity android:name="print.io.ActivityCustomSteps" android:screenOrientation="portrait" />
```

Following activities are no longer used and should be removed:
```xml
<activity android:name="print.io.ActivityStickerbooksType" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityPhoneCaseGrid" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityThickPrintGrid" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityCanvasWrapsGrid" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityCanvasWrapsNext" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityChooseGridLayout" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityThrowPillowGrid" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityStepsListView" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityShoppingMethods" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityShippingAddress" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityAcrylicBlocksGrid" android:screenOrientation="portrait" android:windowSoftInputMode="stateHidden" />
<activity android:name="print.io.ActivityChooseGridLayoutTwoScollViews" android:screenOrientation="portrait" />
<activity android:name="print.io.ActivityPreviewOnWall" android:screenOrientation="portrait" />
```
 ---
**Changes in `PIOConfig` class**

- Method `PIOConfig#setStepByStep()` has been removed.

- Method `PIOConfig#setJumpToScreen()` now accepts `print.io.piopublic.Screen` enum instead of int values from `PublicConstants.ScreenIds`.

For example, instead of using
```java
PIOConfig#setJumpToScreen(PublicConstants.ScreenIds.SCREEN_SHOPPING_CART, 0);
```
you should use
```java
//import print.io.piopublic.Screen;
PIOConfig#setJumpToScreen(Screen.SHOPPING_CART, 0);
```

- Method `PIOConfig#setPaymentOptions()` now accepts a `List` of `<print.io.piopublic.PaymentOptionType>` instead of packed ints from `PublicConstants.PaymentOptions`.

For example, instead of using
```java
PIOConfig#setPaymentOptions(PublicConstants.PaymentOptions.PAYMENT_OPTION_ALL);
```
you should use
```java
//import print.io.piopublic.PaymentOptionType;
List<PaymentOptionType> paymentOptions = new ArrayList<PaymentOptionType>(2);
paymentOptions.add(PaymentOptionType.PAY_PAL);
paymentOptions.add(PaymentOptionType.CREDIT_CARD);
PIOConfig#setPaymentOptions(paymentOptions);
```


Migrating to v2.1.9 from v2.1.8
========
 ---
**Changes with photo sources**

In order to support custom photo sources (defined by SDK users) new mechanism for photo sources has been introduced. 

As of v2.1.8 use of `PhotoSource` enum values have been replaced with corresponding classes implementing new `PhotoSource` interface. These classes are :

```java
print.io.photosource.impl.dropbox.DropboxPhotoSource
print.io.photosource.impl.facebook.FacebookPhotoSource
print.io.photosource.impl.flickr.FlickrPhotoSource
print.io.photosource.impl.instagram.InstagramPhotoSource
print.io.photosource.impl.phone.PhonePhotoSource
print.io.photosource.impl.photobucket.PhotobucketPhotoSource
print.io.photosource.impl.picasa.PicasaPhotoSource
print.io.photosource.impl.preselected.PreselectedPhotoSource
```

For example, previous code for defining list contaning Facebook and Phone photo sources would look like:

```java
List<PhotoSource> photoSources = Arrays.asList(PhotoSource.FACEBOOK, PhotoSource.Phone);
```
Now in order to create photo source simply create object by calling default constructor of photo source implementation class. Which would look like:
```java
List<PhotoSource> photoSources = Arrays.asList(new FacebookPhotoSource(), new PhonePhotoSource());
```
 ---
**Changes in `PIOConfig` class**

- Method `PIOConfig#setPhotoSources()` now accepts list of objects implementing `PhotoSource` interface instead of enum values as it was previously the case.

- Photo source configuration has been moved to corresponding photo source classes. 

For example, instead of using
```java
	PIOConfig#setInstagramClientId(String);
	PIOConfig#setInstagramCallbackUri(String);
```
you should use corresponding methods in `InstagramPhotoSource` class.
```java
	InstagramPhotoSource#setClientId(String);
	InstagramPhotoSource#setCallbackUri(String);
```
 ---
**Changes in AndroidManifest.xml**

Following activity declarations:
```xml
<activity android:name="print.io.social.Instagram" android:noHistory="true"  android:screenOrientation="portrait" />
<activity android:name="print.io.social.Flickr" android:noHistory="true"  android:screenOrientation="portrait" />
<activity android:name="print.io.social.Dropbox" android:noHistory="true" android:screenOrientation="portrait" />
```
should been changed to:
```xml
<activity android:name="print.io.photosource.impl.instagram.Instagram" android:noHistory="true" android:screenOrientation="portrait" />
<activity android:name="print.io.photosource.impl.flickr.Flickr" android:noHistory="true" android:screenOrientation="portrait" />
<activity android:name="print.io.photosource.impl.dropbox.Dropbox" android:noHistory="true" android:screenOrientation="portrait" />
```


Migrating to v2.1.8 from v2.x
========
 ---
**The `ProductType` enum**

`ProductType` enum has been introduced to substitute the use of actual values of Product IDs previously found in `PublicConstatns.ProductIds` class.  
As of v2.1.8, instead of using fields from `PublicConstatns.ProductIds` class you should use corresponding values from `print.io.piopublic.ProductType` enum.  

 ---
**Changes in `PIOConfig` class**

Method `setProductIdFromApp()` has been renamed to `setProductFromApp()`, and now accepts `ProductType` instead of `int` for specifying product. 

All enum definitions from `PIOConfig` class were moved to a separate package called `print.io.piopublic`.  
Because of this, you will have to change the following imports:
```
import print.io.PIOConfig.PhotoSource;
import print.io.PIOConfig.SideMenuButton;
import print.io.PIOConfig.SideMenuInfoButton;
```
to:
```
import print.io.piopublic.PhotoSource;
import print.io.piopublic.SideMenuButton;
import print.io.piopublic.SideMenuInfoButton;
```
### 
Migrating to v2.x from v1.x
========
 ---
- Create an instance of `PIOConfig`:
```
private PIOConfig config = new PIOConfig();
```
## 
- Instead of invoking static methods from `PIO` class, invoke methods on `PIOConfig` instance:
for example:
```
PIO.setLiveApplication(false);
```
becomes:
```
config.setLiveApplication(false);
```
## 
- Change following imports:
```
import print.io.PIO.PhotoSource;
import print.io.PIO.SideMenuButton;
import print.io.PIO.SideMenuInfoButton;
```
to:
```
import print.io.PIOConfig.PhotoSource;
import print.io.PIOConfig.SideMenuButton;
import print.io.PIOConfig.SideMenuInfoButton;
```
## 
- Use API_URL constants from print.io.PublicConstants class:
```
config.setApiUrl(PublicConstants.API_URL_STAGING);
```
or
```
config.setApiUrl(PublicConstants.API_URL_LIVE);
```
## 
- In your application class, replace the following method calls:
```
PIO.setParseApplicationId(PIOConstants.Parse.APPLICATION_ID);
PIO.setParseClientKey(PIOConstants.Parse.CLIENT_KEY);
PIO.initializeParse(this);
```
with:
```
PIO.initializeParse(this, PIOConstants.Parse.APPLICATION_ID, PIOConstants.PayPal.CLIENT_ID);`
```
## 
- If your app is using Instagram Photosource, you need to specify Instagram Callback URI:
```
public static final String CALLBACK_URI = "http://x-oauthflow-instagram";

config.setInstagramCallbackUri(PIOConstants.Instagram.CALLBACK_URI);
```
## 
- Use the following code to start the PIO SDK:
```
try {
	PIO.setConfig(this, config);
	PIO.start(this);
} catch (PIOException e) {
	e.printStackTrace();
}
```

API Changes
========

- `PIOConfig.setInstagramCallbackUri(String)` method is now required for Instagram photosource.

- `PIO.setPayPalReceiverEmail(String)` method has been removed. Receiver e-mail is not necessary anymore.

- `PIO.setParseApplicationId(String)`, `PIO.setParseClientKey(String)` and `PIO.initializeParse(Application)` methods
have been replaced by a single method `PIO.initializeParse(Application, String, String)`.

Quick Start - How to create your white-label app
========
1. Import printio-android-sdk library project into your application project
2. Create Application class and add it to the Manifest
3. Add PIO Config initialization code to you Application class' onCreate() method
4. Let your main activity extend print.io.ActivitySplash
5. Add required print.io activity declarations to your Manifest (refer to README file)
