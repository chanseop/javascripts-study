## callback hell
```js
'use strict';

// synchronous callback
// js는 함수가 hoisting되기떄문에 제일 위에 선언되었다.
function printImmediately(print) {
  print();
}

//asynchronous callback
function printWithDelay(print, timeout) {
  setTimeout(print, timeout);
}
console.log('1'); //동기
setTimeout(() => console.log('2'), 1000); //비동기
console.log('3'); //동기
printImmediately(() => console.log('hello')); //동기
printWithDelay(() => console.log('async callback'), 2000); //비동기

console.clear();
// 콜백지옥 예제

class UserStorage {
  loginUser(id, password, onSuccess, onError) {
    setTimeout(() => {
      if (
        (id === 'seop' && password == 'dream') ||
        (id === 'coder' && password === 'academy')
      ) {
        onSuccess(id);
      } else {
        onError(new Error('not found'));
      }
    }, 2000);
  }

  getRoles(user, onSuccess, onError) {
    setTimeout(() => {
      if (user === 'seop') {
        onSuccess({ name: 'seop', role: 'admin' });
      } else {
        onError(new Error('no access'));
      }
    }, 1000);
  }
}

const userStorage = new UserStorage();
const id = prompt('enter your id');
const password = prompt('enter your password');

userStorage.loginUser(
  id,
  password,
  (user) => {
    userStorage.getRoles(
      user,
      (userWithRole) => {
        alert(
          `hello ${userWithRole.name}, you have a ${userWithRole.role} role`
        );
      },
      (error) => {
        console.log(error);
      }
    );
  },
  (error) => {
    console.log(error);
  }
);
```
