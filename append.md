# append

###### `append :: (Any item, Array array) -> Array [...array, item]`

---

#### description
Add an item at the **end** of an array. `append` is a *pure function* and will return a new array, without modifying the original array. Like many functions in **conductor**, `append` is curried.

#### example
```js
import { append } from '@waldojeffers/conductor'

append('world', ['hello']) // ['hello', 'world']
append('world')(['hello']) // ['hello', 'world']
```