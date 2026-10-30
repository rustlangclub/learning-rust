# 🦀 Rust Integer Types — Butun sonlar va ularning xotiradagi chegaralari

Rust dasturlash tilida butun sonlar bilan ishlash uchun **Integer Types** ishlatiladi.

Integer — kasr qismi bo'lmagan sonlarni ifodalovchi ma'lumot turi.

Masalan:

```rust
let age: i32 = 21;
let temperature: i32 = -15;
let population: u64 = 1000000;
```

Rust'da integer turlari ikki asosiy guruhga bo'linadi:

1. Signed Integers — manfiy, nol va musbat sonlar.
2. Unsigned Integers — nol va musbat sonlar.

Har bir integer turi ma'lum miqdordagi bitlardan foydalanadi. Bitlar soni esa u saqlashi mumkin bo'lgan qiymatlar oralig'ini belgilaydi.

---

## 1. Signed Integer Types

Signed Integer — manfiy va musbat butun sonlarni saqlash uchun ishlatiladi.

Rust'da 6 ta Signed Integer turi mavjud:

| Type | Hajmi | Minimal qiymat | Maksimal qiymat |
|---|---:|---:|---:|
| `i8` | 8 bit | -128 | 127 |
| `i16` | 16 bit | -32,768 | 32,767 |
| `i32` | 32 bit | -2,147,483,648 | 2,147,483,647 |
| `i64` | 64 bit | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807 |
| `i128` | 128 bit | -2¹²⁷ | 2¹²⁷ - 1 |
| `isize` | 32 yoki 64 bit | Platformaga bog'liq | Platformaga bog'liq |

### 1.1. i8 — 8 bit

`i8` 8 bit xotiradan foydalanadi, ya'ni 1 bayt.

Qiymatlar oralig'i:

- Minimum: -128
- Maximum: 127
- Jami: 256 ta turli qiymat.

```rust
let temperature: i8 = -10;
let age: i8 = 21;
let max_value: i8 = 127;
let min_value: i8 = -128;
```

`i8` kichik sonlar bilan ishlashda, masalan, ayrim sensor qiymatlari yoki ixcham ma'lumot formatlarida foydali.

### 1.2. i16 — 16 bit

`i16` 16 bit, ya'ni 2 bayt xotiradan foydalanadi.

Qiymatlar oralig'i:

- Minimum: -32,768
- Maximum: 32,767
- Jami: 65,536 ta turli qiymat.

```rust
let temperature: i16 = -1500;
let population: i16 = 30000;
let max_value: i16 = 32767;
let min_value: i16 = -32768;
```

### 1.3. i32 — 32 bit

`i32` 32 bit, ya'ni 4 bayt xotiradan foydalanadi.

Qiymatlar oralig'i:

- Minimum: -2,147,483,648
- Maximum: 2,147,483,647
- Jami: 4,294,967,296 ta turli qiymat.

```rust
let balance: i32 = -100000;
let population: i32 = 1000000;
let max_value: i32 = 2147483647;
let min_value: i32 = -2147483648;
```

**Muhim:** `i32` Rust'da butun sonlar uchun standart integer turi hisoblanadi.

Agar integer turini aniq ko'rsatmasang, Rust ko'p hollarda `i32` ni tanlaydi.

```rust
let number = 100;
```

Yuqoridagi kodda `number` turi `i32` bo'ladi.

### 1.4. i64 — 64 bit

`i64` 64 bit, ya'ni 8 bayt xotiradan foydalanadi.

Qiymatlar oralig'i:

- Minimum: -9,223,372,036,854,775,808
- Maximum: 9,223,372,036,854,775,807
- Jami: 18,446,744,073,709,551,616 ta turli qiymat.

```rust
let population: i64 = 8000000000;
let distance: i64 = 9000000000;
let max_value: i64 = 9223372036854775807;
let min_value: i64 = -9223372036854775808;
```

