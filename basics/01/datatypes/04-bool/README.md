# 🦀 Rust Boolean Type — Mantiqiy qiymatlar va shartli amallar

Rust dasturlash tilida **Boolean Type (`bool`)** faqat ikkita qiymatni ifodalash uchun ishlatiladi:

1. `true` — rost.
2. `false` — yolg'on.

Boolean qiymatlar dasturda shartlarni tekshirish, qaror qabul qilish, mantiqiy operatsiyalar va dastur oqimini boshqarishda ishlatiladi.

Masalan:

```rust
let is_active: bool = true;
let is_admin: bool = false;

println!("{is_active}");
println!("{is_admin}");
```

Rust'da `bool` alohida primitive data type hisoblanadi.

---

## 1. Boolean Type — Asosiy xususiyatlari

Rust'dagi Boolean turi quyidagi xususiyatlarga ega:

| Xususiyat | Qiymat |
|---|---|
| Type | `bool` |
| Qiymatlar soni | 2 ta |
| Mumkin bo'lgan qiymatlar | `true`, `false` |
| Logical meaning | Rost yoki yolg'on |
| `size_of::<bool>()` | 1 byte |
| `size_of::<bool>()` | 8 bit |
| Signed / Unsigned | Qo'llanilmaydi |

Rust'da Boolean qiymatni quyidagicha e'lon qilamiz:

```rust
let is_active: bool = true;
let is_deleted: bool = false;
```

**Muhim:** Rust'da `bool` xotirada 1 byte joy egallaydi. Lekin u faqat ikkita mantiqiy qiymatni ifodalaydi.

Haqiqiy xotira joylashuvi va bit darajasidagi ishlash kompilyator hamda platformaga bog'liq bo'lishi mumkin.

---

## 2. Boolean qiymatlari

Boolean faqat ikkita qiymatga ega.

### 2.1. true

`true` shartning rost ekanligini bildiradi.

```rust
let is_logged_in: bool = true;

if is_logged_in {
    println!("User is logged in");
}
```

### 2.2. false

`false` shartning yolg'on ekanligini bildiradi.

```rust
let is_logged_in: bool = false;

if is_logged_in {
    println!("Welcome!");
} else {
    println!("Please login");
}
```

**Eslatma:** Rust'da `true` va `false` kichik harflar bilan yoziladi. `True`, `False`, `1` yoki `0` Boolean literal hisoblanmaydi.

---

## 3. Boolean va Comparison Operators

Boolean qiymatlar ko'pincha taqqoslash operatorlari orqali hosil qilinadi.

| Operator | Ma'nosi | Misol |
|---|---|---|
| `==` | Teng | `5 == 5` |
| `!=` | Teng emas | `5 != 3` |
| `>` | Katta | `10 > 5` |
| `<` | Kichik | `3 < 5` |
| `>=` | Katta yoki teng | `5 >= 5` |
| `<=` | Kichik yoki teng | `3 <= 5` |

Barcha taqqoslash operatorlari Boolean natija qaytaradi.

```rust
fn main() {
    let a = 10;
    let b = 20;

    let result1: bool = a < b;
    let result2: bool = a == b;
    let result3: bool = a != b;

    println!("{result1}"); // true
    println!("{result2}"); // false
    println!("{result3}"); // true
}
```

---

## 4. Logical Operators

Logical Operators bir yoki bir nechta Boolean qiymatlar ustida mantiqiy amallar bajaradi.

Rust'da uchta asosiy logical operator mavjud.

### 4.1. AND (`&&`)

Ikkala shart ham `true` bo'lsa, natija `true` bo'ladi.

| A | B | A && B |
|---|---|---|
| false | false | false |
| false | true | false |
| true | false | false |
| true | true | true |

```rust
let age = 21;
let has_ticket = true;

let can_enter = age >= 18 && has_ticket;

println!("{can_enter}"); // true
```

### 4.2. OR (`||`)

Kamida bitta shart `true` bo'lsa, natija `true` bo'ladi.

| A | B | A \|\| B |
|---|---|---|
| false | false | false |
| false | true | true |
| true | false | true |
| true | true | true |

```rust
let is_admin = false;
let is_moderator = true;

let has_permission = is_admin || is_moderator;

println!("{has_permission}"); // true
```

