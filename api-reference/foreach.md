---
description: Call a function for each item of a collection
---

# forEach

**`forEach :: (Function callback, Collection collection) -> undefined`**

## description

Iterates over a collection and calls the provided callback function for each item in the collection. The callback function should have the following signature:

`(Any value, Any key, Collection collection) -> Any`

where: 

* **value** is the current item's value
* **key** is the item's key or index \(depending on if the collection is an `Array`, a `Set`, an `Object`, or a `Map`\).
* **collection** is the collection being iterated on.

{% hint style="info" %}
If the collection is a `Set`, the **value** and the **key** will be equal.
{% endhint %}

## examples

#### basic example

```javascript
import { forEach } from 'conductor'

const numbers = [3, 1, 4]
const log = x => console.log(x)
forEach(numbers, log)
// 3
// 1
// 4
```

