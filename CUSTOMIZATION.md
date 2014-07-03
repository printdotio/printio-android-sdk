#SDK Customization

#Overview
Icons are located in `/res/drawable-xhdpi`.  
Colors are defined in `/res/values/colors.xml`.  
  
To customize the icons, replace them with your own.  
For best results, new icons should be the same sizes as the ones they are replacing.  
Dimensions are expressed in pixels.  

##Header

Header icons 1:  
![alt text](http://bregava.rs/customization screenshots/screen_1.png "Header sample 1")  
  
  
![alt text](http://bregava.rs/customization screenshots/icon_menu_default.png "icon_menu_default.png")
icon_menu_default.png (39x29)  

![alt text](http://bregava.rs/customization screenshots/icon_menu_pressed.png "icon_menu_pressed.png")
icon_menu_pressed.png (39x29)  

![alt text](http://bregava.rs/customization screenshots/icon_cart_default.png "icon_cart_default.png")
icon_cart_default.png (45x42)  

![alt text](http://bregava.rs/customization screenshots/icon_cart_pressed.png "icon_cart_pressed.png")
icon_cart_pressed.png (45x42)  

![alt text](http://bregava.rs/customization screenshots/icon_cart_items_qty_background.png "icon_cart_items_qty_background")
icon_cart_items_qty_background (31x31)  
  
  
Header icons 2:  
![alt text](http://bregava.rs/customization screenshots/screen_2.png "Header sample 2")  
  
  
![alt text](http://bregava.rs/customization screenshots/icon_arrow_back_2.png "icon_arrow_back_2.png")
icon_arrow_back_2.png (19x33)  

![alt text](http://bregava.rs/customization screenshots/icon_question_big.png "icon_question_big.png")
icon_question_big.png (25x38)  
  
  
  
Header color can be changed from xml or programatically:
 - `PIO.setHeaderColor(int);`\*\*
 
 - `<color name="title_bar_background">#ffffff</color>`\*\*

\*\*Note that any color change for header background will be ignored if you set the color at sdk invoking
  
  
 - `<color name="title_bar_text">#000000</color>`
 - `<color name="title_bar_separator">#d6d6d6</color>`
 - `<color name="cart_items_qty_text">#ffffff</color>`

 - **customized header example:**
 
	>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/customized_header1.png)

##Side Menu


 - **icon\_cart\_big.png(53x50px)**
 - **icon_cart_items_qty_side_menu.png(31x31px)**
>![Alt icon_cart.png(53x50px)](http://bregava.rs/customization screenshots/cart_big.png)


 - `<color name="side_menu_background">#1D1D1D</color>`
 - `<color name="side_menu_text">#ffffff</color>`
 - `<color name="side_menu_options">#239EDB</color>`
 - `<color name="side_menu_accounts">#1CBA9B</color>`
 - `<color name="side_menu_info">#6369A6</color>`
 - `<color name="side_menu_cart_items_qty_text">#ffffff</color>`


 - **side menu**
>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/side_menu.png)


##Customize Product screen

 - **icon\_add\_more\_images\_a(111x111px)** - default
 - **icon\_add\_more\_images\_b(111x111px)** - pressed state

>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/icon_add_more_images_a.png)
>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/icon_add_more_images_b.png)


 - **icon\_help\_circle\_grey(50x50px)** - default
 - **icon\_help\_circle\_grey\_dark(50x50px)** - pressed state

>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/icon_help_circle_grey.png)
>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/icon_help_circle_grey_dark.png)

 - **PIO.setShowPhotosInCustomize(boolean);**
 - **PIO.setShowOptionsInCustomize(boolean);**

>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/customize_product_without_options_and_add_photos1.png)
>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/customize_product_without_options1.png)
>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/customize_product1.png)

##Featured Products screen

Set country on Featured Products screen instead on First screen. Default value is NO.

```sh
PIO.setCountryOnFeaturedProducts(boolean);
```


Hide category + search view on Featured Products screen. Default value is NO;

```sh
PIO.setHideCategorySearchBar(boolean);
```

##Photo Sources

 - **Set a list of available photo sources.**
```sh
	ArrayList<PhotoSource> photoSourcesTest = new ArrayList<PIO.PhotoSource>();
	
	photoSourcesTest.add(PhotoSource.PHONE);
	photoSourcesTest.add(PhotoSource.PICASA);
	photoSourcesTest.add(PhotoSource.FACEBOOK);
	photoSourcesTest.add(PhotoSource.DROPBOX);
	photoSourcesTest.add(PhotoSource.FLICKR);
	photoSourcesTest.add(PhotoSource.INSTAGRAM);
	photoSourcesTest.add(PhotoSource.PHOTOBUCKET);
	
	PIO.setPhotoSources(photoSourcesTest);
```


 - **Pass in images URLs.**
```sh
PIO.setImagesUrls(String[]);
```

 - **Set passed in image as thumbnail for templates with one photo. Right now, only supports Canvas Wraps, Framed Prints, Metal Prints and Acrylic Prints.**
```sh
PIO.setPassedImageThumb(boolean); 
```

 - **Allow or stop user to use other image sources if some images are passed to SDK**
```sh
 PIO.setPhotosourcesDisabled(boolean);
```


##Fonts

Custom Light, Normal and Bold fonts should be placed in /assets before calling SDK setters for each style.

```sh
PIO.setFontPathInAssetsLight("HelveticaNeueLTStd-Lt.otf");
PIO.setFontPathInAssetsNormal("HelveticaNeueLTStd-Roman.otf");
PIO.setFontPathInAssetsBold("HelveticaNeueLTStd-Bd.otf");
```

##Image Editor

Set which buttons will be visible in Image Editor toolbar. By default, all buttons are visible. Parameters are respectively for rotate, add text and add effect buttons. Info button is always visible.
```sh
PIO.setUpCropScreen(boolean, boolean, boolean);
```


##Country, Currency and Language

Set country code.
```sh
PIO.setCountryCode(String);
```

##Steps

Jumps directly to product.
```sh
PIO.setIdAndSku(ProductIds.TABLET_CASES, "TabletCase-iPad3/4-Gloss");
```

Jumps directly to product with sku
```sh
PIO.setProductIdFromApp(PublicConstants.ProductIds.PHONE_CASES);
```

Show step by step while setting product layout, size, design, color...

```sh
PIO.setStepByStep(boolean);
```

Set auto arrange photos over the product. Default is dialog where user can choose.
```sh
PIO.setAutoArrange(boolean);
```

Set coaster type. 1 - one duplicated photo, 4 - four different photos. Default is dialog where user can choose.

```sh
PIO.setCoastersType(int);
```

##Other Customization

Enable or disable side menu.

```sh
PIO.setSideMenuEnabled(boolean);
```  

Set the partners/payee name for payment screens.
```sh
PIO.setPartnerName(String);
```

SDK in fullscreen. Note if your application is already in fullscreen mode than this will be ignored.

```sh
PIO.setHideStatusBar(boolean);
```

