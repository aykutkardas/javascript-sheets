## **JSON.stringify()**

Bu metot bir javascript nesnesini bir JSON dizesine döndürür.

### Sözdizimi
```js
JSON.stringify(deger, degistirici?, bosluk?)
```

### Örnek

```js
const nesne = { 
  a: [1, false, "false"], 
  x: 5, 
  y: 6, 
  z: undefined 
};

JSON.stringify(nesne);
//  "{"a":[1,false,"false"],"x":5,"y":6}"

// Sadece belli özellikleri almak için bir filtreleme kullandık.
JSON.stringify(nesne, ["x", "y"]);
// "{"x":5,"y":6}"

// # Okunabilir bir çıktı için 2 boşluk girintileme kullandık.
JSON.stringify(nesne, null, 2);
/*
"{
  "a": [
    1,
    false,
    "false"
  ],
  "x": 5,
  "y": 6
}"
*/
```
---
## **JSON.parse()**

Bu metot bir dizeyi bir javascript değerine döndürür. Döndürme işleminden önce değerleri döndüştürmek için bir geribildirim `revirer` parametresi alabilir.

```js
const nesneDizesi = '{"a":1,"b":2,"c":3}';
const nesne1 = JSON.parse(nesneDizesi);

console.log(nesne1.a);
// 1

const nesne2 = JSON.parse(nesneDizesi, (ozellik, deger) => deger * 2);
console.log(nesne2.a);
// 2

```