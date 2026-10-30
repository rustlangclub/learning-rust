# 🦀 Rust’da `char` — Character Type

Rust dasturlash tilida `char` — bitta Unicode belgini ifodalash uchun ishlatiladigan primitive data type.

Masalan:

```rust
let letter: char = 'A';
let number: char = '7';
let symbol: char = '★';
let emoji: char = '🦀';
let uzbek: char = 'o';
```

Bu qiymatlarning barchasi `char` turiga kiradi.

Lekin Rust’dagi `char` oddiy ASCII belgilar bilangina cheklanmaydi. U Unicode standartidagi belgilarni ham ifodalay oladi.

## 1. `char` qanday yoziladi?

`char` qiymatlari **bitta tirnoq** (`' '`) ichida yoziladi.

```rust
let a: char = 'A';
let b: char = 'B';
let c: char = '1';
let d: char = '?';
```

E'tibor bering:

```rust
let a: char = 'A';  // To'g'ri
let b: char = "A";  // Xato
```

Sababi:

- `'A'` — `char`.
- `"A"` — string literal, ya'ni `&str`.

Rust’da `char` va `&str` bir-biridan farq qiladi.

## 2. `char` xotirada qancha joy egallaydi?

Rust’da `char` turi har doim **4 bayt (32 bit)** xotira egallaydi.

```rust
use std::mem::size_of;

fn main() {
    println!("{}", size_of::<char>());
}
```

Natija:

```text
4
```

Nima uchun 4 bayt?

Chunki Rust `char` turini Unicode Scalar Value sifatida saqlaydi. Unicode belgilarini ifodalash uchun 32 bitlik qiymat ishlatiladi.

Muhim: bu `char` ning xotiradagi hajmi. UTF-8 kodlashida belgining baytlar soni boshqacha bo‘lishi mumkin.

## 3. Unicode nima?

Unicode — dunyodagi turli yozuv tizimlari, belgilar va emoji uchun yagona kodlash standartidir.

Masalan:

| Belgi | Unicode |
|---|---|
| `A` | U+0041 |
| `a` | U+0061 |
| `0` | U+0030 |
| `Ж` | U+0416 |
| `ا` | U+0627 |
| `★` | U+2605 |
| `🦀` | U+1F980 |

Rust `char` Unicode belgilarini ifodalay oladi:

```rust
fn main() {
    let english: char = 'A';
    let russian: char = 'Ж';
    let arabic: char = 'ا';
    let symbol: char = '★';
    let emoji: char = '🦀';

    println!("{english}");
    println!("{russian}");
    println!("{arabic}");
    println!("{symbol}");
    println!("{emoji}");
}
```

Natija:

```text
A
Ж
ا
★
🦀
```

Demak, `char` faqat ingliz alifbosidagi belgilar uchun emas.

## 4. `char` va UTF-8 o‘rtasidagi farq

Bu juda muhim mavzu.

Rust’da `char` 4 bayt bo‘lsa, `String` va `&str` matnni UTF-8 formatida saqlaydi.

UTF-8 da bitta belgi 1 dan 4 baytgacha joy egallashi mumkin.

Masalan:

| Belgi | UTF-8 hajmi |
|---|---:|
| `A` | 1 bayt |
| `Ж` | 2 bayt |
| `ا` | 2 bayt |
| `€` | 3 bayt |
| `🦀` | 4 bayt |

Buni kod orqali tekshiramiz:

```rust
fn main() {
    let a = 'A';
    let b = 'Ж';
    let c = 'ا';
    let d = '🦀';

    println!("{}", a.len_utf8());
    println!("{}", b.len_utf8());
    println!("{}", c.len_utf8());
    println!("{}", d.len_utf8());
}
```

Natija:

```text
1
2
2
4
```

Eslab qoling:

- `size_of::<char>()` — 4 bayt.
- `char.len_utf8()` — belgining UTF-8 formatidagi hajmi.
- `String` va `&str` — UTF-8 formatidagi matn.