`i64` katta sonlar, hisob-kitoblar va 64-bitli identifikatorlar bilan ishlashda foydali.

### 1.5. i128 — 128 bit

`i128` 128 bit, ya'ni 16 bayt xotiradan foydalanadi.

Qiymatlar oralig'i:

- Minimum: -2¹²⁷
- Maximum: 2¹²⁷ - 1
- Jami: 2¹²⁸ ta turli qiymat.

Aniq chegaralari:

- Minimum: -170,141,183,460,469,231,731,687,303,715,884,105,728
- Maximum: 170,141,183,460,469,231,731,687,303,715,884,105,727

```rust
let huge_number: i128 = 170141183460469231731687303715884105727;
let negative_number: i128 = -170141183460469231731687303715884105728;
```

`i128` juda katta butun sonlarni saqlash uchun ishlatiladi.

### 1.6. isize — Platformaga bog'liq integer

`isize` hajmi ishlayotgan platformaning pointer hajmiga bog'liq.

- 32-bit platformada: 32 bit (4 bayt).
- 64-bit platformada: 64 bit (8 bayt).

Qiymatlar oralig'i:

| Platforma | Minimum | Maximum |
|---|---:|---:|
| 32-bit | -2,147,483,648 | 2,147,483,647 |
| 64-bit | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807 |

```rust
let number: isize = -100;
let another_number: isize = 500;
```

`isize` pointer hajmiga mos keladigan signed integer hisoblanadi.

---

## 2. Unsigned Integer Types

Unsigned Integer faqat nol va musbat sonlarni saqlaydi.

Rust'da 6 ta Unsigned Integer turi mavjud:

| Type | Hajmi | Minimal qiymat | Maksimal qiymat |
|---|---:|---:|---:|
| `u8` | 8 bit | 0 | 255 |
| `u16` | 16 bit | 0 | 65,535 |
| `u32` | 32 bit | 0 | 4,294,967,295 |
| `u64` | 64 bit | 0 | 18,446,744,073,709,551,615 |
| `u128` | 128 bit | 0 | 2¹²⁸ - 1 |
| `usize` | 32 yoki 64 bit | 0 | Platformaga bog'liq |

### 2.1. u8 — 8 bit

- Hajmi: 1 bayt.
- Minimum: 0.
- Maximum: 255.
- Jami: 256 ta turli qiymat.

```rust
let age: u8 = 21;
let percentage: u8 = 100;
let max_value: u8 = 255;
let min_value: u8 = 0;
```

`u8` odatda rang qiymatlari, kichik hisoblagichlar va byte ma'lumotlari bilan ishlashda qo'llaniladi.

### 2.2. u16 — 16 bit

- Hajmi: 2 bayt.
- Minimum: 0.
- Maximum: 65,535.
- Jami: 65,536 ta turli qiymat.

```rust
let port: u16 = 8080;
let number: u16 = 50000;
let max_value: u16 = 65535;
```

### 2.3. u32 — 32 bit

- Hajmi: 4 bayt.
- Minimum: 0.
- Maximum: 4,294,967,295.
- Jami: 4,294,967,296 ta turli qiymat.

```rust
let population: u32 = 1000000;
let timestamp: u32 = 1700000000;
let max_value: u32 = 4294967295;
```

### 2.4. u64 — 64 bit

- Hajmi: 8 bayt.
- Minimum: 0.
- Maximum: 18,446,744,073,709,551,615.
- Jami: 18,446,744,073,709,551,616 ta turli qiymat.

```rust
let user_id: u64 = 9000000000;
let max_value: u64 = 18446744073709551615;
```

### 2.5. u128 — 128 bit

- Hajmi: 16 bayt.
- Minimum: 0.
- Maximum: 2¹²⁸ - 1.
- Jami: 2¹²⁸ ta turli qiymat.

Maksimal qiymati:

340,282,366,920,938,463,463,374,607,431,768,211,455

```rust
let huge_number: u128 =
    340282366920938463463374607431768211455;
```

