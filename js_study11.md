## async & await
 - clear style of using promise
 - 비동기 함수를 동기함수처럼 보이게 처리해주는 방법이다.

### async
```js
async function fetchUser(){
    //do network request in 10 sesc...
    return 'seo1p';
}

const user = fetchUser();
user.then(console.log);
console.log(user);
```

### await
```js
function delay(ms){
    return new Promise(resolve=>setTimeout(resolve,ms));
}

async function getApple(){
    await delay(2000);
    // throw 'error';
    return '사과';
}

async function getBanana(){
    await delay(1000);
    return '바나나';
}

// 이런식으로 하면 콜백지옥처럼 프로미스도 너무 많으면 안좋다.
// function pickFruits(){
//     return getApple().then(apple =>{
//         return getBanana().then(banana=>`${apple} + ${banana}`);
//     });
// }

async function pickFruits(){
    const applePromise =getApple();
    const bananaPromise=getBanana();
    const apple =await applePromise;
    const banana = await bananaPromise;
    return `${apple}+${banana}`
}

pickFruits().then(console.log);
```


### useful Promise APIs
 - 사용한 APIs
 - Promise.all:모든 값을 받아와서 배열형태로 받아와서 return 해준다.
 - Promise.race:함수값중에 가장 먼저 오는 함수를 return해준다.
```js
function pickAllFruits(){
    return Promise.all([getApple(),getBanana()])
    .then(fruits=>fruits.join('+'));
}

pickAllFruits().then(console.log);

function pickOnlyone(){
    return Promise.race([getApple(),getBanana()]);
}

pickOnlyone().then(console.log);
```
