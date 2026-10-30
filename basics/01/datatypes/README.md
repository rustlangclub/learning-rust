# 📦 Data Types — Ma'lumotlar turlari nima va nima uchun kerak?

Kompyuter ma'lumotlarni qanday tushunadi? Nega `25`, `"Hello"` va `true` bir-biridan farq qiladi? Kompyuter uchun bularning barchasi shunchaki 0 va 1 lardan iborat bo‘lsa, ularning ma'nosi qanday aniqlanadi?

Bu savollarga javob berish uchun **Data Types (Ma'lumotlar turlari)** tushunchasini bilishimiz kerak.

## 1. Data Types nima?

**Data Type** — bu kompyuter tizimida ma'lumotning qanday turga mansubligini, qanday ma'noda talqin qilinishini va u bilan qanday amallar bajarish mumkinligini belgilaydigan tushuncha.

Oddiy misol:

- `25` — son.
- `"Hello"` — matn.
- `true` — mantiqiy qiymat.
- `3.14` — kasr son.

Ularning barchasi ma'lumot, ammo mazmuni va ulardan foydalanish usullari turlicha.

Masalan, 25 + 10 matematik qo‘shish amalini anglatadi. Ammo `"25" + "10"` matn sifatida qaralsa, natija `"2510"` bo‘lishi mumkin.

Demak, ma'lumotning qiymati bilan birga uning turi ham muhim.

## 2. Kompyuter ma'lumotlarni qanday saqlaydi?

Kompyuterning eng asosiy ishlash tamoyillaridan biri — ikkilik sanoq tizimi (Binary System).

Kompyuter ma'lumotlarni bitlar yordamida ifodalaydi. Bit faqat ikkita holatdan birini qabul qiladi:

- `0`
- `1`

8 bit birgalikda 1 Byte (bayt) hosil qiladi.

Masalan:

`00000001`

Bu bitlar ketma-ketligi turli kontekstlarda turlicha ma'noga ega bo‘lishi mumkin.

U sonni, belgini yoki boshqa ma'lumotning bir qismini ifodalashi mumkin.

Muhim jihat: kompyuter xotirasida har doim ham ma'lumotning ma'nosi alohida saqlanmaydi. Ko‘pincha ma'noni belgilash uchun tizim ma'lumot qanday talqin qilinishi kerakligini bilishi lozim.

Aynan shu yerda Data Types muhim rol o‘ynaydi.

## 3. Ma'lumotlar turlarining asosiy kategoriyalari

Kompyuter fanlarida ma'lumotlar turli kategoriyalarga ajratiladi.

**1. Integer (Butun sonlar)**

Kasr qismi bo‘lmagan sonlar.

Misollar:
- `10`
- `-25`
- `0`
- `1000`

**2. Floating-Point (Haqiqiy sonlarning taxminiy ifodasi)**

Kasr qismiga ega sonlarni ifodalash uchun ishlatiladi.

Misollar:
- `3.14`
- `-0.75`
- `125.5`

**3. Character (Belgi)**

Bitta belgini ifodalaydi.

Misollar:
- `A`
- `b`
- `7`
- `@`

**4. String (Matn)**

Belgilar ketma-ketligidan tashkil topgan ma'lumot.

Misollar:
- `"Hello"`
- `"RustLangClub"`
- `"Computer Science"`

**5. Boolean (Mantiqiy qiymat)**

Faqat ikkita mantiqiy holatni ifodalaydi:

- `True` — rost.
- `False` — yolg‘on.

Bu tur shartlarni tekshirish, qaror qabul qilish va dastur oqimini boshqarishda juda muhim.

**6. Composite Types (Murakkab ma'lumotlar turlari)**

Bir nechta qiymatlarni yagona tuzilma sifatida birlashtiradi.

Masalan:
- Array
- Structure
- Tuple
- Object

Ular murakkab ma'lumotlarni tartibli saqlash va boshqarish imkonini beradi.

## 4. Data Types kompyuter ishlashida qanday ahamiyatga ega?

Ma'lumotlar turlari faqat dasturchilar uchun yaratilmagan. Ular kompyuter arxitekturasi va dasturiy ta'minotning ishlashida ham muhim ahamiyatga ega.

Ularning vazifalarini bir necha jihatdan ko‘rib chiqamiz:

**1. Xotiradan foydalanish**

Har xil turdagi ma'lumotlar turli hajmdagi xotirani talab qilishi mumkin.

Masalan, 8 bit, 16 bit, 32 bit va 64 bit kabi o‘lchamlar mavjud.

Ma'lumotning hajmi uning qancha xotira egallashiga va qanday diapazondagi qiymatlarni ifodalay olishiga ta'sir qiladi.

**2. Ma'lumotlarni talqin qilish**

Bir xil bitlar ketma-ketligi turli ma'nolarni anglatishi mumkin.

Shuning uchun tizim ma'lumotni qanday talqin qilish kerakligini bilishi muhim.

**3. Amallarni bajarish**

Protsessor turli ma'lumotlar ustida turli operatsiyalarni bajaradi.

Masalan:
- Sonlar ustida arifmetik amallar.
- Mantiqiy qiymatlar ustida Boolean operatsiyalari.
- Matnlar ustida belgilarni qayta ishlash.

**4. Xatolarning oldini olish**

Ma'lumotlar turlari noto‘g‘ri amallarni aniqlashga yordam beradi.

Masalan, sana bilan matnni qo‘shish yoki mantiqiy qiymatni oddiy son sifatida ishlatish har doim ham mazmunli emas.

## 5. Dasturlash tillarida Data Types nima uchun kerak?

Dasturlash tili orqali kompyuterga qanday amallarni bajarish kerakligini ko‘rsatamiz.

Dasturlash tillarida Data Types quyidagi vazifalarni bajaradi:

- Ma'lumotning qanday qiymat qabul qilishini belgilaydi.
- Xotiradan foydalanish qoidalarini aniqlashga yordam beradi.
- Ma'lumotlar ustida bajarilishi mumkin bo‘lgan amallarni belgilaydi.
- Noto‘g‘ri foydalanish holatlarini aniqlashga yordam beradi.
- Dastur tuzilishini aniqroq va tushunarliroq qiladi.

Dasturlash tillarida ma'lumot turlari bilan ishlash usullari turlicha bo‘lishi mumkin.

Ba'zi tillarda ma'lumot turi oldindan aniq ko‘rsatiladi. Boshqalarida esa uning turi bajarilish jarayonida aniqlanishi mumkin.

Bu yondashuvlar **Static Typing** va **Dynamic Typing** deb ataladi.

## 6. Xulosa

Data Types — kompyuter fanlarining fundamental tushunchalaridan biri.

Kompyuter ma'lumotlarni bitlar orqali ifodalaydi, ammo bu ma'lumotlarning ma'nosi, tuzilishi va ulardan foydalanish qoidalari alohida aniqlanishi kerak.

Data Types bizga ma'lumotlarni tasniflash, saqlash, talqin qilish va ular ustida to‘g‘ri amallar bajarish imkonini beradi.

Shuni unutmang: dasturlashni o‘rganish faqat kod yozishni o‘rganish emas. Uning ortida kompyuter qanday ishlashini tushunish ham yotadi.

**Computer Science asoslarini tushunish — kuchli dasturchi bo‘lish yo‘lidagi muhim qadamlardan biridir.**

---

📚 **RustLangClub | Learn. Understand. Build.**

# 📦 Data Types — Ma'lumotlar turlari nima va nima uchun kerak?

Kompyuter ma'lumotlarni qanday tushunadi? Nega `25`, `"Hello"` va `true` bir-biridan farq qiladi? Kompyuter uchun bularning barchasi shunchaki 0 va 1 lardan iborat bo‘lsa, ularning ma'nosi qanday aniqlanadi?

Bu savollarga javob berish uchun **Data Types (Ma'lumotlar turlari)** tushunchasini bilishimiz kerak.

## 1. Data Types nima?

**Data Type** — bu kompyuter tizimida ma'lumotning qanday turga mansubligini, qanday ma'noda talqin qilinishini va u bilan qanday amallar bajarish mumkinligini belgilaydigan tushuncha.

Oddiy misol:

- `25` — son.
- `"Hello"` — matn.
- `true` — mantiqiy qiymat.
- `3.14` — kasr son.

Ularning barchasi ma'lumot, ammo mazmuni va ulardan foydalanish usullari turlicha.

Masalan, 25 + 10 matematik qo‘shish amalini anglatadi. Ammo `"25" + "10"` matn sifatida qaralsa, natija `"2510"` bo‘lishi mumkin.

Demak, ma'lumotning qiymati bilan birga uning turi ham muhim.

## 2. Kompyuter ma'lumotlarni qanday saqlaydi?

Kompyuterning eng asosiy ishlash tamoyillaridan biri — ikkilik sanoq tizimi (Binary System).

Kompyuter ma'lumotlarni bitlar yordamida ifodalaydi. Bit faqat ikkita holatdan birini qabul qiladi:

- `0`
- `1`

8 bit birgalikda 1 Byte (bayt) hosil qiladi.

Masalan:

`00000001`

Bu bitlar ketma-ketligi turli kontekstlarda turlicha ma'noga ega bo‘lishi mumkin.

U sonni, belgini yoki boshqa ma'lumotning bir qismini ifodalashi mumkin.

Muhim jihat: kompyuter xotirasida har doim ham ma'lumotning ma'nosi alohida saqlanmaydi. Ko‘pincha ma'noni belgilash uchun tizim ma'lumot qanday talqin qilinishi kerakligini bilishi lozim.

Aynan shu yerda Data Types muhim rol o‘ynaydi.

## 3. Ma'lumotlar turlarining asosiy kategoriyalari

Kompyuter fanlarida ma'lumotlar turli kategoriyalarga ajratiladi.

**1. Integer (Butun sonlar)**

Kasr qismi bo‘lmagan sonlar.

Misollar:
- `10`
- `-25`
- `0`
- `1000`

**2. Floating-Point (Haqiqiy sonlarning taxminiy ifodasi)**

Kasr qismiga ega sonlarni ifodalash uchun ishlatiladi.

Misollar:
- `3.14`
- `-0.75`
- `125.5`

**3. Character (Belgi)**

Bitta belgini ifodalaydi.

Misollar:
- `A`
- `b`
- `7`
- `@`

**4. String (Matn)**

Belgilar ketma-ketligidan tashkil topgan ma'lumot.

Misollar:
- `"Hello"`
- `"RustLangClub"`
- `"Computer Science"`

**5. Boolean (Mantiqiy qiymat)**

Faqat ikkita mantiqiy holatni ifodalaydi:

- `True` — rost.
- `False` — yolg‘on.

Bu tur shartlarni tekshirish, qaror qabul qilish va dastur oqimini boshqarishda juda muhim.

**6. Composite Types (Murakkab ma'lumotlar turlari)**

Bir nechta qiymatlarni yagona tuzilma sifatida birlashtiradi.

Masalan:
- Array
- Structure
- Tuple
- Object

Ular murakkab ma'lumotlarni tartibli saqlash va boshqarish imkonini beradi.

## 4. Data Types kompyuter ishlashida qanday ahamiyatga ega?

Ma'lumotlar turlari faqat dasturchilar uchun yaratilmagan. Ular kompyuter arxitekturasi va dasturiy ta'minotning ishlashida ham muhim ahamiyatga ega.

Ularning vazifalarini bir necha jihatdan ko‘rib chiqamiz:

**1. Xotiradan foydalanish**

Har xil turdagi ma'lumotlar turli hajmdagi xotirani talab qilishi mumkin.

Masalan, 8 bit, 16 bit, 32 bit va 64 bit kabi o‘lchamlar mavjud.

Ma'lumotning hajmi uning qancha xotira egallashiga va qanday diapazondagi qiymatlarni ifodalay olishiga ta'sir qiladi.

**2. Ma'lumotlarni talqin qilish**

Bir xil bitlar ketma-ketligi turli ma'nolarni anglatishi mumkin.

Shuning uchun tizim ma'lumotni qanday talqin qilish kerakligini bilishi muhim.

**3. Amallarni bajarish**

Protsessor turli ma'lumotlar ustida turli operatsiyalarni bajaradi.

Masalan:
- Sonlar ustida arifmetik amallar.
- Mantiqiy qiymatlar ustida Boolean operatsiyalari.
- Matnlar ustida belgilarni qayta ishlash.

**4. Xatolarning oldini olish**

Ma'lumotlar turlari noto‘g‘ri amallarni aniqlashga yordam beradi.

Masalan, sana bilan matnni qo‘shish yoki mantiqiy qiymatni oddiy son sifatida ishlatish har doim ham mazmunli emas.

## 5. Dasturlash tillarida Data Types nima uchun kerak?

Dasturlash tili orqali kompyuterga qanday amallarni bajarish kerakligini ko‘rsatamiz.

Dasturlash tillarida Data Types quyidagi vazifalarni bajaradi:

- Ma'lumotning qanday qiymat qabul qilishini belgilaydi.
- Xotiradan foydalanish qoidalarini aniqlashga yordam beradi.
- Ma'lumotlar ustida bajarilishi mumkin bo‘lgan amallarni belgilaydi.
- Noto‘g‘ri foydalanish holatlarini aniqlashga yordam beradi.
- Dastur tuzilishini aniqroq va tushunarliroq qiladi.

Dasturlash tillarida ma'lumot turlari bilan ishlash usullari turlicha bo‘lishi mumkin.

Ba'zi tillarda ma'lumot turi oldindan aniq ko‘rsatiladi. Boshqalarida esa uning turi bajarilish jarayonida aniqlanishi mumkin.

Bu yondashuvlar **Static Typing** va **Dynamic Typing** deb ataladi.

## 6. Xulosa

Data Types — kompyuter fanlarining fundamental tushunchalaridan biri.

Kompyuter ma'lumotlarni bitlar orqali ifodalaydi, ammo bu ma'lumotlarning ma'nosi, tuzilishi va ulardan foydalanish qoidalari alohida aniqlanishi kerak.

Data Types bizga ma'lumotlarni tasniflash, saqlash, talqin qilish va ular ustida to‘g‘ri amallar bajarish imkonini beradi.

Shuni unutmang: dasturlashni o‘rganish faqat kod yozishni o‘rganish emas. Uning ortida kompyuter qanday ishlashini tushunish ham yotadi.

**Computer Science asoslarini tushunish — kuchli dasturchi bo‘lish yo‘lidagi muhim qadamlardan biridir.**

---


<div align="center">

**RustLangClub**

*Learn. Understand. Build.*

A community for learning Computer Science, Programming and Software Engineering.

**TELEGRAM CHANNEL**

[@RustLangClub](https://t.me/RustLangClub)

**COMMUNITY CHAT**

[@RustLangClubChat](https://t.me/RustLangClubChat)

---

© 2026 RustLangClub. All rights reserved.

</div>