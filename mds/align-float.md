## 정렬과 float

**정렬**

텍스트나 태그를 왼쪽, 가운데 또는 오른쪽에 배치하는 작업

<p class="codepen" data-height="300" data-theme-id="dark" data-default-tab="css,result" data-slug-hash="PoxoMRy" data-user="pshysd" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/pshysd/pen/PoxoMRy">
  Untitled</a> by pshysd (<a href="https://codepen.io/pshysd">@pshysd</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

부모 태그에 `text-align`을 사용하면 자식 태그들이 정렬된다.

가로 정렬은 참 쉬운데 문제는 세로 정렬임

보통 `vertical-align: middle`을 시도해보는데 뜻대로 되지 않는다. 가운데인데 가운데가 아니다

이유: `vertical-align`의 특징은 다른 태그를 기준으로 정렬이 됨.

-> 즉 옆에 다른 태그가 있어야 그 태그에 맞춰서 세로 정렬이 되는 것.

가장 쉬운 방법은

```css
@css display: flex;
align-items: center;
```

요건데 `IE`에서는 문제생김 어차피 죽은 브라우저

**해결책**

### 1. 헬퍼

<p class="codepen" data-height="300" data-theme-id="dark" data-default-tab="css,result" data-slug-hash="vYQEBeM" data-user="pshysd" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/pshysd/pen/vYQEBeM">
  Untitled</a> by pshysd (<a href="https://codepen.io/pshysd">@pshysd</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

width가 0이고 높이가 100%인 보이지 않는 헬퍼 태그를 하나 만들어주면 헬퍼를 기준으로 옆의 요소들이 정렬된다

<br>

**문제점**

child 태그들에 `margin: 0, padding: 0`을 줬음에도 간격이 발생한다!

-> `display: inline-block`의 문제점이기도 함

### 2. 테이블 효과

`display: table`과 `display: table-cell`을 이용하는 것

<p class="codepen" data-height="300" data-theme-id="dark" data-default-tab="css,result" data-slug-hash="LYXEPOg" data-user="pshysd" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/pshysd/pen/LYXEPOg">
  Untitled</a> by pshysd (<a href="https://codepen.io/pshysd">@pshysd</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

이렇게 하면 div가 테이블처럼 동작하여 가운데 정렬을 쉽게 할 수 있음

**문제점**

`table-cell`들의 `width`와 `height`를 조절하기 어려워진다.

### 3. transform

일단 `position: relative; top: 50%`로 위에서 50% 정도 내린다.

근데 끝이 아님 child 태그 높이의 반만큼 더 아래로 내려가있음

여기에 `transform: translateY(-50%);`해서 child 태그 높이의 반만큼 다시 올려줘야 함

<p class="codepen" data-height="300" data-theme-id="dark" data-default-tab="css,result" data-slug-hash="XWyJrVV" data-user="pshysd" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/pshysd/pen/XWyJrVV">
  Untitled</a> by pshysd (<a href="https://codepen.io/pshysd">@pshysd</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

**문제점**

여기서도 `display:inline-block`의 간격 문제가 똑같이 발생함

### 4. float

`float` 속성을 줄 경우 `width`가 100%가 되지 않는다.

위에서 아래로, 왼쪽에서 오른쪽으로 태그들이 순서대로 배치되어 있다가 그 중 한 태그가 공중에 붕 뜨게되면 다른 태그들은 그 자리를 메우려고 할 것

<p class="codepen" data-height="300" data-theme-id="dark" data-default-tab="css,result" data-slug-hash="wvQBwyK" data-user="pshysd" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/pshysd/pen/wvQBwyK">
  Untitled</a> by pshysd (<a href="https://codepen.io/pshysd">@pshysd</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

원래라면 `normal` 태그는 `block`이므로 한 줄을 통째로 차지해야 하지만 `float` 때문에 위로 올라왔다. 이 특성을 사용해서 문단에 이미지를 왼쪽에 넣는다든가 할 수 있음

만약 `normal` 태그처럼 올라가는 것을 방지하려면 `clear: left` 또는 `clear: right`를 먹여줘야 함

`clear:both`도 가능

**문제점**

부모 태그가 `float` 속성의 자식 태그를 인식하지 못한다.

-> `height`가 0이 되어버리는 문제 발생

<p class="codepen" data-height="300" data-theme-id="dark" data-default-tab="css,result" data-slug-hash="yLQyBKX" data-user="pshysd" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/pshysd/pen/yLQyBKX">
  Untitled</a> by pshysd (<a href="https://codepen.io/pshysd">@pshysd</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

위 예시를 보면 `#parent`는 노란색이 되어야 함에도 자식인 `.float` 태그를 인식하지 못해 `height`가 0이 되어 배경색이 나타나지 않는다.

`float` 속성의 자식을 인식하게 하려면 `overflow: auto` 또는 `overflow: hidden`을 주어야 부모 태그가 정상적으로 자식 태그의 높이를 인식한다.

`display: inline-block`의 간격 문제를 해결할 때에도 `float: left`가 사용된다.

<p class="codepen" data-height="300" data-theme-id="dark" data-default-tab="css,result" data-slug-hash="NWEPKMr" data-user="pshysd" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <a href="https://codepen.io/pshysd/pen/NWEPKMr">
  Untitled</a> by pshysd (<a href="https://codepen.io/pshysd">@pshysd</a>)
  on <a href="https://codepen.io">CodePen</a></span>
</p>

`display: inline-block` 대신 `float:left`를 사용했더니 간격 문제가 해결되었다.
