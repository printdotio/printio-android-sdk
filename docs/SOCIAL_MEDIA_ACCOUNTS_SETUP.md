# How to Set Up Facebook and Instagram apps

## Facebook app

1. Go to https://developers.facebook.com/. Choose an existing app or click on "Add a New App" and select Android platform to get started.  
*If you are creating a new App, click "Skip Quick Start" in the top right corner.*  

| Facebook Test app |
| :--- |
| ![][1] |

1. Click "Add Platform" and select "Android"

1. Enter your application's Package Name and Class Name

1. Enter your [Key Hash(es)](https://developers.facebook.com/docs/android/getting-started#release-key-hash)

1. Set "Single Sign On" to `Yes` (leave "Deep Linking" disabled)

1. Click "Save Changes".  
*If your app has not yet been published to the Google Play Store, you will get a warning dialog. Ignore the warning and click "Use this package name"*

### Facebook Settings - Advanced:

- **Native or desktop app?** - YES
- **Is your App Secret embedded?** - YES
- **Deauthorize Callback URL** - Empty

**Security:**  
- **Server IP Whitelist, Update Settings IP Whitelist** - Empty
- **Require App Secret** - NO
- **Require 2-Factor Reauthorization** - NO
- **Allow API Access to App Settings** - YES

**Client OAuth Settings:**
- **Client OAuth Login** - YES
- **Web OAuth Login** - YES
- **Force Web OAuth Reauthentication** - NO
- **Embedded browser OAuth Login** - NO
- **Valid OAuth redirect URIs** - Empty
- **Login from Devices** - NO

### Add "User Photos" Permission to Facebook app
Here is the video on how to do it: https://dl.dropboxusercontent.com/u/19321066/user_photos.m4v

**To add "user_photos" permission, you will be asked to provide the following info:**  

**App Icon set**
**Long Description**
**Privacy Policy URL**

**Items**  
*Click "Add Notes" button*
- **How is your app using user_photos?** - Lets people print their Facebook photos or use them to personalize a product  
- **What platforms does your app use user_photos on?** - Mobile  
- **Detailed step-by-step instructions**

1. Open the app
1. Select "Canvas Wraps"
1. Tap "Create It"
1. Select Square
1. Select 6x6 inch
1. Select "Black Wrap"
1. Select "3 images" 
1. Select "Facebook" in the top right 
1. Log into Facebook
1. Select images from Facebook albums. 
1. Tap "Next" in the bottom right and proceed to the canvas layout 
This process can be replicated for any other product.

| App Notes |
| :--- |
| ![][2] |

**Facebook Login Integration**  
*Please provide step-by-step instructions in English that show how to access Facebook Login.*  
 1. Open the app
 1. Select "Canvas Wraps"
 1. Tap "Create It"
 1. Select Square
 1. Select 6x6 inch
 1. Select "Black Wrap"
 1. Select "3 images" 
 1. Select "Facebook" in the top right 
 1. Log into Facebook

---

## Instagram app

- Go to http://instagram.com/developer/. Register your application, and set up "Developer Signup".

### Screenshots

| Manage Clients |
| :--- |
| ![][3] |

### App Settings:

**Basic:**  
- **Disable implicit OAuth:** needs to be unchecked  

**Security:**  
- **Enforce signed header:** needs to be unchecked  
- **Redirect URI:** - http://x-oauthflow-instagram  

---
[1]: https://lh3.googleusercontent.com/KEoQaAhIXDI8DZ2EHI4ByXSiYIRISCk6JAwmdFVV3TY=w1160-h786-no
[2]: https://lh3.googleusercontent.com/EPeWauC2LzcS_qr4zhdqlG6oZtswU3Tx1DljBiSVUi4=w1896-h1284-no
[3]: https://lh3.googleusercontent.com/P-WxNN2skKIobsTnki3ffPlC6BXwKtlCcExiu3kO6Wg=w1528-h962-no 