## 1. Javascript objects.

**_What are they?_**



*   Objects are the most important data-type in Javascript. Other data-types are numbers, strings, booleans, null, undefined, and symbols.
*   Objects are more complex and generally contain more information than these data-types
*   Within the object, you most commonly see `key:value` pairs
    *   Key is a string, called a property name
    *   Value can be anything: number, string, boolean, null, etc. It can even be a function.
*   In the example below, `series` is the object. `name`, `genre`, and `released` are keys while `Alf`, `Sitcom`, and 1986 are vales.

```
let series = {
    name: 'Alf',
    genre: 'Sitcom',
    released: 1986,
    fun: true,
    getInfo: function() {
        console.log(`The best TV show from ${series.released} is        
            ${series.name}.);
    }
}
```



**_How to access the data?_**

*   There are two main ways to access data within an object: **dot notation** and **bracket notation**.
*   Dot notation is formed like: `objectName.keyName`.
*   If the object contains a function, to call this function, use the parentheses following the keyName.
*   Using the example above, we can call the name of the series by using `series.name` and the function `getInfo()` by calling `series.getInfo()`.

```
objectName.keyName;

series.name;
series.getInfo();
```


*   Bracket notation is formed like: `objectName[‘keyName’]`.
*   An advantage of bracket notation is that you can use key names that include spaces and/or dashes or a key name that begins with a number, all of which are not valid names in JavaScript.
*   You can also have variables inside of the brackets: `objectName[variableName]`.

```
objectName['keyName'];

series['name'];
series['name of genre'];

let key = 'name';
series[key];
```

**_How to create an object?_**



*   Object literal syntax - using the curly braces notation

```
let myObject = {
    myName : "Alf",
    bornIn : 1986,
};
```


*   Object constructor - create an object wrapper and the “new” keyword

```
let myObject = new Object();
myObject.name = 'Alf';
myObject.birthYear = 1986;
```


*   These two ways of creating objects are okay for creating one or two but is impractical for doing dozens of objects. Let’s take a look at two more ways:
*   Constructors - are templates to create objects. They define the properties and methods that are common for all instances of an object

```
function Character(realName, stageName) {
    this.realName = realName;
    this.stageName = stageName;
} 
```



```
let actor1 = new Character('Mr. T', 'B.A. Baracus')
let actor2 = new Character('Dirk Benedict', 'Faceman')
let actor3 = new Character('Dwight Schultz', 'Howling Mad Murdock')
let actor4 = new Character('George Peppard', 'John Hannibal Smith')
```

**_How can I delete a property?_**


*   Use the “delete” operator 

```
let myObject = {
    name : "Alf"
} 
  
// Output : Alf
console.log(myObject.name); 
delete myObject.name
  
// Output : undefined
console.log(myObject.name);   
```


**_What attributes do data properties have?_**



*   In addition to their own properties, as described above, objects can also inherit properties from their prototype.
*   To check if a property is an Own property, use the hasOwnProperty() function

```
let TVShow = function(){
  this.onTV = true;
}

let seriesObject = new TVShow(); 
seriesObject.showName = 'Alf'; 

console.log(seriesObject)
// onTV: true, showName: "Alf"
  
console.log(seriesObject.hasOwnProperty('showName'));
```
*   Data properties:
    *   Value - the property’s value
    *   Writable - that the property can be changed
    *   Configurable - can be deleted, changed to be accessor property or change attributes

*   To check a data property's value, merely call it with dot notation or bracket notation, as noted above.
*   To prevent a property from being deleted, you can use the `Object.seal` method. Following the example above:

```
Object.seal(seriesObject)

delete seriesObject.onTV
// false

seriesObject
// onTV: true, showName: "Alf"

```
*   Then to check if an object is sealed, we can use the `Object.isSealed()` method:

```
Object.isSealed(seriesObject)
// true
```

*   While this prevents deleting the property of the object, it does not prevent these properties from being changed. In order to prevent them from being changed, we use the `Object.freeze()` method:

```
Object.freeze(seriesObject)

// try to change the onTV attribute to false

seriesObject.onTV = false
// false

// call the object again to verify the properties

seriesObject
// onTV: true, showName: "Alf"

```

*   Then, to check if an object has been frozen, we use the `Object.isFrozen()` method:

```
Object.isFrozen(seriesObject)
// true
```


Resources: \
[Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)
