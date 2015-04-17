Migrating to v2.1.9 from v2.1.8
========
 ---
**Changes with photo sources**

In order to support custom photo sources (defined by SDK users) new mechanism for photo sources has been introduced. 

As of v2.1.8 use of `PhotoSource` enum values have been replaced with corresponding classes implementing new `PhotoSource` interface. These classes are :

 -- `print.io.photosource.impl.dropbox.DropboxPhotoSource`
 -- `print.io.photosource.impl.facebook.FacebookPhotoSource`
 -- `print.io.photosource.impl.flickr.FlickrPhotoSource`
 -- `print.io.photosource.impl.instagram.InstagramPhotoSource`
 -- `print.io.photosource.impl.phone.PhonePhotoSource`
 -- `print.io.photosource.impl.photobucket.PhotobucketPhotoSource`
 -- `print.io.photosource.impl.picasa.PicasaPhotoSource`
 -- `print.io.photosource.impl.preselected.PreselectedPhotoSource`

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