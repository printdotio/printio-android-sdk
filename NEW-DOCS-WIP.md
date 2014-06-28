
**SDK Customization**
=====================
---
*Notice: Items that are implemented in iOS SDK but are missing from Android SDK are marked using ~~strikethrough~~*  

---
Navigation bar
--------------
#### > Change navigation bar color, separator color and title bar text color  

This can be done in xml by changing the following item in  
**res/values/colors.xml**
```xml
<color name="title_bar_background">#ffffff</color>
```
~~`<color name="title_bar_left_button_background">#ffffff</color>`~~  
~~`<color name="title_bar_right_button_background">#ffffff</color>`~~  

or programmatically, by using following method.
```java
PIO.setHeaderColor(int color); //color is a 6-digit (rgb) or 8-digit (argb) hex value
```
_Note that the value set programmatically will override the value set in xml!_  
&nbsp;  
To change separator and texts' colors, modify the following items in  
**res/values/colors.xml**
```xml
<color name="title_bar_separator">#d6d6d6</color>
<color name="title_bar_text">#000000</color>
<color name="cart_items_qty_text">#ffffff</color>
```
~~`titleButtonIcon:(NSString *)iPath;`~~  
&nbsp;  
**NOTICE:**  
Never modify xml item names.  
Modify values only.  
&nbsp;  
&nbsp;  
#### > Set icon for back button  

Replace the following icon with your own icon of the same name.  
Recommended dimensions are listed next to the icon name.
```
icon_arrow_back_2.png (19x33)
```
&nbsp;  
&nbsp;  
#### > Hide status bar  

Default value is `false` (not hidden).
```java
PIO.setHideStatusBar(boolean hideStatusBar);
```
&nbsp;  
&nbsp;  
~~#### > Set three buttons title bar style~~

~~Show `Back`, `Menu` and `Cart` buttons in navigation bar for Featured Products screen.~~  
~~Default value is `false`.~~
```java
//TO BE DONE
PIO.useThreeButtonsBarStyle(boolean useThreeButtonsBarStyle);
```
&nbsp;  
&nbsp;  
Side Menu
---------
#### > Change side menu icon  

Replace following icons with your own icons of same names.  
Recommended dimensions are listed next to the icon name.
```
icon_menu_default.png (39x29)
icon_menu_pressed.png (39x29)
```
&nbsp;  
&nbsp;  
#### > Change side menu background color  

To change side menu background color, modify the following item in  
**res/values/colors.xml**
```xml
<color name="side_menu_background">#1D1D1D</color>
```
&nbsp;  
&nbsp;  
#### > Change side menu text color  

To change side menu text color, modify the following item in  
**res/values/colors.xml**
```xml
<color name="side_menu_text">#ffffff</color>
```
&nbsp;  
&nbsp;  
#### > Choose which options will be displayed in side menu

~~**Buttons** section is at the top of the side menu.~~  
&nbsp;  
~~To select buttons for this section, pass a `List` of `SideMenuButton` to the following method~~
```java
//TO BE DONE
PIO.setSideMenuButtons(List<SideMenuButton> sideMenuButtons);

enum SideMenuButton {
	PIO_SM_EXIT_BUTTON,
    PIO_SM_SEARCH_BAR,
    PIO_SM_PRODUCTS,
    PIO_SM_FEATURED_PRODUCTS,
    PIO_SM_VIEW_CART,
    PIO_SM_SHARE_WITH_IMAGE,
    PIO_SM_EMAIL_SUPPORT;
};
```
&nbsp;  

##### **Options** section:  

To modify its title, change the following item in  
**res/values/strings.xml**  
and if your app supports multiple languages, change the appropriate items in  
**res/values-language/strings.xml**  
```xml
<string name="options">Options</string>
```
**NOTICE:**  
Never modify xml item names.  
Modify values only.  
&nbsp;  
~~To change the section title color, modify the following item in~~  
~~**res/values/colors.xml**~~
```xml
//TO BE DONE
<color name="side_menu_options_subtitle_text">#FFFFFF</color>
```
&nbsp;  
To change the section title background color, modify the following item in  
**res/values/colors.xml**
```xml
<color name="side_menu_options">#239EDB</color>
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
**res/values/strings.xml**  
and if your app supports multiple languages, change the appropriate items in  
**res/values-language/strings.xml**  
```xml
<string name="accounts">Accounts</string>
```
&nbsp;  
~~To change the section title color, modify the following item in~~  
~~**res/values/colors.xml**~~
```xml
//TO BE DONE
<color name="side_menu_accounts_subtitle_text">#FFFFFF</color>
```
&nbsp;  
To change the section title background color, modify the following item in  
**res/values/colors.xml**
```xml
<color name="side_menu_accounts">#1CBA9B</color>
```
&nbsp;  
#### > To select Photo Sources that will be displayed here, refer to **Photo Sources** section of this document.
&nbsp;  
##### **Info** section:  
To modify its title, change the following item in  
**res/values/strings.xml**  
and if your app supports multiple languages, change the appropriate items in  
**res/values-language/strings.xml**  
```xml
<string name="info">Info</string>
```
&nbsp;  
~~To change the section title color, modify the following item in~~  
~~**res/values/colors.xml**~~
```xml
//TO BE DONE
<color name="side_menu_info_subtitle_text">#FFFFFF</color>
```
&nbsp;  
To change the section title background color, modify the following item in  
**res/values/colors.xml**
```xml
<color name="side_menu_info">#6369A6</color>
```
&nbsp;  
~~To select buttons for this section, pass a `List` of `SideMenuInfoButton` to the following method~~
```java
//TO BE DONE
PIO.setSideMenuInfoButtons(List<SideMenuInfoButton> sideMenuInfoButtons);

