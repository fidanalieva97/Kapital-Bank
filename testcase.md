## TC 01 – Uğurlu Login

**Modul:** Autentifikasiya  
**Priority:** High  
**Severity:** Critical  

### Precondition:
- İstifadəçi sistemdə qeydiyyatdan keçib  
- Aktiv istifadəçi hesabı mövcuddur  

### Test Steps:
1. Login səhifəsini aç  
2. Düzgün FIN/istifadəçi adı daxil et  
3. Düzgün şifrə daxil et  
4. “Daxil ol” düyməsini kliklə  

### Expected Result:
- İstifadəçi OTP/SMS təsdiqdən sonra şəxsi kabinetə yönləndirilir  
- Sessiya yaradılır  

### Postcondition:
- Aktiv istifadəçi sessiyası mövcuddur

- ## TC 02 – Yanlış Şifrə ilə Login

**Modul:** Autentifikasiya  
**Priority:** High  
**Severity:** Major  

### Precondition:
- Aktiv istifadəçi mövcuddur  

### Test Steps:
1. Login səhifəsini aç  
2. Düzgün istifadəçi adı daxil et  
3. Yanlış şifrə daxil et  
4. “Daxil ol” kliklə  

### Expected Result:
- “İstifadəçi adı və ya şifrə yanlışdır” mesajı göstərilir  
- Sessiya yaradılmır  
- 3 uğursuz cəhddən sonra hesab müvəqqəti bloklanır  

### Postcondition:
- Uğursuz giriş cəhdi haqqında sms göndərilir

- ## TC 03 – Şifrə Bərpası

**Modul:** Şifrə Bərpası  
**Priority:** High  
**Severity:** Critical  

### Precondition:
- İstifadəçinin qeydiyyatda mobil nömrəsi aktivdir  

### Test Steps:
1. “Şifrəni unutdum” seç  
2. FIN kodunu daxil et  
3. SMS OTP kodunu daxil et  
4. Yeni şifrə təyin et  
5. Yeni şifrə ilə login et  

### Expected Result:
- Yeni şifrə uğurla qeyd olunur  
- Köhnə şifrə deaktiv edilir  

### Postcondition:
- Şifrə dəyişmə əməliyyatı yadda saxlanılır  

## TC 04 – Hesab Balansının Yoxlanılması

**Modul:** Akkaunt  
**Priority:** High  
**Severity:** Major  

### Precondition:
- İstifadəçi login olub  

### Test Steps:
1. “Hesablarım” bölməsinə keç  
2. Cari hesabı seç  

### Expected Result:
- Balans real-time və düzgün məbləğdə göstərilir  
- Valyuta düzgün əks olunur  

### Postcondition:
- Heç bir maliyyə dəyişikliyi olmur  

## TC 05 – Daxili Köçürmə (Kapital Bank hesabları arası)

**Modul:** Köçürmələr  
**Priority:** High  
**Severity:** Critical  

### Precondition:
- İstifadəçi hesabına giriş etmişdir  
- Göndərən hesabda kifayət qədər balans var  
- Qəbul edən hesab aktivdir  

### Test Steps:
1. “Köçürmələr” bölməsinə keç  
2. Qəbul edən hesab nömrəsini daxil et  
3. Məbləği daxil et  
4. Təsdiq et (OTP ilə)  

### Expected Result:
- Məbləğ göndərən hesabdan çıxılır  
- Qəbul edən hesaba əlavə olunur  
- Əməliyyat uğurlu status alır  

### Postcondition:
- Əməliyyat tarixçədə görünür  

## TC 06 – Kartdan Karta Köçürmə

**Modul:** Köçürmələr  
**Priority:** High  
**Severity:** Critical  

### Precondition:
- İstifadəçi hesabına daxil olmuşdur  
- Kart aktivdir  
- Göndərən hesabda kifayət qədər balans var  
- 3D Secure aktivdir  

### Test Steps:
1. “Köçürmələr” bölməsinə keç  
2. Kart nömrəsini daxil et  
3. Məbləği yaz  
4. OTP daxil et  
5. Təsdiqlə  

### Expected Result:
- Köçürmə uğurla icra olunur  
- Komissiya düzgün hesablanır  

### Postcondition:
- Əməliyyat çıxarışda görünür  

## TC 07 – Yetərsiz Balans

**Modul:** Köçürmələr  
**Priority:** High  
**Severity:** Major  

### Precondition:
- İstifadəçi hesabına daxil olmuşdur  
- Balans köçürüləcək məbləğdən azdır  

### Test Steps:
1. “Köçürmələr” bölməsinə keç  
2. Kart nömrəsini daxil et  
3. Mövcud balansdan artıq məbləğ daxil et  
4. Təsdiqlə  

### Expected Result:
- “Yetərsiz balans” mesajı göstərilir  
- Əməliyyat icra olunmur  

### Postcondition:
- Balans dəyişmir

## TC 08 – Sessiya Timeout

**Modul:** Security  
**Priority:** Medium  
**Severity:** Major  

### Precondition:
- İstifadəçi hesabına daxil olmuşdur  

### Test Steps:
1. Əsas səhifəyə keçid et  
2. 15 dəqiqə heç bir əməliyyat etmə  

### Expected Result:
- Sessiya avtomatik bağlanır  
- Yenidən login tələb olunur  

### Postcondition:
- Aktiv sessiya silinir

## TC 09 – Əməliyyat Tarixçəsinin Filtrlənməsi

**Modul:** Əməliyyat tarixçəsi  
**Priority:** Medium  
**Severity:** Minor  

### Precondition:
- İstifadəçi hesabına daxil olmuşdur  
- Hesabda ən az 5 əməliyyat mövcuddur  

### Test Steps:
1. Əməliyyat tarixçəsi bölməsinə keçid et  
2. Tarix aralığını seç  
3. Filter tətbiq et  

### Expected Result:
- Seçilmiş tarixə uyğun əməliyyatlar göstərilir  
- Yanlış tarix seçildikdə xəbərdarlıq çıxır  

### Postcondition:
- Məlumat dəyişmir

## TC 10 – Mobil Nömrənin Yenilənməsi

**Modul:** Şəxsi Bilgilər  
**Priority:** High  
**Severity:** Major  

### Precondition:
- İstifadəçi login olub  
- Yeni nömrə aktivdir  

### Test Steps:
1. Profil bölməsinə keç  
2. Nömrəni dəyiş butonuna klik et  
3. Yeni mobil nömrəni daxil et  
4. OTP təsdiq et  

### Expected Result:
- Mobil nömrə uğurla yenilənir  
- Köhnə nömrə deaktiv edilir  

### Postcondition:
- Dəyişiklik yadda saxlanılır  

