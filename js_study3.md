## review
 - immutable data types: premitive types, frozen objects (i.e. object.freeze())
     - example: const
         - 예외: cosnt arr=object => why? object 의 name만 저장하기 때문에 그안에 인자값을 변경 가능하다.
 - mutable data types: all objects by default are mutable in JS
     - example:let
## operators
### string concatenation
```js
console.log('my'+'cat');    // my cat
console.log('1'+2);    // 12
```

### numeric operators
```js
console.log(1+1);    // add
console.log(1-1);    // substract
console.log(1/1);    // divide
console.log(1*1);    // multiply
console.log(1%1);    // remainder
console.log(1**1);    // exponentiation

```

### increment and decrement operators
```js
let counter=2;
const preIncrement = ++counter;
//counter = counter+1;
//preIncrement=counter;

```

### assignment operators
 - 할당하는 operator 
```js
let x = 3;
let y = 6;
x+=y; //x=x+y;
x-= y;
x*=y;
x/=y;
```
### comparison operator
 - 비교하는 operator
```js
console.log(1<1);    // less than
console.log(1<=1);    // less than or equal
console.log(1>1);    // greater than
console.log(1>=1);    // greater than or equal
```

### logical operator
 - || (or)
 ```js
 const value1 = true;
 const value2 =4<2;
 
 console.log(`or: ${value1 || value2 || check()}`); //중요
 
 function check(){
  for (let i=0; i<10; i++){
    console.log('error')
  }
  return true;
 }
 
 ```
  - 여기서 중요한 부분이 위에 중요라고 주석처리한 곳에서 value1 이 true면 뒤에를 보지도 않고 true를 return 하는데 연산이 많은 check까지 갈필요가 없다.
  - 연산자를 계산하는 것을 제일 마지막에 배치하는게 좋다.
 
 
 
 
 - && (and)
```js
console.log(`and: ${value1 && value2 && check()}`);

// often used to compress long if-statement
// nullableObject && nullableObject.something (null check)
// if (nullableObject !=null){
        nullableObject.something;
}

function check(){
  for (let i=0; i<10; i++){
    console.log('error')
  }
  return true;
 }
```

 - ! (not)
```js
const value1=true
console.log(!value1); // false
```
### equality
```js
const stringFive ='5';
const numberFive=5;

// == loose equality, with type conversion
console.log(stringFive==numberFive); // true

// === strict equality, no type conversion(type까지 확인)
console.log(stringFive==numberFive); // false
```

 - object equality by reference
```js
const seop1={name:'seop'};
const seop2={name:'seop'};
const seop3=seop1
```
![image](https://user-images.githubusercontent.com/99310356/235811578-02265ae3-0b59-4f5b-85ca-af620ebbfdeb.png)

 - quiz

![image](https://user-images.githubusercontent.com/99310356/235811789-7b6b380c-425c-4fc1-9fc8-27becb41d288.png)

### conditional operators
 - if, else if, else

```js
const name = 'df';
if (name==='seop'){
  console.log('welcome,seop!');
}else if (name === 'coder'){
  console.log('you are amazing coder');
}else{
  console.log('unkwnon');
}
```

### ternary operator
 - condition ? value1 : value2;

```js
console.log(name==='seop'? 'yes':'no');
```

### switch statement
```js
const browser='IE';
switch (browser){
  case 'IE':
    console.log('go away');
    break;
  case 'Chrome':
  case 'Firefox':
    console.log('love you!');
    break;
  default:
    console.log('same all!');
    break;
}
```

### loop
 -  while
 -  조건검색이 먼저
```js
let i =3;
while (i>0){
  console.log(`while: ${i}`);
  i--;
}
```

 - do-while
 - 실행후 조건검색

```js
do{
  console.log(`do while: ${i}`);
  i--;
}while(i>0);
```

### for loop
 - for(begin ; condition; step)

```js
for (i=3; i>0; i--){
    console.log(`for:${i}`);
    
for (let i=3; i>0; i--){
    // inline variable declaration
    console.log(`inline variable for:${i}`);
}

// nested loops
for (let i=3; i>0; i--){
    for(let j=0; j<10; j++){
    // inline variable declaration
        console.log(`inline variable for:${i}+${j}`);
    }
}
```
- quiz
1. iterate from 0 to 10 and print only even numbers (use continue)
2. iterate from 0 to 10 and pring numbers until reaching 8 (use break)

- solution

```js
// Q1
for (let i=0; i<11; i++){
  if(i%2===0){
     console.log(`q1. ${i}`);  
  }else{
      continue;
  }  
}

//Q2
for (let i=0; i<11; i++){
  if(i===8){
     break;
  }else{
      console.log(`q1. ${i}`);  
  }  
}
```
