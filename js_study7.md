## Array
### 1. Declaration

```js
const arr1= new Array();
const arr2 = [1,2];

```

### 2. Index position
```js
const fruits=['apple','banana'];
console.log(fruits);
```

### 3.Looping over an array
```js
for (value of fruits){
  console.log(value);
}

//forEach
fruits.forEach((fruits,index)=>{
  console.log(fruits,index);
})
```

### 4. Addition, deletion, copy
```js
fruits,push('딸기','복숭아');
console.log('fruits');

//pop
fruits.pop();


//unshift:add and item to the benigging(앞에서 부터 넣기)
fruits.unshift('딸기','레몬')

//shift:앞에서부터 빼기
fruits.shift();

//splice
fruits.splice(start: number)
fruits.splice(1,1,'청사과','수박'); // 1번 인덱스를 지우고 청사과랑 수박을 넣는다.

//concat
const fruits2=['배','코코넛']
const newFruits=fruits.concat(fruits2)
```
 - note:shift,unshift 는 pop,push보다 훨씬 느리다.


### searching
```js
console.log(fruits);
console.log(fruits.indexOf('딸기')); //index return
console.log(fruits.includes('딸기')); //true
```







