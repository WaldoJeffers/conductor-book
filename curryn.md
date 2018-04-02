# curryN

###### `curryN :: (Number arity, Function f) -> Function g`

---

#### description
Returns a [curried version](https://en.wikipedia.org/wiki/Currying) of the provided function. The new function will have the specified arity. `curry` is a _pure function_ and will return a new function, without modifying the original function.

`curryN` is very similar to [`curry`](curry.md), except you provide the desired arity. `curry` actually uses `curryN` internally and is defined as follows: `curry = fn => curryN(fn.length, fn)`. In most cases, [`curry`](curry.md) or [`arity`](arity.md) will be better suited to your needs. The only case where you might want to use `curryN` would be if your function's `length` does not reflect its actual arity (either because it uses the spread parameter operator, or uses the [`arguments`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments) local variable internally).
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


##### deep currying
```js
import { curry } from '@waldojeffers/conductor'

const add = (a, b, c, d) => a + b + c + d
const addCurried = curry(add)
addCurried(1) // Function
addCurried(1)(2) // Function
addCurried(1)(2)(3) // Function
addCurried(1)(2)(3)(4) // 10
```

##### passing more than one argument
```js
import { curry } from '@waldojeffers/conductor'

const add = (a, b, c) => a + b + c
const add3 = curry(add)(1, 2)
add3(3) // 6
```



