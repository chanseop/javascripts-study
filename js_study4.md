## funtion
 - fundamental building block in th program(기본적인 building block)
 - subprogram can be used multiple times(재사용 가능)
 - performs a task or calculates a values(한가지의 일 또는 어떤것을 계산할떄 쓴다.)
 - function is object in JS (함수는 자바스크립트에서는 object이다)

### function declaration(함수 선언)
```js
function printHello(){
  console.log('hello')
}
printHello();

function log(message){
  console.log(message)
}
log('hello');
log(1234);

//typescript
function log(message: string):number{
  console.log(message)
  return 0;
}

```

### parameters
- premitive parameters : passed by value (value 값 전달)
- object parameters: passed by reference (reference 주소값 전달)

```js
function changeName(obj){
  obj.name='coder';
}

const seop=={name:'seop'};
changeName(seop);
console.log(seop)   // {name:'coder'}

```

### default parameters 
```js
function showMessage(message, from='unknown'){
    console.log(`${message} by ${from}`)
}

showMessage('Hi!')
```

### rest parameters
```js
function printAll(...args){
    // 방법 1
    for (let i =0; i<args.length; i++){
        console.log(args[i]);
    }
    // 방법 2
    for (const arg of args){
        console.log(arg);
    }
    
    // 방법 3
    args.forEach((arg)=>console.log(arg));
}

printAll('hi','my','name','is','seop');
```

### local scope
 -  js안에서 스코프 안에서는 그 스코프 안에서만 볼수 있고 밖으로 갈수는 없다
 -  그렇지만 밖에 있는것을 안에서 볼수는 있다.
```js
let globalMessage = 'global'; //global variable
function printMessage(){
  let message='hello';
  console.log(message); //local variable
  console.log(globalMessage);
}
printMessage();
```

### early return, early exit

```js
//bad cording
function upgradeUser(user){
  if (user.point>10){
      //long upgrade logic....
  }
}

//good
function upgradeUser(user){
  if (user.point<=10){
      return;
  }
  // long upgrade logic...
}
```

## First-class function
 - functions are treated like any other variable(다른변수와 같이 사용된다.)
 - can be assigned as a value to variable(할당 가능)
 - can be passed as an argument to other functions.(다른 function에 parameter로 할당 가능)
 - can be returned by another function(return 도 function으로 가능)


### function expression
 - a function declaration can be called earlier than it is defined. (hoisted)(선언전에 호출가능)
 - a function expression is created when the execution reaches it. (요청이 도착하면 생성)

```js
const print = function(){ //
    console.log('print');
};
print();
const printAgain=print;
printAgain();
const sumAgain = sum;
console.log(sumAgain(1,3))

```

- 결과값

![image](https://user-images.githubusercontent.com/99310356/235817987-9b2a043e-0d85-49dd-8cfd-e2e0d8cd0ed6.png)


### Callback function using function expression
```js
function randomQuiz (answer, printYes, printNo){
  if(answer === 'love you'){
    printYes();
  }else{
    printNo();
  }
}

const printYes=function{
  console.log('yes');
};

const printNo=function{
  console.log('no')
}

```

### Arrow function
```js
const simplePrint = ()=> console.log('simplePrint!');
const add= (a,b)=>a+b;
```


### IIFE:Immediately Invoked Function Expression
 - 함수를 선언과 동시에 호출

```js
(function hello(){
  console.log('IIFE');
})();
```

- quiz
1. function calculate (command,a,b)
2. command:add,substract,divide,multiply,remainder

- answer
```js
function caculate(command,a,b){
    return command(a,b);
}

const add=(a,b)=>a+b;
const substract=(a,b)=>a-b;
const divide=(a,b)=>a/b;
const multiply =(a,b)=>a*b;
const remainder=(a,b)=>a%b;

//add
caculate(add,1,2);
caculate(substract,1,2);
caculate(divide,1,2);
caculate(multiply,1,2);
caculate(remainder,1,2);


``

