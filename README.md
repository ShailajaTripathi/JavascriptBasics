# 📘 JavaScript Interview Notes (Beginner → Intermediate)

----------------------------------
This repository contains **well-structured JavaScript notes with examples**, covering all **core concepts frequently asked in interviews**.  
Each topic includes **clean explanations + code snippets** for quick revision.

---------------------------------

## 📌 Table of Contents

- Variables & Scope  
- Data Types  
- Functions  
- Operators  
- Array Methods  
- ES6 Higher Order Functions  
- Destructuring  
- Object Methods  
- Spread & Rest Operators  
- Loops  
- Conditional Statements  
- Scope  
- DOM Basics  
- Asynchronous JavaScript  
- Closures  
- Local & Session Storage  
- Call, Apply & Bind  
- API Fetch Example  

---

## 🟢 Variables (var, let, const)

```js
var a = 10;
a = 12;
var a = 13;
console.log(a); // function scope

let b = 20;
b = 22; // block scope
console.log(b);

const c = 30; // block scope
console.log(c);

```
 ## 📌 JavaScript Data Types

JavaScript data types define **what kind of value** a variable can hold.  
They are mainly divided into **Primitive** and **Non-Primitive (Reference)** data types.

---

## 🔹 Primitive Data Types

Primitive data types store **single, immutable values**.  
They are stored **by value**.

#### Example:
```js
let string = "hello";
let num = 23;
let boolean = true;
let un = undefined;
let n = null;
let bigint = 21525558568345346n;
const sym1 = Symbol("description");

console.log(string, num, boolean, un, n, bigint, sym1);
```
## 📌 Non-Primitive Data Types in JavaScript

Non-primitive data types are used to store **multiple values**, **collections**, or **complex structures**.  
They are **mutable** and stored **by reference** in memory.

---

## 🔹 Types of Non-Primitive Data

| Type | Description |
|----|------------|
| Array | Ordered collection of values |
| Object | Collection of key-value pairs |
| Function | Block of reusable code |

---

## Array

An **Array** is used to store multiple values in a single variable.

### Example:
```js
let array = [10, 20, 30, 40];
console.log(array);

```
## Object: 
```js
let object={
  name:"Mohit",
  age:21
}
```
## Functions
### Function Declaration: 
```
function greet(){
console.log("function declearetion")  
}
greet()
```
### Function Expression
```
let greet1=function(){
  console.log("function expression")
}
greet1()
```
### Arrow Function (Introduced in ES6+)
```
let greet2=()=>{
  console.log("Arrow function")
}

greet2()
```
### Higher Order Function:
```
let higherodderfu =()=>{
 return ()=>{
    console.log("higher order and callback function")
  }
  
}
higherodderfu()();
```

####  arithmatic operators  : + - * / %
#### comparision operators: ==( checks value only ) ,=== ( ckecks value and dataType both ), !=,!== ,<,> 
#### logical operators : && ,||,!


 ## Array methods 
```
let arr=[1,2,3,4,5]
```

#### push():add element at end 
```
arr.push(6)
console.log(arr)
```
#### pop() : remove from end
```
arr.pop()
console.log(arr);
```

 #### unshift(): add at element at beginning
 ```
arr.unshift("apple")
console.log(arr)
```

### shift():remove frome beginning
```
arr.shift();
console.log(arr)
```
#### .length:checks length of Array
```
console.log(arr.length)
```

### includes():check if items is exists /present  and return true /
```
console.log("includes method:",arr.includes(2))
```
### indexOf():get index of items 
```
console.log(arr.indexOf(3))//return 2
```
### slice(): will cope part of array 
```
console.log( arr.slice(0,2))// 2 is excloduing index 
```
 #### splice ():add or remove atany position 
 ```
 arr.splice(1,0,"banana")      
console.log(arr)
```
#### concat():combines array
```
 let res=arr.concat(array);//  it will not modify odd array but return a new arr 
console.log(res);
```
### join(): convert to string
```
let res1=arr.join(",")//seprated by commom
console.log( res1) //return  a new string variable
```
### reverse():reverse the array items 
```
arr.reverse()
console.log(arr)
```
### sort():sort the items
```
let result=arr.sort((a,b)=>a-b)
console.log(result)


arr.pop(); // to remove "banana"
console.log(arr)
````


#### 🔖 ES6+ (Higher order Function )

#### map():change each and every items in array return a new array
```
let double=arr.map(num=>num*2)
console.log(double);
```

#### filter():select item based on condition 
```
let evennumber=arr.filter((num)=>{
  return num%2===0
})
console.log(evennumber)
```
#### reduce(): combine all iteme into single value for ex. sum etc.
```
let total=arr.reduce((acc,curr)=>{
  return acc=acc+curr
},0)

