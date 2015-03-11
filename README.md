#Project Setup
###Prerequisites

In order to follow this guide, you must have minimum the Android 4.0 SDK (API v14) and Eclipse installed on your system. For the latest versions of both of these bundled together, please visit [Android developer page].


#Configuration

**In order to use the SDK in an existing app, following steps need to be followed carefully:**
###1. Clone print.io project from this repository

###2. Import print.io SDK project
*File -> Import -> General -> Existing Projects into Workspace*

###3. Add print.io SDK library to your project
*Project -> Properties -> Android -> Add... -> printio-android*



**After importing and adding print.io SDK project, AndroidManifest.xml file of your project has to be set like so:**
###1. Android target version
As mentioned above, print.io supports Android 4.0+ (API level 14 and higher) as target version. For lower versions, the user will be notified that it is not supported. So the `<uses-sdk>` node of your manifest should look like this:

```xml
<uses-sdk   android:minSdkVersion="8"
            android:targetSdkVersion="14" />
```

###2. Permissions
   You will need to add these permissions to manifest:
   
```xml
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.GET_ACCOUNTS" />
    <uses-permission android:name="android.permission.USE_CREDENTIALS" />
    <uses-permission android:name="android.permission.READ_CONTACTS" />

    <!-- Permissions needed for new paypal integration -->
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.VIBRATE" />
    <!-- for most things, including card.io and paypal -->
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
    <uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />

    <!--
  IMPORTANT: Change "com.example.piosdkpoconcept.permission.C2D_MESSAGE" in the lines below
  to match your app's package name + ".permission.C2D_MESSAGE".
    -->
    <permission
        android:name="com.example.piosdkpoconcept.permission.C2D_MESSAGE"
        android:protectionLevel="signature" />

    <uses-permission android:name="com.example.piosdkpoconcept.permission.C2D_MESSAGE" />
    <uses-permission android:name="android.permission.WAKE_LOCK" />
    <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />

    <uses-feature
        android:name="android.hardware.camera"
        android:required="false" />
    <uses-feature
        android:name="android.hardware.camera.autofocus"
        android:required="false" />
    <uses-feature
        android:name="android.hardware.camera.flash"
        android:required="false" />
```

###3. Activities
Please add following activities to your AndroidManifest.xml file:
```xml
        <activity
            android:name="print.io.PIOActivity"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityCaseColorStyle"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="stateHidden" />
        <activity
            android:name="print.io.ActivityCountry"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="stateHidden" />
        <activity
            android:name="print.io.ActivityAnimatedHelp"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityCurrency"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="stateHidden" />
        <activity
            android:name="print.io.ActivityFeaturedProducts"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="adjustResize" />
        <activity
            android:name="print.io.ActivityProductDetails"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityImageUpload"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityCustomizeProduct"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityStickerBook"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="stateHidden" />
        <activity
            android:name="print.io.ActivityStickerbooksType"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityPhoneCaseGrid"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityThickPrintGrid"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityCanvasWrapsGrid"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityCanvasWrapsNext"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityChooseGridLayout"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityThrowPillowGrid"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityStepsListView"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityShoppingCart"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="stateHidden|adjustResize" />
        <activity
            android:name="print.io.ActivityShoppingMethods"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityShippingAddress"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityPaymentMethod"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="adjustResize" />
        <activity
            android:name="print.io.ActivityChooseShippingAddress"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityAddAddress"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="adjustResize" />
        <activity
            android:name="print.io.ActivityShipmentReview"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="stateHidden" />
        <activity
            android:name="print.io.ActivityOrderCompleted"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="stateHidden" />
        <activity
            android:name="print.io.ActivityHelp"
            android:screenOrientation="portrait" />
        <activity android:name="com.facebook.LoginActivity" />
        <activity
            android:name="print.io.social.Instagram"
            android:noHistory="true"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.social.Flickr"
            android:noHistory="true"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.social.Dropbox"
            android:noHistory="true"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityAbout"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityHowItWorks"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityAcrylicBlocksGrid"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="stateHidden" />
        <activity
            android:name="print.io.ActivityChooseGridLayoutTwoScollViews"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityPreviewOnWall"
            android:screenOrientation="portrait" />

        <!-- Activities needed for new paypal functionalities -->
        <service
            android:name="com.paypal.android.sdk.payments.PayPalService"
            android:exported="false" />

        <activity android:name="com.paypal.android.sdk.payments.PaymentActivity" />
        <activity android:name="com.paypal.android.sdk.payments.LoginActivity" />
        <activity android:name="com.paypal.android.sdk.payments.PaymentMethodActivity" />
        <activity android:name="com.paypal.android.sdk.payments.PaymentConfirmActivity" />
        <activity
            android:name="io.card.payment.CardIOActivity"
            android:configChanges="keyboardHidden|orientation" />
        <activity android:name="io.card.payment.DataEntryActivity" />

        <meta-data
            android:name="com.crashlytics.ApiKey"
            android:value="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" />
        <meta-data
            android:name="com.facebook.sdk.ApplicationId"
            android:value="@string/facebook_app_id" />

        <service android:name="com.parse.PushService" />

        <receiver android:name="com.parse.ParseBroadcastReceiver" >
            <intent-filter>
                <action android:name="android.intent.action.BOOT_COMPLETED" />
                <action android:name="android.intent.action.USER_PRESENT" />
            </intent-filter>
        </receiver>
        <receiver
            android:name="com.parse.GcmBroadcastReceiver"
            android:permission="com.google.android.c2dm.permission.SEND" >
            <intent-filter>
                <action android:name="com.google.android.c2dm.intent.RECEIVE" />
                <action android:name="com.google.android.c2dm.intent.REGISTRATION" />

                <!-- IMPORTANT: Change "com.example.piosdkpoconcept" to match your app's package name. -->
                <category android:name="com.example.piosdkpoconcept" />
            </intent-filter>
        </receiver>
        <receiver
            android:name="print.io.PushNotificationsReceiver"
            android:exported="false" >
            <intent-filter>

                <!-- IMPORTANT: Change "com.example.piosdkpoconcept" to match your app's package name. -->
                <action android:name="com.example.piosdkpoconcept.PUSH_NOTIFICATION" />
            </intent-filter>
        </receiver>

        <!-- IMPORTANT: Change "com.example.piosdkpoconcept" to match your app's package name. -->
        <receiver android:name="com.example.piosdkpoconcept.PrintIOCloseReceiver" >
            <intent-filter>
                <action android:name="ACTION_EXIT_PRINT_IO_SDK" />
            </intent-filter>
        </receiver>
```

