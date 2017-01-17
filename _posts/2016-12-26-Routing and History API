JQuery ajax를 이용하면 페이지의 리로딩 없이 페이지 안의 해당 내용만 바뀌게 된다. 다시 말하면 ajax를 이용한 SPA 개발에서는 URL 주소는 딸랑 하나일 수 있다는 이야기다.
이럴때 browser의 back버튼을 사용자가 누르면 우리의 페이지 그 이전으로 되돌아가게 되는 (사용자 입장에서는) 황당한 일이 발생할 수 있다. broswer의 history에 ajax를 이요하여 보여진 화면에 대한 정보는 담겨져 있지 않기 때문이다.

이럴때 history api를 이용하여 navigation을 조작할 수 있다. 이것은 html5에 새로 나온 것인데 아무래도 최근의 Web Application이 ajax를 이용한 다이나믹 페이지를 사용하다 보니 나오게 된듯하다.
history.pushState()로 history안에 강제로 임의의 주소, 상태를 집어 넣을 수 있다.
여기서 내가 저지를 실수는 history에 state를 push 해놓기만 하면 다 끝나는 걸로 예상했다는 점이다. state에 정보를 넣어 두었으니 사용자가 back 버튼을 누르면 거기로 갈 거라 생각했지만 오산.
사용자의 back 버튼 클릭은 popstate event를 트리거 하고 나는 여기에 이밴트 핸들러를 달아서 컨트롤을 따로 잡아주어야 한다.

MDN(Mozilla Developer Network)에서 찾아보면 아래와 같이 말한다.
history.pushState() 또는 history.replaceState()는 popstate 이벤트를 발생시키지 않는 것에 유의합니다.popstate 이벤트는 브라우저의 백 버튼이나 (history.back() 호출) 등을 통해서만 발생된다. 
브라우저는 popstate 이벤트를 페이지 로딩시에 다르게 처리합니다. Chrome(v34 이전버전) 와 Safari는 popstate 이벤트를 페이지 로딩시에 발생시킵니다. 하지만 Firefox 는 그렇지 않습니다.

그렇다면 페이지를 다시 로딩해야 된다는 말인데 그러면 ajax, SPA의 의미가 없지 않나?

예제:
window.addEventListener("popstate", function(e) {
    window.location.reload();
});

window.onpopstate = function(event) {
  console.log("location: " + document.location + ", state: " + JSON.stringify(event.state));
};

이건 뭐 완전 머리 아프고 잘 동작도 안하고 꼼수를 써야 될 거 같은 느낌이 들고...
이래서 프레임워크를 쓰면 이런것들을 편하게 처리해 주나 하는 생각도 들게 된다. 라우팅이란 이름으로.

프레임워크를 쓰지않고 라우팅을 하는 방법을 찾다보니 크게 2가지로 나누어진다. 찾아보니 고급진 방식으로 Client-Side Routing이라 명명되고 있더만.
- hash tag를 이용한 라우팅. 이것은 URL에 #를 넣어 꼼수를 부리는 방식이다. 내 스타일이 아니니 pass.
- history API를 이용한 방법
그런데 history를 지원하지 않는 브라우져까지 신경쓴다면 두가지 케이스 다 들어가야 한다는게 함정. ㅠㅠ.

이런 내비게이션 라우팅까지 개발자가 신경써서 개발해야 된다면 코드라인이 엄청 길어지게 될거 같다. 이래서 프레임워크를 쓰는구나 생각됨.
프레임워크를 쓰지 않는 상황에서는 routing 라이브러리를 찾아보기로 했다. back 버튼 하나에 어디까지 들어가야 하는걸까..ㅠㅠ
