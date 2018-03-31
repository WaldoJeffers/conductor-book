# compose

`compose :: (Function f, Function g, ...) -> Function f ∘ g ∘ ...`

---

#### description
Returns a function which composes its given parameter functions **right to left**. [Function composition](https://en.wikipedia.org/wiki/Function_composition) is at the heart of functional programming, and that is why it is why one of **conductor**'s most important functions.

But that is not all! `compose` also has magic powers: it will compose _synchronous_ functions, _asynchronous_ functions or even a mix of both! It will accept as many arguments as the rightmost function does, and have the same [arity](https://en.wikipedia.org/wiki/Arity).

#### examples
###### basic example
```js
import {compose} from '@waldojeffers/conductor'

const times2 = x => 2 * x
const minus3 = x => x - 3

compose(minus3, times2)(5) // 10 === (2 * 5) - 3
```