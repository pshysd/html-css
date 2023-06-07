## position

대망의 포지션과 디스플래이 나를 아주 힘들게 해

**static**

모든 태그들의 디폴트 값

차례대로 왼쪽에서 오른쪽, 위에서 아래로 쌓인다.

**relative**

태그의 위치를 살짝 변경하고 싶어질 때 `position:relative`를 사용해준다. top, right, bottom, left로 위치 조절이 가능해진다.

이동하는 기준은 static이던 시절이 기준이다

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="OJaJojB" data-user="pshysd" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/pshysd/pen/OJaJojB">
  Untitled</a> by pshysd (<a href="https://codepen.io/pshysd">@pshysd</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

안나오네;

참고로 값을 줄 때 예를 들어 top에 10px만큼 준다면 static의 위치를 기준으로 10px 내려온다. left일 경우엔 왼쪽으로 10px 밀림.

올리고 싶을 경우엔 음수로 주면 됨

`z-index`는 요소들이 겹칠 경우에 누가 앞으로 올 지 정해주는 것

**absolute**

`relative`가 static인 상태를 기준으로 움직인다면 `absolute`는 `position:static`을 갖고 있지 않은 부모를 기준으로 움직이게 된다.

만약 없으면 body가 기준이 됨

**fixed**

항상 페이지의 특정 위치에 고정시켜버리는 속성

* 참고) absolute와 fixed는 블록 속성의 요소들이 너비(width)를 100% 차지하지 않게 된다.