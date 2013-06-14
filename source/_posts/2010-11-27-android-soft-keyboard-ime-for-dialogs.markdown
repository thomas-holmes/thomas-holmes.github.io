---
layout: post
title: "Android Soft Keyboard For Dialogs"
date: 2010-11-27 00:00
comments: false
categories: [android, java]
---

It seems like such a simple thing, you would like to show the Soft Keyboard automatically for a `Dialog`. You can easily find a number of ways to do this for an `Activity`. You can also find one often repeated, but inadequate, method being proliferated for a `Dialog`

{% codeblock lang:java %}
InputMethodManager imm =
(InputMethodManager) getSystemServer(INPUT_METHOD_SERVICE);
imm.toggleSoftInput(imm.SHOW_FORCED, imm.HIDE_NOT_ALWAYS);
{% endcodeblock %}

There are, however, several problems with this method. It does not…

- respect the user’s phone and presence of a physical keyboard
- close automatically when the dialog closes
- close automatically if the user were to leave the activity or application completely

There is however, a solution if you are targeting at least API Level 3 (Android 1.5). In your `onPrepareDialog()`, or wherever you are displaying your dialog do the following:

{% codeblock lang:java %}
dialog.getWindow()
   .setSoftInputMode(WindowManager.LayoutParams.SOFT_INPUT_STATE_VISIBLE);
{% endcodeblock %}
This will have the same result on a `Dialog` as setting `android:windowSoftInputMode="stateVisible"` for an activity in your `AndroidManifest.xml`
