#Project Setup
###Prerequisites

In order to follow this guide, you must have minimum the Android 4.0 SDK (API v14) and Eclipse installed on your system. For the latest versions of both of these bundled together, please visit [Android developer page].


#Configuration

**In order to use the SDK in an existing app, next steps need to be followed carefully:**
###1. Clone print.io project from this repository

###2. Import print.io SDK project
*File -> Import -> General -> Existing Projects into Workspace*

###3. Add print.io SDK library to your project
*Project -> Properties -> Android -> Add... -> printio-android*



**After importing and adding print.io SDK project, AndroidManifest.xml file of your project has to be set like follows:**
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
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityAllProducts"
            android:screenOrientation="portrait" />
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
            android:windowSoftInputMode="stateHidden" />
        <activity
            android:name="print.io.ActivityShoppingMethods"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityShippingAddress"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityPaymentMethod"
            android:screenOrientation="portrait" />
        <activity
            android:name="print.io.ActivityCheckout"
            android:screenOrientation="portrait" />
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
            android:name="com.paypal.android.MEP.PayPalActivity"
            android:configChanges="keyboardHidden|orientation"
            android:screenOrientation="portrait"
            android:theme="@android:style/Theme.Translucent.NoTitleBar" />
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

print.io SDK is controlled from static PIO class. To launch print.io widget, next 2 lines of code should be included at desired place:
```xml
PIO.start(context, null);
```

PIO.start(Context ctx, PIOCallback pioCallback) method takes 2 parameters, first is your activity Context, second is optional PIOCallback, that can give you information when shopping cart has been changed, or purchase has been finalized.

#print.io Quick Start
Below is sample code for launching a customized print.io widget, with all options included.  
This code should be added to your Application class' onCreate() method.  
PIOConstants class is not a part of the SDK.  
You should create your PIOConstants class and store SDK related constants there. (RECIPE_ID, API_URL, etc...)
```xml
//set live or staging server, on staging you can test purchase process without using real money.
PIO.setLiveApplication(boolean);

//do not show splash screen
PIO.setSplashScreenEnabled(false);

//hide Android status bar
PIO.setHideStatusBar(true);

//API KEY provided for every partner
PIO.setRecipeID(PIOConstants.RECIPE_ID);

// MAKE SURE TO CALL THIS
// http://staging.api.print.io/api/
PIO.setApiUrl(PIOConstants.API_URL);

//enable/disable application side menu.
PIO.setSideMenuEnabled(boolean);

//array of urls or local path for images that will be preloaded into the application.
PIO.setImagesUrls(String[]);

//show passed image first with images from other sources
PIO.setPassedImageFirstInPhotoSources(boolean);

//set passed image as layout with 1 photo for some products
PIO.setPassedImageThumb(boolean);

//forbid user to use his own images and use those passed to sdk.
PIO.setPhotosourcesDisabled(boolean);

//preset the country. Country code is 2 letter code, e.g. "US".
PIO.setCountryCode(String);

//can change country from Featured Products screen.
PIO.setCountryOnFeaturedProducts(boolean);

//hide category and search bar on Featured Products screen
PIO.setHideCategorySearchBar(boolean);

//set header bar color.
PIO.setHeaderColor(int);

//set the name for payment screens.
PIO.setPartnerName(String);

//preset the images always be auto arranged. User can customize product after.
PIO.setAutoArrange(boolean);

//display product variants and options step by step
PIO.setStepByStep(boolean);

//SDK in fullscreen. Note if your application is already in fullscreen mode than this will be ignored.
PIO.setHideStatusBar(boolean);

// 1 - one duplicated photo, 4 - four different photos.
PIO.setCoastersType(int);

//jump directly to the product and select variant.
PIO.setIdAndSku(PublicConstants.ProductIds.TABLET_CASES, "TabletCase-iPad3/4-Gloss");

//jump directly to the product. if PIO.setIdAndSku() is set this will be ignored.
PIO.setProductIdFromApp(PublicConstants.ProductIds.PHONE_CASES);

//show/hide help option through the sdk
PIO.setShowHelp(boolean);

//show/hide choosen photos in Customize Product screen.
PIO.setShowPhotosInCustomize(boolean);

//show/hide bottom tab bar with options in Customize Product screen.
PIO.setShowOptionsInCustomize(boolean);

//in edit photo screen show/hide options(roatate, add text, add effect)
PIO.setUpCropScreen(boolean, boolean, boolean);

//add desired photo sources
ArrayList<PhotoSource> photoSourcesTest = new ArrayList<PIO.PhotoSource>();
photoSourcesTest.add(PhotoSource.PHONE);
photoSourcesTest.add(PhotoSource.PICASA);
photoSourcesTest.add(PhotoSource.FACEBOOK);
photoSourcesTest.add(PhotoSource.DROPBOX);
photoSourcesTest.add(PhotoSource.FLICKR);
photoSourcesTest.add(PhotoSource.INSTAGRAM);
photoSourcesTest.add(PhotoSource.PHOTOBUCKET);
PIO.setPhotoSources(photoSourcesTest);

//initialize Parse push notifications
PIO.setParseApplicationId(PIOConstants.Parse.APPLICATION_ID);
PIO.setParseClientKey(PIOConstants.Parse.CLIENT_KEY);
PIO.initializeParse(this);
```

#See also
###Demo app

For a more comprehensive demonstration of the print.io SDK, see the [print.io SDK sample app].

[Android developer page]:http://developer.android.com/sdk/index.html
[print.io SDK sample app]:https://github.com/printdotio/printio-android-example