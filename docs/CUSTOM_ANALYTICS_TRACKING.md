Custom Analytics Tracking
===============

Since version 3.2.8 there is an option to set custom analytics tracking mechanism to the SDK. 

## AnalyticsTracker interface

The core of custom analytics tracking is `AnalyticsTracker` interface located in `print.io.analytics` package. It is an interface for object used to track user behaviour in the SDK. `AnalyticsTracker` interface exposes single method `trackEvent()` which is called every time when user makes trackable event. These events could be screen views, various button clicks, etc...

Classes implementing AnalyticsTracker interface must be serializable. More precisely, SDK will use Gson library for serialization and deserialization. 

To simplify usability of the SDK we have already implemented AnalyticsTracker for Google Analytics service. You can use this implementation as your tracking mechanism or if you want to develop your own AnalyticsTracker you can use this implementation as a reference. Mentioned implementation is `print.io.analytics.impl.GoogleAnalyticsTracker`.

## Events

Event is used to describe nature of user behaviour in the SDK. Event is passed to `trackEvent()` method each time when user generates tracked behaviour. Events are described using `print.io.analytics.Event` class.

#### Event types
We recognize two different types of behaviours, those types are enumerated in `print.io.analytics.Event.EventType` enum.

 - `SCREEN` - Value used for events sent when the user opens specific screen.
 - `EVENT` - Value used for general events. 

Event type can be obtained using `getType()` method. 

#### Event names
All events have uniquely assigned event names. `SCREEN` event names are listed in `print.io.analytics.EventConstants.Screens` class and `EVENT` event names are listed in `print.io.analytics.EventConstants.Events` class. Event name can be obtained using `getName()` method.

#### Event properties

Events can have additional properties. Properties add more context to an event and are different for each event. Event properties can be obtained using `getProperties()`. Appropriate properties for each event name can be found in the event name Javadoc.