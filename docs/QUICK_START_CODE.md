#Basic Usage

In order to run print.io SDK, the configuration needs to be set.  
This is done by creating a `PIOConfig` object and passing it to `PIO.setConfig()` method.  
```java
PIO.setConfig(context, pioConfig);
```
PIO.setConfig() method takes 2 parameters.  
First is your activity Context, and second is the `PIOConfig` object which holds the entire SDK configuration.

###Launching print.io SDK

After you set your Config object, there are two ways to start the print.io SDK:  

####1. Start the SDK from your activity

   print.io SDK can be launched from any Activity by calling static method from `PIO` class - `PIO.start(...)`.
   ```java
   PIO.start(context);
   ```

####2. or Start the SDK by extending ActivitySplash

   print.io SDK can also be launched using (or extending) `ActivitySplash`.  
   This is useful if you want to create a stand-alone app which uses print.io SDK.  
   You need to add `ActivitySplash` to `AndroidManifest.xml`.  
   Make sure to add `android:screenOrientation="portrait"` and  
   `android:theme="@android:style/Theme.NoTitleBar.Fullscreen"` attributes.
   ```xml
   <activity
       android:name="print.io.ActivitySplash"
       android:label="@string/app_name"
       android:screenOrientation="portrait"
       android:theme="@android:style/Theme.NoTitleBar.Fullscreen" >
       <intent-filter>
           <action android:name="android.intent.action.MAIN" />

           <category android:name="android.intent.category.LAUNCHER" />
       </intent-filter>
   </activity>
   ```

#Quick Start

Below is sample code for launching print.io widget with default options included.  
This code should be added to your `Application` class' onCreate() method.  
You should create your PIOConstants class and store SDK related constants there. (RECIPE_ID, etc...)
PIOConstants class is not built in into the SDK.  
You can find an example of PIOConstants class in the [Demo App](DEMO_APP.md).  

###Minimal Configuration

Create `Application` class
```java
public class ApplicationSampleApp extends Application {

	@Override
	public void onCreate() {
		super.onCreate();

		// Initialize Parse push notifications
		// Needs to be inside Application class' onCreate() method
		// Use empty Strings if you are not using Parse notifications
		PIO.initializeParse(this, PIOConstants.Parse.APPLICATION_ID, PIOConstants.Parse.CLIENT_KEY);

		// Create PIOConfig object which will be used to configure SDK
		PIOConfig config = new PIOConfig();

		// Tells the SDK which server to use (Live or Staging) server.
		// In Staging mode, you can test purchase process without using real money.
		// Note: Some other methods require this to be called first, so make sure to call it as early as possible.
		config.setLiveApplication(false);

		// API KEY provided for every partner
		config.setRecipeID(PIOConstants.RECIPE_ID);

		// PublicConstants.API_URL_STAGING or PublicConstants.API_URL_LIVE
		config.setApiUrl(PublicConstants.API_URL_STAGING);

		// In order to use Credit Card payments, you need to set your Braintree encryption key
		config.setBraintreeEncryptionKey(PIOConstants.Braintree.ENCRYPTION_KEY);

		// Set available photo sources
		config.setPhotoSources(Arrays.asList(
			new PhonePhotoSource(),
			new InstagramPhotoSource(),
			new FacebookPhotoSource(),
			new PhotobucketPhotoSource(),
			new DropboxPhotoSource(),
			new FlickrPhotoSource()
		));
			
		try {
			// Set Config object
			PIO.setConfig(this, config);
		} catch (PIOException e) {
			e.printStackTrace();
		}
	}

}
```

Add your `Application` class to `AndroidManifest.xml`
```xml
<application android:name="com.your.package.ApplicationSampleApp"
```