### 4.3. NOT (`!`)

Boolean qiymatni teskarisiga o'zgartiradi.

| A | !A |
|---|---|
| false | true |
| true | false |

```rust
let is_blocked = false;

let is_allowed = !is_blocked;

println!("{is_allowed}"); // true
```

---

## 5. Truth Table — Mantiqiy qiymatlar jadvali

Barcha asosiy logical operatorlarni birgalikda ko'ramiz.

| A | B | AND | OR | NOT A |
|---|---|---|---|---|
| false | false | false | false | true |
| false | true | false | true | true |
| true | false | false | true | false |
| true | true | true | true | false |

Bu jadval Boolean logic'ning asosiy qoidalarini ifodalaydi.

---

## 6. Short-Circuit Evaluation

Rust'da `&&` va `||` operatorlari Short-Circuit Evaluation mexanizmidan foydalanadi.

Bu nimani anglatadi?

**AND (`&&`):**

Birinchi shart `false` bo'lsa, ikkinchi shart tekshirilmaydi.

```rust
let a = false;
let b = true;

let result = a && b;
```

Natija `false`. Ikkinchi operand natijani o'zgartira olmagani uchun tekshirish davom ettirilmaydi.

**OR (`||`):**

Birinchi shart `true` bo'lsa, ikkinchi shart tekshirilmaydi.

```rust
let a = true;
let b = false;

let result = a || b;
```

Natija `true`.

Bu mexanizm keraksiz amallarni bajarmaslik va ayrim xatolarning oldini olish uchun foydali.

Masalan:

```rust
let numbers = vec![10, 20, 30];

let index = 5;

if index < numbers.len() && numbers[index] > 10 {
    println!("Value is greater than 10");
}
```

Bu yerda `index < numbers.len()` false bo'lsa, `numbers[index]` umuman bajarilmaydi. Natijada chegaradan tashqaridagi indeksga murojaat qilishning oldi olinadi.

---

## 7. Bitwise Boolean Operations

Rust'da Boolean qiymatlar bilan bitwise operatorlardan ham foydalanish mumkin.

| Operator | Vazifasi |
|---|---|
| `&` | Bitwise AND |
| `|` | Bitwise OR |
| `^` | Bitwise XOR |

```rust
fn main() {
    let a = true;
    let b = false;

    println!("{}", a & b); // false
    println!("{}", a | b); // true
    println!("{}", a ^ b); // true
}
```

**Muhim farq:**

- `&&` va `||` — short-circuit logical operators.
- `&`, `|` va `^` — Boolean qiymatlarda ham ishlaydigan bitwise operatorlar.

Bitwise operatorlarda ikkala operand ham baholanadi.

---

## 8. Boolean va if Expressions

Rust'da `if` faqat shartli kod bajarish uchun emas, qiymat qaytaruvchi expression sifatida ham ishlatiladi.

```rust
fn main() {
    let age = 21;

    let status = if age >= 18 {
        true
    } else {
        false
    };

    println!("{status}");
}
```

Bu yerda `if` expression natijasi `bool` hisoblanadi.

Bunday kodni yanada qisqa yozish mumkin:

```rust
let age = 21;

let is_adult = age >= 18;
```

Rust'da `if` shartining o'zi Boolean qiymat talab qiladi.

Quyidagi kod noto'g'ri:

```rust
let number = 1;

if number {
    println!("Hello");
}
```

Sababi: Rust `1` qiymatini avtomatik ravishda `true` ga aylantirmaydi.

To'g'ri ko'rinishi:

```rust
if number != 0 {
    println!("Hello");
}
```

---

## 9. Boolean Functions

Funksiyalar ham Boolean qiymat qaytarishi mumkin.

```rust
fn is_even(number: i32) -> bool {
    number % 2 == 0
}

fn main() {
    println!("{}", is_even(10)); // true
    println!("{}", is_even(7));  // false
}
```

Bu yondashuv dasturdagi shartlarni alohida funksiyalarga ajratish imkonini beradi.

---

## 10. Boolean va Option<bool>

Rust'da `Option<bool>` juda foydali tushuncha.

Oddiy `bool` faqat ikkita qiymatga ega:

- `true`
- `false`

Ammo `Option<bool>` uch xil holatni ifodalay oladi:

- `Some(true)` — qiymat mavjud va rost.
- `Some(false)` — qiymat mavjud va yolg'on.
- `None` — qiymat mavjud emas.

```rust
let is_verified: Option<bool> = Some(true);

let is_active: Option<bool> = Some(false);

let unknown: Option<bool> = None;
```

Masalan, foydalanuvchi profilidagi tasdiqlash holatini tekshirishda foydali:

```rust
fn main() {
    let verified: Option<bool> = None;

    match verified {
        Some(true) => println!("Verified"),
        Some(false) => println!("Not verified"),
        None => println!("Verification status unknown"),
    }
}
```

---

## 11. Boolean va Backend Development

Boolean backend dasturlashda eng ko'p ishlatiladigan turlardan biridir.

Masalan, foydalanuvchi ma'lumotlari:

```rust
struct User {
    id: u64,
    name: String,
    is_active: bool,
    is_admin: bool,
    is_verified: bool,
}
```

Login tekshiruvi:

```rust
fn can_login(user_active: bool, password_correct: bool) -> bool {
    user_active && password_correct
}
```

Ruxsat tekshiruvi:

```rust
fn has_access(is_admin: bool, is_owner: bool) -> bool {
    is_admin || is_owner
}
```

Soft Delete:

```rust
struct Post {
    id: u64,
    is_deleted: bool,
}
```

Boolean backend tizimlarida quyidagilar uchun ishlatiladi:

- User active/inactive holati.
- Admin va permission tekshirish.
- Email verification.
- Account locking.
- Feature flags.
- Soft deletion.
- Authentication va authorization.
- Configuration settings.

---

## 12. Boolean va Memory Size

Rust'da Boolean turining xotira hajmini `size_of` orqali tekshirish mumkin.

```rust
use std::mem::size_of;

fn main() {
    println!("{}", size_of::<bool>());
}
```

Natija:

```text
1
```

Demak, `bool` hajmi 1 byte yoki 8 bit.

Bir nechta Boolean qiymatlarni struct ichida saqlaganda padding sababli struct hajmi oddiy field hajmlari yig'indisidan katta bo'lishi ham mumkin.

---

## 13. Boolean va Integer o'rtasidagi farq

Ba'zi dasturlash tillarida `true` va `false` qiymatlari `1` va `0` bilan bog'liq.

Ammo Rust'da `bool` va integer alohida turlardir.

```rust
let is_active: bool = true;
let number: i32 = 1;
```

Quyidagi amallar Rust'da avtomatik bajarilmaydi:

```rust
// let number: i32 = true;
// let active: bool = 1;
```

Agar Boolean qiymatni integerga aylantirish kerak bo'lsa:

```rust
let active = true;

let number: u8 = active as u8;

println!("{number}"); // 1
```

Teskari yo'nalishda esa aniq shart yozish kerak:

```rust
let number: u8 = 1;

let active: bool = number != 0;
```

---

## 14. Amaliy mashqlar

Quyidagi kodni mustaqil yozib, ishga tushirib ko'ring:

```rust
fn main() {
    let age = 21;
    let is_active = true;
    let is_verified = false;

    let can_access = age >= 18
        && is_active
        && is_verified;

    println!("Can access: {can_access}");

    let is_admin = true;
    let is_owner = false;

    let has_permission = is_admin || is_owner;

    println!("Has permission: {has_permission}");

    println!("Verified: {}", !is_verified);
}
```

**Topshiriqlar:**

1. `true` va `false` o'rtasidagi farqni tushuntiring.
2. `bool` xotirada qancha joy egallaydi?
3. `&&` va `||` operatorlarining farqini tushuntiring.
4. Short-Circuit Evaluation qanday ishlashini misol bilan ko'rsating.
5. `!` operatori qanday vazifani bajaradi?
6. `Option<bool>` nima uchun kerak?
7. Nima uchun Rust'da `if 1` yozish mumkin emas?
8. `is_even()` nomli Boolean funksiya yarating.
9. User uchun `is_active`, `is_admin` va `is_verified` maydonlariga ega `struct` yarating.

---

## Xulosa

Rust'da Boolean Type (`bool`) faqat ikkita qiymatga ega:

- `true`
- `false`

Asosiy xususiyatlari:

- 1 byte xotira haj