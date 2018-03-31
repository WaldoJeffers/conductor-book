# curry

###### `curry :: Function f -> Function g`

---

#### description
Returns a [curried version](https://en.wikipedia.org/wiki/Currying) of the provided function. Currying is a very important concept in functional programming: it enables [partial application](https://en.wikipedia.org/wiki/Partial_application), which in turn allows you to reuse these partially-applied functions and to avoid code repetition. `curry` is a _pure function_ and will return a new function, without modifying the original function. The new function will have the same arity as the original one did.

#### examples
##### basic example
```js
import { curry } from '@waldojeffers/conductor'

const multiply = (x, y) => x * y
const times2 = curry(multiply)(2)

times2(5) // 10
```

##### arity preservation
```js
import { curry } from '@waldojeffers/conductor'

const multiply = (x, y) => x * y
multiply.length // 2
curry(multiply).length // 2
```
The resulting function has the same arity as the original.
