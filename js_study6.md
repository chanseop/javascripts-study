## Object

### 1. Literals and properties
 - object = {key:value}의 집합이다.
```js
const obj1={};    // 'object literal' syntax
const obj2=new Object();  //'object constructor' syntax

function print(person){
  console.log(person.name);
  console.log(person.age);
}

const seop={name: 'seop', age:26};
print(seop);

//add
seop.hasJob =true;
console.log(seop.hasJob);   //true

// delete
delete seop.hasJob;
console.log(seop.hasJob);  //undefined

```

### 2. Computed properties
 - key should be always string

```js
console.log(seop.name);
console.log(seop['name']);
seop['hasJob']=true;

function printValue(obj,key){
  console.log(obj.key)
}
printValue(seop,'name');  //undefined

function printValue(obj,key){
  console.log(obj[key])
}
printValue(seop,'name');  //seop
```
 -  동적으로 key를 받아와서 쓸때 위 코드와 같이 사용한다.


### 3. Property value shorthand
 - key와 value의 변수가 같을떄 생략 가능하다.
```js
const person1 = {name:'bob', age:2}

const person2 = makePerson('seop',20);

function makePerson(name,age){
  return{
    name,
    age,
  }
}
```

### 4. Constructor Function
```js
const person1 = {name:'bob', age:2}

const person2 = new Person('seop',20);

function Person(name,age){
  // this={};
  this.name =name;
  this.age=age;
  //return this;
}
```

### 5. in operator:property existence check
```js
console.log('name' in seop); // true
console.log('random' in seop); // false
console.log(seop.random); // undefined
```

### 6. for..in vs for..of
```js
// for (key in obj)
for (key in seop){
  console.log(key);     // 모든 키들이 출력
}

//for(for of iterable)
const array=[1,2,3,4,5];
// 원래대로 하면
for (let i =0; i<array.length; i++){
  console.log(array[i])
}

for (value of array){
  console.log(value);
}
```

### 7.Fun cloning
```js
const user ={name: 'seop', age:'20'};
const user2=user; //같은 reference
user2.name='coder'

const user4=Object.assign({},user);


// another example
const fruit1={color:'red'};
const fruit2={color:'blue', size:'big' n }
const mixed= Object.assign({},fruit1,fruit2); // {color:'red',size:'big'}
```






