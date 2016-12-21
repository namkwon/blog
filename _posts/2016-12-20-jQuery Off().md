---
layout: post
title: jQuery .off().on()
---

I've realized I need to log my tecnical trouble shooting history. 
This the first one.

Language: jQuery
Description: I tried to add click event handler on img with certain class name. but there are many images with same class name. I expected only one click event handling. but when I clicked one, event handling occured as many as of number of imgages.
Solution: $('.selector').off('click').on('click', function(){});
With above solution, click event occured only once.
