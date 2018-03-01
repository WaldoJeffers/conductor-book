# conductor

Easily mix *asynchronous* and *synchronous* code using functional programming.
___
## purpose
Nearly all of our today JavaScript code uses *asynchronous* operations, whether through Promises, node.js callbacks or async generators. But that was not always the case! Before the rise of AJAX and node.js, there was almost no asynchronous code in our JavaScript. Thus, nearly all utility functions such as `map`, `filter`, or `reduce` were not designed to handle asynchronous code, and neither were great libraries such as [Lodash](https://lodash.com/), [Ramda](ramdajs.com) or [Underscore](http://underscorejs.org/). conductor intends to reconcile all these utility functions with asynchronous code, and let you regain control of the execution flow.

##### example
Let's say we want to know who's really from Tatooine, using the awesome [Star Wars API](https://swapi.co/):
```js
const character_ids = [1, 2, 3, 4, 5]
const isFromTatooine = id => fetch(`https://swapi.co/planets/${id}`)
.then(planet => planet.name === 'Tatooine')
```
###### without conductor
```js
const tatooine_residents = await character_ids.filter(isFromTatooine) // ???
```
###### with conductor
```js
const tatooine_residents = await filter(isFromTatooine, character_ids) // [1, 2, 4]
```
