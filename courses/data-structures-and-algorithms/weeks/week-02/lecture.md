# Week 2 — Mühazirə: Alqoritmə giriş (90 dəq)

**Məqsəd:** tələbə dərsdən çıxanda "eyni məsələnin sürətli və yavaş həlli olur"
fikrini başa düşsün. Formal Big O yoxdur — o, Week 6-dadır. Burada yalnız **hiss**.

## 0-5 dəq · Açılış
Keçən həftənin tapşırığı: kim quraşdırdı, kim repo yaratdı. Əl qaldırtdır, qeyd et.

## 5-20 dəq · Alqoritm nədir?

Tərifdən başlama — nümunədən başla.

**Lüğət nümunəsi.** Lövhəyə qalın bir lüğət təsəvvür etdir. "Alqoritm" sözünü tap.
- Yol 1: birinci səhifədən başla, səhifə-səhifə gəz
- Yol 2: ortadan aç, sözün əvvəldədirsə sol yarını at, sonradadırsa sağ yarını

Soruş: 1000 səhifəlik lüğətdə hansı neçə addım çəkər?
- Yol 1: pis halda 1000
- Yol 2: 1000 → 500 → 250 → 125 → … → 1. **10 addım.**

Bu, semestrin ən vacib şəklidir. Bütün kurs bu fərqin üstündə qurulub.
İndi tərifi ver: *alqoritm — məsələni həll edən, addım-addım, sonlu və birmənalı
təlimatlar ardıcıllığıdır.*

Alqoritmin şərtləri: giriş, çıxış, dəqiqlik, sonluluq, effektivlik.

## 20-40 dəq · Eyni məsələ, iki həll

**Məsələ 1: 1-dən n-ə qədər ədədlərin cəmi**

```
Yol A: dövr             Yol B: düstur
sum = 0                 sum = n * (n + 1) / 2
for i = 1..n
    sum = sum + i
```

n = 1.000.000 üçün: A → 1.000.000 əməliyyat, B → 3 əməliyyat.
Kodu canlı yaz, `System.nanoTime()` ilə ikisini ölç, fərqi ekranda göstər.

**Məsələ 2: massivdə cəmi X olan iki ədəd**

```
Yol A: hər cütü yoxla        Yol B: massiv sortlanıbsa,
for i = 0..n-1               iki uçdan ortaya doğru get
    for j = i+1..n-1         (Week 3-də görəcəyik)
        if a[i] + a[j] == X
```

Yol A: n = 1000 üçün təxminən 500.000 yoxlama. Yol B: 1000 yoxlama.

Burada **iç-içə dövr = kvadratik artım** fikrini otur. Bunu tez-tez təkrar edəcəksən.

## 40-55 dəq · "Sürət" hissi

Lövhəyə cədvəl çək. Saniyədə 1 milyard əməliyyat edən kompüter:

| n | log n | n | n² |
|---|---|---|---|
| 10 | 3 | 10 | 100 |
| 1 000 | 10 | 1 000 | 1 000 000 |
| 1 000 000 | 20 | 1 000 000 | 10¹² |

Son xanaya diqqət çək: 10¹² əməliyyat ≈ **17 dəqiqə**. Eyni məsələ n log n ilə
20 millisaniyə çəkir.

Mesaj: *kompüteri sürətləndirmək yox, alqoritmi dəyişmək lazımdır.*

## 55-75 dəq · Massiv yaddaşda

Bu hissə Week 3-ün özülüdür.

- Massiv = yaddaşda **ardıcıl** xanalar, hamısı eyni ölçüdə
- `a[5]`-ə müraciət: ünvan = başlanğıc + 5 × xananın ölçüsü. **Bir hesablama, O(1)**
- Ortadan silmək: arxadakı bütün elementlər bir addım sürüşməlidir. **O(n)**
- Ölçüsü sabitdir — dolubsa, yeni massiv yaradıb köçürmək lazımdır

Lövhədə xanaları çək, indeks yaz, silmə anını oxlarla göstər.
VisualGo-da array bölməsini göstər: https://visualgo.net/en

## 75-90 dəq · Yekun və tapşırıq

- Bu həftə məşğələdə nə olacaq: Java minimum + debug + 5 warm-up
- Ev tapşırığı (`homework.md`)
- Sual-cavab

## Lövhəyə mütləq yazılacaqlar
1. Lüğət nümunəsi: 1000 → 10 addım
2. n vs n² cədvəli
3. Massiv xanaları və indeks hesablanması

## Gələn il üçün qeyd
Bu mühazirədə slayd demək olar lazım deyil — lövhə və canlı kod daha yaxşı işləyir.
