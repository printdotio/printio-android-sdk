# Developer SDK Customization Reference

Notice: Items that are implemented in iOS SDK but are missing from Android SDK are marked using strikethrough 

---

## Status Bar Settings

Set status bar style and visibility. Default value is light and visible.  
(Hide status bar)  

Default value is `false` (not hidden).

### Code Sample

```java
PIO.setHideStatusBar(boolean hideStatusBar);
```
### Screenshots - to be added

| Currently | Changed |
| :---- | :---- | :---- |

---

## Navigation Bar Settings

- Change navigation bar color and title font color, also set left and right bar button.  

This can be done in xml by changing the following item in  

| Resource | Method |
| :---- | :---- |
| `res/values/colors.xml` | `<color name="title_bar_background">#FFFFFF</color>` |


~~`<color name="title_bar_left_button_background">#FFFFFF</color>`~~  
~~`<color name="title_bar_right_button_background">#FFFFFF</color>`~~  

### Code Sample

```java
PIO.setHeaderColor(int color); //color is a 6-digit (rgb) or 8-digit (argb) hex value
```
_Note that the value set programmatically will override the value set in xml!_  
 
- To change separator and texts' colors, modify the following items in  
 
| Resource | Method |
| :---- | :---- |
| `res/values/colors.xml` | `<color name="title_bar_separator">#d6d6d6</color>` |
| `res/values/colors.xml` | `<color name="title_bar_text">#000000</color>` |
| `res/values/colors.xml` | `<color name="text_cart_items_quantity">#FFFFFF</color>` |

~~`titleButtonIcon:(NSString *)iPath;`~~  

### Screenshots - to be added

| Currently | Changed |
|  :---- | :---- |
  
_NOTICE: Never modify xml item names. Modify values only._  

---

## Set Icon For Back Button  
(Change `Back` button icon)  

Replace the following icon with your own icon of the same name.  
Recommended dimensions are listed next to the icon name.

| Resource | Parameters - Options |
| :---- | :---- |
| `res/drawable-xhdpi` | `icon_arrow_back_2.png (19x33)` |

### Screenshots - to be added

| Currently | Changed |
|  :---- | :---- |

--- 

#### > Set three buttons Back, Menu and Cart button in navigation bar for Featured Products screen  
( > Set three buttons title bar style)

Show `Back`, `Menu` and `Cart` buttons in navigation bar for Featured Products screen.  
Default value is `false`.
```java
PIO.useThreeButtonsBarStyle(boolean useThreeButtonsBarStyle);
```
&nbsp;  
&nbsp;  
Side Menu
---------
#### > Use Side Menu with options.  
( > Change side menu icon)  

Replace following icons with your own icons of same names.  
Recommended dimensions are listed next to the icon name.
```
icon_menu_default.png (39x29)
icon_menu_pressed.png (39x29)
```
&nbsp;  
&nbsp;  
( > Change side menu background color)  

