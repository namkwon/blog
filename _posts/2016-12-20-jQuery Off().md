---
layout: post
title: jQuery .off().on() 한번만 이벤트 발생시키려면
---
개발을 하면서 알게되는 것들을 작은거에서 큰거까지 기록해야 겠다는 생각이 들었다. 신기술이 쏟아지는 이런 상황에서는 더더욱.
오늘은 jQuery에서 .off()와 .on() 이벤트에 대해서.

이미지들이 갤러리처럼 쭉 있고 모두 class 값이 같을 경우, $('.class').on('click', function(){}); 과 같이 하면 이벤트가 한번만 발생하는게 아니라 이미지 갯수만큼 발생해버린다.
한번 클릭하면 그걸로 한번 이벤트만 발생시키려면 $('.class').off('click').on('click', function(){});와 같이 on앞에 off를 하나 둬서 꺼버려야 된다.
jQuery문법이란 쉬우면서도 tricky하다.