###4. Application tag
Important: `android:largeHeap="true"` attribute is required to be set in `<application\>` tag.


#Basic Usage

print.io SDK is launched from static `PIO` class by calling `PIO.start(...)` method similar to this:
```java
PIO.setConfig(context, pioConfig);
PIO.start(context);
```

PIO.setConfig(Context context, PIOConfig pioConfig) method takes 2 parameters. First is your activity Context, second is  PIOConfig object which holds entire SDK configuration.
In order to successfully start SDK some configuration has to be done, which will be described in next chapter.
After you set your Config object, start the SDK using PIO.start(Context context) method.

#print.io Quick Start
Below is sample code for launching a customized print.io widget, with all options included.  
This code should be added to your Application class' onCreate() method.  
PIOConstants class is not built in into the SDK.  
You should create your PIOConstants class and store SDK related constants there. (RECIPE_ID, etc...)
```java
///////////////////////////////
// To launch SDK with minimum configuration your code should be similar to this.
///////////////////////////////

// Initialize Parse push notifications
// Needs to be inside Application class' onCreate() method
PIO.initializeParse(this, PIOConstants.Parse.APPLICATION_ID, PIOConstants.Parse.CLIENT_KEY);

// Create PIOConfig object which will be used to configure SDK
PIOConfig config = new PIOConfig();

// Tells the SDK which server to use (Live or Staging) server.
// In Staging mode, you can test purchase process without using real money.
// Note: Some other methods require this to be called first, so make sure to call it as early as possible.
config.setLiveApplication(boolean);

// API KEY provided for every partner
config.setRecipeID(PIOConstants.RECIPE_ID);

// PublicConstants.API_URL_STAGING or PublicConstants.API_URL_LIVE
config.setApiUrl(...);

// Set Config object
PIO.setConfig(context, config);

// Launch SDK by calling PIO.start
PIO.start(context);

///////////////////////////////
// Other configuration is not mandatory, but you can tweak it to fit your needs.
////////////////////////////

// Do not show splash screen
config.setSplashScreenEnabled(false);

// Set your company's name for payment screens.
config.setPartnerName(String);

// Hide Android status bar
config.setHideStatusBar(false);

// Enable/disable application side menu.
config.setSideMenuEnabled(boolean);
config.setDefaultSideMenuButtonsTop();
config.setDefaultSideMenuInfoButtons();

// Preset the country. Country code is 2 letter code, e.g. "US".
config.setCountryCode(String);

// Can change country from Featured Products screen (default is true).
config.setCountryOnFeaturedProducts(boolean);

// Hide category and search bar on Featured Products screen
config.setHideCategorySearchBar(boolean);

// Set header bar color.
config.setHeaderColor(int);

// Preset the images always be auto arranged. User can customize product after.
config.setAutoArrange(boolean);

// Display product variants and options step by step
config.setStepByStep(boolean);

// 1 - one duplicated photo, 4 - four different photos.
config.setCoastersType(int);

// Jump directly to the product. if PIO.setIdAndSku() is set this will be ignored.
config.setProductIdFromApp(PublicConstants.ProductIds.PHONE_CASES);

// Show/hide help option through the sdk
config.setShowHelp(boolean);

// Show/hide choosen photos in Customize Product screen.
config.setShowPhotosInCustomize(boolean);

// Show/hide bottom tab bar with options in Customize Product screen.
config.setShowOptionsInCustomize(boolean);

// In edit photo screen show/hide options(roatate, add text, add effect)
config.setUpCropScreen(boolean, boolean, boolean);

// Add desired photo sources
ArrayList<PhotoSource> photoSourcesTest = new ArrayList<PIO.PhotoSource>();
photoSourcesTest.add(PhotoSource.PHONE);
photoSourcesTest.add(PhotoSource.PICASA);
photoSourcesTest.add(PhotoSource.FACEBOOK);
photoSourcesTest.add(PhotoSource.DROPBOX);
photoSourcesTest.add(PhotoSource.FLICKR);
photoSourcesTest.add(PhotoSource.INSTAGRAM);
photoSourcesTest.add(PhotoSource.PHOTOBUCKET);
config.setPhotoSources(photoSourcesTest);

// Note: Following methods are not fully implemented yet
// Array of urls or local path for images that will be preloaded into the application.
config.setImagesUrls(String[]);

// Show passed image first with images from other sources
config.setPassedImageFirstInPhotoSources(boolean);

// Set passed image as layout with 1 photo for some products
config.setPassedImageThumb(boolean);

// Forbid user to use his own images and use those passed to sdk.
config.setPhotosourcesDisabled(boolean);
```

#See also
###Demo app

For a more comprehensive demonstration of the print.io SDK, see the [print.io SDK sample app].

[Android developer page]:http://developer.android.com/sdk/index.html
[print.io SDK sample app]:https://github.com/printdotio/printio-android-example