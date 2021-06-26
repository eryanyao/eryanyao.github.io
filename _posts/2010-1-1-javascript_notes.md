---
layout: post
title: JavaScript Note
---

Below is my JavaScript note.

<br>

### Array
```javascript
const items = [
  { name: 'Bike', price: 100 },
  { name: 'Motor', price: 200 },
]
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
