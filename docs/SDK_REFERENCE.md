# Developer SDK Customization Reference

---
#### > Starting PrintIO SDK  

To start PrintIO SDK use the following method:
```java
/**
 * Starts the PrintIO SDK.
 * 
 * @param context
 *            The active {@code Context} for your application.
 * @param config
 *            The {@code PIOConfig} holding configuration of PIO SDK.
 * @throws PIOException
 *             If an error occurs while starting SDK.
 */
PIO.start(Context context, PIOConfig config) throws PIOException;
```
&nbsp;  
&nbsp;  
#### > Get Shopping Cart object 

Returns copy of currently saved shopping cart.
```java
/**
 * Returns copy of currently saved shopping cart.
 * 
 * @param context
 *            The {@code Context} of current application instance.
 * @return currently saved {@code ShoppingCart}
 */
PIO.getShoppingCart(Context context)
```
&nbsp;
&nbsp;  
#### > Set Shopping Cart object

Sets and saves supplied shopping cart.
```java
/**
 * Sets and saves supplied shopping cart.
 * 
 * @param context
 *            The {@code Context} of current application instance.
 * @param cart
 *            The {@code ShoppingCart} to be used inside SDK.
 */
PIO.setShoppingCart(Context context, ShoppingCart cart)
```
&nbsp;  
&nbsp;  
#### > Get number of items in shopping cart
**Sample code:**  
```java
int count = PIO.getShoppingCart(context).getItems().size();
```
#### > Remove all items from shopping cart
**Sample code:**  
```java
ShoppingCart cart = PIO.getShoppingCart(context);
cart.removeAllItems();
PIO.setShoppingCart(context, cart);
```
&nbsp;
&nbsp;  
#### > Set host activity  

```java
PIOConfig.setHostAppActivity(String hostAppActivityClassName)
```

Gooten SDK provides a few "shortcuts" for getting back to the host application.
One of them is the `EXIT` button in the Side Menu (which is visible by default).
In order for these to work, `Host Activity` needs to be set.  
This is the `ClassName` of the `Activity` that the Gooten SDK will navigate back to.  

This is usually the `Activity` that started the Gooten SDK.  
In this case you can use the following sample code:  
**Sample code:**
```java
config.setHostAppActivity(getComponentName().getClassName());
```

