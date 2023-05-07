## Array operator 
### Join
 1. Adds all the elements of an array into a string, separated by the specified separator string.
      - 배열의 모든 요소를 지정된 구분자 문자열로 구분하여 문자열에 추가합니다.
      - 배열을 나누고 나면 그 형태는 문자열이다.
 2.  @param separator A string used to separate one element of the array from the next in the resulting string. If omitted, the array elements are separated with a comma.
     - 구분가 결과 문자열에서 배열의 한 요소를 다음 요소와 구분하는데 사용되는 문자열입니다. (생략하면 쉼표)
 - ``` join(separator?: string): string;```
 
```js
// Q1. make a string out of an array
{
    const fruits = ['apple', 'banana', 'orange'];
    const result=fruits.join()
    console.log(result);  
    // 결과값 : apple,banana,orange
  }
```


### spilt
 1. Split a string into substrings using the specified separator and return them as an array.
    - 지정된 구분 기호를 사용하여 문자열을 하위 문자열로 분할하고 배열로 반환합니다.
     
 2. splitter An object that can split a string.
    - 문자열을 분할할 수 있는 객체

 3. A value used to limit the number of elements returned in the array.
    - 배열에서 반환되는 요소의 수를 제한하는데 사용되는 값
    - 몇개까지 뽑아오는지 정해줄수 있음
    
 - ```  split(splitter: { [Symbol.split](string: string, limit?: number): string[]; }, limit?: number): string[];```

```js
// Q2. make an array out of a string
  {
    const fruits = '🍎, 🥝, 🍌, 🍒';
    const arr=fruits.split(',',2)
    console.log(arr);
  }
  //결과값: ['🍎', '🥝']
```

### revers
 1. Reverses the elements in an array in place.
    - 배열안에 요소들을 반전한다.

 2. This method mutates the array and returns a reference to the same array.
    - 이 메서드는 배열을 변경하고, 동일한 배열에 대한 참조를 반환합니다.
    - 그래서 주의할점이 reverse를 사용하면 사용하기전 배열도 revese된 형태로 된다.

```js
 // Q3. make this array look like this: [5, 4, 3, 2, 1]
  {
    const array = [1, 2, 3, 4, 5];
    const arr=array.reverse();
    console.log(array);
    console.log(arr);
  }
  //결과값
  // [ 5, 4, 3, 2, 1 ]
  // [ 5, 4, 3, 2, 1 ]
```

### slice
```slice(start?: number, end?: number): T[];```
 - start점과 end점을 정해주면 된다.
 - end 안정해주면 끝까지

```js
// Q4. make new array without the first two elements
  {
    const array = [1, 2, 3, 4, 5];
    const arr=array.slice(2);
    console.log(arr);
  }
  // 결과값: [3,4,5]

```


### quiz5~10
```js
 class Student {
    constructor(name, age, enrolled, score) {
      this.name = name;
      this.age = age;
      this.enrolled = enrolled;
      this.score = score;
    }
  }
  const students = [
    new Student('A', 29, true, 45),
    new Student('B', 28, false, 80),
    new Student('C', 30, true, 90),
    new Student('D', 40, false, 66),
    new Student('E', 18, true, 88),
  ];
  ```
   - 위에 구조를 참조해서 문제를 푼다.


### find
 - find함수안에 function 형태로 들어와야 되고 그 function의 return값은 boolean이어야 한다.

```js
// Q5. find a student with the score 90
  {
    for (let i=0; i<students.length; i++){
        if (students[i].score==90){
            console.log(students[i]);
        }
    }

    const result=students.find(function(student){
        return student.score===90;
    });
    console.log(result);
    
        
  }
  //결과값:
  // Student { name: 'C', age: 30, enrolled: true, score: 90 }
  // Student { name: 'C', age: 30, enrolled: true, score: 90 }
```
 - 둘다 같은 코드이지만 find 함수로 더욱더 쉽고 간단하게 코드를 짤수 있다.


### filter
 - filter함수도 안에 함수로 콜백함수를 받는데 콜백함수에 지정된 조건을 충족하는 배열의 요소를 반환한다.

```js
// Q6. make an array of enrolled students
  {
    const result=students.filter((student)=>student.enrolled===true);
    console.log(result);
  }
  //결과값
  // [
  //  Student { name: 'A', age: 29, enrolled: true, score: 45 },
  //  Student { name: 'C', age: 30, enrolled: true, score: 90 },
  //  Student { name: 'E', age: 18, enrolled: true, score: 88 }
  // ]
```

### map
- 배열의 각 요소에 대해 정의된 콜백 함수를 호출하고 결과가 포함된 배열을 반환한다.
- return 할떄 함수에 연산을 먹여서 return할수 있다. 밑에 예시에서 ```students.score*2```하면 2배된 값으로 return 된다.
```js
 // Q7. make an array containing only the students' scores
  // result should be: [45, 80, 90, 66, 88]
  {
    const result=students.map((student)=>student.score);
    console.log(result);
  }
  // 결과값 [45, 80, 90, 66, 88]
```

### some & every
 - some함수는 해당 조건이 존재하면 true를 return한다.
 - every함수는 해당 조건이 모두 만족해야 true를 return한다.

```js

  // Q8. check if there is a student with the score lower than 50
  {
    const result=students.some((student)=>student.score<50);
    console.log(result);

    const result1=!students.every((student)=>student.score<50);
    console.log(result1);
  }
  // 결과값
  // true
  // true
```

### reduce & reduceRight
 - 배열의 모든 요소에 대해 지정된 콜백 함수를 호출후 콜백함수의 반환 값은 누적된 결과이며 다음 콜백 함수 호출시 인수로 제공된다.
 - 밑에 코드에서 보듯이 prev함수와 curr함수가 있는데 curr함수가 다음 콜백함수의 prev변수로 들어갑니다.

 -  reduceRight는 배열에 맨 뒤에서부터 내림차순으로 역으로 reduce함수의 역할을 처리한다.
```js
// Q9. compute students' average score
  {
    const result=students.reduce((prev,curr)=>prev+curr.score,0);
    console.log(result/students.length);
    // 결과값: 73.8
    
    
    const result1=students.reduceRight((prev,curr)=>{
        return prev+curr.score;
    },0)
    console.log(result1)
  }
  결과값:369
  
```

### operator combination
```js
 // Q10. make a string containing all the scores
  // result should be: '45, 80, 90, 66, 88'
  {
    const result=students
    .map((student)=>student.score)
    .filter((score)=>score>=50)
    .join()
    console.log(result);
  }
  
  // Bonus! do Q10 sorted in ascending order
  // result should be: '45, 66, 80, 88, 90'
  {
    const result=students
    .map((student)=>student.score)
    .sort()
    .join()
    console.log(result);
  }
```

