---
layout: post
title: jQuery .off().on()
---
<p>
I've realized I need to log my tecnical trouble shooting history. 
This the first one.
</p>

<p>
Language: jQuery<br />
Description: I tried to add click event handler on img with certain class name. but there are many images with same class name. I expected only one click event handling. but when I clicked one, event handling occured as many as of number of imgages.<br />
Solution: $('.selector').off('click').on('click', function(){});<br />
With above solution, click event occured only once.
</p>
