# map

###### `(collection:: Collection, mapper:: Function) -> Collection | Promise<Collection>`

Iterates over a *collection* (`Array, Object, Map, Set`) and returns a new collection of the same type containing each value from the input collection after it has been transformed by the provided *mapper* function.

Like many Collection methods in Conductor, `map` works with **both asynchronous & synchronous** mappers. If you use a synchronous mapper, `map` will work like `Array.prototype.map`, Ramda or Lodash's `map`, and return a Collection synchronously.
```js
const values = [0, 2, 4]
const double = x => 2 * x
map(double, values) // [0, 4, 8]
```
If you use an *asynchronous* mapper, `map` will return a `Promise`, and you will need to use `await` or `Promise.prototype.then` to retrieve the new collection.

```js
const values = [0, 2, 4]
const double = async x => 2 * x
map(double, values) // Promise<Pending>
await map(double, values) // [0, 4, 8]
```