## 5. `char` ustida ishlash

Rust `char` bilan ishlash uchun bir nechta foydali metodlarni taqdim etadi.

### Belgini tekshirish

```rust
fn main() {
    let letter = 'A';
    let digit = '7';
    let space = ' ';

    println!("{}", letter.is_alphabetic());
    println!("{}", digit.is_numeric());
    println!("{}", space.is_whitespace());
}
```

Natija:

```text
true
true
true
```

Asosiy metodlar:

| Metod | Vazifasi |
|---|---|
| `is_alphabetic()` | Harf ekanini tekshiradi |
| `is_numeric()` | Raqamli belgi ekanini tekshiradi |
| `is_alphanumeric()` | Harf yoki raqam ekanini tekshiradi |
| `is_whitespace()` | Bo‘sh joy yoki whitespace ekanini tekshiradi |
| `is_uppercase()` | Katta harf ekanini tekshiradi |
| `is_lowercase()` | Kichik harf ekanini tekshiradi |
| `is_ascii()` | ASCII belgisi ekanini tekshiradi |
| `len_utf8()` | UTF-8 hajmini baytlarda qaytaradi |
| `to_uppercase()` | Katta harfga o‘zgartirish iteratorini qaytaradi |
| `to_lowercase()` | Kichik harfga o‘zgartirish iteratorini qaytaradi |

### Katta va kichik harflar

```rust
fn main() {
    let letter = 'a';

    println!("{}", letter.is_lowercase());
    println!("{}", letter.to_uppercase().to_string());
}
```

Natija:

```text
true
A
```

Muhim: `to_uppercase()` va `to_lowercase()` oddiy `char` emas, iterator qaytaradi. Chunki ayrim Unicode belgilarining katta yoki kichik harfga o‘tishi bir nechta belgidan iborat bo‘lishi mumkin.

## 6. `char` ni Unicode qiymatiga aylantirish

Har bir Rust `char` qiymatining Unicode kod nuqtasi mavjud.

Buni `as u32` orqali olish mumkin:

```rust
fn main() {
    let letter = 'A';
    let emoji = '🦀';

    println!("{}", letter as u32);
    println!("{}", emoji as u32);
}
```

Natija:

```text
65
129408
```

Unicode ko‘rinishida chiqarish:

```rust
fn main() {
    let letter = 'A';

    println!("U+{:04X}", letter as u32);
}
```

Natija:

```text
U+0041
```

Aksincha, Unicode qiymatidan `char` olish uchun `char::from_u32()` ishlatiladi:

```rust
fn main() {
    let code = 65;

    let character = char::from_u32(code);

    println!("{:?}", character);
}
```

Natija:

```text
Some('A')
```

Nega `Some`?

Chunki har qanday `u32` qiymati yaroqli Unicode Scalar Value emas. Shu sababli funksiya `Option<char>` qaytaradi.

## 7. `char` va `String` farqi

Bu ikki tur orasidagi farqni yaxshi tushunish kerak.

```rust
let letter: char = 'A';

let text: String = String::from("A");
```

| Xususiyat | `char` | `String` |
|---|---|---|
| Ma'nosi | Bitta Unicode Scalar Value | UTF-8 matn |
| Xotira | 4 bayt | Dinamik hajm |
| Belgilar soni | Bitta | Bir yoki bir nechta |
| O‘zgaruvchan | Qiymatni qayta tayinlash mumkin | Matnni o‘zgartirish mumkin |
| Heap | Odatda stack qiymati | Matn ma’lumoti heap’da |

Masalan:

```rust
fn main() {
    let letter: char = 'R';
    let word: String = String::from("Rust");

    println!("{letter}");
    println!("{word}");
}
```

Natija:

```text
R
Rust
```

## 8. String ichidan `char` olish

`String` UTF-8 formatida saqlanganligi sababli uning indeksiga to‘g‘ridan-to‘g‘ri murojaat qilib bo‘lmaydi.

Bunday yozish mumkin emas:

