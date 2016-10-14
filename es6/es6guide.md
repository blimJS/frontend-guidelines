# JavaScript Antipatterns

* Readability
* Clean Clode

 

###Conditionals
#### Declaration 
```javascript 
// Avoid this it's fragile and easy to break , if you 
// have to remove the last variable you have to add  the semicolon if the list is hard to maintain

var firstVariable = 1,
    secondVariable = 2, 
    thirdVariable = 3,
    fourthVariable = 4;

// Easier to maintain 
var firstVariable = 1;
var secondVariable = 2;
var thirdVariable = 3;
var fourthVariable = 4;
```

####Simple conditions

```javascript 
//avoid this, it's hard to read
if ( _.find( list, function (item) {
  return compare(item.something, external);
} ) ) {
    // Do stuff
}

// Do this 
var found = _.find(list, function (item) {
  return compare(item.something, external);
});

// Simple conditions
if ( found ) {
    // do stuff
} 

```

####Abuse of Ternary Operator 
The ternary operator should be used only for assignation, it should only be used for one liners as long it doens't affect the  readability and clearness. 

```javascript 
// Only for use for assignation
var size = name.length > 10 ? 'large' : 'small';

// Never do this
foo() ? bar() : doo(); 

// avoid this , it's confusing not readable 
var url = age > 18 ? (
    alert("OK, you can go."), 
    "continue.html"
) : (
    alert("You are much too young!"),
    alert("Sorry"),
    "stop.html"
);

```

#### Loops & Iterators
```javascript 
// Hierarchy
//- use more iterators
map
```

### Functions 

```javascript
let test
```