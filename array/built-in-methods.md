# Array Built-In Metotlar

## **Array.from()**
> ES6 ile birlikte gelmiştir.

Bir dizi veya yinelenebilir nesneden yüzeysel bir Array örneği oluşturur.

Bu metod üç parametre alır.

- İlki array benzeri bir nesne. *(Map, Set, Array, String ya da length değeri içeren nesneler kullanılabilir)*

- İkincisi array benzeri nesneye uygulanacak map metodu. *(Opsiyonel)*

- Üçüncüsü ise map fonksiyonu çalıştırılırken kullanılacak **this** nesnesi değeridir. *(Opsiyonel)*

```js
Array.from("kahve");
// ["k", "a", "h", "v", "e"]

Array.from([1,2,3], n => n + n);
// [2, 4, 6]
```
---

## **Array.isArray()**
Verilen değerin bir dizi olup olmadığını kontrol eder.

Tek bir parametre alır.

```js
Array.isArray([]);
// true

Array.isArray("");
// false
```
---
## **Array.of()**
> ES6 ile birlikte gelmiştir.

Aldığı tüm parametrelerden bir dizi oluşturur.

```js
Array.of(7);
// [7]

Array.of(1, 2, 3);
// [1, 2, 3]
```
---
## **Array.prototype.concat()**

İki veya daha fazla diziyi birleştirir. Mevcut dizileri değiştirmez, yeni bir dizi döndürür.

