---
title: "JavaScript This Explained"
date: 2018-03-03T21:20:25+01:00
draft: true
---

# Learn this in Javascript

There are four rules that help us determining the `this` object. The order of the rule 
matters. If your coming from an OOP language like Java or C# you most likely be confused
about this dynamic beeing of `this` in JavaScript. Lets demistify it a bit.

### 1. Function is called with `new`
```javascript
if (isAwesome){
  return true
}
```
### 2. Function is called with `apply` / `call`
### 3. Function is called within an object
### 4. Normal function call