console.log(total);
```

#### find():find the first matching condition
```
let firstelement=arr.find((num)=>{
 return num%2===0  
})
console.log(firstelement,"first even number ");
```
#### Destructuing array 
```
const [first,second]=arr //storing the first and the second value inside first and second variable
console.log("Array Destructuing",first,second)
````

## 🟢 object :
```
 let obj={
   firstName:"Mohit",
   lastName:"Yadav",
   age:22
 }
 ```
 ###  Destructuing object :
 ```
 const {firstName,lastName}=obj // storing keys of object 
console.log("Object Destructuing",firstName,lastName) 
 ````
 ### Object.keys():returns an array of an object's keys
 ````
 console.log("Object.keys() :",Object.keys(obj));
 ````
 ### Object.value():returns an array of an object's value 
 ````
 console.log("Object.values():",Object.values(obj));
````
 ### Object.entries():returns an array of an object's key value pairs 
 ```
 console.log("Object.entries():", Object.entries(obj));
````
 ### Object.assign():copies properties from one or more object into target object 
 ```
 let resobj=Object.assign({},obj,object)
 console.log("Object.assign() :",resobj);
 ```
 ### Object.freeze():Prevent addding, deleting ,uptading.
 ```
 obj.age = 25;     // ❌ not allowed
 ```

 ## 🟢 Spread and rest operators [...]
 
 ### Spread operator expands or shallow copy arrays / object 
 ```
 let arr1=[100,200,300,400]
 let arr2=[...arr1,800,900];// copys/ Spread  arr1 into arr2
 console.log("Spread operator :",arr2)
````
### Rest operator collects remaning / rest element  for Destructuing etc 
```
let[one,...rest]=arr1//Destructuing by rest operators 
 console.log("rest operator :",one ,rest)
 
 ```
 ## 🔺Loop : loops are used to repeat of block of code multipl times depending on the condition 
 
### for loop:best why to know how many time to loop
```
for(let i=0;i<arr.length;i++){
  console.log("for Loop:",arr[i]))
}

````
### while loop:when you don't know how many times of but only the condition 
```
let i=0;
while(i<arr.length){
  console.log("while Loop:",arr[i]*2)
i++ 
}

```
### Do while loop:similer to while while loop but run at least if condition is false 
```
let j=0;
do{
  console.log("Do While Loop:",arr[j]);
  
}
while   (j>0);

````
### For of Loop: used to Loop throught  array or string
```
for(let i of arr){
  console.log("array elements by For of Loop",i)
}
```

### For in Loop: used to loop througth object Properties 
```
for(let key in obj){
  console.log("Object values by for in loop ",obj[key])
}
```
## 🔺 conditional statement 
### if condition:Runs the block only if condition is true 
```
let  age=18;
if(age>=18){
  console.log("if condition:You can vote")
}
```
### if else:run the block when if condition is true else consdition is false 
```
 if(age>=21){
   console.log("you can vote ")
 }
 
 else{
  console.log("if else :You can not vote ") 
 }
 ````
 ### if else-if else :checks multiple condition one by one 
 ```
let marks=75;
if(marks>=90){
  console.log("A grade")
}
else if(marks>=75){
  console.log("else if: B grade")
}
else{
  console.log("C grade ")
} 
```
### switch condition: best when you have many fixed value to compare
```
let day ="friday";
switch (day){
  case "monday":
  console.log("start of the week ")
  break;
  
  case "tuesday":
  console.log("second day of week")
  break;
  
  case "wednesday":
  console.log("third day of week")
  break;
  
  case "thursday":
  console.log("fourth day of week")
  break ;
  
  case "friday":
  console.log(" switch condition: fifth day of the week")
  break;
  
  case "saturday":
  console.log("sixth day of week")
  break;
 default:
 console.log("sunday is a holiday")
};
```

