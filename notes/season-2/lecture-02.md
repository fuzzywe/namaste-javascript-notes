# Episode 21 : Promises

> Promises are used to handle async operations in JavaScript.

> A Promise is an object which represents eventual completion or failure of an asynchronous operation.
> Promises are immutable once resolved and they give us a lot of control over our code.
> They have three state pending, fulfilled or rejected. The promise object contains two parts
> 1) PromiseState(stores the sate of the prmise) and
> 2) 2)PromiseResult(stores data)


1. What are Promises?
Promises are objects which are used to perform asynchronous operations. They are just like placeholders to store a future value that will be returned after some time. They contain two properties: PromiseState and PromiseResult.

 2. Importance of Promises:
a) Promises can help us to write trust worthy code.
b) Promises are used to solve the problems of callbacks like inversion of control and callback hell.
c) They give us the result prompt in three states: 1) Pending 2) Fulfilled 3) Rejected
d) We can attach function to promise object and retrieve its value unlike callbacks no need to pass the function.
e) Nesting can be done in Promises and with the help of that we can return the values in each individual chain

1. Before promise we used to depend on callback functions which would result in 1.) Callback Hell (Pyramid of doom) | 2.) Inversion of control
2. Inversion of control is overcome by using promise.
  2.1) A promise is an object that represents eventual completion/failure of an asynchronous operation.
  2.2) A promise has 3 states: pending | fulfilled | rejected.
  2.3)  As soon as promise is fulfilled/rejected => It updates the empty object which is assigned undefined in pending state.
  2.4) A promise resolves only once and it is immutable. 
  2.5) Using .then() we can control when we call the cb(callback) function.

3. To avoid callback hell (Pyramid of doom) => We use promise chaining. This way our code expands vertically instead of horizontally. Chaining is done using '.then()'
4. A very common mistake that developers do is not returning a value during chaining of promises. Always remember to return a value. This returned value will be used by the next .then()


1) A Promise is an object that represents the eventual completion or failure of an asynchronous operations.
2) Importance of promise is that we do not loose the control of the program, a promise object is immutable and can be send anywhere without worrying about changes, also it resolves only once either to success or failure.

1: A Promise is an object that represent eventual completion of asynchronous operation. 
2. Promise come into picture because using callback function we have face callback hell and inversion of Control.
CallBackHell - Nested Multiple call back function and Code should be grow vertical but it grow horizontally. 
Inversion of Control - We are passing function to other function. but we don't know weather it will run or not and we  don't have control. 
3. Advantage _ 
     Resolved Call back Hell Problem.
     Code Readibilty
     Now we control of all function.


 Using callbacks for asynchronous operations can lead to issues like inversion of control and lack of reliability.
05:18 🛠 Promises provide a more structured and reliable way to handle asynchronous operations in JavaScript compared to callbacks.
08:13 📝 Promises allow attaching callback functions, ensuring control over the program flow and providing a guarantee of execution.
11:35 🤝 Promises offer trust and certainty by ensuring callback execution when data is available, enhancing code reliability.
15:29 💡 Promises have distinct states (pending, fulfilled, rejected) and are immutable once fulfilled, enhancing code predictability and control.
22:07 💡 Promises in JavaScript serve as a placeholder for values from asynchronous operations, representing a future value or completion.
23:30 🧩 MDN defines promises as objects representing the eventual completion of an asynchronous operation, simplifying their understanding and usage.
25:40 🔄 Callback hell refers to the complexity and difficulty of maintaining code written with nested callbacks, leading to horizontal growth and decreased readability.
28:07 🔗 Promise chaining allows for sequential execution of asynchronous tasks, enhancing code clarity and avoiding callback hell.
30:21 🐛 Developers must ensure proper data flow in promise chains by consistently returning promises from each then function to prevent bugs and maintain code integrity.

we can print the promise object using console.table(<promise_object>) to see the state (pending) and result [at the time of logging]. Since expanding a object will always show the current value rather than at the time of printing. By using "console.table", it prints the values at the logging time and provide an option to view the current value beneath it.
Promises: It is an object which represent the eventual completion or failure of asyn operation.

