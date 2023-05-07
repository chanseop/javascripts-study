## console출력
자바스크립트 공식문서 (developer.mozilla.org)
 - index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- main.js 불러오기 -->
    <script src="main.js"></script> 
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```
 - main.js
``` javascript
console.log("hello world!");
```

## script async 와 defer의 차이점
### head
![image](https://user-images.githubusercontent.com/99310356/235465103-25adfbd8-7655-4a8a-8111-90a0a3c31f72.png)

![image](https://user-images.githubusercontent.com/99310356/235463751-61f400da-792d-4222-95f3-d750472a6a2c.png)
 1. head안에 script가 포함되어 있을때 위에서부터 한줄한줄 읽어나간다.
 2. html을 parsing 하다가 script가 나오면 parsing하던것을 멈추고 fetching 한다.
 3. 다시 html파일을 parsing한다.
 - 단점: 처음에 parsing하다가 중간에 fetching 후 다시 parsing하기 때문에 main.js가 사이즈가 클경우 늦게 보일수가 있다.


### body
- ![image](https://user-images.githubusercontent.com/99310356/235465150-37c06e08-6336-40dc-9a65-9751ba25adcd.png)

![image](https://user-images.githubusercontent.com/99310356/235464798-0403bc80-c8d2-4751-98d5-242a7eacbec3.png)
 - body 제일 마지막에 js를 넣은 방법
 - 장점:html코드를 parsing을 다하고 마지막에 js를 불러온다.
 - 단점:사용자가 기본적인 html을 보는것을 빠르지만 만약 웹사이트가 js기능에 의존적이면 시간이 끌린다는 단점이 있다.

### head+async
![image](https://user-images.githubusercontent.com/99310356/235465536-dd6d54d9-6d94-4061-9935-01f1f12b8f39.png)
![image](https://user-images.githubusercontent.com/99310356/235465573-d4cd7434-3d64-4e02-8222-2bccfb87925b.png)
 1. async 는 boolean타입이라서 선언하는것만으로도 true 로 설정
 2. html을 parsing하다가 js파일이 있으면 위 사진처럼 병렬로 fetching다운로드 하라고 명령후 다시 parsing을 한다.
 3. fetching이 완료되면 html parsing을 멈추고 js를 실행한다.
 4. 실행후 나머지 parsing을 한다.
 - 장점: body끝에 하는것보다 더 빨리 다운로드 될수도 있다.
 - 단점: html에서 들어와서 작동하는 js경우 아직 들어오기 전이라 위험할수 있다.

### head+defer
![image](https://user-images.githubusercontent.com/99310356/235466757-0f74367b-582e-495c-b8f3-f81047f33b31.png)
![image](https://user-images.githubusercontent.com/99310356/235466794-73399950-2d61-42dc-a92f-5c33cba82de5.png)
 1. html parsing을 하다가 js를 보면 fetching 명령어만 내린다.
 2. html을 끝까지 parsing후 js를 실행한다.

### defer vs async
![image](https://user-images.githubusercontent.com/99310356/235467289-37e898ca-abe5-44ab-98e1-45f0dcfc0224.png)

![image](https://user-images.githubusercontent.com/99310356/235467325-186d4132-49bc-412a-b658-02b774a8f8ac.png)

### Tip!
```javascript
'use strict';
// error 
a=6;
// non error
let a;
```

- js는 flexible한 언어기 때문에 위험할수도 있다. 그래서 위에 'use strict'를 선언해주므로써 그러한 위험한 상황을 대처한다.

