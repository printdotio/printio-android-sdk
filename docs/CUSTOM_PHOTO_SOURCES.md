Custom Photo Sources
===============

Since version 2.1.9a there is an option to add a custom photo source to the Print.IO SDK. 


## Introduction

When selecting images, you have an option to include up to six photo sources from the following list:

- Phone
- Facebook
- Instagram
- Picasa (Google Photos)
- Flickr
- Photobucket
- Dropbox
- Preselected 

Since version 2.1.9a you have an ability to add your own custom photo source to the list.

## Default generic implementation

There are two interfaces you should get familiar with: `PhotoSource` and`PhotoSourceNavigator` found in `print.io.photosource` package.  By implementing these two interfaces you can write you own custom photo source and use it in SDK just like any other photo source.

**`PhotoSource`** is an interface describing photo source by: 

 - describing appearance of photo source in SDK (name, icons, etc..)
 - providing authentication mechanism to your API
 - providing mechanism for opening connection for downloading photos
 - providing `PhotoSourceNavigator` implementation for this photo source
	
**`PhotoSourceNavigator`** is an interface for classes holding logic used on "Select Images" screen. `PhotoSourceNavigator` does everything from revealing preview of photo source,  responding to user inputs and notifying holder of `PhotoSourceNavigator` when user has selected/unselected image(s).

**`PhotoSourceNavigatorHolder`** is an interface implemented by object holding `PhotoSourceNavigator`. It's purpose is to provide `PhotoSourceNavigator` with necessary mechanism, common to any photo source, on "Select Images" screen.

In order to help you to create your own custom photo source quickly, we have created *default generic* implementation of photo sources found in package `print.io.photosource.defaultgenericimpl`. Term "*default generic*" implementation comes from the fact that this implementation can cover any photo source which is for *generic* part. And *default* part is tied to the fact that this implementation provides you with default photo source structure which is common to all photo sources provided by our SDK, as they are all derivatives of default generic implementation. E.g. if you would like to have search for images on "Select Images" screen it would be out of the scope of default implementation but it would be still feasible to implement by extending default generic implementation or by creating completely new photo source implementation.

What this default generic implementation will do for you is:

- provide you with structure for default implementation of photo source
- create default preview of your photo source based on media items set
- respond to user inputs and cover all navigation logic

## How to create a custom photo source using default generic implementation

Let's see an example of a custom photo source implementation and walk through the flow. 

### Creating `PhotoSource` class

First off, you will have to start by crating your `PhotoSource` interface implementation by extending `DefaultPhotoSource` class. Class `DefaultPhotoSource` has unimplemented methods for which you would need to provide implementation. Those methods are listed below.

#### List of unimplemented methods

#####Method getServiceId
```java
public int getServiceId()
```
This method should always return unique ID of this photo source.  In order to avoid overlapping by IDs used by photo sources defined in Print.IO SDK your photo source ID should not be `0 <= ID <= 200` as these values are reserved for Print.IO SDK photo sources.

#####Method getName
```java
public String getName(Context context) 
```
This method should return name of your photo source.

#####Method isAuthorized
```java
public boolean isAuthorized(Context context)
```
This method should return `true` if user is authorized to your photo source, or `false` otherwise. If your photo source does not require authorization this method should always return `true`. In this case you can leave implementation of  `login` and `logout` methods empty.

#####Method login
```java
public void login(Activity context, AuthorizationCompleteCallback authorizationCompleteCallback)
```
This method is called when user attempts to login to your photo source either from side menu or from "Select Images" screen in case if user is not currently authorized (method `isAuthorized` has returned `false`). In this method you need to implement authorization logic to your photo source and notify authorization callback with method outcome.

Let's assume that your photo source API only needs to validate combination of username and password. You can easily show login dialog and validate credentials like so:

```java
@Override
public void login(final Activity context, final AuthorizationCompleteCallback authorizationCompleteCallback) {
	showLoginDialog((FragmentActivity) context, new DialogPhotoSourceLoginCallback() {

		@Override
		public boolean attemptLogin(String username, String password) {
		    // Validate credentials using your API
			boolean result = "foo".equals(username) && "bar".equals(password);
			
			if (result) {
			   // Store authorization result to shared preferences so it could be 
			   // accessed in isAuthorized() method. Optionally you can also store 
			   // acccess token or any other authorization data  
				SharedPreferences.Editor editor = context.getSharedPreferences("PS_EXAMPLE", 0).edit();
				editor.putBoolean("LOGGED", true).commit();
			}
			return result;
		}

		@Override
		public void onLoginComplete(boolean success, String response) {
			if (authorizationCompleteCallback != null) {
				authorizationCompleteCallback.call(false, success, response);
			}
		}

		@Override
		public void onCancel() {
			if (authorizationCompleteCallback != null) {
				authorizationCompleteCallback.call(true, false, null);
			}
		}

	});
}
```

Hint: If you need advanced login mechanism like Instagram, Facebook etc.. has you can create an Activty which will implement authorization logic and which should be started from `login` method.

