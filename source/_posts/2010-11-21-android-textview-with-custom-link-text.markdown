---
layout: post
title: "Android TextView With Custom Link Text"
date: 2010-11-21 00:00
comments: false
categories: android
---

This is just going to be a quick how-to on creating a TextView with custom URL text.

To do this, you need to create a Spannable text object by using Html.fromHtml and then setting the MovementMethod of the TextView to a LinkMovementMethod. Here is an example using a dialog.

{% codeblock lang:java %}
dialog = new Dialog(this);dialog.setContentView(R.layout.about);
dialog.setTitle(R.string.about_score_it);
TextView website = (TextView)dialog.findViewById(R.id.about_website);

String realURL = "http://blog.devminded.com/projects/score-it";
String visibleURL = "http://blog.devminded.com";

//The following builds the spannable item and will cause the text to display as a link
website.setText(Html.fromHtml("<a href=\" + realURL + "\">" + visibleURL + "</a>"));

//The following makes it clickable
website.setMovementMethod(LinkMovementMethod.getInstance());
{% endcodeblock %}

Or with resources:

{% codeblock lang:java %}
dialog = new Dialog(this);
dialog.setContentView(R.layout.about);
dialog.setTitle(R.string.about_score_it);
TextView website = (TextView)dialog.findViewById(R.id.about_website);         

website.setText(Html.fromHtml("<a href=\"" + mRes.getString(R.string.about_score_it_website_url) + "\">" + mRes.getString(R.string.about_score_it_website_text) + "</a>"));

website.setMovementMethod(LinkMovementMethod.getInstance());
{% endcodeblock %}

To see the full context of this example please check out [ScoreIt.java](http://code.devminded.com/score-it/src/78a59d314ce2/src/com/devminded/scoreit/ScoreIt.java)
