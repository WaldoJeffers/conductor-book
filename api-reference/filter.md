# filter

### `filter :: (Collection collection, Function predicate) -> Collection | Promise<Collection>`

## description

Iterates over a _collection_ \(`Array, Object, Map, Set`\) and returns a new collection of the same type containing only the values for which the `predicate` function evaluates to `true`.

Like many `Collection` methods in Conductor, `filter` works with **both asynchronous & synchronous** mappers. If you use a synchronous predicate function, `filter` will work like `Array.prototype.filter` and return a Collection synchronously.

```javascript
const values = [0, 1, 2, 3]
const isEven = x => x % 2 === 0
filter(isEven, values) // [0, 2]
```

If you use an _asynchronous_ mapper, `filter` will return a `Promise`, and you will need to use `await` or `Promise.prototype.then` to retrieve the new collection.

```javascript
const values = [0, 1, 2, 3]
const isEven = async x => x % 2 === 0
filter(double, values) // Promise<Pending>
await filter(double, values) // [0, 2]
```

**Important**

If you use an _asynchronous_ predicate function, all `predicate` calls will be done in **parallel**, but the input collection's **order will be preserved**.

