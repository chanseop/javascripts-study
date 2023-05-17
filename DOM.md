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
