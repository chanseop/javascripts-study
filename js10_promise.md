## Promise
### 특징
 - Promise is a JavaScript object for asynchoronous operation
 - 1. state: pending -> fulfilled or rejected
 
 -  프로세스가 무거운 operation을 수행하고 있는 중인지 아니면 기능 수행이 다 이루어져서 성공했는지 실패했는지 상태에 대해서 이해하는게 중요
 - 2. producer vs consumer

### Producer
 - network 요청을 사용자가 요청해야 할 경우라면 promise로 만들면 안된다. promise가 만들어지자 마자 바로 실행되는것을 알고 잘 염두하고 코드를 짜야된다.

```js
const promise = new Promise((resolve,reject)=>{
		// doing some heavy work(network, read files)
		console.log('doing something...');
		setTimeout(()=>{
				resolve('seop');
				// reject(new Error('no network'));
		},2000)
});

```

### Consumers : then, catch, finally
 -  promise를 이루는 함수로는 then, catch, finally가 있다.
 -  then: then안에 함수값을 받아서 계산을 처리하거나 다른 then으로 넘겨주거나 한다.
 -  catch: reject를 넘겨 받았을때 catch에서 걸려서 설정한 error문을 실행한다.
 -  finally: then을 실행하든 catch이 실행되든 결국 finally문을 실행된다.
```js
promise.then((value)=>{
		console.log(value);
})
.catch(error=>{
		console.log(error);
})
.finally(()=>console.log('finally'));
```

### Promise chaining
```js
const fetchNumber = new Promise((resolve,reject)=>{
		setTimeout(()=> resolve(1),1000);
});

fetchNumber
.then(num=>num*2)
.then(num=>num*3)
.then(num=>{
		return new Promise((resolve,reject)=>{
				setTimeout(()=>resolve(num-1),1000);
		});
}).then(num=>console.log(num));
```

### Error Handing
```js
const getHen = ()=>
	new Promise((resolve,reject)=>{
		setTimeout(()=>resolve('닭~~~'),1000);
	});

const getEgg=hen=>
	new Promise((resolve,reject)=>{
		setTimeout(()=>reject(new Error(`error! ${hen} => 달걀`)),1000);
	});

const cook = egg =>
	new Promise((resolve,reject)=>{
			setTimeout(()=>resolve(`${egg}=>닭22`),1000);
	}); 
// getHen()
// .then(hen => getEgg(hen))
// .then(egg =>cook(egg))
// .then(meal=>console.log(meal));

// then 안에 받아오는 인자값과 함수안에 들어가는 인자값이 같은경우 생략가능하다.
getHen()
	.then(getEgg)
	.catch(error=>{
		return '빵';
	})
	.then(cook)
	.then(console.log)
	.catch(console.log());
  
```

### callbackhell_solve_promise
앞서 callback지옥 문제를 promise를 이용해서 쉽게 풀어내었다.
```js
'use strict';


// 콜백지옥 예제

class UserStorage{
    loginUser(id,password){
        return new Promise((resolve,reject)=>{
            setTimeout(()=>{
                if(
                    (id==='seop' && password == 'dream')||
                    (id==='coder' && password === 'academy')
                ){
                    resolve(id);
                }else{
                    reject(new Error('not found'));
                }
            },2000);
        });
        
    }

    getRoles(user){
        return new Promise((resolve,reject)=>{
            setTimeout(()=>{
                if (user === 'seop'){
                    resolve({name:'seop',role:'admin'});
                }else {
                    reject(new Error('no access'));
                }
            },1000)
        })

    }
}

const userStorage= new UserStorage();
const id= prompt('enter your id');
const password=prompt('enter your password');

userStorage
    .loginUser(id,password)
    .then(userStorage.getRoles)
    .then(user=>alert(`Hello ${user.name}, you have a ${user.role} role`))
    .catch(console.log());

```


