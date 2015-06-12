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