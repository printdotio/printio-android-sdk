#SDK Customization

#1. Changing icons, colors and fonts
All icons are located in /res/drawable-xhdpi folder in print.io SDK project.
Colors are preset in /res/values/colors.xml file inf print.io SDK project.

In this document we will identify some of icons, color and fonts that are most likely to change.
For best results, please keep the icons the same size as they are currently.

###Header Bar

Header bar changeable icons:

 - **icon\_menu.png(35x34px)**
 - **icon\_cart.png(35x34px)**
>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/cart.png)


 - **icon\_menu\_pressed.png(35x34px)**
>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/menu_pressed.png)

Header background, text and separator line colors can be changed in /res/values/colors.xml:
 - `<color name="title_bar">#42BE9C</color>`
 - `<color name="title_bar_text">#000000</color>`
 - `<color name="title_bar_separator">#d6d6d6</color>`

\*\*Note that any color change for header background will be ignored if you set the color at sdk invoking


 - **Customized header example:**

>![Alt icon_cart.png(35x34px)](http://bregava.rs/customization screenshots/customized_header.png)
