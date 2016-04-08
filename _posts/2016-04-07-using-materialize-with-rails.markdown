---
layout: post
title:  "Using Materialize with Rails"
date:   2016-04-07 19:32:40 -0500
categories: rails, materializecss
---

For a few years now, I've been a pretty big fan of Bootstrap, using it in most of my Wordpress projects.

As soon as I began learning Ruby on Rails, I knew I wanted to try a few other new things, namely SASS and a new CSS framework. Choosing a new framework to use proved pretty daunting, as there are some good ones out there, but I finally landed on [Materialize](http://materializecss.com/), the framework built on [Google's Material Design](https://www.google.com/design/spec/material-design/introduction.html).

To include Materialize in my current Rails project, I followed the following steps:

Included [this gem](https://github.com/mkhairi/materialize-sass) in my `Gemfile`.

{% highlight ruby %}
gem 'materialize-sass'
{% endhighlight %}

Bundle
{% highlight ruby %}
bundle install
{% endhighlight %}

In `app/assets/stylesheets/application.scss`:
{% highlight sass %}
@import "materialize";
{% endhighlight %}

I went ahead and created a new stylesheet, `materialize.scss`, and added all the components. Example [here](https://github.com/mkhairi/materialize-sass/blob/master/app/assets/stylesheets/materialize.scss). This is also the file I used to change the default colors to the ones I'd be using. Example:
{% highlight sass %}
$primary-color: color("grey") !default
{% endhighlight %}

In `app/assets/javascripts/application.js`:
{% highlight javascript %}
//= require jquery
//= require materialize-sprockets
{% endhighlight %}


There are a few other things you can include that are all detailed in the gem documentation, but by this point, you should be ready to get started using Materialize.

A few things to note:

* One thing I was used to with Bootstrap, after including the JS file, I was able to use anything by simply adding the correct class, but Materialize does require you to initialize a few things. I learned this the hard way, after trying for way too long to get a select tag to show up. To get that working, I created a new JS file, `materialize.js`, and added this:
{% highlight javascript %}
$(document).ready(function() {
  $('select').material_select();
});
{% endhighlight %}

* Make sure that if you do add this bit of jQuery, to either remove the turbolinks gem from your app completely, or include the [turbolinks-jquery gem](https://github.com/kossnocorp/jquery.turbolinks). Again, I learned this the hard way.
