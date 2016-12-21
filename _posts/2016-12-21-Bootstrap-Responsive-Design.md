---
layout: post
title: Bootstrap Responsive Design breakpoint
---

Responsive 디자인은 요즘과 같이 디바이스가 다양할 때 중요성이 크다.
랩탑 화면에서는 구성이 괜찮았는데 iphone에서 본 화면구성은 너무 작고 겹쳐졌다.
bootstrap은 아래와 같이 네가지 타입으로 나눈다.
<ul>
<li>- Extra small devices: phones(<768px)</li>
<li>- Small devices: tablets (>=768px)</li>
<li>- Medium devices: Desktops (>= 992px)</li>
<li>- Large devices: Desktops (>= 1200px)</li>
</ul>
나는 구닥다리 노트북으로 작업을 하고 있는데 그냥 딱 봐서 md라고 생각했다. 그래서 코드에 상당한 .col-md 클래스를 포함했다.
그러나 alert("width: " + $(window).width());와 같은 방식으로 테스트 한 결과 1455라는 값이 나왔고 나는 ld에 속한다는 것을 알게됐다.
이게 미심적어 아래와 같은 방식으로 또 한번 테스트한 결과 lg라고 나왔다.
<pre>
<code>
<div class="visible-xs hidden-sm hidden-md hidden-lg">xs</div>
<div class="hidden-xs visible-sm hidden-md hidden-lg">sm</div>
<div class="hidden-xs hidden-sm visible-md hidden-lg">md</div>
<div class="hidden-xs hidden-sm hidden-md visible-lg">lg</div>
</code>
</pre>
여기서 또 하나. 컴퓨터 스크린 레졸루션을 확인해 보면 1600X900이다. 이건 bootstrap에서 구분짓는 기준이 아니라는 것을 알아야 한다. bootstrap은 화면의 width를 기준하지, 레졸루션을 기준하지 않는다.