#####Method logout
```java
public void logout(Activity context);
```
This method is called when current user needs to be unauthorized from your photo source. Following example form `login` method, this method could look like:

```java
@Override
public void logout(Activity context) {
	SharedPreferences.Editor editor = context.getSharedPreferences("PS_EXAMPLE", 0).edit();
	editor.putBoolean("LOGGED", false).commit();
}
```

#####Method isVisibleInSideMenu
```java
public boolean isVisibleInSideMenu()
```
This method should return `true` if photo source should be visible in side menu.

#####Method getSideMenuIcon
```java
public Drawable getSideMenuIcon(Context context)
```
This method should return icon used in side menu.  

Photo sources implemented in Print.IO SDK return different icons based on users current authorization state.  When user is authorized to the photo source icon has white background, otherwise background is transparent. 

Implementation of this method could look like:
```java
@Override
public Drawable getSideMenuIcon(Context context) {
	int res = isAuthorized(context) ? R.drawable.icon_ps_sm_example_signed : R.drawable.icon_ps_sm_example_unsigned;
	return context.getResources().getDrawable(res);
}
```

#####Method getSelectImagesIcon
```java
public boolean getSelectImagesIcon()
```
This method should return icon used on "Select Images" screen.  

Unlike `getSideMenuIcon`  method, icons returned by this method always have white background.

#####Method createPhotoSourceNavigator
```java
public PhotoSourceNavigator<? extends PhotoSource> createPhotoSourceNavigator(PhotoSourceNavigatorHolder holder)
```

This method is factory method for creating `PhotoSourceNavigator` for this photo source. Implementation of this method could look like:

```java
@Override
public PhotoSourceNavigator<ExamplePhotoSource> createPhotoSourceNavigator(PhotoSourceNavigatorHolder holder) {
	return new ExamplePhotoSourceNavigator(this, holder);
}
```
Where `ExamplePhotoSource` is the class name of this photo source and `ExamplePhotoSourceNavigator` is name of the class extending `DefaultPhotoSourceNavigator` which is going to be covered in "Creating `PhotoSourceNavigator`" section.

#### List of methods with default implementation
All unimplemented methods of `PhotoSource` interface have been covered. However, there is method of `PhotoSource` interface which has default implementation. That method is listed below.

#####Method openConnectionForImageDownload
```java
public HttpURLConnection openConnectionForImageDownload(Context context, String url) throws IOException;
```
This method should open connection for downloading image resource referred by `url` parameter. 

Note: You can override this method if you need to provide special attributes to HTTP request properties or to request parameters. 


### Creating `PhotoSourceNavigator` class

Final part of your photo source is implementation of `PhotoSourceNavigator` interface.  Luckily is trivial to do when you are using default generic implementation.

To create photo source navigator you need to extend `DefaultPhotoSourceNavigator` and do two things:

- create constructor which should call constructor of super class
- provide implementation for `onLoadMedia` method

#### Method `onLoadMedia`
```java
protected abstract LoadMediaResult onLoadMedia(Folder folder, int page, int itemsPerPage);
```
Method `onLoadMedia` is called when media items for this navigator needs to be loaded. This method returns `LoadMediaResult` describing method call outcome. Essentially this method should return media item hierarchy representing your photo source.

Parameters:

- **folder**: The `Folder` object for who media needs to be loaded. Or `null` if navigator should load media for root preview.
- **page**: The page of media items to load. Starts at `0`. If your photo source does not support paging you can ignore this.
- **itemsPerPage**: Default number of media items to load per page. If your photo source does not support paging you can ignore this.

`LoadMediaResult` is interface of `onLoadMedia` method call result. This interface has three methods describing the result:

- `getItems` which returns list of loaded media items
- `hasMoreMedia` which returns `true` if there are more media pages to be loaded. If your photo source does not support paging (e.g. all media items are loaded at once) this method can be ignored.
- `getMessage` which returns information message to be shown to the user. Message will not be shown if message is blank or `null`.

Classs  `DefaultLoadMediaResult` has default implementation of `LoadMediaResult` interface methods which just returns data passed via class constructor.


#### Media items
Media items is term used to describe all items that could be presented by `DefaultPhotoSourceNavigator` on "Select Images" screen. All media items are found in `print.io.photosource.defaultgenericimpl.items`  package  and they all extend `Item` class. Media items can have fallowing types:

- **Photo** is base class for all items representing photos.
- **Folder** is base class for all items representing folders (folder holds collection of media items).
	- **Album** is base class for all items representing albums (album is folder which holds collection of photo items).
- **BackItem** is base class for item representing back navigation button inside Folder. Back item is automatically added by `DefaultPhotoSourceNavigator`.

## Notes

Print.IO SDK has mechanism for caching downloaded images, so you will not need to worry about that.

## Custom photo source example
Inside Print.IO demo application there is [simple example](https://github.com/printdotio/printio-android-example/tree/master/PIOSDKPOConcept/src/com/piosdkexample/photosource/vlado) of custom photo source implementation.
