# 🦀 Rust Floating-Point Types — Kasr sonlar va kompyuter xotirasida ularning ifodalanishi

Rust dasturlash tilida kasr sonlar bilan ishlash uchun **Floating-Point Types** ishlatiladi.

Floating-point — butun va kasr qismlariga ega sonlarni ifodalash uchun mo'ljallangan ma'lumot turi.

Masalan:

```rust
let price: f64 = 19.99;
let temperature: f32 = 36.6;
let pi: f64 = 3.141592653589793;
```

Rust'da ikkita asosiy Floating-Point turi mavjud:

1. `f32` — 32-bit Floating-Point.
2. `f64` — 64-bit Floating-Point.

Ularning ikkalasi ham IEEE 754 standartiga asoslangan.

---

## 1. f32 — 32-bit Floating-Point

`f32` xotirada 32 bit, ya'ni 4 bayt joy egallaydi.

U IEEE 754 Single Precision formatidan foydalanadi.

**f32 xotira tuzilishi:**

| Qism | Bit | Vazifasi |
|---|---:|---|
| Sign | 1 bit | Sonning ishorasi |
| Exponent | 8 bit | Sonning darajasi |
| Fraction | 23 bit | Sonning kasr aniqligi |
| Jami | 32 bit | 4 bayt |

```rust
let temperature: f32 = 36.6;
let price: f32 = 19.99;
let pi: f32 = 3.1415927;
```

### f32 ning asosiy xususiyatlari

| Xususiyat | Qiymat |
|---|---|
| Xotira hajmi | 32 bit (4 bayt) |
| Sign bit | 1 bit |
| Exponent | 8 bit |
| Fraction | 23 bit |
| Decimal precision | Taxminan 6–9 raqam |
| Standart formati | IEEE 754 Single Precision |

**Eng katta musbat finite qiymati:**

```text
3.4028234663852886 × 10³⁸
```

**Eng kichik musbat normal qiymati:**

```text
1.1754943508222875 × 10⁻³⁸
```

**Eng kichik musbat subnormal qiymati:**

```text
1.401298464324817 × 10⁻⁴⁵
```

Manfiy qiymatlar uchun ham mos chegaralar mavjud.

---

## 2. f64 — 64-bit Floating-Point

`f64` xotirada 64 bit, ya'ni 8 bayt joy egallaydi.

U IEEE 754 Double Precision formatidan foydalanadi.

**f64 xotira tuzilishi:**

| Qism | Bit | Vazifasi |
|---|---:|---|
| Sign | 1 bit | Sonning ishorasi |
| Exponent | 11 bit | Sonning darajasi |
| Fraction | 52 bit | Sonning kasr aniqligi |
| Jami | 64 bit | 8 bayt |

```rust
let price: f64 = 19.99;
let pi: f64 = 3.141592653589793;
let distance: f64 = 123456.789123;
```

### f64 ning asosiy xususiyatlari

| Xususiyat | Qiymat |
|---|---|
| Xotira hajmi | 64 bit (8 bayt) |
| Sign bit | 1 bit |
| Exponent | 11 bit |
| Fraction | 52 bit |
| Decimal precision | Taxminan 15–17 raqam |
| Standart formati | IEEE 754 Double Precision |

**Eng katta musbat finite qiymati:**

```text
1.7976931348623157 × 10³⁰⁸
```

**Eng kichik musbat normal qiymati:**

```text
2.2250738585072014 × 10⁻³⁰⁸
```

**Eng kichik musbat subnormal qiymati:**

```text
4.9406564584124654 × 10⁻³²⁴
```

---

## 3. f32 va f64 — umumiy taqqoslash

| Xususiyat | f32 | f64 |
|---|---:|---:|
| Bit | 32 | 64 |
| Byte | 4 | 8 |
| Sign | 1 bit | 1 bit |
| Exponent | 8 bit | 11 bit |
| Fraction | 23 bit | 52 bit |
| Decimal precision | 6–9 raqam | 15–17 raqam |
| Standart | IEEE 754 | IEEE 754 |
| Maksimal qiymat | ≈ 3.4 × 10³⁸ | ≈ 1.8 × 10³⁰⁸ |

**Qaysi biri yaxshiroq?**

`f32` kamroq xotira sarflaydi, `f64` esa yuqoriroq aniqlik va kengroq sonlar oralig'ini taqdim etadi.

Rust'da standart Floating-Point turi — `f64`.

```rust
let number = 3.14; // f64

let another_number: f32 = 3.14;
```

---

## 4. IEEE 754 — Floating-Point qanday ishlaydi?

Kompyuter kasr sonlarni oddiy o'nlik shaklda emas, balki ikkilik ilmiy yozuvga o'xshash formatda saqlaydi.

Floating-Point uchta asosiy qismdan tashkil topadi:

1. Sign — musbat yoki manfiy ekanligi.
2. Exponent — sonning darajasi.
3. Fraction — sonning ahamiyatli raqamlari.

