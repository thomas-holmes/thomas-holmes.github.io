---
layout: post
title: "Custom Android RadioButton"
date: 2010-11-24 00:00
comments: false
categories: android
---

I was browsing StackOverflow and came across a question about making custom `RadioButtons` and figured I could answer so I decided to take the plunge.

To implement a custom styled RadioButton you can follow the below steps or look at the complete example source [here](http://code.devminded.com/custom-radiobutton/src).

Create the drawable resources for your custom RadioButton. You should have at least 4 icons:

|Pressed |Checked
|------- |-------
|True    |True   
|True    |False  
|False   |True   
|False   |False  

Place your images in `res/drawable` or if if you have a version for each screen density place them in their corresponding `res/drawable-ldpi`, `res/drawable-mdpi`, and `res/drawable-hdpi` folders.

Then create a `selector` type XML file in res/drawable. Here is my `res/drawable/button_radio.xml`

{% codeblock lang:xml %}
<selector xmlns:android="http://schemas.android.com/apk/res/android">
  <item android:state_checked="true" android:state_pressed="false"
      android:drawable="@drawable/radio_on"/>
  <item android:state_checked="false" android:state_pressed="false"
      android:drawable="@drawable/radio_off"/>
  <item android:state_checked="true" android:state_pressed="true"
      android:drawable="@drawable/radio_on_pressed"/>
  <item android:state_checked="false" android:state_pressed="true"
      android:drawable="@drawable/radio_off_pressed"/>
</selector>
{% endcodeblock %}

Setup your RadioGroup like so:

{% codeblock lang:xml %}
<RadioGroup android:layout_width="fill_parent"
   android:layout_height="50dp"
   android:orientation="horizontal"
   android:checkedButton="@+id/first">
   <RadioButton android:id="@+id/first"
      android:width="50dp"
      android:height="50dp"
      android:button="@drawable/button_radio"/>
   <RadioButton android:id="@+id/second"
      android:width="50dp"
      android:height="50dp"
      android:button="@drawable/button_radio"/>
   <RadioButton android:id="@+id/third"
      android:width="50dp"
      android:height="50dp"
      android:button="@drawable/button_radio"/>
   <RadioButton android:id="@+id/fourth"
      android:width="50dp"
      android:height="50dp"
      android:button="@drawable/button_radio"/>
</RadioGroup>
{% endcodeblock %}

I have specified dimension of 50dp as the dimension of my drawables are 50px x 50px. Also notice I am setting `android:button` and not `android:background`.

{% img /images/customradio.png 'Custom RadioButton' %}

Hopefully this can serve as a nice starting point for anyone looking to create some new and interesting effects with simple `RadioButtons`.
