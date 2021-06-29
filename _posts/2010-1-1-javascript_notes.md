---
layout: post
title: JavaScript Note
---

Below is my JavaScript note.

<br>

### Object
- Encapsulation: the capability to store related information, whether data or methods, together in an object. 封装
- Aggregation: the capability to store one object inside another object. 聚合
- Inheritance: the capability of a class to rely upon another class (or number of classes) for some of its properties and methods. 继承
- Polymorphism: the capability to write one function or method that works in a variety of different ways. 多态性
```javascript
objectName.objectProperty = propertyValue;

var str = document.title;

document.write ("This is test");
```
- new operator
```javascript
var employee = new Object();
var books = new Array("C++", "Perl", "Java");
var day = new Date("August 15, 1947");
```
- **Object() Constructor**
1. Eg1
```javascript
var book = new Object(); // Create the object
book.subject = "Perl"; // Assign properties to the object
book.author = "Mohtashim";
```
2. Eg2
```javascript
function book(title, author){
 this.title = title;
 this.author = author;
}

var myBook = new book("Perl", "Mohtashim"); //create new object

myBook.title //display 
myBook.author
```
- define method for object
```javascript
// Define a function which will work as a method
function addPrice(amount){
 this.price = amount;
}
function book(title, author){
 this.title = title;
 this.author = author;
 this.addPrice = addPrice; // Assign that method as property.
}
```
```javascript
 var myBook = new book("Perl", "Mohtashim");
 myBook.addPrice(100);
```
```javascript
document.write("Book title is : " + myBook.title + "<br>");
document.write("Book author is : " + myBook.author + "<br>");
document.write("Book price is : " + myBook.price + "<br>");
```

```javascript
var user = {
 name: 'Johnson',
 birth: 1999,
 calculateAge: function(){
   //code to calculate
 }
}
```
### Array
> create array object
```javascript
var fruits = new Array( "apple", "orange", "mango" );
```
```javascript
var fruits = [ "apple", "orange", "mango" ];
```
output:
```javascript
fruits[0] is the first element
fruits[1] is the second element
fruits[2] is the third element
```
```javascript
const items = [
  { name: 'Bike', price: 100 },
  { name: 'Motor', price: 200 },
]
```
- array.length
> to know the length of the array
- .concat()
```javascript
 var alpha = ["a", "b", "c"];
 var numeric = [1, 2, 3];
 
 var alphaNumeric = alpha.concat(numeric);
 
 //output: alphaNumeric : a,b,c,1,2,3
```
- .indexOf() 
> check the item's index
```javascript
var index = [12, 5, 8, 130, 44].indexOf(8);
document.write("index is : " + index ); //index is : 2

var index = [12, 5, 8, 130, 44].indexOf(13);
document.write("<br />index is : " + index ); //index is : -1 (-1 mean not available in the array)
```

- filter
```javascript
const filteredItems = items.filter((item)=>{
  return item.price <= 100
})
```
- map
```javascript
const itemName = items.map((item)=>{
  return item.name
})

const itemPrice = items.map((item)=>{
  return item.price
})
```
```javascript
var numbers = [1, 4, 9];
var roots = numbers.map(Math.sqrt);
document.write("roots is : " + roots ); //roots is : 1,2,3
```
- find
```javascript
const findItem = items.find((item)=>{
  return item.name === 'Bike'
})
```
- forEach
```javascript
items.forEach((item)=>{
  console.log(item.price)
})
```
- some
> single array items map condition it will return true
```javascript
const hasInexpensiveItems = items.some((item)=>{
  return item.price <=100 //return true or false
})
```
- every
> all array item must met the condition then it will return true
```javascript
const hasInexpensive = items.some((item)=?{
  return item.price <= 1000 //return true or false
})
```
- reduce
```javascript
const total = items.reduce((currentTotal,item)=>{
  return item.price + currentTotal
},0)
//currentTotal will have the previous data
```
- include
```javascript
const includesTwo = items.price.includes(100)
//return true, check item having data or not
```

### Equality
```javascript
"88" == 88 //true, it will convert make it same
"88" === 88 //false
```
### function
#### Function() Constructor
```javascript
var func = new Function("x","y","return x+y")

var result = func(10,10);
```
#### Function Literals
>  is an expression that defines an unnamed function.
```javascript
var func = function(x,y){return x+y}
```
### void
```javascript
void func()
javascript:void func()
OR
void(func())
javascript:void(func())
```

