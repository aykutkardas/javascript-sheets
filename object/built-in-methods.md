# Object Built-In Metotlar

## **Object.assign()**

Bir veya daha fazla kaynak objeyi belirtilen bir hedef objeye kopyalar. Hedef objeyi döndürür.

```js
const hedef = { a: 1, b: 2 };
const kaynak = { b: 4, c: 5 };

const dondurulenHedef = Object.assign(hedef, kaynak);
// { a: 1, b: 4, c: 5 }
```
---

## **Object.create()**

Varolan bir nesnenin prototipini, yeni oluşturulan nesne için kullanarak yeni bir nesne döndürür.

```js
const kisi = {
  insanMi: false,
  bilgiGoster: function () {
    console.log(`Benim adım ${this.isim}. Ben insan mıyım? ${this.insanMi ? 'Evet' : 'Hayır'}.`);
  }
};


const ben = Object.create(kisi);

// isim özelliği ben nesnesi için tanımlanmış 
// fakat kisi nesnesi için tanımlanmamış bir özelliktir.
ben.isim = "John"; 
ben.insanMi = true;

ben.bilgiGoster();

// Benim adım John. Ben insan mıyım? Evet.

```
---

## **Object.defineProperties()**

Nesneye birden fazla özellik ekler ya da varolan özellikleri değiştirir. Nesnenin kendisini döner.

```js
const nesne = {};

Object.defineProperties(nesne, {
  ozellik1: {
    value: 1,
  },
  ozellik2: {}
});

console.log(nesne.ozellik1);
// 1
```

**configurable:** Özellik tanımlayıcısının türü değiştirilebiliyor ya da özellik silinebiliyorsa `true` değerini kullanır. Varsayılan değeri `false` tur.

#### Örnek
```js
const nesne = {};

Object.defineProperties(nesne, {
  ozellik1: {
    value: 1,
  },
  ozellik2: {
    value: 2,
    configurable: true,
  }
});

delete nesne.ozellik1;
console.log(nesne.ozellik1);
// 1

delete nesne.ozellik2;
console.log(nesne.ozellik2);
// undefined
```

**enumerable:** Eğer `true` verilirse özelliğin numaralandırma sırasında görünmesini sağlar. Varsayılan değeri `false` tur.

#### Örnek
```js
const nesne = {};

Object.defineProperties(nesne, {
  ozellik1: {
    value: 1,
  },
  ozellik2: {
    value: 2,
    enumerable: true,
  }
});

console.log(nesne);
// { ozellik2: 2 }

console.log(nesne.ozellik1);
// 1
```

**value:** Özelliğe atanacak değer herhangi bir veri tipi olabilir. Varsayılan değeri `undefined` dır.

**writable:** Değeri `true` ise özelliğin değerini değiştirilebilir yapar. Varsayılan değeri `false` tur.


#### Örnek
```js
const nesne = {};

Object.defineProperties(nesne, {
  ozellik1: {
    value: 1,
  },
  ozellik2: {
    value: 2,
    writable: true,
  }
});

nesne.ozellik1 = 3;
console.log(nesne.ozellik1);
// 1

nesne.ozellik2 = 4;
console.log(nesne.ozellik2);
// 4
```
---

## **Object.defineProperty()**

Nesneye bir özellik ekler ya da varolan bir özelliği değiştirir. Nesnenin kendisini döner.

`Object.defineProperties` de olduğu gibi `enumerable`, `writable`, `configurable` ve `value` değerleri alır.

```js
const nesne = {};

Object.defineProperty(nesne, "ozellik1", {
    value: 1,
    enumerable: true,
});

console.log(nesne.ozellik1);
// 1
```
---

## **Object.entries()**

Nesnenin özellik ve değerlerini `[ozellik, deger]` gibi dizi şeklinde bir dizi de toplar.

```js
const nesne = { a: 1, b: 2 };

Object.entries(nesne);
// [ ["a", 1], ["b", 2] ]
```