```rust
let text = String::from("Rust");

// Xato!
let first = text[0];
```

Buning o‘rniga `chars()` ishlatiladi:

```rust
fn main() {
    let text = String::from("Rust");

    for character in text.chars() {
        println!("{character}");
    }
}
```

Natija:

```text
R
u
s
t
```

Birinchi Unicode Scalar Value ni olish:

```rust
fn main() {
    let text = String::from("Rust");

    let first = text.chars().next();

    println!("{:?}", first);
}
```

Natija:

```text
Some('R')
```

Eslatma: `chars()` Unicode Scalar Value larni beradi. U har doim foydalanuvchi ko‘radigan bitta grafik belgiga (grapheme cluster) teng bo‘lavermaydi. Masalan, ayrim emoji bir nechta Unicode qiymatidan tashkil topadi.

## 9. `char` qayerlarda ishlatiladi?

`char` dasturlashda ko‘plab vazifalarni bajaradi.

**1. Belgilarni tekshirish**

```rust
fn main() {
    let input = '7';

    if input.is_numeric() {
        println!("Bu raqam!");
    }
}
```

**2. Matnni tahlil qilish**

```rust
fn main() {
    let text = "Rust Language";

    let mut count = 0;

    for character in text.chars() {
        if character.is_alphabetic() {
            count += 1;
        }
    }

    println!("Harflar soni: {count}");
}
```

**3. Parser va lexer yaratish**

Dasturlash tillari uchun parser yoki lexer yozishda belgilarni tekshirish muhim.

```rust
fn main() {
    let character = '+';

    match character {
        '+' => println!("Qo‘shish operatori"),
        '-' => println!("Ayirish operatori"),
        '*' => println!("Ko‘paytirish operatori"),
        '/' => println!("Bo‘lish operatori"),
        _ => println!("Noma'lum belgi"),
    }
}
```

**4. Input validatsiyasi**

```rust
fn main() {
    let username = "Rust123";

    let valid = username
        .chars()
        .all(|c| c.is_alphanumeric());

    println!("{valid}");
}
```

## 10. Muhim xulosa

Rust’da `char` — bitta Unicode Scalar Value ni ifodalovchi primitive type.

Esda saqlang:

1. `char` qiymatlari bitta tirnoq bilan yoziladi: `'A'`.
2. `char` xotirada 4 bayt egallaydi.
3. Rust `char` Unicode belgilarini qo‘llab-quvvatlaydi.
4. UTF-8 da belgilar 1–4 bayt bo‘lishi mumkin.
5. `String` va `&str` matnni UTF-8 formatida saqlaydi.
6. `chars()` matn ichidagi Unicode Scalar Value larni ketma-ket beradi.
7. `char` va `String` bir xil data type emas.

## 🧠 Amaliy topshiriqlar

**1-topshiriq.** Quyidagi belgilarni `char` sifatida e'lon qiling:

- `A`
- `Ж`
- `7`
- `★`
- `🦀`

**2-topshiriq.** Foydalanuvchi kiritgan belgining harf, raqam yoki bo‘sh joy ekanini aniqlaydigan dastur yozing.

**3-topshiriq.** `char` ning xotiradagi hajmini va turli belgilar UTF-8 hajmini chiqaradigan dastur yarating.

**4-topshiriq.** Berilgan `String` ichidagi barcha belgilarni alohida qatorda chiqaring.

**5-topshiriq.** Berilgan matndagi katta harflar, kichik harflar va raqamlar sonini hisoblang.

**6-topshiriq.** `char::from_u32()` yordamida Unicode qiymatidan belgi hosil qiladigan dastur yozing. Yaroqsiz qiymatni ham to‘g‘ri qayta ishlang.

---

📚 **GitHub — RustLangClub o‘quv materiallari:**

https://github.com/rustlangclub/learning-rust

📢 **Telegram kanal:** https://t.me/RustLangClub

💬 **Telegram chat:** https://t.me/RustLangClubChat