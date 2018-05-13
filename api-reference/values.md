---
description: Get a collection's values
---

# values

```erlang
values :: Collection input => Array output
```

## description

Returns an input `Collection`'s values as an `Array`.

## example

```javascript
import { values } from 'conductor'

const words = { word1: 'Bonsoir', word2: 'Elliot' }

values(words) // ['Bonsoir', 'Elliot']
```