To change side menu background color, modify the following item in  
`res/values/colors.xml`
```xml
<color name="side_menu_background">#1D1D1D</color>
```
&nbsp;  
&nbsp;  
*On iOS this is a part of "Set which options to use in side menu"
( > Change side menu separators' colors)  

To change side menu separators' colors, modify the following items in  
`res/values/colors.xml`
```xml
<color name="separator_color_1">#000000</color>
<color name="separator_color_2">#343434</color>
```
&nbsp;  
&nbsp;  
( > Change side menu text color)  

To change side menu text color, modify the following item in  
`res/values/colors.xml`
```xml
<color name="side_menu_text">#FFFFFF</color>
```
&nbsp;  
&nbsp;  
#### > Set which options to use in side menu  
( > Choose which options will be displayed in side menu)  

**Buttons** section is at the top of the side menu.  
&nbsp;  
To select buttons for this section, pass a `List` of `SideMenuButton` to the following method
```java
PIO.setSideMenuButtons(List<SideMenuButton> sideMenuButtons);

enum SideMenuButton {
	EXIT_BUTTON,
    SEARCH_BAR,
    PRODUCTS,
    FEATURED_PRODUCTS,
    SHARE_WITH_IMAGE,
    EMAIL_SUPPORT,
    HELP,
    VIEW_CART;
};
```
or, to use the default buttons, call
```java
PIO.setDefaultSideMenuButtonsTop();
```
&nbsp;  
To modify buttons' icons, replace the corresponding icon with your own.
Recommended dimensions are listed next to the icon name.
```
icon_exit_sdk.png (17x30)
icon_products.png (52x52)
icon_featured_products.png (52x52)
icon_email.png (52x52)
icon_help.png (17x26)
icon_cart_white.png (45x42)
```
&nbsp;  
#### > Get order information when SDK is closed  

In order to get back order information, host activity needs to be specified.  
Control will be returned to this activity when PrintIO SDK is closed.  
To set host activity, use the following method:
```java
//Use qualified class name, like this: "com.example.piosdkpoconcept.ActivityTest"
PIO.setHostAppActivity(String className);
```

Order information is passed back to the host activity through Intent.  
To obtain this data, use the following code snippet:
```java
ArrayList<String> cartItems = getIntent().getStringArrayListExtra("ShoppingCartItems");
```
&nbsp;  
#### > Pass promo coupon code to SDK  

Pass a promo coupon code which will be shown to user in `Shopping Cart` screen.  
The user can choose to apply the coupon to get discounts or promotions.  

Once products in shopping cart are purchased, coupon code is cleared.  

To set promo coupon code, use the following method:
```java
PIO.setPromoCode(String promoCode);
```
&nbsp;
#### > Set support email address  

To set support email address, use the following method:
```java
PIO.setSupportEmail(String supportEmail);
```
&nbsp;  
##### **Options** section:  

To modify its title, change the following item in  
`res/values/strings.xml`  
and if your app supports multiple languages, change the appropriate items in  
`res/values-language/strings.xml`
```xml
<string name="options">Options</string>
```
**NOTICE:**  
Never modify xml item names.  
Modify values only.  
&nbsp;  
To change the section title color, modify the following item in  
`res/values/colors.xml`
```xml
<color name="side_menu_options_subtitle_text">#FFFFFF</color>
```
&nbsp;  
To change the section title background color, modify the following item in  
`res/values/colors.xml`
```xml
<color name="side_menu_options">#239EDB</color>
```
&nbsp;  
To change the currency code color, modify the following item in  
`res/values/colors.xml`
```xml
<color name="side_menu_change_currency_text">#FFFFFF</color>
```
&nbsp;  
To change the `Change Country` icon, replace the following icon
with your own icon of same name.  
Recommended dimensions are listed next to the icon name.
```
icon_change_country.png (80x80)
```
&nbsp;  
To change the `Change Language` icon, replace the following icon
with your own icon of same name.  
Recommended dimensions are listed next to the icon name.
```
icon_change_language.png (80x80)
```
&nbsp;  
These methods control if the user is allowed to change the preset country, currency and language.  
The default values are `true`.
```java
PIO.setChangeableCountry(boolean changeableCountry);
PIO.setChangeableCurrency(boolean changeableCurrency);
PIO.setChangeableLanguage(boolean changeableLanguage);
```
&nbsp;  
##### **Accounts** section:
Contains the available photo sources that the app will use.  
To modify its title, change the following item in  
`res/values/strings.xml`  
and if your app supports multiple languages, change the appropriate items in  
`res/values-language/strings.xml`
```xml
<string name="accounts">Accounts</string>
```
&nbsp;  
To change the section title color, modify the following item in  
`res/values/colors.xml`
```xml
<color name="side_menu_accounts_subtitle_text">#FFFFFF</color>
```
&nbsp;  
To change the section title background color, modify the following item in  
`res/values/colors.xml`
```xml
<color name="side_menu_accounts">#1CBA9B</color>
```
&nbsp;  
#### > To select Photo Sources that will be displayed here, refer to **Photo Sources** section of this document.
#### > To hide **Accounts** section, use the following method
```java
PIO.hidePhotoSourcesInSideMenu(boolean hidePhotoSources);
```
&nbsp;  
##### **Info** section:  
To modify its title, change the following item in  
`res/values/strings.xml`  
and if your app supports multiple languages, change the appropriate items in  
`res/values-language/strings.xml`
```xml
<string name="info">Info</string>
```
&nbsp;  
To change the section title color, modify the following item in  
`res/values/colors.xml`
```xml
<color name="side_menu_info_subtitle_text">#FFFFFF</color>
```
&nbsp;  
To change the section title background color, modify the following item in  
`res/values/colors.xml`
```xml
<color name="side_menu_info">#6369A6</color>
```
&nbsp;  
To select buttons for this section, pass a `List` of `SideMenuInfoButton` to the following method
```java
PIO.setSideMenuInfoButtons(List<SideMenuInfoButton> sideMenuInfoButtons);

enum SideMenuButton {
    PRICING_CHART,
    SHARE_APP,
    LIKE_US_FB,
    RATE_APP,
    ABOUT,
    HOW_IT_WORKS,
    PAST_ORDERS;
};
```
or, to use the default buttons, call
```java
PIO.setDefaultSideMenuInfoButtons();
```
&nbsp;  
To modify buttons' icons, replace the corresponding icon with your own.
Recommended dimensions are listed next to the icon name.
```
icon_side_menu_pricing_chart.png (baseline-mdpi:26x26; xhdpi:52x52)
icon_side_menu_share_this_app.png (baseline-mdpi:26x26; xhdpi:52x52)
icon_side_menu_like_us_on_facebook.png (baseline-mdpi:26x26; xhdpi:52x52)
icon_side_menu_rate_our_app.png (baseline-mdpi:26x26; xhdpi:52x52)
icon_side_menu_about.png (baseline-mdpi:26x26; xhdpi:52x52)
icon_side_menu_how_it_works.png (baseline-mdpi:26x26; xhdpi:52x52)
icon_side_menu_past_orders.png (baseline-mdpi:26x26; xhdpi:52x52)
```
&nbsp;  
&nbsp;  
#### > Slide side menu from right. Default value is NO.  
( > Slide side menu from right side)  

Default value is `false` (side menu slides from left side).
```java
PIO.setRightSideMenu(boolean rightSideMenu);
```
&nbsp;  
&nbsp;  
#### > This is option from Side Menu, in order to use it, Side Menu needs to be enabled first.  
( > Set share text)  

This is an option from Side Menu.  
In order to use it, Side Menu needs to be enabled.
```java
/**
 * @param shareText - Text that will be used when sharing. May contain link.
 */
PIO.setShareText(String shareText);
```
&nbsp;  
&nbsp;  
Featured Products
--------------
#### > Set country on Featured Products screen instead on First screen. Default value is YES.  
( > Set country on Featured Products screen instead on First screen)  

Default value is `true`.
```java
PIO.setCountryOnFeaturedProducts(boolean setCountryOnFeaturedProducts);
```
&nbsp;  
&nbsp;  
#### > Hide category+search view on Featured Products screen. Default value is NO;  
( > Hide category+search view on Featured Products screen)  

Default value is `false`.
```java
PIO.setHideCategorySearchBar(boolean hideCategorySearchBar);
```
&nbsp;  
&nbsp;  
Photo Sources
--------------
#### > Set available photo sources. The order of photo sources on screen will be the same like order they are placed in array.  
( > Set available photo sources)  

To select photo sources for this section, pass a `List` of `PhotoSource` to the following method.  
The order of photo sources on screen is determined by order of elements in the list.
```java
PIO.setPhotoSources(List<PhotoSource> photoSources);

enum PhotoSource {
	PHONE,
	INSTAGRAM,
	FACEBOOK,
	DROPBOX,
	PICASA,
	FLICKR,
	PHOTOBUCKET;
};

```
**NOTICE:**  
`PHONE` photo source will not be displayed in side menu.  
Up to 6 photo sources are supported.  
&nbsp;  
&nbsp;  
#### > Set default photo source.  

Set photo source that will be selected by default.
```java
PIO.setDefaultPhotoSource(PhotoSource defaultPhotoSource);
```
&nbsp;  
&nbsp;  
#### > Pass in images URLs or UIImage objects.  
( > Pass in images URLs)  

Set predefined list of images that will be available to the user.
```java
PIO.setImageUrls(String[] imageUrls);
```
&nbsp;  
&nbsp;  
#### > If user pass in images usinig method 'images', this method can disable photo sources, forcing user to use only passed photos. This method overrides method 'availablePhotoSources'  
( > Disable photo sources)  

If images were preset using `setImageUrls(...)`, this method can be used to disable photo sources and force the user to only use predefined photos.
```java
PIO.setPhotosourcesDisabled(boolean isPhotosourcesDisabled);
```
&nbsp;  
&nbsp;  
~~#### > Disable photo sources only if image is passed in, and user selects template with one photo~~  

```java
//TO BE DONE
PIO.setPhotosourcesDisabledForOnePhotoTemplate(boolean isPhotosourcesDisabledForOnePhotoTemplate);
```
&nbsp;  
&nbsp;  
#### > Set passed in image to be first in row for all photo sources  

```java
PIO.setPassedImageFirstInPhotoSources(boolean passedImageFirstInPhotoSources);
```
**NOTICE:**  
Currently works only for `PHONE` photo source.
&nbsp;  
&nbsp;  
#### > Set passed in image as thumbnail for templates with one photo. Right now, only supports Canvas Wraps and Framed Prints.  
( > Set passed in image as thumbnail for templates with one photo)  

```java
PIO.setPassedImageThumb(boolean passedImageThumb);
```
**NOTICE:**  
Currently supports Canvas Wraps, Framed Prints and Acrylic Prints.
&nbsp;  
&nbsp;  
~~#### > ??? Hide icon for Upload Instructions text in Photo Sources screen~~  

~~Default value is `false`.~~
```java
//TO BE DONE
PIO.setHideIconForUploadInstructions(boolean hideIconForUploadInstructions);
```
&nbsp;  
&nbsp;  
Photo Sources Credentials
-------------------------
#### > Set Instagram credentials  

In order to use Instagram as a photo source, credentials are required.  
To obtain Instagram `CLIENT_ID`, refer to documentation at http://instagram.com/developer
```java
PIO.setInstagramClientId(String INSTAGRAM_CLIENT_ID);
```
~~**NOTICE:**~~  
~~If you are asked for `REDIRECT URI`, set it to `http://x-oauthflow-instagram`.~~
&nbsp;  
&nbsp;  
#### > Set Flickr credentials  

In order to use Flickr as a photo source, credentials are required.  
To obtain Flickr `CONSUMER_KEY` and `CONSUMER_SECRET`, refer to documentation at https://www.flickr.com/services/developer/api
```java
PIO.setFlickrConsumerKey(String FLICKR_CONSUMER_KEY);
PIO.setFlickrConsumerSecret(String FLICKR_CONSUMER_SECRET);
```
~~**NOTICE:**~~  
~~If you are asked for `REDIRECT URI`, set it to `http://x-oauthflow-flickr`.~~
&nbsp;  
&nbsp;  
#### > Set Dropbox credentials  

In order to use Dropbox as a photo source, credentials are required.  
To obtain Dropbox `CONSUMER_KEY` and `CONSUMER_SECRET`, refer to documentation at https://www.dropbox.com/developers/apps
```java
PIO.setDropboxConsumerKey(String DROPBOX_CONSUMER_KEY);
PIO.setDropboxConsumerSecret(String DROPBOX_CONSUMER_SECRET);
```
~~**NOTICE:**~~  
~~If you are asked for `REDIRECT URI`, set it to `http://x-oauthflow-dropbox`.~~
&nbsp;  
&nbsp;  
#### > Set Facebook credentials  

In order to use Facebook as a photo source, credentials are required.  
To obtain Facebook `APP_ID`, refer to documentation at https://developers.facebook.com/apps  
&nbsp;  
You need to provide `facebook_app_id` in your app's `strings.xml` file.
```xml
<string name="facebook_app_id">000000000000000</string>
```
You can then reference it in java code (**required**) like this:
```java
PIO.setFacebookAppId(getString(R.string.facebook_app_id));
```
&nbsp;  
&nbsp;  
#### > Set Photobucket credentials  

In order to use Photobucket as a photo source, credentials are required.  
To obtain Photobucket `CLIENT_ID` and `CLIENT_SECRET`, refer to documentation at http://pic.pbsrc.com/dev_help/WebHelpPublic/Content/FAQ/FAQOverview.htm#HowDoIUseAPI
```java
PIO.setPhotobucketClientId(String PHOTOBUCKET_CLIENT_ID);
PIO.setPhotobucketClientSecret(String PHOTOBUCKET_CLIENT_SECRET);
```
&nbsp;  
If your app already logs user in to Photobucket, you will want to save the user from having to log in again inside the PrintIO SDK.  

To do this, you need to provide a Photobucket `USERNAME`, `BASE_API_URL`, `ACCESS_TOKEN` and `REFRESH_TOKEN` using the following methods.
```java
PIO.setPhotobucketUsername(String photobucketUsername);
PIO.setPhotobucketBaseApiUrl(String photobucketBaseApiUrl);
PIO.setPhotobucketAccessToken(String photobucketAccessToken);
PIO.setPhotobucketRefreshToken(String photobucketRefreshToken);
```
&nbsp;  
&nbsp;  
#### > Set Picasa credentials  

In order to use Picasa as a photo source, **no credentials are required**.  
Picasa will allow the user to select one of the Google accounts set up on the device.
&nbsp;  
&nbsp;  
Customize Product
-----------------
#### > Show/hide tab bar in Customize Product screen. Default value is YES.  
( > Show toolbar in Customize Product screen)  

The toolbar contains the following buttons: `Photos`, `Edit Tools`, `Options` and `Layout`.  
Default value is `true`.
```java
PIO.setShowOptionsInCustomize(boolean showOptionsInCustomize);
```
**NOTICE:**  
Not all of those buttons' functions have been implemented yet.  
&nbsp;  
&nbsp;  
#### > Hide list with images in customization screen.  
( > Show a list of selected images in Customize Product screen)  

Default value is `true`.
```java
PIO.setShowPhotosInCustomize(boolean showPhotosInCustomize);
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
PIO.setAutoArrange(boolean autoArrange);
```
**DIFFERENCES BETWEEN iOS and Android:**  
iOS version of the SDK provides the following choices:
- PIO_PHOTO_ARRANGEMENT_CHOOSE
- PIO_PHOTO_ARRANGEMENT_AUTO
- PIO_PHOTO_ARRANGEMENT_MANUAL
whereas in Android, this method corresponds to choice between:
- PIO_PHOTO_ARRANGEMENT_CHOOSE
- PIO_PHOTO_ARRANGEMENT_AUTO
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
#### > Change icon for Help Button on Customize Product screen.  
( > Change the `Help` button icon in Customize Product screen)  

Replace following icons with your own icons of same names.  
Recommended dimensions are listed next to the icon name.
```
icon_help_circle_grey.png (50x50px) - default state
icon_help_circle_grey_dark.png (50x50px) - pressed state
```
&nbsp;  
&nbsp;  
#### > Set Pop up balloon in Customize Product screen.  
( > Customize tooltip in Customize Product screen)  

To modify tooltip text, change the following item in  
`res/values/strings.xml`
```xml
<string name="customize_product_tooltip_text">Double click photo to edit</string>
```
To change tooltip background color, modify the following item in  
`res/values/colors.xml`
```xml
<color name="customize_product_tooltip">#42BE9C</color>
```
&nbsp;  
&nbsp;  
#### > Show custom dialog for helping user how to edit a photo.  
~~( > ??? Show custom help dialog on Image Editor screen)~~  

```java
//TO BE DONE
PIO.setImageEditorHelpDialog(...);
```
&nbsp;  
&nbsp;  
Image Editor
------------
#### > Set which buttons will be visible in Image Editor toolbar. By default, all buttons are visible.  
( > Choose buttons to display in Image Editor)  

Available buttons are `Rotate`, `Edit Text` and `Effects`.  
By default, all buttons are visible.
```java
PIO.setUpCropScreen(boolean isRotateAllowed, boolean isTextAllowed, boolean isEffectsAllowed);
```
**NOTICE:**  
`Info` button is always visible.  
Not all of those buttons' functions have been implemented yet.  
&nbsp;  
&nbsp;  
Shopping Cart
-------------
#### > Set custom icon for Shopping Cart  

Replace following icons with your own icons of same names.  
Recommended dimensions are listed next to the icon name.
```
icon_cart_default.png (45x42)
icon_cart_pressed.png (45x42)
icon_cart_items_qty_background (31x31) //Background for the badge that displays cart items count
```
Shopping cart quantity badge is bottom-right aligned with the shopping cart icon  
and its position is controlled by bottom and right margins.  
To change the margins, modify the respective items in `res/values/dimens.xml`.  
These are the default values.
```xml
<dimen name="cart_items_quantity_bottom_offset">5dip</dimen>
<dimen name="cart_items_quantity_right_offset">1dip</dimen>
```
To change cart quantity text color, modify the following item in  
`res/values/colors.xml`
```xml
<color name="text_cart_items_quantity">#FFFFFF</color>
```

**DIFFERENCES BETWEEN iOS and Android:**  
iOS version of the SDK allows the badge to be hidden.  
On Android version, the badge is always visible and its background can be changed.
&nbsp;  
&nbsp;  
#### > Customize `Shopping Cart` side menu button  

Replace following icons with your own icons of same names.  
Recommended dimensions are listed next to the icon name.
```
icon_cart_white.png (45x42)
icon_cart_items_qty_background_side_menu.png (31x31) //Background for the badge that displays cart items count
```
To change cart quantity text color, modify the following item in  
`res/values/colors.xml`
```xml
<color name="text_cart_items_quantity_side_menu">#FFFFFF</color>
```
&nbsp;  
&nbsp;  
#### > Remove plus sign from "Add more products" button. By default, sign is visible.  
( > Remove `+` sign from `Add More Products` button)  

Default value is `false` (`+` sign is visible).
```java
PIO.removePlusFromAddMoreProductsButton(boolean removePlusSign);
```
To change the icon for "Add More Products" button,
replace the following icon with your own icon of the same name.  
Recommended dimensions are listed next to the icon name.  
```
icon_add_more_products.png (36×36 xhdpi, 54x54 xxhdpi)
```
&nbsp;  
&nbsp;  
Payment Screen
--------------
#### > Remove logo from Payment and Order Confirmation screen.  
( > Remove logo from Payment ~~and Order Confirmation~~ screen)  

Default value is `false` (logo is visible).
```java
PIO.removeLogoFromPaymentScreen(boolean removeLogo);
```
To change the logo on Payment and Order Confirmation screens,
replace the following icon with your own icon of the same name.  
Recommended dimensions are listed next to the icon name.  
Default logo is a 100% transparent image (no logo).
```
icon_logo.png (71×80)
```
&nbsp;  
&nbsp;  
Country, Currency and Language
------------------------------
#### > Set country code  

Sets the default shipping country.
```java
/**
 * @param countryCode - A two-letter country code
 */
PIO.setCountryCode(String countryCode);
```
**NOTICE:**  
If `setCountryOnFeaturedProducts()` was set to `true`, default country code is `us`.  
Otherwise, the user is taken to Select Country screen and there is no default value.
&nbsp;  
&nbsp;  
#### > Set currency code  

If not set, default value is determined by the selected Country Code.
```java
/**
 * @param currencyCode - A three-letter currency code
 */
PIO.setCurrencyCode(String currencyCode);
```
&nbsp;  
&nbsp;  
~~#### > Set language code~~  

~~If not set, default value is determined by the selected Country Code.~~
```java
//TO BE DONE
/**
 * @param languageCode - A two-letter language code
 */
PIO.setLanguageCode(String languageCode);
```
&nbsp;  
&nbsp;  
Steps
-----
#### > Jumps directly to product.  
( > Jump to product)  

Instead of opening Featured Products screen, go directly to specified product.
```java
/**
 * @param productIdFromApp - ID of a product to jump to (Default value is -1)
 */
PIO.setProductIdFromApp(int productIdFromApp);
```
**NOTICE:**  
PRODUCT_IDS constants are currently `private`,
but will be made `public` in upcoming versions of the SDK.  
&nbsp;  
&nbsp;  
#### > Jumps directly to product with sku  
( > Jump to product with specific SKU)  

```java
/**
 * @param productIdFromApp - ID of a product to jump to
 * @param productSkuFromApp - SKU for product
 */
PIO.setIdAndSku(int productIdFromApp, String productSkuFromApp);
```
**NOTICE:**  
PRODUCT_IDS constants are currently `private`, but will be made `public` in upcoming versions of the SDK.  
SKUs currently work only for Phone Cases and Coasters.  
&nbsp;  
&nbsp;  
#### > Jump to SKU (no equivalent method on iOS exists)  

Force a SKU for product.
```java
PIO.setProductSkuFromApp(String productSkuFromApp);
```
**NOTICE:**  
This method only works for Phone Cases, **not** for Coasters.  
&nbsp;  
&nbsp;  
~~#### > Set Product Variant options~~  

```java
//TO BE DONE
PIO.setProductVariantFromApp(String productVariantFromApp);
```
&nbsp;  
&nbsp;  
Push Notifications
------------------
#### > Set applicationId and apiKey provided from parse.com  
#### > Register device to receive push notifications.  
( > Initialize Parse.com push notifications)  

To obtain Parse.com credentials, refer to https://parse.com/  
Set the Parse.com `APPLICATION_ID` and `CLIENT_KEY`.  
Pass an `Application` reference to `initializeParse(...)` method.
```java
PIO.setParseApplicationId(String PARSE_APPLICATION_ID);
PIO.setParseClientKey(String PARSE_CLIENT_KEY);
PIO.initializeParse(Application application);
```
&nbsp;  
&nbsp;  
#### > Display notification pop up from bottom of screen. On tap it will dismiss notification.  
(Does not exist on Android)  
&nbsp;
&nbsp;
PayPal Settings
---------------
#### > Set PayPal's client ids, for both modes, staging and production. Default values are client ids from PrintIO.  
( > Set up PayPal credentials)  

Our SDK is using the legacy PayPal MPL library for Android.  
(https://developer.paypal.com/webapps/developer/docs/classic/mobile/gs_MPL/)  

PayPal APP_ID is the id of the PayPal application.  
You can manage your applications here:  
https://developer.paypal.com/webapps/developer/applications/myapps  
PayPal APP_ID should look like this: "APP-XXXXXXXXXXXXXXXXX"  

PayPal CLIENT_ID is the public key for your app.  
You can find it in your app's credentials page.  
```java
PIO.setPayPalAppId(String PAY_PAL_APP_ID);
PIO.setPayPalClientId(String PAY_PAL_CLIENT_ID);
```
**NOTICE:**  
If `PIO.setLiveApplication(...)` was set to `true`, PayPal **Live** environment is used.  
Otherwise, **Sandbox** environment is used.  
&nbsp;  
&nbsp;  
#### > Define PayPal receiver email and set up fees  
(Does not exist on iOS)  

PayPal Receiver Email is your PayPal business account that will receive the payments from the app.  

PayPal Fee Payer decides who pays the PayPal fees.  
Default (and suggested) value is `FEEPAEYER_ACHRECEIVER`.  
You can read more about it here:  
https://developer.paypal.com/docs/classic/api/adaptive-payments/Pay_API_Operation/  
(search the page for "feesPayer")  
```java
PIO.setPayPalReceiverEmail(String PAY_PAL_RECEIVER_EMAIL);

/**
 * @param PAY_PAL_FEE_PAYER  
 * Sets who pays any transaction fees.
 * Possible values:
 * FEEPAYER_SENDER, FEEPAYER_PRIMARYRECEIVER, FEEPAYER_EACHRECEIVER,
 * and FEEPAYER_SECONDARYONLY
 */
PIO.setPayPalFeePayer(int PAY_PAL_FEE_PAYER);
```
&nbsp;  
&nbsp;  
Braintree Settings
------------------
#### > Set Braintree encryption key for staging and production mode. By default, keys from PrintIO will be used.  
( > Set up Braintree encryption key)  

```java
PIO.setBraintreeEncryptionKey(String BRAINTREE_ENCRYPTION_KEY);
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
(Does not exist on iOS)  

Fonts sizes are organized into six "buckets".  
To change their sizes, modify the respective items in `res/values/dimens.xml`.  
These are the default values which work well with default fonts.
```xml
<dimen name="text_size_small">12dip</dimen>
<dimen name="text_size_normal">14dip</dimen>
<dimen name="text_size_large">18dip</dimen>
<dimen name="text_size_title">20dip</dimen>
<dimen name="text_size_huge">32dip</dimen>

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
PIO.setFontPathInAssetsLight("HelveticaNeueLTStd-Lt.otf");
PIO.setFontPathInAssetsNormal("HelveticaNeueLTStd-Roman.otf");
PIO.setFontPathInAssetsBold("HelveticaNeueLTStd-Bd.otf");
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

To modify loading dialog title and message, change the following items in  
`res/values/strings.xml`
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
PIO.setApplicationIconId(int imageResourceId);
```
&nbsp;  
&nbsp;  
#### > Set payee name.  
( > Set PayPal payee name)  

Default is blank (no name).
```java
PIO.setPartnerName(String partnerName);
```
&nbsp;  
&nbsp;  
#### > Jumps to screen  
~~( > Jump to screen)~~  

```java
//TO BE DONE
/**
 * @param screen - Screen to jump to.
 * Can be one of following:
 * PRINTIO_SCREEN_SHOPING_CART
 */
PIO.goToScreen(int screen);
```
~~**NOTICE:**~~  
~~Screens constants are defined in Screens.java~~  
&nbsp;  
&nbsp;  
#### > Set url for Terms and Conditions  
~~( > Set Terms and Conditions URL)~~  

```java
//TO BE DONE
PIO.setTermsAndConditionsUrl(String termsAndConditionsUrl);
```
&nbsp;  
&nbsp;  
#### > Change buttons' colors  
(Does not exist on iOS)

To change buttons' colors, modify the following items in  
`res/values/colors.xml`  
&nbsp;  
Primary button:
```xml
<color name="blue_light">#22a0dd</color> <!--Default state-->
<color name="blue_dark">#0e79ad</color> <!--Pressed state-->
```
&nbsp;
Secondary button:
```xml
<color name="green">#42be9c</color> <!--Default state-->
<color name="green_dark">#09866d</color> <!--Pressed state-->
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
#### > “Product Details” screen  
( > Change Product Details screen labels icons and colors)  

Replace the following icon(s) with your own icon(s) of the same name(s).  
Recommended dimensions are listed next to the icon name.
```
icon_details.png (40x40)
icon_shipping_info.png (42x40)
icon_quality_guarantee.png (40x40)
```
To change labels' colors, modify the following items in  
`res/values/colors.xml`
```xml
<!--Details-->
<color name="green">#42be9c</color>
<!--Same color is currently being used for secondary buttons!-->
<!--Needs fixing-->

<!--Shipping Info-->
<color name="blue_light">#22a0dd</color>
<!--Same color is currently being used for primary buttons!-->
<!--Needs fixing-->

<!--Quality Guarantee-->
<color name="purple">#646aa6</color>
```
**DIFFERENCES BETWEEN iOS and Android:**  
Icons cannot be changed on iOS.  
`Description` label color cannot be changed on Android.  
&nbsp;  
&nbsp;  
#### > "Dialog Arrange Photos"  
( > Change buttons labels in Auto Arrange dialog)  

To modify buttons' labels, change the following items in  
`res/values/strings.xml`
```xml
<string name="random_auto_arrange">Auto Random\nArrange</string>
<string name="manual_drag_drop">Manual\nDrag and Drop</string>
```
**NOTICE:**  
Use `newline` character `\n` to manually add new lines.  
&nbsp;  
&nbsp;  
#### > "Dialog Address Type"  
( > Change Address Type dialog labels)  

To modify labels, change the following items in  
`res/values/strings.xml`
```xml
<string name="business_residential">Is this address Business or Residental?</string>
<string name="business">Business\nAddress</string>
<string name="residential">Residential\nAddress</string>
```
**NOTICE:**  
Use `newline` character `\n` to manually add new lines.  
&nbsp;  
&nbsp;  
#### > "Product image Preview" screen  
( > Change Product Preview screen labels)  

Labels' colors are the same color as the secondary button  
&nbsp;  
&nbsp;  
#### > Set url for Help in side menu  

```java
PIO.setHelpUrl(String helpUrl);
```
&nbsp;  
&nbsp;  
#### > Set "About" text  

To modify "About" text, change the following item in  
`res/values/strings.xml`
```xml
<string name="about_text">Our Mission is to foster creative individuality and bring on-demand printed products to people all over the world. We hope to surround people with their favorite memories and brands, to remind them of the better things in life, improving the world one creation at a time.\n\nWe have an unwavering commitment to quality and customer satisfaction. If you\'re not happy, we\'re not happy. That\'s why we go the extra mile to insure that we carry the highest quality products, printed by the best printers, at the best possible prices.\n\nWe have print facilities all over the world, so whether you\'re in the USA, India, or Laos, we can ship to you! Since inception, we\'ve shipped to over 100 countries.\n\nSupport@print.io for support and friends</string>
```
**NOTICE:**  
Use `newline` character `\n` to manually add new lines.  
&nbsp;  
&nbsp;  
#### > Set "How it Works" text  

To modify "How it Works" text, change the following item in  
`res/values/strings.xml`
```xml
<string name="how_it_works_text">1. Browse through our selection of products and choose the item or items you would like to purchase. We carry the highest quality products, printed by the best printers, at the best possible prices.\n\n2. Customize your item. Choose the size, shape, layout and product options you like best.\n\n3. Upload your images, or designs. Import from your phone, Instagram, Facebook, Flickr, Picasa, or Dropbox.\n\n4. Ship to any country in the world! Specify your location and choose shipping method. We\'ve shipped to over 100 countries and counting.\n\n5. Pay using PayPal or the credit card of your choice. Our custom credit card imaging system makes it easier than ever to pay! All of your credit card info is automatically entered with one simple photo.\n\n6. Enjoy! We place the utmost importance on quality and customer satisfaction. We know you\'ll love the products! Enjoy.</string>
```
**NOTICE:**  
Use `newline` character `\n` to manually add new lines.  
&nbsp;  
&nbsp;  
#### > Get shopping cart items count without starting the SDK  

To get the count of items in shopping cart, use the following method:
```java
PIO.getNumberOfItemsInShoppingCart(Context context);
```
&nbsp;  
&nbsp;
#### > Change photosources text and background colors  

To change photosources text and background colors, modify following items in  
`res/values/colors.xml`
```xml
<color name="photosources_background">#333333</color>
<color name="photosources_text">#FFFFFF</color>
```
&nbsp;  
&nbsp;  

