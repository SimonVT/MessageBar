MessageBar
==========

An Android Toast replacement, similar to the one seen in the GMail app.
Multiple messages can be posted in succession, and each message will be
shown for 5 seconds.


Usage
=====

There's two ways to use the MessageBar. It can either be attached directly
to an activity, or a View can be passed.

Attaching to an activity
------------------------

This approach requires adding the following attributes to the Activity's theme.

```xml
<item name="messageBarContainerStyle">@style/MessageBar.Container</item>
<item name="messageBarTextStyle">@style/MessageBar.Message</item>
<item name="messageBarButtonStyle">@style/MessageBar.Button</item>
```

Attaching the MessageBar is then done by passing the Activity to the
MessageBar constructor.

```java
mMessageBar = new MessageBar(this);
```

This will automatically add a MessageBar layout to the content view.

Attaching to a View
-------------------

This can be used e.g. when attaching to a Fragment, or if custom views
are to be used for showing the message.

When using this approach, child views with the following id's must be added
to the passed View.

 * `mbContainer`: The container that holds the message and the button views.
 * `mbMessage`: A TextView that displays the message.
 * `mbButton`: A TextView that displays the button text.

As an example, this is the default layout that's used when attaching to an Activity.

```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@id/mbContainer"
    style="?attr/messageBarContainerStyle">

    <TextView
        android:id="@id/mbMessage"
        style="?attr/messageBarTextStyle" />

    <TextView
        android:id="@id/mbButton"
        style="?attr/messageBarButtonStyle" />
</LinearLayout>
```

The MessageBar is then attached by passing a parent view to the constructor.

Showing a message
-----------------

A message is shown simple by calling `MessageBar#show(...)`. A few methods are
available here. It can either simply show a message or show a message and a
button. When a button is shown, a Parcelable has to be passed that's then returned
via `MessageBar$OnMessageClickListener` if the button is clicked.

Example:
```java
mMessageBar.show("This is a message");
```


Credits
=======

 * Roman Nurik for creating the [example][1] this library is based on.


License
=======

    Copyright 2012 Simon Vig Therkildsen

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.




 [1]: https://code.google.com/p/romannurik-code/source/browse/#git%2Fmisc%2Fundobar
