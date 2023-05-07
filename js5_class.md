## class
### 1.class declarations
```js
'use strict';
class Person{
  //constructor
  constructor(name,age){
    //fields
    this.name=name;
    this.age=age;
  }
  
  //method
  speak(){
    console.log(`${this.name}:hello!`);
  }
}

const seop=new Person('seop',20);

console.log(seop.name);
console.log(seop.age);
seop.speak();
```

### 2.Getter and setters
```js
class User{
  constructor (firstName,lastName, age){
    this.firstName= firstName;
    this.lastName= lastName;
    this.age = age;
  }
  
  get age(){
    return this._age;
  }
  set age(value){
    //if(value<0){
    //  throw Error('age can not be negative');
    //}
    this._age = value < 0 ? 0 : value;
  }
}

const user1 = new User('Steve', 'Job',-1);
console.log(user1.age); //-1
```

### 3.Fields (public, private)
```js
class Experiment{
  publicField =2;
  #privateField=0;  // #을 써서 private하게 변수 선
}
const experiment= new Experiment();
console.log(experiment.publivField);  // 2
console.log(experiment.privateField);   // undefined
```

### 4.Static properties and methods
```js
class Article {
  static publisher = 'Dream Coding';
  constructor(articleNumber){
    this.articleNumber = articleNumber;
  }
  
  static printPublisher(){
    console.log(Article.publisher);
  }
} 

const article1 =  new Article(1);
const article2 = new Article(2);

console.log(article1.publisher);  //undefined
console.log(Article.publisher);   //Dream Coding
```
 - static은 object에서 할당되는것이 아니라 class에서 할당되기 때문에 위 코드와 같이 article1에서 호출되지 않는다.
 - 사용법: 오브젝로 들어오는 값에 상관없이 그냥 공통적으로 class에서 정의 되어있는 값을 가져올때 쓰기 좋다.


## 상속&다형성

![image](https://user-images.githubusercontent.com/99310356/235834061-cf20adab-f159-4e97-ac10-32fb80f1a54d.png)
 - 공통적으로 사용가능한 것을 정의해서 필요할때마다 사용

### Inheritance
```js
class Shape{
  constructor (width,height,color){
    this.width=width;
    this.height=height;
    this.color=color;
  }
  
  draw(){
    console.log(`drawing ${this.color} color of`);
  }
  
  getArea(){
    return this.width * this.height;
  }
}

class Rectangle extends Shape{}   //상속
class Triangle extends Shape{
  draw(){
    super.draw()  // 부모의 함수 호출
    console.log('red')
  }
  getArea(){
    return (this.width * this.height)/2;
  }
}
const rectangle = new Rectangle (20,20,'blue');
rectangle.draw();   // drawing blue color of
const triangle =  new Triangle(20,20,'red');
rectangle.getArea();  //400
triangle.getArea();   //200

```

### Class checking : instanceOf
```js
console.log(rectangle instanceof Rectangle);  //t
console.log(triangle instanceof Rectangle);   //f
console.log(triangle instanceof Triangle);  //t
console.log(triangle instanceof Shape);     //t
console.log(triangle instanceof Object);    //t

```



