Fetch API
비동기 호출 구현을 위해 기존에 콜백을 사용했다면 ES6에 나온 Promise 스펙의 구현으로 자바스크립트의 네이티브 API인 Fetch가 있다. 
현재 React로 개인 프로젝트를 하는 와중에 Ajax 콜을 하는데 이것만을 위해서 jQuery 라이브러리를 가져올 필요없이 가벼운 Fetch를 써보기로 했다.

기본 형식은 아래와 같다.
fetch(url)
.then(response){ //1번
	return response.json();
}).then(json) { //2번
	return json;
}).catch() {}

콜백이 then으로 이어진다. 1번이 되면 2번 실행하는 형식.
그런데 이해해야 되는것중 1번에서 받은 fetch의 return 값인  response는 말 그대로 Response Object이다. 이것에 대해서는 인터넷 Spec을 찾아보면 자세힌 나와있다.
1번 실행 내용에서 response.json()으로 해서 리턴되는 것은 Promise Object이다. 그냥 보기엔 바로 JSON 오브젝트가 리턴될거 같은데 아니다. Promise형식으로 싸여있다.
그래서 다시한번 then으로 콜백을 불러서 거기서 json으로 리턴한다. 

이 fetch function을 utils에 두고 여러군데서 콜해서 쓰고 싶었다. 그래서 
export function fetchData(url) {
	fetch()...//위의 부분
}

이걸 부르는 방식에서 많이 헷갈린다. 비동기 방식은 계속 헷갈린다.
var result = fetchData(url);
틀렸다. 안된다. 이것은 웃기지만 엣날에 전형적인 방식 아닌가. ㅠㅠ
fetchData(url).then(do something);
요건 뭔가 비동기식 같고 될 거 같은데 작동이 안됬다. 값을 받아오질 못한다. 분명 fetch내에서 return 값에는 있는데 여기로 넘어오질 못한다.

return fetch(url)
.then()
.then()

방식으로 전체를 return해야 된다는거!! 이걸 알아내는데 3일이 걸렸다. ㅠㅠ