Umumiy ko'rinishi:

```text
(-1)^sign × significand × 2^exponent
```

Masalan, 5.75 sonini ikkilik ko'rinishda ifodalaymiz:

```text
5.75 = 101.11₂
```

Normalizatsiya qilingan ko'rinishi:

```text
1.0111 × 2²
```

Bu yerda:

- Sign = 0 (musbat).
- Exponent = 2.
- Significand = 1.0111.

Kompyuter shu qismlar orqali sonni xotirada ifodalaydi.

**Eslatma:** IEEE 754 formatida exponent maydoni bias bilan kodlanadi. `f32` uchun bias 127, `f64` uchun esa 1023.

---

## 5. Floating-Point Precision — Aniqlik

Floating-Point sonlar cheksiz aniqlikka ega emas.

Masalan, `f32` taxminan 6–9 ta, `f64` esa 15–17 ta o'nlik raqam aniqligini ta'minlaydi.

```rust
fn main() {
    let a: f32 = 1.2345678;
    let b: f64 = 1.2345678901234567;

    println!("{a:.10}");
    println!("{b:.17}");
}
```

Aniqlik sonning butun va kasr qismlaridagi muhim raqamlarning umumiy soniga bog'liq.

---

## 6. Floating-Point Rounding Error

Floating-Point bilan ishlashda eng muhim muammolardan biri — Rounding Error.

Sababi: ayrim o'nlik kasr sonlarni ikkilik sanoq sistemasida aniq ifodalab bo'lmaydi.

Masalan:

```rust
fn main() {
    let a: f64 = 0.1;
    let b: f64 = 0.2;

    println!("{}", a + b);
}
```

Natija ko'pincha:

```text
0.30000000000000004
```

Nega `0.3` emas?

Chunki `0.1` va `0.2` ikkilik Floating-Point formatida aniq ifodalanmaydi. Ular eng yaqin mavjud qiymatga yaxlitlanadi.

Shuning uchun natijada kichik farq paydo bo'ladi.

**To'g'ri yondashuv:**

```rust
let a: f64 = 0.1;
let b: f64 = 0.2;

let result = a + b;

if (result - 0.3).abs() < 0.000001 {
    println!("Values are approximately equal");
}
```

Floating-Point qiymatlarni ko'pincha `==` orqali to'g'ridan-to'g'ri taqqoslash tavsiya etilmaydi.

---

## 7. Special Floating-Point Values

IEEE 754 standartida oddiy sonlardan tashqari maxsus qiymatlar ham mavjud.

### 7.1. Infinity

Infinity — cheksizlikni ifodalaydi.

Ikki ko'rinishi mavjud:

- Positive Infinity: `f64::INFINITY`
- Negative Infinity: `f64::NEG_INFINITY`

```rust
let positive = f64::INFINITY;
let negative = f64::NEG_INFINITY;

println!("{positive}");
println!("{negative}");
```

### 7.2. NaN — Not a Number

`NaN` matematik jihatdan aniqlanmagan yoki haqiqiy son bo'lmagan natijani ifodalaydi.

```rust
let result = f64::NAN;

println!("{result}");
```

Masalan:

```rust
let result = 0.0 / 0.0;

println!("{result}");
```

Muhim: `NaN` boshqa `NaN` qiymatiga ham teng emas.

```rust
let value = f64::NAN;

println!("{}", value == value); // false
println!("{}", value.is_nan()); // true
```

### 7.3. Positive Zero va Negative Zero

IEEE 754 da musbat va manfiy nol mavjud.

```rust
let positive_zero: f64 = 0.0;
let negative_zero: f64 = -0.0;

println!("{positive_zero}");
println!("{negative_zero}");
```

Ular `==` orqali teng hisoblanadi, lekin ayrim matematik operatsiyalarda farq qilishi mumkin.

---

## 8. Floating-Point Overflow va Underflow

Floating-Point ham o'zining ifodalay oladigan chegaralariga ega.

### 8.1. Overflow

Son maksimal finite qiymatdan oshib ketsa, Infinity paydo bo'lishi mumkin.

```rust
let number = f64::MAX;

let result = number * 2.0;

println!("{result}"); // inf
```

### 8.2. Underflow

Juda kichik son ifodalash chegarasidan pastga tushganda, subnormal qiymatga yoki nolga aylanishi mumkin.

```rust
let number = f64::MIN_POSITIVE;

let result = number / 2.0;

println!("{result}");
```

Bu yerda `MIN_POSITIVE` eng kichik musbat normal qiymatni anglatadi. Undan kichik musbat subnormal qiymatlar ham mavjud.

---

## 9. Floating-Point bilan ishlash metodlari

Rust'da Floating-Point qiymatlarini boshqarish uchun ko'plab metodlar mavjud.