Advantages: It saves data from api called and attach the callback api which makes code run only ones. It gives developers to more control over code. 
1. A promise is an object which will represent eventual completion or failure of an asynchronous operation.
2. Importance of Promises:
a. Promise will give control over our code.
b. Promises are used to solve problems of callbacks like inversion of control and callback hell.
c. In promise object we will attach the function and retrieve its value, no need to pass the function like callbacks.
d. Promised has two steps: 1> PromiseState 2> PromiseResult
e. Promise will give us result in 3 steps: 1> Initially it will be in pending state. 2> Then it will move to fulfilled state once our operation will be successful. 3> If our operation will fail our promise will be moved to rejected state.
f. Chaining can be done in promises and with the help of this we can return values in each individual chain.


Promise is an object that represent eventual completions of an asynchronous function. Its like a placeholder, it will fill when the async function return the value. 

Advantage: the promise chain concept replace the callback hell. We don't want to write the callback function as an argument to another callback function, 
Promise have 3 state(pending, fulfilled, rejected)

Promise:  Promise is an object representing the eventual completion of a sync operation.

To solve the callback hell and inversion of control, we use promises. Also, promises give us a guarantee to get executed once.

promise is basically an object, which represents the eventual completion or failure of an asynchronous operation. In order to over come the 2 drawbacks with callback functions, promises were introduced as part of ECMAScript6. 2 drawbacks are like callback hell (nested callbacks), inversion of control.

1) What is promise?
A) Promise is an object that represents eventual completion/failure  of an asynchronous operation.

2)Why it is used?
A) Promises are useful to eliminate inversion control and better readability.

Topic - 3:
--> Chaining promises using   " .then"
----> fetch() is an api used to get/fetch data from source given.

**COMMON MISTAKES IN PROMISES :
--> we have to return the data when pipelining to anoteher operation.


Promises build the trust. By using callback function we are depending on other function in some api to complete the callback functionality - which may be fulfilled or not - which causes Inversion of control. By using Promise, the control is in our hand - we can also chain the another callback function using then in promise.

We will discuss with code example that how things used to work before `Promises` and then how it works after `Promises`

Suppose, taking an example of E-Commerce

```js
const cart = ["shoes", "pants", "kurta"];

// Below two functions are asynchronous and dependent on each other
const orderId = createOrder(cart);
proceedToPayment(orderId);

// with Callback (Before Promise)
// Below here, it is the responsibility of createOrder function to first create the order then call the callback function
createOrder(cart, function () {
  proceedToPayment(orderId);
});
// Above there is the issue of `Inversion of Control`
```

Q: How to fix the above issue?  
_A: Using Promise._

Now, we will make `createOrder` function return a promise and we will capture that `promise` into a `variable`

Promise is nothing but we can assume it to be empty object with some data value in it, and this data value will hold whatever this `createOrder` function will return.

Since `createOrder` function is an async function and we don't know how much time will it take to finish execution.

So the moment `createOrder` will get executed, it will return you a `undefined` value. Let's say after 5 secs execution finished so now `orderId` is ready so, it will fill the `undefined` value with the `orderId`.

In short, When `createOrder` get executed, it immediately returns a `promise object` with `undefined` value. then javascript will continue to execute with other lines of code. After sometime when `createOrder` has finished execution and `orderId` is ready then that will `automatically` be assigned to our returned `promise` which was earlier `undefined`.

Q: Question is how we will get to know `response` is ready?  
_A: So, we will attach a `callback` function to the `promise object` using `then` to get triggered automatically when `result` is ready._

```js
const cart = ["shoes", "pants", "kurta"];

const promiseRef = createOrder(cart);
// this promiseRef has access to `then`

// {data: undefined}
// Initially it will be undefined so below code won't trigger
// After some time, when execution has finished and promiseRef has the data then automatically the below line will get triggered.

promiseRef.then(function () {
  proceedToPayment(orderId);
});
```

Q: How it is better than callback approach?

In Earlier solution we used to pass the function and then used to trust the function to execute the callback.

But with promise, we are attaching a callback function to a promiseObject.

There is difference between these words, passing a function and attaching a function.

