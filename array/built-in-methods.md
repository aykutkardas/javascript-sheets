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
> IE12 den itibaren desteklenir. Tarayıcı destekleri için: [Caniuse - Array.copyWithin](https://caniuse.com/#feat=mdn-javascript_builtins_array_copywithin)

Aynı dizinin içerisinde kopyalama yapmak için kullanılır. Dizinin uzunluğu değişmez. Dizinin kendisini değiştirir ve değişen diziyi döndürür.

Üç parametre alır.

- İlki yapıştırmaya başlanacak indis. Negatif değer verilirse sondan saymaya başlar.

- İkincisi kopyalamanın başlayacağı indis. Değer verilmezse 0 kabul edilir. *(Opsiyonel)*
 
- Üçüncüsü kopyalamanın sonlanacağı indis. Değer verilmezse dizinin son indisini alır. *(Opsiyonel)*

```js
[1, 2, 3, 4, 5].copyWithin(-2);
// [1, 2, 3, 1, 2]

[1, 2, 3, 4, 5].copyWithin(0, 3, 4);
// [4, 2, 3, 4, 5]
```
---
## **Array.prototype.entries()**
> IE12 den itibaren desteklenir. Tarayıcı destekleri için: [Caniuse - Array.entries](https://caniuse.com/#feat=mdn-javascript_builtins_array_entries)

Dizideki her eleman için indis ve değer çiftini içeren bir Array Iterator nesnesi döndürür.

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
> IE12 den itibaren desteklenir. Tarayıcı destekleri için: [Caniuse - Array.fill](https://caniuse.com/#feat=mdn-javascript_builtins_array_fill)

Bir dizinin belirtilen elemanlarının verilen bir değer ile doldurmayı sağlar. Dizinin kendisini değiştirir ve değişen diziyi return eder.

Üç parametre alır.

- İlki doldurulacak değerdir.

- İkinci parametre doldurmanın başlayacağı indisdir. Değer verilmezse 0 değerini alır. *(Opsiyonel)*

- Üçüncü parametre doldurmanın biteceği indistir. Değer verilmezse dizin uzunluğunu alır. *(Opsiyonel)*

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
