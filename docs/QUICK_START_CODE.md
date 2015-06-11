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

###Minimal Configuration

```java
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
```

###Optional Configuration

```java
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

// Or forbid user to use his own images and use only those passed to sdk.
config.setPhotosourcesDisabled(boolean);

// Array of urls or local path for images that will be preloaded into the application.
config.setImageUrls(List<String>);

// Preset the images always be auto arranged. User can customize product after.
config.setAutoArrange(boolean);

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
```