```js
const arr1 = [1, 2, 3];
const arr2 = ["a", "b", "c"];

arr1.concat(arr2);
// [1, 2, 3, "a", "b", "c"]
```
---
## **Array.prototype.copyWithin()**
> IE12 den itibaren desteklenir. Tarayıcı destekleri için: [Caniuse - copyWithin](https://caniuse.com/#feat=mdn-javascript_builtins_array_copywithin)

Aynı dizinin içerisinde kopyalama yapmak için kullanılır. Dizinin uzunluğu değişmez. Dizinin kendisini değiştirir ve değişen diziyi döndürür.

Üç parametre alır.

- İlki yapıştırmaya başlanacak indeks. Negatif değer verilirse sondan saymaya başlar.

- İkincisi kopyalamanın başlayacağı indeks. Değer verilmezse 0 kabul edilir. *(Opsiyonel)*
 
- Üçüncüsü kopyalamanın sonlanacağı indeks. Değer verilmezse dizinin son indeksini alır. *(Opsiyonel)*

```js
[1, 2, 3, 4, 5].copyWithin(-2);
// [1, 2, 3, 1, 2]

[1, 2, 3, 4, 5].copyWithin(0, 3, 4);
// [4, 2, 3, 4, 5]
```
---
## **Array.prototype.entries()**
> IE12 den itibaren desteklenir. Tarayıcı destekleri için: [Caniuse - entries](https://caniuse.com/#feat=mdn-javascript_builtins_array_entries)

Dizideki her eleman için indeks ve değer çiftini içeren bir Array Iterator nesnesi döndürür.

```js
const arr = ["a", "b"];
const iterator = arr.entries();

iterator.next().value;
// [0, "a"]

iterator.next().value;
// [1, "b"]
```
---
## **Array.prototype.every()**

Dizide ki tüm elemanların uygulanan koşulu sağlayıp sağlamadığını kontrol etmeyi sağlar. Boolean bir değer döndürür.

```js
const arr = [1, 2, 3, 4, 5];

arr.every(item => item < 10);
// true

arr.every(item => item < 3);
// false
```
---
## **Array.prototype.fill()**
> IE12 den itibaren desteklenir. Tarayıcı destekleri için: [Caniuse - fill](https://caniuse.com/#feat=mdn-javascript_builtins_array_fill)

Bir dizinin belirtilen elemanlarının verilen bir değer ile doldurmayı sağlar. Dizinin kendisini değiştirir ve değişen diziyi return eder.

Üç parametre alır.

- İlki doldurulacak değerdir.

- İkinci parametre doldurmanın başlayacağı indeks. Değer verilmezse 0 değerini alır. *(Opsiyonel)*

- Üçüncü parametre doldurmanın biteceği indeks. Değer verilmezse dizin uzunluğunu alır. *(Opsiyonel)*

```js 
[1, 2, 3, 4, 5].fill(0);
// [0, 0, 0, 0, 0]

[1, 2, 3, 4, 5].fill(0, 2, 4);
// [1, 2, 0, 0, 5]
```
---
## **Array.prototype.filter()**

Verilen koşulu sağlayan tüm dizi elemanlarından yeni bir dizi oluşturur. Dizinin kendisini değiştirmez.

### **Sözdizimi**
```
arr.filter((item, index, array) => { ... });
```

### **Örnek**
```js
[1, 2, 3, 4, 5].filter(n => n < 3);
// [1, 2]

[1, 2, 3, 4, 5].filter(n => n > 5);
// []
```
---
## **Array.prototype.find()**
> IE12 den itibaren desteklenir. Tarayıcı destekleri için: [Caniuse - find](https://caniuse.com/#feat=array-findl)

Verilen koşulu sağlayan ilk dizi elemanını döndürür.

### **Sözdizimi**
```
arr.find((item, index, array) => { ... });
```

### **Örnek**
```js
[1, 2, 3, 4, 5].find(n => n > 3);
// 4

[1, 2, 3, 4, 5].find(n => n > 5);
// undefined
```
---
## **Array.prototype.findIndex()**
> IE12 den itibaren desteklenir. Tarayıcı destekleri için: [Caniuse - findIndex](https://caniuse.com/#feat=mdn-javascript_builtins_array_findindex)

Verilen koşulu sağlayan ilk dizi elemanının indeksini döndürür.

### **Sözdizimi**
```
arr.findIndex((item, index, array) => { ... });
```

### **Örnek**
```js
[1, 2, 3, 4, 5].findIndex(n => n > 3);
// 3

[1, 2, 3, 4, 5].findIndex(n => n > 5);
// -1
```
---
## **Array.prototype.forEach()**
Verilen işlevi dizinin her bir elemanı için bir kez çalıştırır. Mevcut diziyi değiştirmez ve geriye yeni bir dizi döndürmez.

### **Sözdizimi**
```
arr.forEach((item, index, array) => { ... });
```

### **Örnek**
```js
[1, 2, 3].forEach(n => { console.log(n) });
// > 1
// > 2
// > 3
```
---
## **Array.prototype.inculdes()**
> Tarayıcı destekleri için: [Caniuse - includes](https://caniuse.com/#feat=array-includes)

Dizinin belirtilen elemanı içerip içermediğini verir. 

### **Sözdizimi**
```
arr.includes(value);
```

### **Örnek**
```js
[1, 2, 3].includes(2);
// true

[1, 2, 3].includes(4);
// false
```
---
## **Array.prototype.indexOf()**

Belirtilen elemanın dizide bulunduğu ilk konumun indeksini verir. Eğer aranan elemanı dizide bulamazsa **-1** değerini döndürür.

### **Sözdizimi**
```
arr.indexOf(value);
```

### **Örnek**
```js
[1, 2, 3].indexOf(3);
// 2

[1, 2, 3].indexOf(4);
// -1
```
---
## **Array.prototype.lastIndexOf()**

Belirtilen elemanın dizide bulunduğu son konumun indeksini verir. Eğer aranan elemanı dizide bulamazsa **-1** değerini döndürür.

### **Sözdizimi**
```
arr.lastIndexOf(value);
```

### **Örnek**
```js
[1, 2, 3, 1].lastIndexOf(1);
// 3

[1, 2, 3, 1].lastIndexOf(4);
// -1
```
---
## **Array.prototype.map()**

Dizideki her eleman için çağrılan işlevi çalıştırır ve sonuçlarından yeni bir dizi döner. Mevcut diziyi değiştirmez.

### **Sözdizimi**
```
arr.map((item, index) => { ... });
```

### **Örnek**
```js
[1, 2, 3].map(n => n + n);
// [2, 4, 6]

["a", "b", "c"].map((item, index) => index + item);
// ["0a", "1b", "2c"]
```
---
## **Array.prototype.join()**

Dizideki tüm elemanları virgül ile birleştirerek yeni bir dize döndürür. Özel bir ayırıcı da tanımlanabilir.

### **Sözdizimi**
```
arr.join(separator?);
```

### **Örnek**
```js
[1, 2, 3].join();
// "1,2,3"

[1, 2, 3].join("-");
// "1-2-3"

[1].join();
// "1"
```
---
## **Array.prototype.push()**

Dizinin sonuna bir veya daha fazla eleman ekler. Dizinin yeni uzunluğunu döndürür.

### **Sözdizimi**
```
arr.push(eleman1, elaman2, ...elemanN);
```

### **Örnek**
```js
const arr = [];

arr.push("a");
// 1

console.log(arr);
// ["a"]

arr.push("b", "c");
// 3

console.log(arr);
// ["a", "b", "c"]
```
---
## **Array.prototype.pop()**

Dizinin sonundan bir eleman çıkarır ve çıkardığı elamanı döndürür.

### **Sözdizimi**
```
arr.pop();
```

### **Örnek**
```js
const arr = ["a", "b", "c"];

arr.pop();
// "c"

console.log(arr);
// ["a", "b"]

arr.pop();
// "b"

console.log(arr);
// ["a"]
```
---
## **Array.prototype.shift()**

Dizinin başından bir eleman çıkarır ve çıkardığı elamanı döndürür.

### **Sözdizimi**
```
arr.shift();
```

### **Örnek**
```js
const arr = ["a", "b", "c"];

arr.shift();
// "a"

console.log(arr);
// ["b", "c"]

arr.shift();
// "b"

console.log(arr);
// ["c"]
```
---
## **Array.prototype.unshift()**

Dizinin başına bir veya daha fazla eleman ekler. Dizinin yeni uzunluğunu döndürür.

### **Sözdizimi**
```
arr.unshift(eleman1, elaman2, ...elemanN);
```

### **Örnek**
```js
const arr = ["a", "b", "c"];

arr.unshift("d");
// 4

console.log(arr);
// ["d", "a", "b", "c"]

arr.unshift("e", "f");
// 6

console.log(arr);
// ["e", "f", "d", "a", "b", "c"]
```
---
## **Array.prototype.reduce()**

Dizinin her öğesinde *reducer* bir işlev uygulayarak tek bir çıktı döndürür. 

### **Sözdizimi**
```
arr.reduce((birikenDeger, mevcutDeger) => { ... }, baslangicDegeri?);
```

### **Örnek**
```js
const arr = [1, 2, 3];

arr.reduce((total, current) => total + current); // 1 + 2 + 3
// 6

arr.reduce((total, current) => total + current, 4); // 4 + 1 + 2 + 3
// 10
```
---
## **Array.prototype.reduceRight()**

Sondan başlayarak dizinin her öğesinde *reducer* bir işlev uygulayarak tek bir çıktı döndürür. 

### **Sözdizimi**
```
arr.reduceRight((birikenDeger, mevcutDeger) => { ... }, baslangicDegeri?);
```

### **Örnek**
```js
const arr = [1, 2, 3];

arr.reduceRight((total, current) => total + current); // 3 + 2 + 1
// 6

arr.reduceRight((total, current) => total + current, 4); // 4 + 3 + 2 + 1
// 10
```
---