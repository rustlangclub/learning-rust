# 🦀 Rust Data Types — Rust dasturlash tilidagi ma'lumot turlari

Rust dasturlash tilida har bir qiymat ma'lum bir **Data Type** ga ega. Data Type kompyuter xotirasida qanday ma'lumot saqlanishini va u bilan qanday amallar bajarish mumkinligini belgilaydi.

Rust statically typed language hisoblanadi. Ya'ni har bir o'zgaruvchining turi kompilyatsiya vaqtida aniqlanadi.

Ushbu darsda Rust tilidagi asosiy ma'lumot turlari, ularning vazifalari va ishlatilishini o'rganamiz.

## 1. Scalar Types

Scalar — bitta qiymatni ifodalovchi ma'lumot turi.

Rust'da to'rtta asosiy scalar kategoriya mavjud:

### 1.1. Integer Types

Butun sonlarni saqlash uchun ishlatiladi.

**Signed Integers (manfiy va musbat sonlar):**

| Type | Hajmi | Qiymatlar oralig'i |
|---|---:|---|
| `i8` | 8 bit | -128 dan 127 gacha |
| `i16` | 16 bit | -32,768 dan 32,767 gacha |
| `i32` | 32 bit | -2³¹ dan 2³¹-1 gacha |
| `i64` | 64 bit | -2⁶³ dan 2⁶³-1 gacha |
| `i128` | 128 bit | -2¹²⁷ dan 2¹²⁷-1 gacha |
| `isize` | Platformaga bog'liq | Pointer hajmiga teng |

```rust
let age: i32 = 21;
let temperature: i16 = -10;
let balance: i64 = -5000;
let number: i128 = 1000000;
let size: isize = 100;
```

**Unsigned Integers (faqat 0 va musbat sonlar):**

| Type | Hajmi | Qiymatlar oralig'i |
|---|---:|---|
| `u8` | 8 bit | 0 dan 255 gacha |
| `u16` | 16 bit | 0 dan 65,535 gacha |
| `u32` | 32 bit | 0 dan 2³²-1 gacha |
| `u64` | 64 bit | 0 dan 2⁶⁴-1 gacha |
| `u128` | 128 bit | 0 dan 2¹²⁸-1 gacha |
| `usize` | Platformaga bog'liq | Pointer hajmiga teng |

```rust
let age: u8 = 21;
let count: u16 = 500;
let population: u32 = 1000000;
let distance: u64 = 500000;
let index: usize = 10;
```

**Eslatma:** `usize` odatda array va vector indekslari uchun ishlatiladi. `isize` va `usize` hajmi 32-bit tizimda 32 bit, 64-bit tizimda 64 bit bo'ladi.

### 1.2. Floating-Point Types

Kasr sonlarni saqlash uchun ishlatiladi.

Rust ikkita floating-point turini taqdim etadi:

- `f32` — 32 bit.
- `f64` — 64 bit.

```rust
let height: f32 = 1.75;
let price: f64 = 19.99;
let pi: f64 = 3.1415926535;
```

`f64` Rust'da odatda standart floating-point turidir.

### 1.3. Boolean Type

Faqat ikkita qiymatga ega:

- `true`
- `false`

```rust
let is_active: bool = true;
let is_admin: bool = false;

if is_active {
    println!("User is active");
}
```

Boolean odatda shartlar va mantiqiy operatsiyalarda ishlatiladi.

### 1.4. Character Type

Bitta Unicode scalar value saqlaydi. Rust'da `char` hajmi 4 bayt (32 bit).

```rust
let letter: char = 'A';
let symbol: char = '🦀';
let uzbek: char = 'O';
```

**Muhim:** `char` bitta belgini, `String` yoki `str` esa matnni ifodalash uchun ishlatiladi.

## 2. Compound Types

Compound Types bir nechta qiymatni bitta tur ostida birlashtiradi.

Rust'da ikkita asosiy compound type mavjud.

### 2.1. Tuple

Turli xil data type qiymatlarini bitta strukturada saqlaydi.

```rust
let user: (i32, &str, bool) = (21, "Tokhir", true);

let age = user.0;
let name = user.1;
let active = user.2;

println!("{age}, {name}, {active}");
```

Tuple ichidagi qiymatlarga indeks orqali murojaat qilinadi.

Tuple destructuring:

```rust
let (age, name, active) = (21, "Tokhir", true);
```

Tuple qiymatlari turli data type'larga ega bo'lishi mumkin.

### 2.2. Array

Bir xil data type'dagi bir nechta qiymatni saqlaydi.

Array uzunligi yaratilgan vaqtda belgilanadi va keyinchalik o'zgarmaydi.

```rust
let numbers: [i32; 5] = [10, 20, 30, 40, 50];

let first = numbers[0];

println!("{first}");
```

Barcha elementlar bir xil turga ega bo'lishi shart.

Bir xil qiymat bilan to'ldirish:

```rust
let zeros: [i32; 5] = [0; 5];
```

## 3. String Types

Rust'da matn bilan ishlash uchun ikki muhim primitive va standard library turi mavjud.

