# Object Built-In Metotlar

## **Object.assign()**

Bir veya daha fazla kaynak objeyi belirtilen bir hedef objeye kopyalar. Hedef objeyi döndürür.

```js
const hedef = { a: 1, b: 2 };
const kaynak = { b: 4, c: 5 };

const dondurulenHedef = Object.assign(hedef, kaynak);
// { a: 1, b: 4, c: 5 }
```
