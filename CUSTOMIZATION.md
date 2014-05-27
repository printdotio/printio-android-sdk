#SDK Customization

#1. Changing icons, colors and fonts
Icons are located in /res/drawable-xhdpi.
Colors have been preset in /res/values/colors.xml.

In this document we will identify some of icons, color and fonts that are most likely to change.
For best results, please keep the icons the same size as they are currently.

##Header Bar

Header bar changeable icons:

 - **icon\_menu_default.png(35x34px)**
 - **icon\_cart_default.png(35x34px)**
 - **icon\_cart\_items\_qty\_background.png(31x31px)**
 
    >![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/cart.png)


 - **icon\_menu\_pressed.png(35x34px)**
>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/menu_pressed.png)

 - **icon\_menu\_pressed.png(35x34px)**
>![Alt icon_cart_pressed.png(35x34px)](http://bregava.rs/customization screenshots/cart_pressed.png)


 - **icon\_arrow\_back\_2.png(19x33px)**
 - **icon\_question\_big.png(25x38px)**
>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/icon_help_back.png)



 - `<color name="title_bar_background">#ffffff</color>`
 - `<color name="title_bar_text">#000000</color>`
 - `<color name="title_bar_separator">#d6d6d6</color>`
 - `<color name="cart_items_qty_text">#ffffff</color>`

\*\*Note that any color change for header background will be ignored if you set the color at sdk invoking

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




