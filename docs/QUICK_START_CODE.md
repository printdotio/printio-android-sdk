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

####2. Or start the SDK by extending ActivitySplash

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

		// Create PIOConfig object which will be used to configure SDK
		PIOConfig config = new PIOConfig();

		// Mandatory config - set API keys provided for every partner
		config.setRecipeIDs(PIOConstants.RECIPE_ID_LIVE, PIOConstants.RECIPE_ID_STAGING);

		// Optional config - tell SDK which environment to use (Live or Staging)
		// In Staging mode, you can test purchase process without using real money.
		config.setLiveApplication(false);

		// Optional config - set available photo sources
		config.setPhotoSources(Arrays.asList(
			new PhonePhotoSource(),
			new InstagramPhotoSource(),
			new FacebookPhotoSource()
		));
			
		try {
			// Set configuration object and start PIO SDK
			PIO.setConfig(this, config);
			PIO.start(this);
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