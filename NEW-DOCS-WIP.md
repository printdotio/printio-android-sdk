
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

Default value is false (not hidden).
```java
PIO.setHideStatusBar(boolean hideStatusBar);
```
&nbsp;  
&nbsp;  
~~#### > Set three buttons title bar style~~

~~Show `Back`, `Menu` and `Cart` buttons in navigation bar for Featured Products screen.~~  
~~Default value is false.~~
```java
TO BE DONE
PIO.useThreeButtonsBarStyle(boolean useThreeButtonsBarStyle);
```
&nbsp;  
&nbsp;  
Side Menu
---------
#### > Change side menu icon  

Replace the following icons with your own icons of same names.  
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
TO BE DONE
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
TO BE DONE
<color name="side_menu_options_title">#FFFFFF</color>
```
&nbsp;  
To change the section title background color, modify the following item in  
**res/values/colors.xml**
```xml
<color name="side_menu_options">#239EDB</color>
```
&nbsp;  
These methods control if the user is allowed to change the preset country, currency and language.  
The default values are false.
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
TO BE DONE
<color name="side_menu_accounts_title">#FFFFFF</color>
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
TO BE DONE
<color name="side_menu_info_title">#FFFFFF</color>
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
TO BE DONE
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

Default value is false (side menu slides from left side).
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

Default value is false.
```java
PIO.setCountryOnFeaturedProducts(boolean setCountryOnFeaturedProducts);
```
&nbsp;  
&nbsp;  
#### > Hide category+search view on Featured Products screen  

Default value is false.
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
TO BE DONE
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
~~#### > Hide icon for Upload Instructions text in Photo Sources screen~~  

~~Default value is false.~~
```java
TO BE DONE
PIO.setHideIconForUploadInstructions(boolean hideIconForUploadInstructions);
```
&nbsp;  
&nbsp;  