### 3.1. str

`str` — string slice turi. U o'zgaruvchan uzunlikdagi UTF-8 matnni ifodalaydi.

Odatda `&str` ko'rinishida ishlatiladi:

```rust
let message: &str = "Hello, Rust!";
```

`&str` matnning o'ziga egalik qilmaydi, balki unga reference saqlaydi.

### 3.2. String

`String` — standard library tomonidan taqdim etilgan, Heap'da saqlanadigan va o'zgaruvchan matn turi.

```rust
let mut name = String::from("Rust");

name.push_str(" Language");

println!("{name}");
```

`String` matnni qo'shish, o'zgartirish va kengaytirish imkonini beradi.

**Farqi:**
- `&str` — string slice, odatda mavjud matnga reference.
- `String` — matnga egalik qiluvchi, o'zgaruvchan string turi.

## 4. Slice Types

Slice — array yoki boshqa ketma-ket ma'lumotlarning bir qismini reference orqali ifodalash imkonini beradi.

```rust
let numbers = [10, 20, 30, 40, 50];

let part: &[i32] = &numbers[1..4];

println!("{:?}", part);
```

Natija:

```text
[20, 30, 40]
```

String slice ham slice hisoblanadi:

```rust
let text = "Hello Rust";

let part: &str = &text[0..5];

println!("{part}");
```

## 5. Reference Types

Reference boshqa qiymatning xotira manziliga murojaat qilish imkonini beradi.

**Immutable Reference (`&T`):**

Qiymatni o'zgartirmasdan o'qish imkonini beradi.

```rust
let number = 100;

let reference: &i32 = &number;

println!("{reference}");
```

**Mutable Reference (`&mut T`):**

Qiymatni reference orqali o'zgartirish imkonini beradi.

```rust
let mut number = 100;

let reference: &mut i32 = &mut number;

*reference = 200;

println!("{number}");
```

`*` operatori dereference deyiladi.

## 6. Pointer Types

Rust'da raw pointer turlari mavjud.

Ular xotira manzillari bilan to'g'ridan-to'g'ri ishlash imkonini beradi.

**Immutable Raw Pointer (`*const T`):**

```rust
let number = 100;

let pointer: *const i32 = &number;
```

**Mutable Raw Pointer (`*mut T`):**

```rust
let mut number = 100;

let pointer: *mut i32 = &mut number;
```

Raw pointer orqali qiymatni dereference qilish `unsafe` blokini talab qiladi.

```rust
let number = 100;

let pointer: *const i32 = &number;

unsafe {
    println!("{}", *pointer);
}
```

Raw pointer bilan ishlashda xotira xavfsizligi uchun dasturchining o'zi javobgar bo'ladi.

## 7. Unit Type — `()`

Unit Type hech qanday mazmunli qiymatga ega bo'lmagan holatni ifodalaydi.

Rust'da funksiya hech qanday qiymat qaytarmasa, uning qaytarish turi `()` hisoblanadi.

```rust
fn say_hello() {
    println!("Hello!");
}
```

Bu funksiya aslida `()` qaytaradi.

Uni aniq ko'rsatish ham mumkin:

```rust
fn say_hello() -> () {
    println!("Hello!");
}
```

Bo'sh tuple ham `()` hisoblanadi.

## 8. Never Type — `!`

Never Type hech qachon normal holatda qiymat qaytarmaydigan ifodalarni ifodalaydi.

Masalan, `panic!()` dastur bajarilishini to'xtatadi.

```rust
fn stop_program() -> ! {
    panic!("Program stopped!");
}
```

`!` odatda hech qachon davom etmaydigan yoki normal qiymat qaytarmaydigan kodlarda ishlatiladi.

## 9. Struct Types

Struct — o'zimiz yaratadigan ma'lumot turi. Bir nechta turli qiymatlarni bitta strukturaga birlashtiradi.

```rust
struct User {
    id: u64,
    name: String,
    active: bool,
}

let user = User {
    id: 1,
    name: String::from("Tokhir"),
    active: true,
};
```

Rust'da uchta asosiy struct shakli mavjud.

**Named-field Struct:**

```rust
struct User {
    id: u64,
    name: String,
}
```

**Tuple Struct:**

```rust
struct Color(u8, u8, u8);

let red = Color(255, 0, 0);
```

**Unit Struct:**

```rust
struct Admin;

let admin = Admin;
```

## 10. Enum Types

Enum — oldindan belgilangan bir nechta variantlardan birini ifodalovchi ma'lumot turi.

```rust
enum Direction {
    North,
    South,
    East,
    West,
}

let direction = Direction::North;
```

Enum variantlari ichida ma'lumot ham saqlash mumkin:

```rust
enum Message {
    Text(String),
    Number(i32),
    Quit,
}
```

Rust'da juda muhim ikkita enum:

**Option<T>**

Qiymat mavjud yoki mavjud emasligini ifodalaydi.

```rust
let name: Option<String> = Some(String::from("Rust"));

let empty: Option<String> = None;
```

**Result<T, E>**

