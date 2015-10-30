Specific Page Methods
===
- [**A. Products Screen**](SPECIFIC_PAGE_METHODS.md#a-products-screen)
- [**B. Product Details screen**](SPECIFIC_PAGE_METHODS.md#product-details-screen)
- [**C. Choose Options screen**](SPECIFIC_PAGE_METHODS.md#choose-options-screen)
- [**D. Select Photos screen**](SPECIFIC_PAGE_METHODS.md#select-photos-screen)
- [**E. Customization screen**](SPECIFIC_PAGE_METHODS.md#customization-screen)
- [**F. Image Editor screen**](SPECIFIC_PAGE_METHODS.md#image-editor-screen)
- [**G. Shopping Cart screen**](SPECIFIC_PAGE_METHODS.md#shopping-cart-screen)
- [**H. Select Address screen**](SPECIFIC_PAGE_METHODS.md#select-address-screen)
- [**I. Payment screen**](SPECIFIC_PAGE_METHODS.md#payment-screen)
- [**J. Order Completed screen**](SPECIFIC_PAGE_METHODS.md#order-completed-screen)
- [**K. Choose Country screen**](SPECIFIC_PAGE_METHODS.md#choose-country-screen)
- [**L. About screen**](SPECIFIC_PAGE_METHODS.md#about-screen)
- [**M. How It Works screen**](SPECIFIC_PAGE_METHODS.md#how-it-works-screen)
- [**N. Side Menu**](SPECIFIC_PAGE_METHODS.md#side-menu)

---

- [**Global Methods**](SPECIFIC_PAGE_METHODS.md#global-methods)

---

## A. Products screen

![enter image description here][1]
---
![enter image description here][2]
---
![enter image description here][23]

#### A1. Set list of available products in the SDK. 

- [**PIOConfig.setAvailableProducts()**](SDK_REFERENCE.md#-set-list-of-available-products-in-the-sdk)

#### A2. Hide category/search view on Featured Products screen. Default value is NO.

- [**PIOConfig.setHideCategorySearchBar()**](SDK_REFERENCE.md#-hide-categorysearch-view-on-featured-products-screen-default-value-is-no)

#### A3. Shows featured products by default. If disabled all products screen is shown. Default value is YES.

- [**PIOConfig.setShowFeaturedProductsByDefault()**](SDK_REFERENCE.md#-shows-featured-products-by-default-if-disabled-all-products-screen-is-shown-default-value-is-yes)

#### A4. Hide Coming Soon products. Default value is false.

- [**PIOConfig.setHideComingSoonProducts()**](SDK_REFERENCE.md#-shows-featured-products-by-default-if-disabled-all-products-screen-is-shown-default-value-is-yes)

---

## Product Details screen

![enter image description here][3]
---
![enter image description here][11]

#### B1. Hide prices in Product Details screen. Default value is false.

- [**PIOConfig.setPriceTitleHidden()**](SPECIFIC_PAGE_METHODS.md#a1-hide-prices-in-product-details-screen-default-value-is-false)

#### B2. Change Product Details screen labels icons and colors.

- [**Resource**](SDK_REFERENCE.md#-product-details-screen)

---

## Choose Options screen

---

## Select Photos screen

![enter image description here][4]
---
![enter image description here][5]

#### D1. Set available photo sources.

- [**PIOConfig.setPhotoSources()**](SDK_REFERENCE.md#-set-available-photo-sources-the-order-of-photo-sources-on-screen-will-be-the-same-like-order-they-are-placed-in-array)

#### D2. Set default photo source.

- [**PIOConfig.setDefaultPhotoSource()**](SDK_REFERENCE.md#-set-default-photo-source)

#### D3. Pass in images URLs or UIImage objects.

- [**PIOConfig.setImageUrls()**](SDK_REFERENCE.md#-pass-in-images-urls-or-uiimage-objects)

#### D4. Disable photo sources.

- [**PIOConfig.setPhotosourcesDisabled()**](SDK_REFERENCE.md#-if-user-pass-in-images-usinig-method-images-this-method-can-disable-photo-sources-forcing-user-to-use-only-passed-photos-this-method-overrides-method-availablephotosources)

#### D5. Change photosources text and background colors. 

- [**Resource**](SDK_REFERENCE.md#-change-photosources-text-and-background-colors)

---

## Customization screen 

![enter image description here][6]
---
![enter image description here][7]
---
![enter image description here][8]

#### E1. Show/hide tab bar in Customize Product screen. Default value is YES.

- [**PIOConfig.setShowOptionsInCustomize()**](SDK_REFERENCE.md#-showhide-tab-bar-in-customize-product-screen-default-value-is-yes)

#### E2. Hide list with images in customization screen.

- [**PIOConfig.setShowPhotosInCustomize()**](SDK_REFERENCE.md#-hide-list-with-images-in-customization-screen)

#### E3. Shows button for adding images when photo sources are disabled.

- [**PIOConfig.enablePhotoSourcesInCustomizeProduct()**](SDK_REFERENCE.md#-shows-button-for-adding-images-when-photo-sources-are-disabled)

#### E4. Set photo(s) arrangement in Customize Product screen. Default value is false.

- [**PIOConfig.setAutoArrange()**](SDK_REFERENCE.md#-set-photos-arrangement-in-customize-product-screen)

#### E5. Change image for "Add photos" button in Customize Product screen.

- [**Resource**](SDK_REFERENCE.md#-change-image-for-add-photos-button-in-customize-product-screen)

#### E6. Set Pop up balloon in Customize Product screen.

- [**Resource**](SDK_REFERENCE.md#-set-pop-up-balloon-in-customize-product-screen)

#### E7. Set Pop up balloon in Customize Product screen visibility timeout.

- [**PIOConfig.setDoubleTapBalloonVisibilityTime()**](SDK_REFERENCE.md#-set-pop-up-balloon-in-customize-product-screen-visibility-timeout)

#### E8. Dialog Arrange Photos.

- [**Resource**](SDK_REFERENCE.md#-dialog-arrange-photos)

---

## Image Editor screen

![enter image description here][9]

#### F1. Set which buttons will be visible in Image Editor toolbar. By default, all buttons are visible.

- [**PIOConfig.setUpCropScreen()**](SDK_REFERENCE.md#-set-which-buttons-will-be-visible-in-image-editor-toolbar-by-default-all-buttons-are-visible)

---

## Shopping Cart screen

![enter image description here][10]

#### G1. Show "Add more products" button on Shopping Cart screen.

- [**PIOConfig.setShowAddMoreProductsInShoppingCart()**](SDK_REFERENCE.md#-show-add-more-products-button-on-shopping-cart-screen)

#### G2. Hide edit button in shopping cart swipe menu.

- This button and the corresponding method were removed.

#### G3. Controls if widget should be closed when tap on Back button in "Shopping Cart" screen. Default value is false. 

- [**PIOConfig.closeWidgetFromShoppingCart()**](SDK_REFERENCE.md#-controls-if-widget-should-be-closed-when-tap-on-back-button-in-shopping-cart-screen)

#### G4. Remove all items from shopping cart.

- [**Sample code**](SDK_REFERENCE.md#-remove-all-items-from-shopping-cart)

---

## Select Address screen

![enter image description here][22]

#### H1. Clear all saved shipping addresses.

- [**PIO.clearShippingAddresses()**](SDK_REFERENCE.md#--clear-all-saved-shipping-addresses)

#### H2. Dialog Address Type.

- [**Resource**](SDK_REFERENCE.md#-dialog-address-type)

---

## Payment screen

![enter image description here][12]

#### I1. Show logo on Payment screen.

- [**PIOConfig.setVendorLogoOnScreen()**](SDK_REFERENCE.md#-show-vendor-logo-on-screens)

#### I2. Set Available Payment Options.

- [**PIOConfig.setPaymentOptions()**](SDK_REFERENCE.md#-set-available-payment-options)

---

## Order Completed screen

![enter image description here][13]

#### J1. Show logo on Order Completed screen.

- [**PIOConfig.setVendorLogoOnScreen()**](SDK_REFERENCE.md#-show-vendor-logo-on-screens)

---

## Choose Country screen

---

## About screen

![enter image description here][17]

#### L1. Set "About" text.

- [**Resource**](SDK_REFERENCE.md#-set-about-text)

---

## How It Works screen

![enter image description here][14]

#### M1. Set "How it Works" text.

- [**Resource**](SDK_REFERENCE.md#-set-how-it-works-text)

---

## Side Menu

![enter image description here][16]
---
![enter image description here][24]
---
![enter image description here][25]

#### N1. Customize Shopping Cart side menu button.

- [**Resource**](SDK_REFERENCE.md#-customize-shopping-cart-side-menu-button)

#### N2. Set url for Help in side menu.

- [**PIOConfig.setHelpUrl()**](SDK_REFERENCE.md#-set-url-for-help-in-side-menu)

#### N3. Enable or disable Side Menu.

- [**PIOConfig.setSideMenuEnabled()**](SDK_REFERENCE.md#-enable-or-disable-side-menu)

#### N4. Use Side Menu with options.

- [**Resource**](SDK_REFERENCE.md#-use-side-menu-with-options)

#### N5. Set which options to use in side menu.

- [**PIOConfig.setSideMenuButtons()**](SDK_REFERENCE.md#-set-which-options-to-use-in-side-menu)

#### N6. Set support email address.

- [**PIOConfig.setSupportEmail()**](SDK_REFERENCE.md#-set-support-email-address)

#### N7. Hide Accounts section, use the following method.

- [**PIOConfig.hidePhotoSourcesInSideMenu()**](SDK_REFERENCE.md#-to-hide-accounts-section-use-the-following-method)

#### N8. Hide SDK Version from Side Menu.

- [**PIOConfig.hideVersionInSideMenu()**](SDK_REFERENCE.md#hide-sdk-version-from-side-menu)

#### N9. Slide side menu from right. Default value is NO.

- [**PIOConfig.setRightSideMenu()**](SDK_REFERENCE.md#-slide-side-menu-from-right-default-value-is-no)

#### N10. This is option from Side Menu, in order to use it, Side Menu needs to be enabled first.

- [**PIOConfig.setShareText()**](SDK_REFERENCE.md#-this-is-option-from-side-menu-in-order-to-use-it-side-menu-needs-to-be-enabled-first)

---

Global Methods
===

![enter image description here][18]
---
![enter image description here][19]
---
![enter image description here][20]
---
![enter image description here][21]
---
![enter image description here][26]
---
![enter image description here][27]
---
![enter image description here][28]
---
![enter image description here][29]

#### A. Set custom icon for Shopping Cart.

- [**Resource**](SDK_REFERENCE.md#-set-custom-icon-for-shopping-cart)

#### B. Jumps directly to product.

- [**PIOConfig.setProductFromApp()**](SDK_REFERENCE.md#-jumps-directly-to-product)

#### C. Force a SKU for product.

- [**PIOConfig.setProductSkuFromApp()**](SDK_REFERENCE.md#force-a-sku-for-product)

#### D. Register device to receive push notifications.

- [**PIO.initializeParse()**](SDK_REFERENCE.md#-register-device-to-receive-push-notifications)

#### E. Adjust font sizes.

- [**Resource**](SDK_REFERENCE.md#-adjust-font-sizes)

#### F. Set custom fonts from main app bundle.

- [**PIOConfig.setFontPathInAssets()**](SDK_REFERENCE.md#-set-custom-fonts-from-main-app-bundle)

#### G. Change "Loading" GIF animation.

- [**Resource**](SDK_REFERENCE.md#-change-loading-gif-animation)

#### H. Change title of loading dialog.

- [**Resource**](SDK_REFERENCE.md#-change-title-of-loading-dialog)

#### I. Change icon for Help Button.

- [**Resource**](SDK_REFERENCE.md#-change-icon-for-help-button)

#### J. Change logo in SDK.

- [**PIOConfig.setApplicationIconId()**](SDK_REFERENCE.md#-change-logo-in-sdk)

#### K. Set payee name. 

- [**PIOConfig.setPartnerName()**](SDK_REFERENCE.md#-set-payee-name)

#### L. Change buttons' colors.

- [**Resource**](SDK_REFERENCE.md#-change-buttons-colors)

#### M. Set country code.

- [**PIOConfig.setCountryCode()**](SDK_REFERENCE.md#-set-country-code)

#### N. Set currency code.

- [**PIOConfig.setCurrencyCode()**](SDK_REFERENCE.md#-set-currency-code)

#### O. Get shopping cart items count without starting the SDK.

- [**PIO.getNumberOfItemsInShoppingCart()**](SDK_REFERENCE.md#-get-shopping-cart-items-count-without-starting-the-sdk)

#### P. Status Bar visibility.

- [**PIOConfig.setHideStatusBar()**](SDK_REFERENCE.md#-set-status-bar-visibility)

#### Q. Navigation Bar Settings.

- [**Resource**](SDK_REFERENCE.md#-navigation-bar-settings)

#### R. Set Icon For Back Button.

- [**Resource**](SDK_REFERENCE.md#-set-icon-for-back-button)

#### S. Set three buttons Back, Menu and Cart button in navigation bar for Products screen.

- [**PIOConfig.useThreeButtonsBarStyle()**](SDK_REFERENCE.md#-set-three-buttons-back-menu-and-cart-button-in-navigation-bar-for-products-screen)

#### T. Pass promo coupon code to SDK.

- [**PIOConfig.setPromoCode()**](SDK_REFERENCE.md#-pass-promo-coupon-code-to-sdk)

#### U. Show Country selection bar on screens.

- [**PIOConfig.showCountrySelectionOnScreen()**](SDK_REFERENCE.md#-show-country-selection-bar-on-screens)

#### V. Change background color of Select Country bar.

- [**Resource**](SDK_REFERENCE.md#-change-background-color-of-select-country-bar)

---


[1]: https://www.dropbox.com/s/vcalbc0y648gkkq/Products%20A01%2C%20A02.PNG?dl=1
[2]: https://www.dropbox.com/s/6aiztnqim70fv9x/Products%20A03.PNG?dl=1
[3]: https://www.dropbox.com/s/vkp4q8gnb3bx64h/Product%20Detail%20B01.png?dl=1
[4]: https://www.dropbox.com/s/sjk9p7v5j9g1t8x/Products%20D01%2C%20D02.PNG?dl=1
[5]: https://www.dropbox.com/s/lzw9e4lfo3ta7uq/Products%20D03%2C%20D04.PNG?dl=1
[6]: https://www.dropbox.com/s/4y7rporps06a30m/Products%20E01%2C%20E02.PNG?dl=1
[7]: https://www.dropbox.com/s/68huinimygb1080/Products%20E03%2C%20E05%2C%20E6%2C%20E7.PNG?dl=1
[8]: https://www.dropbox.com/s/5e8a4n3uk346arx/Products%20E04.PNG?dl=1
[9]: https://www.dropbox.com/s/6q73cgyc8l4hj0p/Products%20F01.PNG?dl=1
[10]: https://www.dropbox.com/s/pjftf0buasnapih/Shopping%20Cart%20screen%20G01%2C%20G02.png?dl=1
[11]: https://www.dropbox.com/s/889zb38cwjuephj/Product%20Detail%20B02.png?dl=1
[12]: https://www.dropbox.com/s/d41mjiupn4eq3rj/Payment%20I01%2C%20I02.PNG?dl=1
[13]: https://www.dropbox.com/s/7e7pu5ghva6qgbb/Order%20Completed%20E01.PNG?dl=1
[14]: https://www.dropbox.com/s/po9atvydg2ao778/How%20it%20works%20M1.png?dl=1
[16]: https://www.dropbox.com/s/rlsgq9v37h60zuh/Side%20Menu%20N1%2C%20N2.png?dl=1
[17]: https://www.dropbox.com/s/x4pqdf942v21plg/About%20L1.png?dl=1
[18]: https://www.dropbox.com/s/vo7ajbh245gaat3/Full%20App%20A%2C%20E%2C%20F.png?dl=1
[19]: https://www.dropbox.com/s/tj575e9htc0eq2z/Full%20App%20G%2C%20H.png?dl=1
[20]: https://www.dropbox.com/s/u7vjolc62vg32e9/Full%20App%20I.png?dl=1
[21]: https://www.dropbox.com/s/mcy1jnkosl0hmz5/Full%20App%20K.png?dl=1
[22]: https://www.dropbox.com/s/8v39jsnvpapjmnd/Address%20H2%20.png?dl=1
[23]: https://www.dropbox.com/s/ss7c9vw4xf56gfj/Products%20A04.PNG?dl=1
[24]: https://www.dropbox.com/s/m3k0d6mg9br6c8h/Side%20Menu%20N5%20N6%20.png?dl=1
[25]: https://www.dropbox.com/s/bfau0buhfrlyb95/Side%20Menu%20N7%20N8%20.png?dl=1
[26]: https://www.dropbox.com/s/exk01xj3jicz39k/Full%20App%20P.png?dl=1
[27]: https://www.dropbox.com/s/7a2dvd3rwq5sv6d/Full%20App%20R%2C%20Q.png?dl=1
[28]: https://www.dropbox.com/s/fb8jipmheb3dclj/Full%20App%20T.png?dl=1
[29]: https://www.dropbox.com/s/uoceczsvcn2ucqr/Full%20App%20U%2C%20V.png?dl=1