enum SideMenuButton {
    PIO_SM_PRICING_CHART,
    PIO_SM_SHARE_APP,
    PIO_SM_LIKE_US_FB,
    PIO_SM_RATE_APP,
    PIO_SM_ABOUT,
    PIO_SM_HOW_IT_WORKS,
    PIO_SM_PAST_ORDERS;
};
```
&nbsp;  
&nbsp;  
#### > Slide side menu from right side  

Default value is `false` (side menu slides from left side).
```java
PIO.setRightSideMenu(boolean rightSideMenu);
```
&nbsp;  
&nbsp;  
#### > Set share text

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
#### > Set country on Featured Products screen instead on First screen  

Default value is `false` (country selection screen is the first screen).
```java
PIO.setCountryOnFeaturedProducts(boolean setCountryOnFeaturedProducts);
```
&nbsp;  
&nbsp;  
#### > Hide category+search view on Featured Products screen  

Default value is `false`.
```java
PIO.setHideCategorySearchBar(boolean hideCategorySearchBar);
```
&nbsp;  
&nbsp;  
Photo Sources
--------------
#### > Set available photo sources  

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
#### > Pass in images URLs  

Set predefined list of images that will be available to the user.
```java
PIO.setImageUrls(String[] imageUrls);
```
&nbsp;  
&nbsp;  
#### > Disable photo sources  

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
#### > Set passed in image as thumbnail for templates with one photo  

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
#### > Show toolbar in Customize Product screen  

The toolbar contains the following buttons: `Photos`, `Edit Tools`, `Options` and `Layout`.  
Default value is `true`.
```java
PIO.setShowOptionsInCustomize(boolean showOptionsInCustomize);
```
**NOTICE:**  
Not all of those buttons' functions have been implemented yet.  
&nbsp;  
&nbsp;  
#### > Show a list of selected images in Customize Product screen  

Default value is `true`.
```java
PIO.setShowPhotosInCustomize(boolean showPhotosInCustomize);
```
&nbsp;  
&nbsp;  
#### > Auto-arrange photos in Customize Product screen  

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
#### > Change the `Add photos` icon in Customize Product screen  

Replace following icons with your own icons of same names.  
Recommended dimensions are listed next to the icon name.
```
icon_add_more_images_a (111x111) - default state
icon_add_more_images_b (111x111) - pressed state
```
&nbsp;  
&nbsp;  
#### > Change the `Help button` icon in Customize Product screen  

Replace following icons with your own icons of same names.  
Recommended dimensions are listed next to the icon name.
```
icon_help_circle_grey (50x50px) - default state
icon_help_circle_grey_dark (50x50px) - pressed state
```
&nbsp;  
&nbsp;  
~~#### > ??? Customize Pop up balloon in Customize Product screen~~  

```java
//TO BE DONE
PIO.setUpPopUpBalloonCustomize(...);
```
&nbsp;  
&nbsp;  
~~#### > ??? Show custom help dialog on Image Editor screen~~  

```java
//TO BE DONE
PIO.setImageEditorHelpDialog(...);
```
&nbsp;  
&nbsp;  
Image Editor
------------
#### > Choose buttons to display in Image Editor  

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
**DIFFERENCES BETWEEN iOS and Android:**
iOS version of the SDK allows the badge to be hidden.  
On Android version, the badge is always visible and its background can be changed.
&nbsp;  
&nbsp;  
~~#### > Remove `+` sign from `Add More Products` button~~  

~~Default value is `false` (`+` sign is visible).~~
```java
//TO BE DONE
//Android version does not have + sign on this button
PIO.removePlusFromAddMoreProductsButton(boolean removePlusSign);
```
&nbsp;  
&nbsp;  
Payment Screen
--------------
~~#### > Remove logo from Payment ~~and Order Confirmation~~ screen~~  

~~Default value is `false` (logo is visible).~~
```java
//TO BE DONE
PIO.removeLogoFromPaymentScreen(boolean removeLogo);
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