Operatsiya muvaffaqiyatli yoki xatolik bilan yakunlanganini ifodalaydi.

```rust
let result: Result<i32, &str> = Ok(100);

let error: Result<i32, &str> = Err("Something went wrong");
```

`Option` va `Result` Rust'da xatolarni va mavjud bo'lmagan qiymatlarni xavfsiz boshqarish uchun juda muhim.

## 11. Union Types

Union — bir nechta field uchun bir xil xotira maydonidan foydalanadigan maxsus ma'lumot turi.

```rust
union Value {
    integer: u32,
    float: f32,
}

let value = Value { integer: 100 };

unsafe {
    println!("{}", value.integer);
}
```

Union bilan ishlashda `unsafe` talab qilinadi, chunki qaysi field'da haqiqiy qiymat borligini dasturchi nazorat qilishi kerak.

## 12. Function Types

Rust'da funksiyalar ham ma'lumot turi sifatida ifodalanishi mumkin.

```rust
fn add(a: i32, b: i32) -> i32 {
    a + b
}

let operation: fn(i32, i32) -> i32 = add;

println!("{}", operation(10, 20));
```

Bu yerda `fn(i32, i32) -> i32` — function pointer turi.

## 13. Closure Types

Closure — boshqa funksiyalarga o'xshash, lekin tashqi muhitdagi o'zgaruvchilarni ham qamrab olishi mumkin bo'lgan anonim funksiya.

```rust
let multiplier = 2;

let double = |number: i32| number * multiplier;

println!("{}", double(10));
```

Closure'larning o'ziga xos, kompilyator tomonidan aniqlanadigan anonim turlari mavjud.

Closure'lar `Fn`, `FnMut` va `FnOnce` trait'lari orqali ifodalanadi.

## 14. Trait Objects — `dyn Trait`

Trait Object turli konkret turlardagi obyektlar bilan umumiy interfeys orqali ishlash imkonini beradi.

```rust
trait Animal {
    fn sound(&self);
}

struct Dog;

impl Animal for Dog {
    fn sound(&self) {
        println!("Woof!");
    }
}

let animal: Box<dyn Animal> = Box::new(Dog);

animal.sound();
```

Bu yerda `dyn Animal` — trait object.

## 15. Generic Types

Generics yordamida bir nechta data type bilan ishlay oladigan umumiy kod yozish mumkin.

```rust
fn display<T: std::fmt::Display>(value: T) {
    println!("{value}");
}

display(100);
display("Rust");
display(3.14);
```

Bu yerda `T` — generic type parameter.

Generics kodni qayta ishlatish va turli ma'lumot turlari bilan ishlash imkonini beradi.

## 16. Type Aliases

Type Alias — mavjud ma'lumot turiga yangi nom berish imkonini beradi.

```rust
type UserId = u64;

let user_id: UserId = 100;
```

Bu yangi alohida type yaratmaydi, faqat mavjud type uchun boshqa nom beradi.

## 17. Opaque Types — `impl Trait`

`impl Trait` orqali funksiya qaytaradigan yoki qabul qiladigan qiymatning aniq konkret turini tashqaridan yashirish mumkin.

```rust
fn get_number() -> impl Iterator<Item = i32> {
    1..5
}
```

Bu yerda funksiya `Iterator` trait'ini amalga oshiruvchi konkret tur qaytaradi.

---

## Xulosa

Rust'dagi ma'lumot turlarini quyidagicha guruhlash mumkin:

| Kategoriya | Turlar |
|---|---|
| Integer | `i8`–`i128`, `isize`, `u8`–`u128`, `usize` |
| Floating-point | `f32`, `f64` |
| Boolean | `bool` |
| Character | `char` |
| Compound | `tuple`, `array` |
| String | `str`, `String` |
| Slice | `[T]`, `&[T]` |
| Reference | `&T`, `&mut T` |
| Raw Pointer | `*const T`, `*mut T` |
| Special | `()`, `!` |
| User-defined | `struct`, `enum`, `union` |
| Function | `fn`, closure |
| Dynamic | `dyn Trait` |
| Generic | `T`, `impl Trait` |
| Alias | `type` |

**Muhim eslatma:** `String`, `Vec<T>`, `Box<T>`, `Option<T>`, `Result<T, E>`, `HashMap<K, V>`, `Rc<T>` va `Arc<T>` kabi turlar ham Rust'da juda muhim. Bular primitive type emas, balki standard library tomonidan taqdim etilgan turlardir.

Rust'da data type'larni tushunish — ownership, borrowing, memory management va backend dasturlashni o'rganish uchun muhim poydevor hisoblanadi.

**Keyingi boosqichlarda ushbu turlarni amaliy loyihalar orqali chuqurroq o'rganamiz.**

---

📚 **GitHub Materials:**  
https://github.com/rustlangclub/learning-rust/tree/main/basics/01/datatypes/01-dt-in-rust/README.md

📢 **Telegram Channel:**  
https://t.me/RustLangClub

💬 **Telegram Community:**  
https://t.me/RustLangClubChat

**RustLangClub — Learn. Understand. Build.** 🦀