Promise guarantee, it will callback the attached function once it has the fulfilled data. And it will call it only once. Just once.

Earlier we talked about promise are object with empty data but that's not entirely true, `Promise` are much more than that.

Now let's understand and see a real promise object.

fetch is a web-api which is utilized to make api call and it returns a promise.

We will be calling public github api to fetch data
https://api.github.com/users/alok722

```js
// We will be calling public github api to fetch data
const URL = "https://api.github.com/users/alok722";
const user = fetch(URL);
// User above will be a promise.
console.log(user); // Promise {<Pending>}

/** OBSERVATIONS:
 * If we will deep dive and see, this `promise` object has 3 things
 * `prototype`, `promiseState` & `promiseResult`
 * & this `promiseResult` is the same data which we talked earlier as data
 * & initially `promiseResult` is `undefined`
 *
 * `promiseResult` will store data returned from API call
 * `promiseState` will tell in which state the promise is currently, initially it will be in `pending` state and later it will become `fulfilled`
 */

/**
 * When above line is executed, `fetch` makes API call and return a `promise` instantly which is in `Pending` state and Javascript doesn't wait to get it `fulfilled`
 * And in next line it console out the `pending promise`.
 * NOTE: chrome browser has some in-consistency, the moment console happens it shows in pending state but if you will expand that it will show fulfilled because chrome updated the log when promise get fulfilled.
 * Once fulfilled data is there in promiseResult and it is inside body in ReadableStream format and there is a way to extract data.
 */
```

Now we can attach callback to above response?

Using `.then`

```js
const URL = "https://api.github.com/users/alok722";
const user = fetch(URL);

user.then(function (data) {
  console.log(data);
});
// And this is how Promise is used.
// It guarantees that it could be resolved only once, either it could be `success` or `failure`
/**
    A Promise is in one of these states:

    pending: initial state, neither fulfilled nor rejected.
    fulfilled: meaning that the operation was completed successfully.
    rejected: meaning that the operation failed.
 */
```

💡Promise Object are immutable.  
-> Once promise is fulfilled and we have data we can pass here and there and we don't have to worry that someone can mutate that data. So over above we can't directly mutate `user` promise object, we will have to use `.then`

### Interview Guide

💡What is Promise?  
-> Promise object is a placeholder for certain period of time until we receive value from asynchronous operation.

-> A container for a future value.

-> **A Promise is an object representing the eventual completion or failure of an asynchronous operation.**

We are now done solving one issue of callback i.e. Inversion of Control

But there is one more issue, callback hell...

```js
// Callback Hell Example
createOrder(cart, function (orderId) {
  proceedToPayment(orderId, function (paymentInf) {
    showOrderSummary(paymentInf, function (balance) {
      updateWalletBalance(balance);
    });
  });
});
// And now above code is expanding horizontally and this is called pyramid of doom.
// Callback hell is ugly and hard to maintain.

// 💡 Promise fixes this issue too using `Promise Chaining`
// Example Below is a Promise Chaining
createOrder(cart)
  .then(function (orderId) {
    proceedToPayment(orderId);
  })
  .then(function (paymentInf) {
    showOrderSummary(paymentInf);
  })
  .then(function (balance) {
    updateWalletBalance(balance);
  });

// ⚠️ Common PitFall
// We forget to return promise in Promise Chaining
// The idea is promise/data returned from one .then become data for next .then
// So,
createOrder(cart)
  .then(function (orderId) {
    return proceedToPayment(orderId);
  })
  .then(function (paymentInf) {
    return showOrderSummary(paymentInf);
  })
  .then(function (balance) {
    return updateWalletBalance(balance);
  });

// To improve readability you can use arrow function instead of regular function
```

<hr>

Watch Live On Youtube below:

<a href="https://www.youtube.com/watch?v=ap-6PPAuK1Y&list=PLlasXeu85E9eWOpw9jxHOQyGMRiBZ60aX&index=3&ab_channel=AkshaySaini" target="_blank"><img src="https://img.youtube.com/vi/ap-6PPAuK1Y/0.jpg" width="750"
alt="promise in Javascript Youtube Link"/></a>
