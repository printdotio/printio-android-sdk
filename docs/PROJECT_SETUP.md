#Project Setup
###Prerequisites

In order to follow this guide, you must have minimum the Android 4.4.2 SDK (API v19) and Eclipse installed on your system.  
For download instructions, please visit [Installing ADT Plug-in for Eclipse](http://developer.android.com/sdk/installing/installing-adt.html).  
_Please note that we will be migrating to Android Studio soon, as it is now the official IDE for Android._  


#Configuration

In order to use the SDK in an existing app, following steps need to be followed carefully:

###1. Clone print.io project from this repository

###2. Import print.io SDK project
File -> Import -> General -> Existing Projects into Workspace*

###3. Add print.io SDK library to your project
Project -> Properties -> Android -> Add... -> printio-android*



#AndroidManifest Configuration

After importing and adding print.io SDK project, AndroidManifest.xml file of your project has to be set like so:

###1. Android target version
As mentioned above, print.io supports Android 4.0+ (API level 14 and higher) as target version. For lower versions, the user will be notified that it is not supported. So the `<uses-sdk>` node of your manifest should look like this:

```xml
<uses-sdk   android:minSdkVersion="9"
            android:targetSdkVersion="19" />
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
            android:name="print.io.ActivityShoppingCart"
            android:screenOrientation="portrait"
            android:windowSoftInputMode="stateHidden|adjustResize" />
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

###4. Application element
Important: `android:largeHeap="true"` attribute is required to be set in `<application\>` element.