## 🔺 scope--
 
### Global scope ----------------//
 ```
 let x=10;// global scope
 
function test(){
  let y=20 //function scope
  if(y>10){
    let z=30 //block scope
    console.log("block scope :",z)
  }
 console.log(" function scope :",y)
}
console.log("Global scope",x)

test()
 
 ```

 ## 🟢 Dom:(Document object model)
  #### Select: geteElementById(),geteElementByClassName(),quarrySelector(),quarrySelectorAll()
 #### Content : element.textContent="Hello",element.innerhtml=<p> this is new paragraph </p>
 #### Style :element.style.color="red",element.style.backgroundColor="yellow"
 #### Events:element.EventListner("click",() => alert ("button clicked"))
 ####  remove: element.remove()
 ####  Create : 
 ```
 let newP=document.createElement("p"); 
 newP.textContent="New Paragraph";
  document.body.appendchild(newP);  ]
  
````



 ## 🟢 Asynchronous JavaScript: callstack ,webAPI,macrotaskqueue,microtask queue(higher priority ),eventLoop 
 
 ### Promise 
 ```
 function myPromise(){
return new Promise ((resolve,reject)=>{
resolve ("resolved")  
})
}
```
#### By .then() and .catch() methods
```
myPromise().then((result)=>{
  console.log("Promise is fullfiled :",result)
}).catch((error)=>{
  console.log(error)
})
 
 ````
 #### By Async and await keyward and try{} catch{} block 
 ```
 async function getData(){
   try{
     let result=await Promise.reject("fetch Data");
     console.log(result);
   }
   catch(error){
     console.log("Error",error)
   }
 } 
 
 getData();
```

 ## 🟢 Closure: A function bind together with its lexical environment is called  closure.
 
 ### Simple Closure function 
 ```
 function outer(){
   let a=10;
   function inner(){
     console.log("value give to closure :",a)
   }
   inner();
 }
 outer();
 
 ````
 ### Closure by setTimeout function
 ```
 function parent(){
   let a=22;
   setTimeout(()=>{
     console.log("closure with setTimeout:",a)
   },100)
 }
 parent();
 ```

 ## Local Storage : stores data in browser parmanently even after page is refresh or closed
 
 - set: localstorage.setItem("user","Mohit")
- Get: localstorage.getItem("user")
  -  remove : localstorage.remove("user")
 
 
 ## Session Storage : stores data until tab is closed or refresh.
 -  set: sessionstorage.setItem("user","Mohit")
 -   Get: sessionstorage.getItem("user")
 -   remove : sessionstorage.remove("user")
 
 
 ## call, Apply,bind All three are the function borrowing methods
 ## this refers to  owner object 

```  
  let newobj={
    name:"Mohit Yadav",
    age:21
  }
  
  function demo(city){
    console.log(` My name is ${this.name} I am ${this.age} year old and I am from ${city}`)
  }
```
### call: Pass argument individuly
``
 demo.call(newobj,"Itarsi")
 ``
 
 ### Apply : passes argument as an array
 ``
 demo.apply(newobj,["Bhopal"]);
 ``
 ### bind :returns a new function to run later 
 ```
 let results =demo.bind(newobj,"Indore")
 results();
```

 ## API (Application Programming interface) : API connect frontend + backend to give data comes from a server 
 
 ```
 async function users(){
   try{
     let result = await fetch("https://jsonplaceholder.typicode.com/posts/1") //  1 call the api using fetch 
     // 2 convert the result  into json
      let  data = await result.json()
      // 3 use data
      console.log("API user data ",data)
   }
   catch(error){
     console.log("Error",error)
   }
 }
 
 users()
 ```
--------------------------

### ⭐ Author

### Shailaja Tripathi
 React Developer
 