`u128` juda katta musbat butun sonlar bilan ishlashda qo'llaniladi.

### 2.6. usize — Platformaga bog'liq Unsigned Integer

`usize` ham pointer hajmiga bog'liq.

| Platforma | Hajmi | Minimum | Maximum |
|---|---:|---:|---:|
| 32-bit | 32 bit | 0 | 4,294,967,295 |
| 64-bit | 64 bit | 0 | 18,446,744,073,709,551,615 |

```rust
let index: usize = 10;

let numbers = [10, 20, 30];

let first = numbers[index - 10];
```

`usize` Rust'da array indekslari, collection uzunliklari va xotira hajmlari bilan ishlashda juda muhim.

---

## 3. Integer Types — umumiy taqqoslash

Barcha integer turlarini bitta jadvalda ko'rib chiqamiz.

| Type | Bit | Byte | Signed / Unsigned |
|---|---:|---:|---|
| `i8` | 8 | 1 | Signed |
| `i16` | 16 | 2 | Signed |
| `i32` | 32 | 4 | Signed |
| `i64` | 64 | 8 | Signed |
| `i128` | 128 | 16 | Signed |
| `isize` | 32 / 64 | 4 / 8 | Signed |
| `u8` | 8 | 1 | Unsigned |
| `u16` | 16 | 2 | Unsigned |
| `u32` | 32 | 4 | Unsigned |
| `u64` | 64 | 8 | Unsigned |
| `u128` | 128 | 16 | Unsigned |
| `usize` | 32 / 64 | 4 / 8 | Unsigned |

**Xotira hisoblash:**

8 bit = 1 byte

16 bit = 2 byte

32 bit = 4 byte

64 bit = 8 byte

128 bit = 16 byte

---

## 4. Integer qiymatlari qanday hisoblanadi?

Integer turlarining qiymat oralig'i bitlar soniga qarab aniqlanadi.

**Signed Integer formulasi:**

\[
-2^{n-1} \quad \text{dan} \quad 2^{n-1}-1
\]

**Unsigned Integer formulasi:**

\[
0 \quad \text{dan} \quad 2^n-1
\]

Bu yerda `n` — bitlar soni.

Masalan, `i8` uchun:

\[
-2^7 = -128
\]

\[
2^7-1 = 127
\]

`u8` uchun:

\[
2^8-1 = 255
\]

Nima uchun `i8` -128 dan 127 gacha, `u8` esa 0 dan 255 gacha?

Chunki signed integer manfiy qiymatlarni ham ifodalashi kerak. Rust'da signed integerlar two's complement usulidan foydalanadi.

---

## 5. Integer Overflow nima?

Overflow — integer o'z turi qabul qila oladigan maksimal yoki minimal chegaradan chiqib ketishi.

Masalan, `u8` maksimal qiymati 255:

```rust
let number: u8 = 255;

// let result = number + 1;
```

Agar `255 + 1` hisoblasak, `u8` bu qiymatni oddiy ko'rinishda saqlay olmaydi.

Rust'da overflow bilan ishlashning bir nechta usuli mavjud.

### 5.1. checked_add()

Overflow yuz bersa, `None` qaytaradi.

```rust
let number: u8 = 255;

let result = number.checked_add(1);

println!("{result:?}"); // None
```

### 5.2. wrapping_add()

Qiymat chegaradan o'tsa, aylanish orqali davom etadi.

```rust
let number: u8 = 255;

let result = number.wrapping_add(1);

println!("{result}"); // 0
```

### 5.3. saturating_add()

Maksimal qiymatdan oshib ketganda maksimal qiymatni saqlaydi.

```rust
let number: u8 = 255;

let result = number.saturating_add(1);

println!("{result}"); // 255
```

### 5.4. overflowing_add()

Natija va overflow yuz berganini bildiruvchi `bool` qaytaradi.

```rust
let number: u8 = 255;

let (result, overflowed) = number.overflowing_add(1);

println!("{result}");    // 0
println!("{overflowed}"); // true
```

