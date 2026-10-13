# Week 5 — Ev tapşırığı: Sortlama I + Sliding window

İlk 2 tapşırıq sortlamanın tamamlanmasıdır. 3-5 bu həftənin pattern-indəndir
(sliding window — sabit ölçülü pəncərə). Məşğələdə yazdığın 4 sortlama
metodunu bitirməmisənsə, əvvəlcə onları tamamla.

## 1. 4 sortu bir yerdə sına

`bubbleSort`, `selectionSort`, `insertionSort`, `countingSort` metodlarının
hamısını eyni `main`-ə yığ, aşağıdaki massivlərin hər biri üzərində sına,
nəticəni qeyd et (hamısı eyni sortlanmış nəticəni verməlidir):

- `{5, 2, 9, 1, 5, 6, 3}`
- Boş massiv `{}`
- Bir elementli `{7}`
- Artıq sortlanmış `{1, 2, 3, 4, 5}`
- Tərsinə sortlanmış `{5, 4, 3, 2, 1}`

Bunlar şifahi sorğuda soruşulan "kənar hal" sualları ilə birbaşa bağlıdır —
hazırlıqlı gəl.

## 2. Stability-ni öz gözünlə gör

`(dəyər, etiket)` cütlərindən ibarət massiv düşün: `(3,A), (1,B), (3,C), (2,D)`.
Selection sort-la dəyərə görə sırala, `A` və `C`-nin nisbi sırasının qorunub-
qorunmadığını yoxla (ipucu: qorunmur — bu, selection sort-un qeyri-stabil
olduğunun sübutudur). Eynisini bubble sort-la təkrarla, bu dəfə sıra qorunur.

## 3. Maximum Average Subarray I (LeetCode 643)

Dərsdəki `maxSumSubarray`-ə çox bənzəyir — sabit `k` ölçülü pəncərənin
ortalamasını tap.

## 4. Sliding window sıfırdan — massivin maksimum cəmi

Dərsdə yazdığın `maxSumSubarray`-i şablonsuz, yaddaşdan yenidən yaz. `k=3`,
`a = {4, 2, 1, 7, 8, 1, 2, 8, 1, 0}` ilə sına.

## Bonus (tez bitirənlər üçün)

**Minimum Size Subarray Sum (LeetCode 209).** Pəncərə sabit ölçülü deyil —
cəm verilən dəyərdən böyük-bərabər olana qədər böyüyür, sonra kiçilə bilər.
Dərsdə qısa göstərilən dəyişən ölçü ideyasının tam versiyası.
