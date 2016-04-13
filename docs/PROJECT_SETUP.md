#Project Setup

##Setting up PrintIO SDK in your IDE

On this page we are going to guide you through setting up the PrintIO SDK in an existing app. This guide will cover Android Studio and Eclipse IDE.

### Android Studio guide

####1. Clone print.io project from this repository

####2. Import print.io SDK to your project as module
Open Module Setting -> New Module -> Import Existing Project (Phone and Tablet Application) -> Choose directory of print.io SDK

### Eclipse guide

####1. Clone print.io project from this repository

####2. Import print.io SDK project
File -> Import -> General -> Existing Projects into Workspace*

####3. Mark print.io SDK as library project
Select print.io SDK project -> Properties -> Android -> Make sure that "Is Library" is ticked

####4. Add print.io SDK dependencies 
Libraries will have to be added manually when developing with Eclipse  
(In Android Studio, these dependencies are automatically resolved by Gradle dependency management mechanism).

* 4.1 Required dependencies (Mandatory)

	To make your life easer we have bundled these libraries together. You can download [this archive](https://www.dropbox.com/s/0r5837d3t20kab0/libs.zip?dl=1) and extract the files to the `libs` folder of the PrintIO SDK.

* 4.2 Facebook SDK (This step is required only if you intend to use Facebook as a photo source)

	If your project is not currently using Facebook SDK you will have to clone Facebook SDK version 4.5 for Android and import it into workspace. Then add Facebook SDK library to the print.io SDK library like so:

	Select print.io SDK project-> Properties -> Android -> Add... -> Choose Facebook SDK library

####5. Add print.io SDK library to your project
Select your project -> Properties -> Android -> Add... -> Choose printio SDK library



##AndroidManifest Configuration

After importing and adding print.io SDK project, AndroidManifest.xml file of your project has to be set like so:

###1. Android target version
As mentioned above, print.io supports Android 4.0+ (API level 14 and higher) as target version. For lower versions, the user will be notified that it is not supported. So the `<uses-sdk>` node of your manifest should look like this:

```xml
<uses-sdk android:minSdkVersion="9" android:targetSdkVersion="19" />
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

<!-- IMPORTANT: Change "com.example.piosdkpoconcept.permission.C2D_MESSAGE" in the lines below to match your app's package name + ".permission.C2D_MESSAGE". -->
<permission android:name="com.example.piosdkpoconcept.permission.C2D_MESSAGE" android:protectionLevel="signature" />

<uses-permission android:name="com.example.piosdkpoconcept.permission.C2D_MESSAGE" />
<uses-permission android:name="android.permission.WAKE_LOCK" />
<uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />

<uses-feature android:name="android.hardware.camera" android:required="false" />
<uses-feature android:name="android.hardware.camera.autofocus" android:required="false" />
<uses-feature android:name="android.hardware.camera.flash" android:required="false" />
```

###3. Activities
Please add following activities to your AndroidManifest.xml file:
```xml
<activity
	android:name="print.io.PIOActivity"
	android:screenOrientation="portrait" />
<activity
	android:name="print.io.ActivityOptionBackground"
	android:screenOrientation="portrait"
	android:windowSoftInputMode="stateHidden" />
<activity
	android:name="print.io.ActivityCountry"
	android:screenOrientation="portrait"
	android:windowSoftInputMode="stateHidden" />
<activity
	android:name="print.io.ActivityCurrency"
	android:screenOrientation="portrait"
	android:windowSoftInputMode="stateHidden" />
<activity
	android:name="print.io.ActivityProducts"
	android:screenOrientation="portrait"
	android:windowSoftInputMode="adjustResize|stateHidden" />
<activity
	android:name="print.io.ActivityProductsV2"
	android:screenOrientation="portrait"
	android:windowSoftInputMode="adjustResize|stateHidden" />
<activity
	android:name="print.io.ActivityProductDetails"
	android:screenOrientation="portrait" />
<activity
	android:name="print.io.ActivityProductDetailsV2"
	android:screenOrientation="portrait" />
<activity
	android:name="print.io.ActivitySelectPhotos"
	android:screenOrientation="portrait" />
<activity
	android:name="print.io.ActivityCustomizeProduct"
	android:screenOrientation="portrait"
	android:windowSoftInputMode="adjustResize" />
<activity
	android:name="print.io.ActivityCustomizePhotobook"
	android:screenOrientation="landscape"
	android:windowSoftInputMode="adjustResize" />
<activity
	android:name="print.io.ActivityProductOptions"
	android:screenOrientation="portrait" />
<activity
	android:name="print.io.ActivityCustomizeList"
	android:screenOrientation="portrait"
	android:windowSoftInputMode="stateHidden" />
<activity
	android:name="print.io.ActivityShoppingCart"
	android:screenOrientation="portrait"
	android:windowSoftInputMode="stateHidden|adjustResize" />
<activity
	android:name="print.io.ActivityPaymentMethod"
	android:screenOrientation="portrait"
	android:windowSoftInputMode="adjustResize|stateUnchanged" />
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
<activity
	android:name="print.io.photosource.impl.facebook.Facebook"
	android:screenOrientation="portrait" />
<activity
	android:name="print.io.photosource.impl.instagram.Instagram"
	android:screenOrientation="portrait" />
<activity
	android:name="print.io.photosource.impl.flickr.Flickr"
	android:screenOrientation="portrait" />
<activity
	android:name="print.io.photosource.impl.dropbox.Dropbox"
	android:screenOrientation="portrait" />
<activity
	android:name="print.io.ActivityAbout"
	android:screenOrientation="portrait" />
<activity
	android:name="print.io.ActivityHowItWorks"
	android:screenOrientation="portrait" />
<activity
    android:name="print.io.ActivityQualityGuarantee"
    android:screenOrientation="portrait" />
<activity
	android:name="com.facebook.FacebookActivity"
	android:screenOrientation="portrait" />
<activity
    android:name="print.io.ActivityOrderDetails"
    android:screenOrientation="portrait" />
<activity
    android:name="print.io.ActivityOrderStatus"
    android:screenOrientation="portrait" />
<activity
    android:name="print.io.ActivityPastOrders"
    android:screenOrientation="portrait" />

<!-- Activities needed for new PayPal functionalities -->
<service
    android:name="com.paypal.android.sdk.payments.PayPalService"
    android:exported="false" />

<activity
    android:name="com.paypal.android.sdk.payments.PaymentActivity"
    android:screenOrientation="portrait" />
<activity
    android:name="com.paypal.android.sdk.payments.LoginActivity"
    android:screenOrientation="portrait" />
<activity
    android:name="com.paypal.android.sdk.payments.PaymentMethodActivity"
    android:screenOrientation="portrait" />
<activity
    android:name="com.paypal.android.sdk.payments.PaymentConfirmActivity"
    android:screenOrientation="portrait" />
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
```

###4. Application element
Important: `android:largeHeap="true"` attribute is required to be set in `<application\>` element.

###5. Facebook App ID
Add your facebook_app_id to `res/strings.xml`.
```xml
<string name="facebook_app_id">YourFacebookAppId</string>
```

###6. Add fonts for Text feature  
Copy PIO SDK `fonts` folder to the `assets` folder of the host app.  
The folder can be found in our [Example app](https://github.com/printdotio/printio-android-example/tree/master/PIOSDKPOConcept/assets)