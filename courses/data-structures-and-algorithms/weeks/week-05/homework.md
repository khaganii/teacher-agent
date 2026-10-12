# Week 5 — Ev tapşırığı: Divide & conquer

Hamısı bu həftənin pattern-indəndir (böl → həll et → birləşdir). Məşğələdə
yazdığın `mergeSort`/`quickSort`-u bitirməmisənsə, əvvəlcə onu tamamla —
qalan tapşırıqlar onun üstündə qurulur.

## 1. Rekursiya isinmə — massivin cəmi

Dövr olmadan, yalnız rekursiya ilə massivin elementlərinin cəmini tap.

```java
static int sum(int[] a, int index) {
    // TODO: base case — index massivin sonuna çatanda 0 qaytar
    // TODO: recursive case — a[index] + qalanının cəmi
}
```

`main`-də `{3, 7, 1, 9, 2}` ilə sına, nəticə `22` olmalıdır.

## 2. Merge Sorted Array (LeetCode 88)

İki sortlanmış massivi bir sortlanmış massivə birləşdir — bu, dərsdə yazdığın
`merge` metoduna çox bənzəyir, fərq ikinci massivin birinci massivin sonuna
yazılmasıdır.

## 3. Sort an Array (LeetCode 912)

Öz `mergeSort` və ya `quickSort`-unu (dərsdən) birbaşa istifadə et. Əgər
dərsdə yetişdirə bilmədinsə, bu, onu bitirmək üçün fürsətdir.

## 4. Kənar halları yoxla

`mergeSort`-unu (və ya `quickSort`-unu) aşağıdaki massivlərin hər biri üzərində
işlət, nəticəni qeyd et (düzgün sortlayır, ya yox):

- Boş massiv `{}`
- Bir elementli `{5}`
- Bütün elementlər eyni `{4, 4, 4, 4}`
- Artıq sortlanmış `{1, 2, 3, 4, 5}`
- Tərsinə sortlanmış `{5, 4, 3, 2, 1}`

Bunlar şifahi sorğuda soruşulan "kənar hal" sualları ilə birbaşa bağlıdır —
hazırlıqlı gəl.

## Bonus (tez bitirənlər üçün)

**Sort Colors (LeetCode 75).** Massivdə yalnız `0`, `1`, `2` var — bir keçiddə
(əlavə sort çağırmadan) sırala. Partition-dakı "kiçik/böyük ayırma" fikri
burada üç qrupa bölünür.