**Eslatma:** Oddiy integer arifmetikasida overflow debug build'da odatda panic keltirib chiqaradi, release build'da esa odatda wrapping xatti-harakatiga ega. Aniq xatti-harakat kerak bo'lsa, yuqoridagi metodlardan foydalanish ma'qul.

---

## 6. Integer Literals

Rust'da integer qiymatlarini bir nechta ko'rinishda yozish mumkin.

```rust
let decimal = 100;       // O'nlik
let hexadecimal = 0x64;  // O'n oltilik
let octal = 0o144;       // Sakkizlik
let binary = 0b01100100; // Ikkilik
let byte = b'A';         // Byte literal
```

Bu qiymatlarning barchasi 100 ga teng, `byte` esa `u8` turidagi 65 qiymatidir.

Katta sonlarni o'qish oson bo'lishi uchun `_` ishlatish mumkin:

```rust
let million = 1_000_000;
let billion = 1_000_000_000;
```

Type suffix ham yozish mumkin:

```rust
let number = 100_i32;
let count = 200_u64;
```

---

## 7. Qaysi Integer Type'dan foydalanish kerak?

Har doim eng katta integer turidan foydalanish to'g'ri emas.

Kerakli type ma'lumotning xususiyatiga qarab tanlanadi.

| Vazifa | Tavsiya etiladigan Type |
|---|---|
| Kichik byte qiymatlari | `u8` |
| Ranglar (RGB) | `u8` |
| Yosh | `u8` yoki `u32` |
| Port raqami | `u16` |
| Oddiy hisoblagich | `u32` yoki `usize` |
| Array indeksi | `usize` |
| Katta ID | `u64` |
| Juda katta butun sonlar | `i128` yoki `u128` |
| Manfiy va musbat qiymatlar | `i32` yoki `i64` |

Rust'da ma'lumot turini tanlashda qiymatning chegarasi, xotira sarfi va boshqa tizimlar bilan mosligi hisobga olinadi.

---

## 8. Amaliy mashq

Quyidagi kodni o'zingiz yozib, ishga tushirib ko'ring:

```rust
fn main() {
    let a: i8 = 127;
    let b: u8 = 255;
    let c: i16 = 32767;
    let d: u16 = 65535;
    let e: i32 = 2147483647;
    let f: u32 = 4294967295;

    println!("i8: {a}");
    println!("u8: {b}");
    println!("i16: {c}");
    println!("u16: {d}");
    println!("i32: {e}");
    println!("u32: {f}");
}
```

**Topshiriqlar:**

1. Har bir integer turining maksimal qiymatini o'zingiz yozing.
2. `i8` va `u8` o'rtasidagi farqni tushuntiring.
3. `i32` va `i64` xotira sarfini taqqoslang.
4. `usize` nima uchun array indekslarida ishlatilishini tushuntiring.
5. `u8` da `255 + 1` hisoblash uchun `checked_add()` va `wrapping_add()` metodlarini sinab ko'ring.

---

## Xulosa

Rust'da jami 12 ta asosiy integer turi mavjud:

**Signed:**
- `i8`
- `i16`
- `i32`
- `i64`
- `i128`
- `isize`

**Unsigned:**
- `u8`
- `u16`
- `u32`
- `u64`
- `u128`
- `usize`

Ularning farqi faqat saqlaydigan sonlar oralig'ida emas, balki xotira hajmi va qo'llanilish maqsadida ham namoyon bo'ladi.

Integer Types'ni chuqur tushunish — Rust'da memory management, bitwise operations, systems programming, embedded development va backend engineering uchun muhim poydevordir.

---

📚 **GitHub Materials:**
https://github.com/rustlangclub/learning-rust

📢 **Telegram Channel:**
https://t.me/RustLangClub

💬 **Telegram Community:**
https://t.me/RustLangClubChat

**RustLangClub — Learn. Understand. Build.** 🦀