### Loop
#### while
> The most basic loop in JavaScript is the while loop which would be discussed in
this chapter. The purpose of a while loop is to execute a statement or code
block repeatedly as long as an expression is true. Once the expression
becomes false, the loop terminates.
```javascript
while (expression){
 Statement(s) to be executed if expression is true
}
```
#### while loop
>  The do...while loop is similar to the while loop except that the condition check
happens at the end of the loop. This means that the loop will always be executed
at least once, even if the condition is false.
```javascript
do{
  statement;
}while(condition)
```

### for
#### for-in loop
> The for...in loop is used to loop through an object's properties. As we have not
discussed Objects yet, you may not feel comfortable with this loop. But once you
understand how objects behave in JavaScript, you will find this loop very useful.
```javacript
for (variable in object){
  statement;
}
```

### break n continue
#### break
> stop the looping
```javascript
var x = 1;
document.write("Entering the loop<br /> ");
while (x < 20)
{
 if (x == 5){
 break; // breaks out of loop completely
 }
 x = x + 1;
 document.write( x + "<br />");
}
document.write("Exiting the loop!<br /> ");
```
#### continue
> skip the following looping and continue
```javascript
var x = 1;
document.write("Entering the loop<br /> ");
while (x < 10)
{
 x = x + 1;
 if (x == 5){
 continue; // skill rest of the loop body
 }
 document.write( x + "<br />");
}
document.write("Exiting the loop!<br /> ");
```
#### use Labels to Control the Flow
```javascript
document.write("Entering the loop!<br /> ");
outerloop: // This is the label name
for (var i = 0; i < 5; i++)
{
 document.write("Outerloop: " + i + "<br />");
 innerloop:
 for (var j = 0; j < 5; j++)
  {
 if (j > 3 ) break ; // Quit the innermost loop
 if (i == 2) break innerloop; // Do the same thing
 if (i == 4) break outerloop; // Quit the outer loop
 document.write("Innerloop: " + j + " <br />");
 }
}
document.write("Exiting the loop!<br /> ");
```
Output:
```
Entering the loop!
Outerloop: 0
Innerloop: 0
Innerloop: 1
Innerloop: 2
Innerloop: 3
Outerloop: 1
Innerloop: 0
Innerloop: 1
Innerloop: 2
Innerloop: 3
Outerloop: 2
Outerloop: 3
Innerloop: 0
Innerloop: 1
Innerloop: 2
Innerloop: 3
Outerloop: 4
Exiting the loop!
```
### Number
- .toPrecision()
```javascript
num.toPrecision() is 7.123456
num.toPrecision(4) is 7.123
num.toPrecision(2) is 7.1
num.toPrecision(1) is 7
```
- .toString()
```javascript
num.toString() is 15
num.toString(2) is 1111 \\binary
num.toString(4) is 33
```
- .valueOf()
> Returns the primitive value of the specified number object.
```javascript
var num = new Number(15.11234);
num.valueOf() is 15.11234
```
### Promise
> promise is an object provides useful construct when dealing with asynchronous tasks. Promise can ensure success or failure of the  taks
```javascript
//create a promise
const p = new Promise((resolve,reject)=>{

 setTimeout(()=>{
   if(){
    resolve('success');
   }
   else{
    reject('fail');
   }
  },2000)
})

//use a promise
p.then((res)=>{
 console.log(res)
})
.catch((err)=>{
 console.log(err)
})
```
### Constructor
```javascript
//define constructor
function Car(make,model,year){
 this.make = make;
 this.model = model;
 this.year = year;
 
 this.setMiles = function(miles){
  this.miles =  miles;
  return miles;
 }
}

//use constructor
const car1 = new Car('Toyota','Vios',2005);

//add method to the constructor
Car.prototype.age = function(){
 return (new Date().getFullYear() - this.year; //this year = 2021 (calculation: 2021-2005)
}

car1.age(); //return 16
```
#### Source
<https://www.tutorialspoint.com/javascript/index.htm> \
<https://www.youtube.com/watch?v=a00NRSFgHsY> 
