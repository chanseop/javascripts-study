## appendChild & insertBefore
 - appendChild는 부모 노드의 마지막에 자식 노드를 추가하는 메서드
 - insertBefore는 부모의 특정 노드 앞에 노드를 삽입하는 메서드
 - 둘다 새로 생성한 노드 뿐만 아니라 기존의 노드의 위치도 옮길수 있다.
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script defer src="appendChild_insertBefore.js".js"></script>
    
    <title>Document</title>
</head>
<body>
    <div>
        <h1>리스트 시작</h1>
        <ol id="ol-id">
        <li id="first-li-id">1</li>
        <li>2</li>
        </ol>
    </div>

    
</body>
</html>
```

### appendChild 결과 및 코드
![image](https://github.com/chanseop/javascripts-study/assets/99310356/f0268b57-e37e-406c-9674-68ba49135a0c)

```js
const divElem=document.createElement("div");
const liElem=document.createElement("li");

liElem.className="li-class-name";
liElem.id="li-id";
liElem.innerHTML='<strong>삽입되는 요소</strong>';

const olElem=document.getElementById("ol-id");
const firstLiElem=document.getElementById("first-li-id");

olElem.appendChild(firstLiElem)
olElem.appendChild(liElem);
```


### insertBefore결과 및 코드
![image](https://github.com/chanseop/javascripts-study/assets/99310356/4180633a-e58b-477c-986a-fa7d623bcc44)

```js
const divElem=document.createElement("div");
const liElem=document.createElement("li");

liElem.className="li-class-name";
liElem.id="li-id";
liElem.innerHTML='<strong>삽입되는 요소</strong>';

const olElem=document.getElementById("ol-id");
const firstLiElem=document.getElementById("first-li-id");

olElem.insertBefore(liElem,firstLiElem);
```


## append,prepend,after,before
 - prepend: 요소 내부의 가장 앞으로 이동
 - append: 요소 내부의 마지막으로 이동, appendchild와 다르게 여러노드를 추가할수 있다.
 - before: 요소 앞으로 이동
 - after: 요소 뒤로 이동

## removeChild,remove
 - removeChild: DOM 트리 내에 노드를 제거할 때 사용합니다. 제거하고자 하는 노드가 존재할 경우 부모 노드에서 removeChild 메서드를 호출해 제거합니다.
 - remove: removeChild와 비슷하게 DOM 트리 내에서 노드를 제거하고 싶을경우 node.remove() 형태로 제거합니다.

```js
// removeChild
divElm.removeChild(divElm)
// remove
divElm.remove
```

## insertAdjacentHTML
 - XML 또는 HTML로 해석될 수 있는 문자열을 파싱한 뒤 적정한 노드를 생성해 특정 위치에 삽입
 - 방법:
   - beforebegin, afterbegin, beforeend, afternd
```JS
elem.insertAdjacentHTML('beforebegin', '<span>hello, world</span>')
```







