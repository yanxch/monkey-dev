---
title: "JavaScript This Explained"
date: 2016-03-10T21:20:25+01:00
draft: false
---

# Learn this in Javascript

There are four rules that help us determining the `this` object. The order of the rule 
matters. If your coming from an OOP language like Java or C# you most likely be confused
about this dynamic behaviour of `this` in JavaScript. So lets demistify it a bit.

### 1. Function is called with `new`
When a function is called with the `new` keyword then the `this` object inside of the function is the newly created object.

<div class="codeblock">
  <img src="/img/mac1.png" height="20px" style="user-select: text;position:  relative;top: 33px;">
  <pre>
    <code class="language-javascript">
function Note(name, text) {
  this.name = name;
  this.text = text;
}

var note = new Note('My first note', 'I have to learn Javascript');

console.log(note.name); // My first note</code></pre>
</div>

\
\  
### 2. Function is called with `apply` / `call`
When a function is called with `call`or `apply` the `this` object is the object that is specified as first function argument.

<div class="codeblock">
  <img src="/img/mac1.png" height="20px" style="user-select: text;position:  relative;top: 33px;">
  <pre>
    <code class="language-javascript">
function Note(name, text) {
  this.name = name;
  this.text = text;
}

var my_this_object = {};
var note = Note.call(my_this_object, 'My first note', 'I have to learn Javascript');

console.log(my_this_object.name); // My first note 
console.log(note.name); // undefined</code></pre>
</div>

\
\ 
### 3. Function is called within an object
When a function is called from an containing object, then the containing object is the `this`object within the function

<div class="codeblock">
  <img src="/img/mac1.png" height="20px" style="user-select: text;position:  relative;top: 33px;">
  <pre>
    <code class="language-javascript">
function Note(name, text) {
  this.name = name;
  this.text = text;
  this.toString = function() {
    return this.name + ', ' + this.text;
  }
}

var note = new Note('My first note', 'I have to learn Javascript');

console.log(note.toString()); // My first note, I have to learn JavaScript</code></pre>
</div>

\
\ 
### 4. Normal function call
When a function is called the `this`object is the scope from where the function is called.

<div class="codeblock">
  <img src="/img/mac1.png" height="20px" style="user-select: text;position:  relative;top: 33px;">
  <pre>
    <code class="language-javascript">
var name = 'Chris';

setNameOfCurrentNote('Michael'); // Function call uses current scope as this

function setNameOfCurrentNote(name) {
  this.name = name; 
}

console.log(name); // Herbert</code></pre>
</div>

