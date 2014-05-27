#SDK Customization

#1. Changing icons, colors and fonts
Icons are located in /res/drawable-xhdpi.
Colors have been preset in /res/values/colors.xml.

In this document we will identify some of icons, color and fonts that are most likely to change.
For best results, please keep the icons the same size as they are currently.

###Header Bar

Header bar changeable icons:

 - **icon\_menu_default.png(35x34px)**
 - **icon\_cart_default.png(35x34px)**
 - **icon_cart_items_qty_background**
>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/cart.png)


 - **icon\_menu\_pressed.png(35x34px)**
>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/menu_pressed.png)

 - **icon\_menu\_pressed.png(35x34px)**
>![Alt icon_cart_pressed.png(35x34px)](http://bregava.rs/customization screenshots/cart_pressed.png)

Header background, text and separator line colors can be changed in /res/values/colors.xml:
 - `<color name="title_bar_background">#ffffff</color>`
 - `<color name="title_bar_text">#000000</color>`
 - `<color name="title_bar_separator">#d6d6d6</color>`
 - `<color name="cart_items_qty_text">#ffffff</color>`

\*\*Note that any color change for header background will be ignored if you set the color at sdk invoking


 - **customized header example:**

    >![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/customized_header.png)