If your application is just a wrapper around the Gooten SDK, you should remove the `EXIT` button from the [Side Menu](#-set-buttons-to-be-displayed-in-side-menu)
&nbsp;  
&nbsp; 
#### > Set all products and variants
Sets if SDK should use all products and variants available with default pricing. By default, value is set to `false` - SDK will use products and variants with prices that are set via admin panel.

```java
PIOConfig.setAllProductsAndVariants(boolean isAll)
```
&nbsp;  
&nbsp;   
#### > Set testing mode for order placing
Sets if SDK should use testing mode for placing orders. In testing mode orders are submitted without payment verification. This is only used in live environment. By default, value is set to `false` - SDK will use live mode for placing orders. 

```java
PIOConfig.setOrderTesting(boolean isOrderTesting)
```
&nbsp;  
&nbsp;   
#### > PrintIO SDK publicly exposed data

PrintIO SDK provides SDK user with following data which could be accessed at all times:

 1. Current shopping cart state
 2. Last successful order information

Methods for accessing these structures are `PIO.getShoppingCart(Context)` and `PIO.getLastOrder(Context)` respectively.

&nbsp;
#### > PrintIO SDK Events

PrintIO SDK uses BroadcastReceiver mechanism to notify user of SDK with events. PrintIO SDK broadcast following events:

 1. Event when chopping cart is changed (when new is added to the cart, or when item is removed from the cart, etc...).
 2. Event when end SDK user successfully completes an order. 

All events (Intents) are broadcasted locally within SDK. All Intents have the same action `"PIO_SDK_EVENTS"` but type of en event could be determined by `"TYPE"` Intent extra data holding String identifier of en event. Possible values are following:

 1. `"CART_CHANGED"` - when cart is changed
 2. `"ORDER_COMPLETED"` - when end SDK user successfully completes an order

&nbsp;  
##### > Example code for handling PrintIO SDK events

First, create your implementation of `BroadcastReceiver` which will receive Intents describing events sent by the PrintIO SDK.

```java
public class PIOSDKEventListener extends BroadcastReceiver {

	@Override
	public void onReceive(Context context, Intent intent) {
		String type = intent.getStringExtra(PIOConstants.PIO_SDK_EVENT_TYPE);
		if (PIOConstants.PIO_SDK_EVENT_CART_CHANGED.equals(type)) {
			Log.d("PIOSDKEventListener", "Cart changed");
			// Use PIO.getShoppingCart(context) to get current shopping cart state
		} else if (PIOConstants.PIO_SDK_EVENT_ORDER_COMPLETED.equals(type)) {
			Log.d("PIOSDKEventListener", "Order finished");
			// Use PIO.getLastOrder(context) to get last successful order information
		}
	}

}
```

Then, register event listener in `onCreate()` method of your `Application`.

```java
@Override
public void onCreate() {
	super.onCreate();
	LocalBroadcastManager.getInstance(this).registerReceiver(new PIOSDKEventListener(), new IntentFilter(PIOConstants.PIO_SDK_EVENTS));
}
```
&nbsp;  
&nbsp; 
#### > Set analytics tracker
Sets `AnalyticsTracker` object used to receive analytics events from the SDK.
```java
PIOConfig.setAnalyticsTracker(AnalyticsTracker tracker)
```
Default implementations proved by SDK:

 - `print.io.analytics.impl.GoogleAnalyticsTracker` - uses Google Analytics service for tracking analytics events

Usage example:
```java
config.setAnalyticsTracker(new GoogleAnalyticsTracker("UA-00000000-0"));
```
&nbsp;  
&nbsp;  
#### > Set Status Bar visibility
( > Set Status Bar visibility)

Default value is `false` (Status Bar is visible).

```java
PIOConfig.setHideStatusBar(boolean hideStatusBar);
```
&nbsp;  
&nbsp;  
#### > Splash Screen Settings

Set Splash Screen timeout in milliseconds.  
Default value is 0 which means that Splash Screen will not be shown.  

```java
PIOConfig.setSplashScreenTimeout(int splashScreenTimeout);
```

NOTICE: In order to show Splash Screen, you need to override ActivitySplash (See [Basic usage code](QUICK_START_CODE.md)).
&nbsp;  
&nbsp; 
#### > Set country code  

Sets the default shipping country. Country code must be valid ISO 3166-1 (two-letter) country code.
```java
PIOConfig.setCountryCode(String countryCode);
```
&nbsp; 
&nbsp;  
#### > Set currency code  

If not set, default value is determined by the selected Country Code. Currency code must be valid ISO 4217 currency code.
```java
PIOConfig.setCurrencyCode(String currencyCode);
```
&nbsp;  
&nbsp;
#### > Pass promo coupon code to SDK  

Pass a promo coupon code which will be shown to user in `Shopping Cart` screen.  
The user can choose to apply the coupon to get discounts or promotions.  

Once products in shopping cart are purchased, coupon code is cleared.  

To set promo coupon code, use the following method:
```java
PIOConfig.setPromoCode(String promoCode);
``` 
&nbsp;  
&nbsp;
Side Menu
---------
#### > Enable or disable Side Menu

Default value is `true` - Side Menu is enabled.
```java
PIOConfig.setSideMenuEnabled(boolean isSideMenuEnabled);
```
&nbsp;  
&nbsp;  
#### > Slide Side Menu from right
Controls if Side Menu should slide from left or right.
 
Default value is `false` (side menu slides from left side).
```java
PIOConfig.setRightSideMenu(boolean rightSideMenu);
```
&nbsp;  
&nbsp;  
( > Change Side Menu icon)  

Replace following icons with your own icons of same names.  
Recommended dimensions are listed next to the icon name.
```
icon_menu_default.png (39x29)
icon_menu_pressed.png (39x29)
```
&nbsp;  
&nbsp;  
( > Change color of elements inside Side Menu)  

To change color of Side Menu elements, you can modify the following items in `res/values/colors.xml`:

Background color:
```xml
<color name="side_menu_background">#1D1D1D</color>
```
Separator color:
```xml
<color name="side_menu_separator_color">#343434</color>
```
Text color:
```xml
<color name="side_menu_text">#FFFFFF</color>
```
&nbsp;  
&nbsp;  
#### > Set buttons to be displayed in side menu  

&nbsp;  
To select which buttons will be used, pass a `List` of `SideMenuButton` to the following method. By default all buttons are visible.

**Important:** Host `Activity` needs to be set for the `EXIT` button to work. Refer to [setting host activity](#-set-host-activity)
```java
PIOConfig.setVisibleSideMenuButtons(List<SideMenuButton> sideMenuButtons);

enum SideMenuButton {
	EXIT,
	ABOUT,
	HELP,
    HOW_IT_WORKS,
    PAST_ORDERS,
    ORDER_STATUS,
    CONTACT_US,
    QUALITY_GUARANTEE;
};
```

&nbsp;  
To modify buttons' icons, replace the corresponding icon with your own.
```
icon_side_menu_button_exit_sdk
icon_side_menu_button_about_us.png
icon_side_menu_button_help.png
icon_side_menu_button_contact_us.png
icon_side_menu_button_how_it_works.png
icon_side_menu_button_order_status.png
icon_side_menu_button_past_orders.png
icon_side_menu_button_quality_quarantee.png
```
&nbsp;  
To modify buttons' labels, change the following items in `res/values/strings.xml` .
```
<string name="side_menu_button_label_exit">Exit</string>
<string name="side_menu_button_label_order_status">Order Status</string>
<string name="side_menu_button_label_past_orders">Past Orders</string>
<string name="side_menu_button_label_about_us">About us</string>
<string name="side_menu_button_label_help">Help</string>
<string name="side_menu_button_label_contact_us">Contact us</string>
<string name="side_menu_button_label_how_it_works">How it works</string>
<string name="side_menu_button_label_quality_guarantee">Quality Guarantee</string>
```
&nbsp; 
&nbsp;   
##### **Options** section:  

To modify section title, change the following item in `res/values/strings.xml` .
```xml
<string name="side_menu_section_title_options">Options</string>
```
&nbsp;  
To change the currency code color, modify the following item in `res/values/colors.xml`
```xml
<color name="side_menu_change_currency_text">#FFFFFF</color>
```
&nbsp;  
These methods control if the user is allowed to change the preset country and currency.  
Default values are `true`.
```java
PIOConfig.setChangeableCountry(boolean isChangeable);
PIOConfig.setChangeableCurrency(boolean isChangeable);
```
&nbsp;  
&nbsp;  
##### **Log in with** section:
Contains the available photo sources that the app will use.  To select Photo Sources that will be displayed here, refer to **Photo Sources** section of this document.

To modify section title, change the following item in `res/values/strings.xml`.
```xml
<string name="side_menu_section_title_log_in_with">Log in with</string>
```
&nbsp;  
 To hide this section, use the following method
```java
PIOConfig.hidePhotoSourcesInSideMenu(boolean hidePhotoSources);
```
&nbsp; 
&nbsp;   
##### **Information** section:  
To modify its title, change the following item in `res/values/strings.xml`.
```xml
<string name="side_menu_section_title_information">Information</string>
```
&nbsp; 
#### > Set support email address  

To set support email address, use the following method:
```java
PIOConfig.setSupportEmail(String supportEmail);
``` 
####> Set help URL
To set help URL, use the following method:
```java
PIOConfig.setHelpUrl(String url);
```
&nbsp;  
&nbsp;  
#### Set visibility of **SDK Version** in Side Menu:  
By default, the SDK version is shown at the bottom of the Side Menu.  
To hide the SDK version, use the following method
```java
PIOConfig.hideVersionInSideMenu(boolean isHidden);
```
&nbsp;  
&nbsp;
Screens version
--------------
&nbsp;  
&nbsp;
#### > Set screens version 
Changes screens version used by the SDK.  
By default `ScreenVersion.V_1` is used.
```java
PIOConfig.setScreenVersion(ScreenVersion screenVersion)
```
&nbsp;  
&nbsp; 
General screen configuration
--------------
&nbsp;  
&nbsp; 
#### > Navigation Bar Settings
( > Change navigation bar color and title font color, also set left and right bar button.) 
To change navigation bar color, modify the following item in `res/values/colors.xml`
```xml
<color name="title_bar_background">#FFFFFF</color>
```
```java
PIOConfig.setHeaderColor(int color); //color is a 6-digit (rgb) or 8-digit (argb) hex value
```
_Note that the value set programmatically will override the value set in xml._  

To change separator and texts' colors, modify the following item in `res/values/colors.xml`
```xml
<color name="title_bar_separator">#d6d6d6</color>
<color name="title_bar_text">#000000</color>
<color name="text_cart_items_quantity">#FFFFFF</color>
```
_NOTICE: Never modify xml item names. Modify values only._   
&nbsp;  
&nbsp;  
#### > Change screen title
To change screen title,  modify the following item in `res/values/strings.xml`
```xml
<string name="screen_title_products">Products</string>
<string name="screen_title_product_details">Product Details</string>
<string name="screen_title_product_options">Choose Options</string>
<string name="screen_title_shopping_cart">Shopping Cart</string>
<string name="screen_title_select_photos">Select Photos</string>
<string name="screen_title_past_orders">Past Orders</string>
<string name="screen_title_order_status">Order Status</string>
<string name="screen_title_order_details">Order Details</string>
<string name="screen_title_quality_guarantee">Quality Guarantee</string>
<string name="screen_title_how_it_works">How It Works</string>
<string name="screen_title_about">About</string>
<string name="screen_title_add_address">Checkout</string>
<string name="screen_title_select_address">Select Address</string>
<string name="screen_title_choose_country">Choose Country</string>
<string name="screen_title_choose_currency">Choose Currency</string>
<string name="screen_title_order_completed">Order Completed</string>
<string name="screen_title_payment_method">Payment</string>
<string name="screen_title_shipment_review">Shipment Review</string>
<string name="screen_title_help">Help</string>
```
_NOTICE: Never modify xml item names. Modify values only._   
&nbsp;  
&nbsp;  
#### > Set Icon For Back Button  
( > Change `Back` button icon)  

Replace the following icon with your own icon of the same name.  
Recommended dimensions are listed next to the icon name.

To change icon with your own icon, modify the following item in `res/drawable-xhdpi`
```xml
icon_arrow_back.png (19x33)
```
&nbsp;  
&nbsp;  
#### > Set three buttons Back, Menu and Cart button in navigation bar for Products screen  
( > Set three buttons title bar style)

Show `Back`, `Menu` and `Cart` buttons in navigation bar for Products screen.  
Default value is `false`.
```java
PIOConfig.useThreeButtonsBarStyle(boolean useThreeButtonsBarStyle);
```
&nbsp;  
&nbsp;
#### > Show Country selection bar on screens.
By default, only `Screen.PRODUCTS` has country selection bar displayed. The following Screens support this method: `Screen.PRODUCTS`, `Screen.PRODUCT_DETAILS` and `Screen.OPTIONS`.
```java
PIOConfig.showCountrySelectionOnScreen(List<Screen> screens)
```
&nbsp;  
#### > Change background color of Select Country bar.

To change the background color of Select Country bar, modify the following item in `res/values/colors.xml`
```xml
<color name="select_country_background">#2277D4</color>
```
&nbsp;  
&nbsp;  
#### > Show vendor logo on screens.

Sets drawable resource ID to be used as vendor logo for supplied `Screen`
```java
/**
 * Sets drawable resource ID to be used as vendor logo for supplied
 * {@link Screen}. By default, no screens have logo associated
 * with them. Following screens have support for showing vendor logo:
 * {@link Screen#PAYMENT}, {@link Screen#ORDER_COMPLETED} and
 * {@link Screen#PRODUCT_DETAILS}.
 * 
 * @param screen
 *            The screen where logo should be shown.
 * @param resourceId
 *            The logo drawable resource ID that will be asociated to the
 *            supplied {@code screen}. If {@code null} value is supplied
 *            vendor logo will be hidden.
 */
PIOConfig.setVendorLogoOnScreen(Screen screen, Integer resourceId)
```
&nbsp;  
&nbsp;  
#### > Show vendor logo in Title Bar on screens.

Sets drawable resource ID to be used as vendor logo in Title Bar for supplied `Screen`
```java
/**
 * Sets drawable resource ID to be used as vendor logo in Title Bar for
 * supplied {@link Screen}. By default, no screens have logo associated
 * with them. Following screens have support for showing vendor logo:
 * {@link Screen#PRODUCTS} and {@link Screen#SHOPPING_CART}.
 * 
 * @param screen
 *            The screen where logo should be shown.
 * @param resourceId
 *            The logo drawable resource ID that will be asociated to the
 *            supplied {@code screen}. If {@code null} value is supplied
 *            vendor logo will be hidden.
 */
PIOConfig.setTitleBarVendorLogoOnScreen(Screen screen, Integer resourceId)
```
&nbsp;  
&nbsp;
Screens v2 specific configuration
--------------
&nbsp;  
&nbsp;
#### > Set product screens layouts image URL
Sets URL of image resource used on product layouts on product screens.  
This configuration is mandatory when v2 screens are used.
```java
PIOConfig.setScreenProductImageUrl(String url)
```
&nbsp;  
&nbsp;
#### > Set products with special offer banner
Sets  products for who special offer banner will be shown.
```java
PIOConfig.setProductsWithSpecialOfferBanner(List<ProductType> products)
```
&nbsp;  
&nbsp;

Products screen
--------------
#### > Set list of available products in the SDK.

By default, all values defined in `ProductType` enum are used.

```java
PIOConfig.setAvailableProducts(List<ProductType> availableProducts);
```
&nbsp;  
&nbsp; 
#### > Hide category/search view on Products screen  
( > Hide category/search view on Products screen)  

Default value is `false`.
```java
PIOConfig.setHideCategorySearchBar(boolean hideCategorySearchBar);
```
&nbsp;  
&nbsp;    
#### > Hide `Coming Soon` products  

Default value is `false`.
```java
PIOConfig.setHideComingSoonProducts(boolean hideComingSoonProducts);
```
&nbsp;  
&nbsp;  
#### > Set bottom bar visibility

Default value is `true` (bottom bar is visible).
```java
PIOConfig.setProductsBottomBarVisibility(boolean isVisible);
```
&nbsp;  
&nbsp;  
#### > Set Facebook Page URL for `Like` button in bottom bar

There is no default value.
```java
PIOConfig.setFacebookPageUrl(String facebookPageUrl);
```
&nbsp;  
&nbsp;  
#### > Set featured products in Hero

Default value is `null` (default featured products, returned from API are shown in Hero).
```java
PIOConfig.setFeaturedProducts(List<ProductType> products);
```
&nbsp;  
&nbsp;  
#### > Set promo image with link in Hero

The link will open in external application.
```java
PIOConfig.setHeroItem(HeroItem heroItem);
```
&nbsp;  
&nbsp;  
Product Details
--------------
#### > Hide prices in Product Details screen  

Default value is `false`.
```java
PIOConfig.setPriceTitleHidden(boolean isHidden);
```
&nbsp;  
&nbsp;  
#### > Set discount percentage for retail price   
Sets discount percentage for retail price. Value should be in range [0-99].

Default value is `null` (functionality is ignored). 
```java
PIOConfig.setRetailDiscountPercent(Float discountPercent);
```
&nbsp;  
&nbsp;
#### > Set price style
For `V_1` screens:

To change background color of price container, color of price text or color of retail price text, modify following items `res/values/colors.xml` in respectively.
```xml
<color name="product_details_v1_price_container_background">#EBEBEB</color>
<color name="product_details_v1_price_text_color">#323232</color>
<color name="product_details_v1_retail_price_text_color">#c6c8cc</color>
``` 
To change size of price text or retail price text,  modify following items `res/values/dimens.xml` in respectively.
```xml
<dimen name="product_details_v1_price_text_size">16dip</dimen>
<dimen name="product_details_v1_retail_price_text_size">16dip</dimen>
```

For `V_2` screens: 

To change background color of price container, color of starting at text, color of retail price text or color of price text, modify following items `res/values/colors.xml` in respectively.
```xml
<color name="product_details_v2_price_container_background">#2277D4</color>
<color name="product_details_v2_staring_at_text_color">#FFFFFFFF</color>
<color name="product_details_v2_retail_price_text_color">#FFFFFFFF</color>
<color name="product_details_v2_price_text_color">#FFFFFFFF</color>
``` 
To change size of starting at text, retail price text or price text,  modify following items `res/values/dimens.xml` in respectively.
```xml
<dimen name="product_details_v2_staring_at_text_size">14dip</dimen>
<dimen name="product_details_v2_retail_price_text_size">14dip</dimen>
<dimen name="product_details_v2_price_text_size">14dip</dimen>
``` 
#### > Change style of "Create it" button 

To change style of "Create it" button, modify following resources:

`res/layout/item_button_create_it_v1.xml` if you are using `ScreenVersion.V_1`, or/and
`res/layout/item_button_create_it_v2.xml` if you are using `ScreenVersion.V_2`.

_Note that layout attributes (such as width, height, margin, etc..) will be overridden in files were these layouts are included._

Button can have product name loaded to the label. In order to use this, string resource
`button_label_create_it_with_product` needs to be defined. E.g.
`<string name="button_label_create_it_with_product">Create %1$s</string>` 
would result with button label with following value "Create Framed Print".
&nbsp; 
&nbsp;  
Product Options screen
--------------
#### > Set strategy for steps with single option 
Set strategies used for displaying steps when there is single option to choose.

Possible strategies:

* `PRESELECT` - If step has single option, option will be preselected.
* `SKIP` - If step has single option, step will not be shown.

Default value is `SingleOptionStepStrategy.PRESELECT`.
```java
PIOConfig.setSingleOptionStepStrategy(SingleOptionStepStrategy strategy);
```
&nbsp;  
&nbsp;
#### > Set strategy for layout step on Product Options screen

Possible strategies:

* `SHOW` - Choose layout step is always shown when there is more then one layout.
* `SKIP_BEST_FIT_TO_PASSED_IMAGES_COUNT` - Skips choose layout step and uses layout that fits the best for passed in images count.
* `FILTER_LAYOUTS_UP_TO_PASSED_IMAGES_COUNT` - Shows step but with layouts which have image slots up to passed in images count. If there are no layouts that satisfy filtering criteria all layouts will be shown. In case when there is single layout step is skipped.
* `SKIP_FOR_SINGLE_PASSED_IMAGE` - Skips choose layout step when single images is passed in and uses one photo layout, otherwise step is shown.

Default value is `LayoutStepStrategy.SHOW`.
```java
PIOConfig.setLayoutStepStrategy(LayoutStepStrategy strategy);
```
&nbsp;  
&nbsp;
#### > Set cancel button visibility

Sets the visibility of cancel button in title bar. When clicked SDK will return control to the host `Activity`.  

Default value is `false` (hidden).
```java
PIOConfig.setCancelOptionsButtonVisibility(boolean isVisible);
```
**Important:** Host `Activity` needs to be set. Refer to [setting host activity](#-set-host-activity)

To customize `Cancel` button appearance, you can modify following XML file:
`res/layout/item_nav_bar_button_cancel.xml`. 
Item representing button must retain the same `android:id` property value as well as `android:onClick` property.  
&nbsp;  
&nbsp;
#### > Set `Swipe to see more sizes` overlay visibility

Sets the visibility of `Swipe to see more sizes` hint overlay in Couch step (for applicable products).  
The overlay is shown once per each product.  

Default value is `false` (hidden).
```java
PIOConfig.setShowCouchHintOverlay(boolean showCouchHintOverlay);
```
&nbsp;  
&nbsp;

Photo Sources screen
--------------
#### > Set available photo sources. 

To select photo sources for this section, pass a `List` of `PhotoSource` objects to the following method.  

```java
PIOConfig.setPhotoSources(List<PhotoSource> photoSources);
```
**NOTICE:**  
- `PHONE` photo source will not be displayed in side menu.  
- Up to 6 photo sources are supported.  
- The order of photo sources on screen is determined by order of elements in the list.

&nbsp;  
&nbsp;  
#### > Set default photo source.  

Set photo source that will be selected by default.
```java
PIOConfig.setDefaultPhotoSource(PhotoSource defaultPhotoSource);
```
&nbsp;  
&nbsp;  
#### > Pass in images URLs or UIImage objects.  
( > Pass in images URLs)  

Set predefined list of images that will be available to the user.
```java
PIOConfig.setImageUrls(List<String> imageUris);
```
&nbsp;  
&nbsp;  
#### > If user pass in images usinig method 'images', this method can disable photo sources, forcing user to use only passed photos. This method overrides method 'availablePhotoSources'  
( > Disable photo sources)  

If images were preset using `setImageUrls(...)`, this method can be used to disable photo source screen and force the user to only use predefined photos.
```java
PIOConfig.setDisabledScreens(Arrays.asList(Screen.SELECT_IMAGES)));
```
&nbsp;  
&nbsp;  
Photo Sources credentials
-------------------------
#### > Set Instagram credentials  

In order to use Instagram as a photo source, credentials are required.  To obtain Instagram `CLIENT_ID`, refer to documentation at http://instagram.com/developer.
```java
// import print.io.photosource.impl.instagram.InstagramPhotoSource

InstagramPhotoSource instagramPS = new InstagramPhotoSource();
instagramPS.setClientId(String INSTAGRAM_CLIENT_ID);
instagramPS.setCallbackUri(String INSTAGRAM_CALLBACK_URI);
```
&nbsp;  
&nbsp;  
#### > Set Flickr credentials  

In order to use Flickr as a photo source, credentials are required. To obtain Flickr `CONSUMER_KEY` and `CONSUMER_SECRET`, refer to documentation at https://www.flickr.com/services/developer/api.
```java
// import print.io.photosource.impl.flickr.FlickrPhotoSource;

FlickrPhotoSource flickrPS = new FlickrPhotoSource();
flickrPS.setConsumerKey(String FLICKR_CONSUMER_KEY);
flickrPS.setConsumerSecret(String FLICKR_CONSUMER_SECRETT);
```
&nbsp;  
&nbsp;  
#### > Set Dropbox credentials  

In order to use Dropbox as a photo source, credentials are required.  To obtain Dropbox `CONSUMER_KEY` and `CONSUMER_SECRET`, refer to documentation at https://www.dropbox.com/developers/apps.
```java
DropboxPhotoSource dropboxPS = new DropboxPhotoSource();
dropboxPS.setConsumerKey(String DROPBOX_CONSUMER_KEY);
dropboxPS.setConsumerSecret(String DROPBOX_CONSUMER_SECRET);
```
&nbsp;  
&nbsp;  
#### > Set Facebook credentials  

In order to use Facebook as a photo source, credentials are required. To obtain Facebook `APP_ID`, refer to documentation at https://developers.facebook.com/apps.
&nbsp;  
You need to provide `facebook_app_id` in your app's `strings.xml` file.
```xml
<string name="facebook_app_id">000000000000000</string>
```
You can then reference it in java code (**required**) like this:
```java
PIOConfig.setFacebookAppId(getString(R.string.facebook_app_id));
```
&nbsp;  
&nbsp;  
#### > Set Photobucket credentials  

In order to use Photobucket as a photo source, credentials are required.  To obtain Photobucket `CLIENT_ID` and `CLIENT_SECRET`, refer to documentation at  http://pic.pbsrc.com/dev_help/WebHelpPublic/Content/FAQ/FAQOverview.htm#HowDoIUseAPI.

```java
// import print.io.photosource.impl.photobucket.PhotobucketPhotoSource;

PhotobucketPhotoSource photobucketPS = new PhotobucketPhotoSource();
photobucketPS.setClientId(String PHOTOBUCKET_CLIENT_ID);
photobucketPS.setClientSecret(String PHOTOBUCKET_CLIENT_SECRET);
```
&nbsp;  
If your app already logs user in to Photobucket, you will want to save the user from having to log in again inside the PrintIO SDK.  

To do this, you need to provide a Photobucket `USERNAME`, `BASE_API_URL`, `ACCESS_TOKEN` and `REFRESH_TOKEN` using the following methods.
```java
PhotobucketPhotoSource.setPhotobucketUsername(String photobucketUsername);
PhotobucketPhotoSource.setPhotobucketBaseApiUrl(String photobucketBaseApiUrl);
PhotobucketPhotoSource.setPhotobucketAccessToken(String photobucketAccessToken);
PhotobucketPhotoSource.setPhotobucketRefreshToken(String photobucketRefreshToken);
```
&nbsp;  
&nbsp;  
#### > Set Picasa credentials  

In order to use Picasa as a photo source, **no credentials are required**.  Picasa will allow the user to select one of the Google accounts set up on the device.
&nbsp;  
&nbsp;  
Customize Product screen
-----------------
#### > Show/hide tab bar in Customize Product screen.  
( > Show toolbar in Customize Product screen)  

The toolbar contains the following buttons: `Photos`, `Edit Tools`, `Options` and `Layout`.  
Default value is `true`.
```java
PIOConfig.setShowOptionsInCustomize(boolean showOptionsInCustomize);
```
**NOTICE:**  
Not all of those buttons' functions have been implemented yet.  
&nbsp;  
&nbsp;  
#### > Hide list with images in customization screen.  
( > Show a list of selected images in Customize Product screen)  

Default value is `true`.
```java
PIOConfig.setShowPhotosInCustomize(boolean showPhotosInCustomize);
```
&nbsp;  
&nbsp;  
#### > Shows button for adding images when photo sources are disabled.  
( >  Shows button for adding images when photo sources are disabled.)  

Default value is `false`.
```java
PIOConfig.enablePhotoSourcesInCustomizeProduct(boolean isEnabled);
```
&nbsp;  
&nbsp;  
#### > Set photo(s) arrangement in Customize Product screen.  
( > Auto-arrange photos in Customize Product screen)  

If this is set to `true`, instead of showing a blank product, images will be pre-arranged on it.  
The user will still be able to change the arrangement.  

If it is set to `false`, a dialog will appear allowing the user to choose between automatic and manual arrangement.  

Default value is `false`.
```java
PIOConfig.setAutoArrange(boolean autoArrange);
```
&nbsp;  
&nbsp;  

#### > Change image for "Add photos" button in Customize Product screen.  
( > Change the `Add photos` button icon in Customize Product screen)  

Replace following icons with your own icons of same names.  
Recommended dimensions are listed next to the icon name.
```
icon_add_more_images_a.png (111x111) - default state
icon_add_more_images_b.png (111x111) - pressed state
```
&nbsp;  
&nbsp;  
#### > Set Pop up balloon in Customize Product screen.  
( > Customize tooltip in Customize Product screen)  

To modify tooltip text, change the following item in `res/values/strings.xml`
```xml
<string name="customize_product_tooltip_text">Double click photo to edit</string>
```
To change tooltip background color, modify the following item in `res/values/colors.xml`
```xml
<color name="customize_product_tooltip">#42BE9C</color>
```
&nbsp;  
&nbsp;  
#### > Set Pop up balloon in Customize Product screen visibility timeout.  

By default, the pop up balloon disappears after 10 seconds.  
To change this value, use the following method:  
```java
PIOConfig.setDoubleTapBalloonVisibilityTime(int visibilityTimeoutSeconds);
```
**NOTICE:**  
The method takes SECONDS (not milliseconds) as argument.

&nbsp;  
&nbsp;  
Image Editor
------------
#### > Set which buttons will be visible in Image Editor toolbar. By default, all buttons are visible.  
( > Choose buttons to display in Image Editor)  

Available buttons are `Rotate`, `Edit Text` and `Effects`.  
By default, all buttons are visible.
```java
PIOConfig.setUpCropScreen(boolean isRotateAllowed, boolean isTextAllowed, boolean isEffectsAllowed);
```

To modify icons, replace following icons with your own icons of same names.  
Recommended dimensions for all icons:
height: 26dp (26 pixels mdpi, 78 pixels xxhdpi)
width: up to 52dp (52 pixels mdpi, 156 pixels xxhdpi)
```
icon_edit_image_info_default.png - default state
icon_edit_image_info_pressed.png - pressed state
icon_edit_image_rotate_default.png - default state
icon_edit_image_rotate_pressed.png - pressed state
icon_edit_image_text_default.png - default state
icon_edit_image_text_pressed.png - pressed state
icon_edit_image_effects_default.png - default state
icon_edit_image_effects_pressed.png - pressed state
```

To change background highlight colors, modify following items in `res/values/colors.xml`
```xml
<color name="edit_image_info_background_highlight">#EFEFF2</color>
<color name="edit_image_rotate_background_highlight">#42BE9C</color>
<color name="edit_image_text_background_highlight">#D94217</color>
<color name="edit_image_effects_background_highlight">#646AA6</color>
```

To change text colors, modify following items in `res/values/colors.xml`
```xml
<color name="edit_image_info_text_default">#22A0DD</color>
<color name="edit_image_info_text_pressed">#404040</color>

<color name="edit_image_rotate_text_default">#42BE9C</color>
<color name="edit_image_rotate_text_pressed">#FFFFFF</color>

<color name="edit_image_text_text_default">#D94217</color>
<color name="edit_image_text_text_pressed">#FFFFFF</color>

<color name="edit_image_effects_text_default">#646AA6</color>
<color name="edit_image_effects_text_pressed">#FFFFFF</color>
```
&nbsp;  
&nbsp;  
**NOTICE:**  
`Info` button is always visible.  
Not all of those buttons' functions have been implemented yet.  
&nbsp;  
&nbsp;  
Shopping Cart screen
-------------
#### > Set custom icon for Shopping Cart  

Replace following icons with your own icons of same names.  
Recommended dimensions are listed next to the icon name.
Dimensions are listed in baseline (MDPI) density.
```
icon_cart_default.png (24x24)
icon_cart_pressed.png (24x24)
icon_cart_items_qty_background (16x16) //Background for the badge that displays cart items count
```
Shopping cart quantity badge is top-right aligned with the shopping cart icon  
and its position is controlled by top and right margins.  
To change the margins, modify the respective items in `res/values/dimens.xml`.  
These are the default values.
```xml
<dimen name="cart_items_quantity_top_offset">10dip</dimen>
<dimen name="cart_items_quantity_right_offset">0dip</dimen>
```
To change cart quantity text color, modify the following item in `res/values/colors.xml`
```xml
<color name="text_cart_items_quantity">#FFFFFF</color>
```

The badge is only visible when there are items in the cart.
&nbsp;  
&nbsp;  
#### > Show Checkout Progress below the title bar in Shopping Cart  

Default value is 'false' (Checkout Progress is hidden).
```java
PIOConfig.setShowCheckoutProgress(boolean showCheckoutProgress);
```
&nbsp;  
&nbsp;  
#### > Show "Add more products" button on Shopping Cart screen  

Default value is 'true' (button is visible).
```java
PIOConfig.setShowAddMoreProductsInShoppingCart(boolean isVisible);
```
&nbsp;  
&nbsp;  
#### > Set click action strategy for "Add more products" button

Possible strategies:

* `OPEN_PRODUCTS_SCREEN` - Opens "Products" screen.
* `RETURN_TO_HOST_ACTIVITY` - Closes SDK and returns to the host `Activity`.

Default value is `AddMoreProductsButtonStrategy.OPEN_PRODUCTS_SCREEN`.
```java
PIOConfig.setAddMoreProductsButtonStrategy(AddMoreProductsButtonStrategy strategy);
```

**Important:** In order to use `RETURN_TO_HOST_ACTIVITY`, host `Activity` needs to be set. Refer to [setting host activity](#-set-host-activity)
&nbsp;  
&nbsp;  
#### > Change style of "Add more products" button

To change color of button text, modify the following item in `res/values/colors.xml`.
`<color name="button_add_more_products_text">#22A0DD</color>`

To change button text, modify the following item in `res/values/strings.xml`.
`<string name="button_add_more_products_text">Keep Shopping</string>`
&nbsp;  
&nbsp;
#### > Set delete mode for Shopping Cart

Available modes:

* `HIDDEN` - Delete buttons are displayed using "Remove Item" button at the bottom of the screen.
* `VISIBLE` - Each item has its own delete button in the top right corner.

Default value is `ShoppingCartDeleteMode.HIDDEN`.
```java
PIOConfig.setShoppingCartDeleteMode(ShoppingCartDeleteMode shoppingCartDeleteMode);
```
&nbsp;  
&nbsp;    
#### > Controls if widget should be closed when tap on Back button in "Shopping Cart" screen. 

Default value is false (functionality is ignored).
```java
PIOConfig.closeWidgetFromShoppingCart(boolean closeWidgetFromShoppingCart);
```
&nbsp;  
&nbsp; 
#### > Change style of "Remove Item" button
To change style of "Remove Item" button, modify following resources
`res/layout/item_button_remove_item.xml`.

_Note that layout attributes (such as width, height, margin, etc..) will be overridden in files were these layouts are included._
&nbsp;  
&nbsp;
Add Address screen
--------------
#### > Change design of "Choose From Contacts" button

To change design of "Choose From Contacts" button modify following resource: 
`res/layout/item_choose_from_contacts.xml`.

_Note that button element has to remain the same id property value._

Payment screen
--------------
#### > Set Available Payment Options  

To select available payment options, pass a `List` of `PaymentOptionType` to the following method.  
By default, all payment options defined in `PaymentOptionType` enum are used.
```java
PIOConfig.setPaymentOptions(List<PaymentOptionType> paymentOptions);

public enum PaymentOptionType {
	PAY_PAL,
	CREDIT_CARD;
}
```
&nbsp;  
&nbsp;  
Steps
-----
#### > Jumps directly to product.  
( > Jump to product)  

Instead of opening Products screen, go directly to specified product's details.
```java
/**
 * Set product type of the product whose "Product Details" screen will be
 * shown directly when SDK launches. To disable this functionality set
 * {@code product} to {@code null}.
 * 
 * @param product
 *            The {@code ProductType} of the product to jump to. Default
 *            value is {@code null} (functionality is ignored).
 */
PIOConfig.setProductFromApp(ProductType product);
```
Or go to the `Product Options` screen by disabling `Product Details` screen (or to the `Product Customization` screen if `Product Options` and `Select Images` screens are disabled).

```java
PIOConfig.setDisabledScreens(Arrays.asList(Screen.PRODUCT_DETAILS /*, Screen.OPTIONS, Screen.SELECT_IMAGES */)));
```
&nbsp;  
&nbsp;  
#### > Predefine a SKU for product

If product options page is disabled, you can predefine a SKU for product. Otherwise, default SKU will be used.

```java
PIOConfig.setProductSkuFromApp(String productSkuFromApp);
```
**NOTICE:**  
This method will **not** work for Coasters products.  
&nbsp;  
&nbsp;  
Shipping Addresses screen
------------------
#### >  Clear all saved shipping addresses 
```java
PIO.clearShippingAddresses(Context context);
```
&nbsp;
&nbsp;
Choose Country screen
------------------
#### >  Set shopping cart button visibility
Sets shopping cart button visibility in navigation bar. Default value is `false` (button is invisible).

```java
PIOConfig.setShowShoppingCartButtonVisibilityOnCountryScreen(boolean isVisible)
```
&nbsp;
&nbsp;
PayPal Settings
---------------
#### > Set PayPal's client ID

To configure SDK to work with your PayPal account, set appropriate PayPal client ID. If not specified, SDK will use Gooten's account client ID.  

Gooten SDK is currently using PayPal Android SDK version 1.2.1.

PayPal CLIENT_ID can be obtained here  
https://developer.paypal.com/webapps/developer/applications/myapps  
```java
PIOConfig.setPayPalClientId(String PAY_PAL_CLIENT_ID);
```
**NOTICE:**  
If `PIOConfig.setLiveApplication(...)` was set to `true`, PayPal **Live** environment is used. Otherwise, **Sandbox** environment is used.  Therefore, make sure to set appropriate PayPal client ID (based on used environment).
&nbsp;  
&nbsp;  
Braintree Settings
------------------
#### > Set Braintree encryption key

To configure SDK to work with your Braintree account, set appropriate Braintree encryption key. If not specified, SDK will use Gooten's account encryption key.  

```java
PIOConfig.setBraintreeEncryptionKey(String BRAINTREE_ENCRYPTION_KEY);
```
&nbsp;  
&nbsp;  
Other Customization
===================

#### > Import customization XML file  
(Does not exist on Android)
&nbsp;
&nbsp;
#### > Adjust font sizes  

Fonts sizes are organized into five "buckets", plus some sizes for special uses.  
To change their sizes, modify the respective items in `res/values/dimens.xml`.  
These are the default values which work well with default fonts.
```xml
<dimen name="text_size_small">12dip</dimen>
<dimen name="text_size_normal">14dip</dimen>
<dimen name="text_size_large">18dip</dimen>
<dimen name="text_size_title">20dip</dimen>
<dimen name="text_size_huge">32dip</dimen>

<dimen name="text_size_button_create_it">12dip</dimen>

<dimen name="text_size_photosources">12dip</dimen>

<dimen name="text_size_cart_items_quantity">8dip</dimen>

<dimen name="text_size_side_menu_button">14dip</dimen>
```
&nbsp;  
&nbsp;  
#### > Set custom fonts from main app bundle.  
( > Set custom fonts)  

Pass font's filename to appropriate method.  
`.otf` and `.ttf` fonts are supported.
```java
setFontPathInAssetsNormal("HelveticaNeueLTStd-Roman.otf");
setFontPathInAssetsLight("HelveticaNeueLTStd-Lt.otf");
setFontPathInAssetsBold("HelveticaNeueLTStd-Bd.otf");
setFontPathInAssetsTitle("HelveticaNeueLTStd-Roman.otf");
```
**NOTICE:**  
Fonts need to be placed in `assets` dir.  
&nbsp;  
&nbsp;  
#### > Change "Loading" GIF animation  
( > Change Loading animation)  

Currently, Android's GIF support is very limited.
PrintIO Android SDK does not use GIF animations directly.  
To set a custom loading animation, follow these steps:  
&nbsp;  
1) Extract individual frames from GIF animation.  
This can be done using free online tools, for example: http://gif-explode.com/  
&nbsp;  
2) Copy individual frames to appropriate drawable(s) folder(s).  
&nbsp;  
3) Modify `res/anim/progress_anim_multicolor.xml` to reference new frames.
```xml
<?xml version="1.0" encoding="utf-8"?>
<animation-list xmlns:android="http://schemas.android.com/apk/res/android" >

    <item
        android:drawable="@drawable/loading_01_multicolor"
        android:duration="80"/>
    <item
        android:drawable="@drawable/loading_02_multicolor"
        android:duration="80"/>

    ...

    <item
        android:drawable="@drawable/loading_26_multicolor"
        android:duration="80"/>
</animation-list>
```
**NOTICE:**  
`android:duration` parameter specifies the amount of time a single frame will be shown, in milliseconds.  
Smaller value equals faster animation and vice-versa.  
&nbsp;  
&nbsp;  
#### > Change title of loading dialog  
( > Change loading dialog text)  

To modify loading dialog title and message, change the following items in `res/values/strings.xml`
```xml
<string name="progress_text_pt1">Loading... Please wait.</string>
<string name="progress_text_pt2">Think Happy Thoughts</string>
```
&nbsp;  
&nbsp;  
#### > Change icon for Help Button.  
( > Change `Help` button icon)  

Replace the following icon with your own icon of the same name.  
Recommended dimensions are listed next to the icon name.
```
icon_question_big.png (25x38)
```
&nbsp;  
&nbsp;  
#### > Change logo in SDK.  
( > Set custom logo for the SDK)  

Logo is hidden by default.
To show logo in the navigation bar, use the following method
```java
/**
 * @param imageResourceId - ID of a drawable resource to be used.
 * Make sure to use the image of appropriate size.
 */
PIOConfig.setApplicationIconId(int imageResourceId);
```
&nbsp;  
&nbsp;  
#### > Set payee name.  
( > Set PayPal payee name)  

Default is blank (no name).
```java
PIOConfig.setPartnerName(String partnerName);
```
&nbsp;  
&nbsp;  
#### > Jump to screen  
( > Jumps directly to screen)

Sets the screen to jump to when SDK launches  and the screen which should be shown when user navigates back.  
Following screens are supported by this method:
- `Screen.PRODUCTS`
- `Screen.SHOPPING_CART`

```java
/**
 * Sets the screen to jump to when SDK launches and screen which should be
 * shown when user navigates back.
 * 
 * @param screen
 *            The screen to be shown first when SDK launches. Default value
 *            is {@code null} (functionality is ignored).
 * @param navigateBackScreen
 *            The screen to be shown after user navigates back from the
 *            screen on which has been jumped to. Default value is
 *            {@code null} (functionality is ignored).
 */
PIOConfig.setJumpToScreen(Screen screen, Screen navigateBackScreen)
```

&nbsp;  
&nbsp;  
#### > Change buttons' colors  

To change buttons' colors, modify the following items in `res/values/colors.xml`  
&nbsp;  
Primary button:
```xml
<color name="button_primary_default">#42BE9C</color>
<color name="button_primary_pressed">#09866D</color>
<color name="button_primary_text">#FFFFFF</color>
```
&nbsp;
Secondary button:
```xml
<color name="button_secondary_default">#22A0DD</color>
<color name="button_secondary_pressed">#0E79AD</color>
<color name="button_secondary_text">#FFFFFF</color>
```
&nbsp;
Save To Cart button:
```xml
<color name="button_save_to_cart_background_default">#22A0DD</color>
<color name="button_save_to_cart_background_pressed">#0E79AD</color>
<color name="button_save_to_cart_text">#000000</color>
```
&nbsp;
Save To Cart button in Customize Photobooks screen:
```xml
<color name="button_save_to_cart_photobooks_text">#000000</color>
<color name="button_save_to_cart_photobooks_border">#000000</color>
<color name="button_save_to_cart_photobooks_background">#00000000</color>
```
**NOTICE:**  
Those buttons are used throughout the application.  
Do **not** change colors' names, only change the values (#xxxxxx).  
"Primary" and "Secondary" do not hold any significance beyond simply differentiating between buttons' colors:  
All "Primary" buttons have same color and all "Secondary" buttons have same color.  
More categories may be added in the future.  
Colors' names will be changed to more generic names in the future.  
&nbsp;  
&nbsp;  
#### > Product Details screen  
( > Change Product Details screen labels icons and colors)  

Replace the following icon(s) with your own icon(s) of the same name(s).  
Recommended dimensions are listed next to the icon name.
```
icon_details.png (40x40)
icon_shipping_info.png (42x40)
icon_quality_guarantee.png (40x40)
```
To change labels' colors, modify the following items in `res/values/colors.xml`
```xml
<!--Description-->
<color name="product_details_header_1">#323232</color>

<!--Details-->
<color name="product_details_header_2">#42BE9C</color>

<!--Shipping Info-->
<color name="product_details_header_3">#22A0DD</color>

<!--Quality Guarantee-->
<color name="product_details_header_4">#646AA6</color>
```
To change 'Quality Guarantee' text, modify following item in
`res/values/strings.xml`
```xml
<string name="quality_guarantee_text">Your memories are our top priority...</string>
```
&nbsp;  
&nbsp;  
#### > Dialog "Arrange Photos"  
( > Change buttons labels in Auto Arrange dialog)  

To modify buttons' labels, change the following items in `res/values/strings.xml`
```xml
<string name="random_auto_arrange">Auto Random\nArrange</string>
<string name="manual_drag_drop">Manual\nDrag and Drop</string>
```
**NOTICE:**  
Use `newline` character `\n` to manually add new lines.  
&nbsp;  
&nbsp;  
#### > Dialog "Address Type"  
( > Change Address Type dialog labels)  

To modify labels, change the following items in  `res/values/strings.xml`
```xml
<string name="business_residential">Is this address Business or Residental?</string>
<string name="business">Business\nAddress</string>
<string name="residential">Residential\nAddress</string>
```
**NOTICE:**   
Use `newline` character `\n` to manually add new lines.  
&nbsp;  
&nbsp; 
#### > Dialog "What's New"  
( > Change What's New dialog text)

  To modify text, change the following item in `res/values/strings.xml`
```xml
<string name="whats_new_dialog_text"></string>
```
**NOTICE:**   
Dialog text will be converted to HTML markup when displayed. Dialog will not be shown when text is undefined.
 &nbsp;  
&nbsp; 
#### > "Product image Preview" screen  
( > Change Product Preview screen labels)  

Labels' colors are the same color as the secondary button  
&nbsp;  
&nbsp;  
#### > Set "About" text  

To modify "About" text, change the following item in `res/values/strings.xml`
```xml
<string name="about_subtitle">About:</string>
<string name="about_text">Our Mission is to foster creative individuality and bring on-demand printed products to people all over the world. We hope to surround people with their favorite memories and brands, to remind them of the better things in life, improving the world one creation at a time.\n\nWe have an unwavering commitment to quality and customer satisfaction. If you\'re not happy, we\'re not happy. That\'s why we go the extra mile to insure that we carry the highest quality products, printed by the best printers, at the best possible prices.\n\nWe have print facilities all over the world, so whether you\'re in the USA, India, or Laos, we can ship to you! Since inception, we\'ve shipped to over 100 countries.\n\nsupport@gooten.com for support and friends</string>
```
**NOTICE:**  
Use `newline` character `\n` to manually add new lines.  
&nbsp;  
&nbsp;  
#### > Set "How it Works" text  

To modify "How it Works" section, change the following items in `res/values/strings.xml`
```xml
<string name="how_it_works_subtitle">How It Works:</string>
<string name="how_it_works_text">1. Browse through our selection of products and choose the item or items you would like to purchase. We carry the highest quality products, printed by the best printers, at the best possible prices.\n\n2. Customize your item. Choose the size, shape, layout and product options you like best.\n\n3. Upload your images, or designs. Import from your phone, Instagram, Facebook, Flickr, Picasa, or Dropbox.\n\n4. Ship to any country in the world! Specify your location and choose shipping method. We\'ve shipped to over 100 countries and counting.\n\n5. Pay using PayPal or the credit card of your choice. Our custom credit card imaging system makes it easier than ever to pay! All of your credit card info is automatically entered with one simple photo.\n\n6. Enjoy! We place the utmost importance on quality and customer satisfaction. We know you\'ll love the products! Enjoy.</string>
```
**NOTICE:**  
Use `newline` character `\n` to manually add new lines.  