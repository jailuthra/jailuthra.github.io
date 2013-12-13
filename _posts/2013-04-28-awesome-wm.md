---
layout: post
title: "Awesome WM"
summary: "Since a month I have not used any desktop environment like KDE or Gnome on my Arch desktop (called HaVoK). It has been a great experience so far.
What I have been using is called Awesome, a word that describes it very well!"
category: 
tags: 
- arch
- linux
---
{% include JB/setup %}
Since a month I have not used any desktop environment like KDE or Gnome on my Arch desktop (called [HaVoK](ssh://havok.jailuthra.in)). It has been a great experience so far.  
What I have been using is called [**Awesome**](http://awesome.naquadah.org), a word that describes it very well!

<a href="/img/awesome.png"><img src="/img/awesome.png" style="width:100%" /></a>

* Awesome is a [dynamic window manager](https://wiki.archlinux.org/index.php/Window_managers#Dynamic_window_managers). A window manager just manages your windows, providing _no_ application suites, fancy panels blah blah, like you get with KDE or Gnome. The only task it achieves is to arrange your windows by stacking and/or tiling. 
* It is **highly configurable**, uses lua scripts which are pretty straight forward. 
* User has the full control over it, _user-is-the-king_ philosophy is what drove me to awesome-wm and also arch linux.
* It seems a little hard to configure in the beginning, but as you explore more, you fall in love with its elegance.
* [Openbox](http://openbox.org/) is another popular window manager, but it is a stacking wm, tiling support can be added by applications like Pytyle, but Awesome has both stacking and tiling out of the box.

Adding widgets in awesome is achieved again by lua scripting. Steps to add many widgets like date, memory and cpu usage are in the [Awesome Wiki](http://awesome.naquadah.org/wiki/Vicious).  

I am also using some other widgets that I found through googling and are not in the awesome wiki, like core-temperature, and weather widgets. You can add these in your rc.lua -  

**thermal widget** 
{% highlight lua linenos %}
-- Thermal widget
  local thermalwidget  = wibox.widget.textbox()
  vicious.register(thermalwidget, vicious.widgets.thermal, "CPU: $1C | ", 20, { "coretemp.0", "core"} )
{% endhighlight %}

**weather widget**
{% highlight lua linenos %}
-- Weather widget
  local weatherwidget = wibox.widget.textbox()
  weather_t = awful.tooltip({ objects = { weatherwidget },})

  vicious.register(weatherwidget, vicious.widgets.weather,
    function (widget, args)
      weather_t:set_text("City: " .. args["{city}"] .."\nWind: " .. args["{windkmh}"] .. "km/h " .. args["{wind}"] .. "\nSky: " .. args["{sky}"] .. "\nHumidity: " .. args["{humid}"] .. "%")
      return " Weather: " .. args["{tempc}"] .. "C | "
      end, 300, "VIDP")
      --'300': check every 5 minutes.
      --'VIDP': the New Delhi ICAO code.   
{% endhighlight %}

These widgets then need to be added on the panel:
{% highlight lua %}
   right_layout:add(weatherwidget)
   right_layout:add(thermalwidget)
{% endhighlight %}

You might be interested in the entire rc.lua script that I use. [**Download it here**](/files/rc.lua).
