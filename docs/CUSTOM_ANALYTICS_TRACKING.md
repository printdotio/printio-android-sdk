Custom Analytics Tracking
===============

Since version 3.2.8 there is an option to set custom analytics tracking mechanism to the SDK. 

## AnalyticsTracker interface

The core of custom analytics tracking is `AnalyticsTracker` interface located in `print.io.analytics` package. It is an interface for object used to track user behaviour in the SDK. `AnalyticsTracker` interface exposes three methods `trackAction()`, `trackScreenView()` and `trackTransaction()` which are called whenever the user performs a trackable event. These events could be screen views, various button clicks, etc...

Classes implementing AnalyticsTracker interface must be serializable. More precisely, SDK will use Gson library for serialization and deserialization. 

To simplify usability of the SDK we have already implemented AnalyticsTracker for Google Analytics service. You can use this implementation as your tracking mechanism or if you want to develop your own AnalyticsTracker you can use this implementation as a reference. Mentioned implementation is `print.io.analytics.impl.GoogleAnalyticsTracker`.

## Events

Event is passed to appropriate `track` method every time the user performs a trackable action. All events implement `print.io.analytics.BaseEvent` interface.

#### Event types
We recognize three different types of events.

 - `print.io.analytics.ScreenViewEvent` - For tracking screen views
 - `print.io.analytics.ActionEvent` - For tracking various user actions
 - `print.io.analytics.TransactionEvent` - For tracking purchases 