```rust
fn main() {
    let number: f64 = -12.75;

    println!("{}", number.abs());       // 12.75
    println!("{}", number.floor());     // -13
    println!("{}", number.ceil());      // -12
    println!("{}", number.round());     // -13
    println!("{}", number.trunc());     // -12
    println!("{}", number.sqrt());      // Kvadrat ildiz
    println!("{}", number.is_finite()); // true
    println!("{}", number.is_nan());    // false
}
```

Ko'p ishlatiladigan metodlar:

| Method | Vazifasi |
|---|---|
| `abs()` | Absolyut qiymat |
| `floor()` | Pastga yaxlitlash |
| `ceil()` | Yuqoriga yaxlitlash |
| `round()` | Eng yaqin butun songa yaxlitlash |
| `trunc()` | Kasr qismini olib tashlash |
| `fract()` | Kasr qismini olish |
| `sqrt()` | Kvadrat ildiz |
| `powf()` | Darajaga oshirish |
| `is_finite()` | Chekli son ekanligini tekshirish |
| `is_infinite()` | Infinity ekanligini tekshirish |
| `is_nan()` | NaN ekanligini tekshirish |

---

## 10. Floating-Point va Financial Calculations

Pul bilan ishlashda `f32` yoki `f64` dan foydalanish har doim ham to'g'ri emas.

Masalan:

```rust
let price: f64 = 0.1;
let quantity: f64 = 3.0;

let total = price * quantity;
```

Floating-Point yaxlitlash xatolari moliyaviy hisob-kitoblarda muammo tug'dirishi mumkin.

Shuning uchun pul qiymatlarini ko'pincha eng kichik birlikda integer orqali saqlash tavsiya etiladi.

Masalan, dollar sentlarda:

```rust
let price_in_cents: u64 = 1999;
let quantity: u32 = 3;

let total = price_in_cents * quantity as u64;

println!("{total} cents"); // 5997 cents
```

Yoki maxsus decimal kutubxonalardan foydalanish mumkin.

---

## 11. Qaysi Floating-Point Type'dan foydalanish kerak?

| Vazifa | Tavsiya |
|---|---|
| Oddiy matematik hisob-kitoblar | `f64` |
| Ilmiy hisoblashlar | `f64` |
| Grafik va 3D hisoblashlar | `f32` yoki `f64` |
| Sensor ma'lumotlari | `f32` yoki `f64` |
| Machine Learning | Vazifaga qarab `f32` yoki `f64` |
| Moliyaviy hisob-kitoblar | Integer yoki Decimal |
| Juda katta sonlar diapazoni | `f64` |

**Muhim:** `f64` har doim `f32` dan yaxshi degani emas. Xotira, tezlik, aniqlik va platforma talablariga qarab tanlanadi.

---

## 12. Amaliy mashqlar

Quyidagi kodni yozib, ishga tushirib ko'ring:

```rust
fn main() {
    let a: f32 = 3.14;
    let b: f64 = 3.141592653589793;

    println!("f32: {a:.10}");
    println!("f64: {b:.17}");

    let x: f64 = 0.1;
    let y: f64 = 0.2;

    println!("Sum: {}", x + y);

    let infinity = f64::INFINITY;
    let nan = f64::NAN;

    println!("Infinity: {}", infinity.is_infinite());
    println!("NaN: {}", nan.is_nan());
}
```

**Topshiriqlar:**

1. `f32` va `f64` orasidagi farqni tushuntiring.
2. Har ikkala turda `1.0 / 3.0` ni hisoblang.
3. `0.1 + 0.2` natijasini tekshiring.
4. `f64::MAX` qiymatini ikki baravar oshirib ko'ring.
5. `NaN` nima uchun o'ziga teng emasligini tushuntiring.
6. `floor()`, `ceil()` va `round()` metodlarini sinab ko'ring.
7. Nima uchun moliyaviy hisob-kitoblarda Floating-Point o'rniga integer yoki Decimal ishlatilishi mumkinligini tushuntiring.

---

## Xulosa

Rust'da ikkita asosiy Floating-Point turi mavjud:

**f32:**
- 32 bit.
- 4 bayt.
- 6–9 ta o'nlik raqam aniqligi.
- IEEE 754 Single Precision.

**f64:**
- 64 bit.
- 8 bayt.
- 15–17 ta o'nlik raqam aniqligi.
- IEEE 754 Double Precision.

Floating-Point turlarini tushunish — matematika, ilmiy hisoblashlar, embedded systems, graphics programming va backend engineering uchun muhim.

**Esda tuting:** Floating-Point sonlar haqiqiy sonlarning barchasini aniq ifodalay olmaydi. Ular cheklangan aniqlikdagi ikkilik yaqinlashuvlardir.

---

📚 **GitHub Materials:**
https://github.com/rustlangclub/learning-rust

📢 **Telegram Channel:**
https://t.me/RustLangClub

💬 **Telegram Community:**
https://t.me/RustLangClubChat

**RustLangClub — Learn. Understand. Build.** 🦀