# conductor

Easily mix *asynchronous* and *synchronous* code using functional programming.
___
## purpose
Nearly all of our today JavaScript code uses *asynchronous* operations, whether through Promises, node.js callbacks or async generators if you are among *the cool kids*. But that was not always the case! Before the rise of AJAX and node.js, there was almost no asynchronous code in our JavaScript. Thus, nearly all utility functions such as `map`, `filter`, or `reduce` were not designed to handle asynchronous code, and neither were great libraries such as [Lodash](https://lodash.com/), [Ramda](ramdajs.com) or [Underscore](http://underscorejs.org/). **conductor** intends to reconcile all these utility functions with asynchronous code, and let you regain control of the execution flow.

##### example
Let's say we want to know who's really from Tatooine, using the awesome [Star Wars API](https://swapi.co/):
```js
const characters = [
    { id: 1, name: 'Luke Skywalker', planet_id: 1 },
    { id: 2, name: 'C-3P0', planet_id: 1 },
    { id: 3, name: 'R2-D2', planet_id: 8 },
    { id: 4, name: 'Darth Vader', planet_id: 1 },
    { id: 5, name: 'Leia Organa', planet_id: 2 }
]
const isFromTatooine = character => fetch(`https://swapi.co/planets/${character.planet_id}`)
    .then(response => response.json())
    .then(planet => planet.name === 'Tatooine')
```
###### without conductor
```js
const tatooine_residents = await characters.filter(isFromTatooine) // [Luke, C-3PO, R2-D2, Darth Vader, Leia]... wait what???
```
###### with conductor
```js
const tatooine_residents = await filter(isFromTatooine, characters) // [Luke, C-3PO, Darth Vader]
```
