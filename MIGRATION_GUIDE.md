Migrating to v2.x from v1.x
========

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