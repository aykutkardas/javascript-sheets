# Object Built-In Metotlar

## **Object.assign()**

Bir veya daha fazla kaynak nesneyi belirtilen bir hedef nesneye kopyalar. Hedef nesneyi döndürür.

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
  bilgiGoster: function() {
    console.log(
      `Benim adım ${this.isim}. Ben insan mıyım? ${
        this.insanMi ? "Evet" : "Hayır"
      }.`
    );
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
    value: 1
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
    value: 1
  },
  ozellik2: {
    value: 2,
    configurable: true
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
    value: 1
  },
  ozellik2: {
    value: 2,
    enumerable: true
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
    value: 1
  },
  ozellik2: {
    value: 2,
    writable: true
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
  enumerable: true
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

---

## **Object.is()**

İki değerin aynı olup olmadığını kontrol eder.

```js
Object.is("foo", "foo"); // true
Object.is(window, window); // true
Object.is("foo", "bar"); // false
Object.is([], []); // false

var foo = { a: 1 };
var bar = { a: 1 };

Object.is(foo, foo); // true
Object.is(foo, bar); // false
Object.is(null, null); // true
Object.is(0, -0); // false
Object.is(-0, -0); // true
Object.is(NaN, 0 / 0); // true
```

## **Object.keys()**

Nesnenin numaralandırılabilir (`enumerable`) tüm özelliklerinin isimlerini bir dizi olarak döner.

```js
const nesne = { a: 1, b: 2, c: 3 };

Object.keys(nesne);
// [ "a", "b", "c" ]
```

---

## **Object.values()**

Nesnenin numaralandırılabilir (`enumerable`) tüm özelliklerinin değerlerini bir dizi olarak döner.

```js
const nesne = { a: 1, b: 2, c: 3 };

Object.values(nesne);
// [ 1, 2, 3]
```

---

## **Object.seal()**

Verilen nesnenin tüm elemanlarını yapılandırılamaz (`configurable: false`) olarak işaretler ve nesneye yeni bir özellik eklenmesine izin vermez. Eğer özelliklerin değeri `writable: true` ise değerleri değiştirilebilir.

```js
const nesne = {
  ozellik1: 1
};

Object.seal(nesne);
nesne.ozellik1 = 2;
console.log(nesne.ozellik1);
// 2

// Object.seal ile mühürlendiği için silinemez.
delete nesne.ozellik1;
console.log(nesne.ozellik1);
// 2
```

---

## **Object.isSealed()**

Bir neslenin `Object.seal()` ile mühürlenip mühürlenmediğini kontrol eder.

```js
const nesne = {
  ozellik1: 10
};

Object.isSealed(nesne);
// false

Object.seal(nesne);

Object.isSealed(nesne);
// true
```

---

## **Object.freeze()**

Verilen nesneyi dondurur. Bir nesneyi dondurmak ona yeni değerler eklemeyi, bir değeri silmeyi veya değerin `writable`, `enumerable`, `configurable` ve `value`, gibi değerlerinin değiştirilmesini engeller.

```js
const nesne = {
  ozellik: 1
};

Object.freeze(nesne);

nesne.ozellik = 2;
// strict mod 'da hata fırlatır.

console.log(nesne.ozellik);
// 1
```

---

## **Object.isFrozen()**

Bir neslenin `Object.freeze()` ile dondurulup dondurulmadığını kontrol eder.


```js
const nesne = {
  ozellik1: 10
};

Object.isFrozen(nesne);
// false

Object.freeze(nesne);

Object.isFrozen(nesne);
// true
```

---

## **Object.preventExtensions()**

Bu yöntem bir nesneye yeni özelliklerin eklenmesini önler. Önlenen bir nesneye `Object.defineProperty` ile özellik eklenmek istediğinde hata fırlatır. Eğer bir `try catch` bloğu içine alınmazsa kod çalışmayı durdurur.

```js
const nesne = {};

Object.preventExtensions(nesne);

try {
  Object.defineProperty(nesne, 'ozellik1', {
    value: 10
  });
} catch (e) {
  console.log(e);
  // TypeError: Cannot define property property1, object is not extensible
}
```

---

## **Object.isExtensible()**

Bu yöntem bir nesneye yeni özelliklerin eklenebilir olup olmadığını kontrol eder.

```js
const nesne = {};

Object.isExtensible(nesne);
// true

Object.preventExtensions(nesne);

Object.isExtensible(nesne);
// false

```

---
