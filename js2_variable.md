## Variable 
### let
```js
let name='seop';
console.log(name);
//seop
name=hello;
console.log(name)
//hello
```

### block scope
```js
{
let name='seop';
console.log(name);
//seop
name=hello;
console.log(name);
//hello
}
console.log(name);
// 아무것도 나오지 않는다.
```
 - block scope안에서 선언한거는 block밖에서 선언되지 않는다.
 - 밖에 선언한 경우 global scope이라고 하고 어디서든 사용 가능하다.
 
 
### var
```js
age=4;
var age
```
 -  var hoistin (move,declaration from bottom to top)
 -  어디서 선언 한것에 상관없이 항상 선언을 끌어올려주는 것을 말한다.
 -  var no block scope
 -  block scope 안에 선언했어도 다 보이게 한다.

### const
```js
const daysInWeek=7;
const maxNumber =5;
```
 - facor immutable data type always for a few reasons(변경되지 않음)
    - security(보안성):변수를 바꾸지 않게해서 보안성이 좋다
    - thread safety(쓰레드 보호): 어플리케이션이 실행되면 한가지 프로세스가 할당되고 그 프로세스 안에서는 다양한 쓰레드가 동시에 돌아가면서 어플리케이션이 돌아가게 도와주는 그 쓰레드들이 동시에 변경하여 문제가 되는것을 막아준다.                
    - reduce human mistakes :사람의 코드 실수를 잡아준다.

## Variable types
### number
```js
const count=17; // integer
const size=17.1; // decimal number

const infinity=1/0; //Infinity
cost negativeInfinity=-1/0 //-Infinity
const nAn ='not a number'/2; //NaN
```
 -  number 범위: -2**53 ~ 2**53
 -  새로운 타입 bigInt= 123457802456n; 뒤에 n을 붙히면 된다.

### string
```js
const char='c'; //string
const brendan = 'brendan';  //string
const greeting='hello'+brendan;  //string
```

### boolean
```js
// false: 0,null,undefinded,NaN
const canRead=true;
const text=3>1;  //false

```

### null
```js
let nothing =null;  //empty
```

### undefinde
```js
let x; // undefined
```
### object
```js
const seop={name:'seop',age:20};
seop.age=21;
```

### symbol
```js
const symbol1= Symbol('id');
const symbol2= Symbol('id');
console.log(symbol1===symbol2)  //false

const gsymbol1= Symbol.for('id');
const gsymbol2= Symbol.for('id');
console.log(gsymbol1===gsymbol2)  //true

console.log(`value: ${symbol1.description}`) // symbol 타입을 항상 description으로 string으로 변환
```

## Dynamic typing
- 선언할때 어떤타입인지 선언하지 않고 동잘할때 같이 선언되는 것을 말한다.

```js
let text='hello';
console.log(`value:${text}, type:${text}`); //hello, string
text=1;
console.log(`value:${text}, type:${text}`); //1, number
text='7'+5;
console.log(`value:${text}, type:${text}`); //75, string
text='8'/'2';
console.log(`value:${text}, type:${text}`); //75, number
```
## hosting



