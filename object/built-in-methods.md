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