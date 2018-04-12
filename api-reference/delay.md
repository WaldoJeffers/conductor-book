---
description: 'delay :: (Number duration, Any value) -> Promise.resolve(value)'
---

# delay

## description

Returns a `Promise` resolving to the output value \(passed as the second argument\) after the desired delay \(passed as the first argument\). It is particularly useful when it is used in its partially applied form in a composition chain.

## examples

### basic example

```javascript
import { delay } from '@waldojeffers/conductor'

await delay(1000, 'hello') // 'hello world'
```

### partially applied form

```javascript
import { compose, delay } from '@waldojeffers/conductor'

const add1 = x => x + 1
await compose(delay(500), add1)(2) // 3
```

