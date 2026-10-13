# Week 5 — Mühazirə: Sortlama I — bubble, insertion, selection, counting (90 dəq)

**Qeyd (müəllim üçün):** bu, planda olan Week 5 mövzusu deyil — ICAO həftəsində
(Week 4) qalan sortlama materialı tam keçilməmişdi. Bu mühazirə o boşluğu bağlayır
və üstünə insertion/selection sort əlavə edir. Rekursiya + merge/quick sort +
divide & conquer bu səbəbdən **Week 6**-ya keçdi (bax `weeks/week-06/`).

**Məqsəd:** tələbə 4 sadə sortlama alqoritmini (necə işlədiyini, niyə sortlanmış
nəticə verdiyini) izah edə bilsin, sürətlərini müqayisə edə bilsin, stability
nə olduğunu bilsin.

## 0-5 dəq · Açılış

"Bu günə qədər massiv, ArrayList, linear search, prefix sum, two pointers
gördünüz. İndi massivi necə **sortlamaq** olduğuna keçirik — 4 üsul, sondan
əvvəl ən sadədən ən ağıllısına."

## 5-25 dəq · Bubble sort

**İdeya:** yan-yana iki elementi müqayisə et, böyük olanı sağa "köpüklə" (bubble).
Bir keçiddə ən böyük element sona çıxır.

```
[5, 2, 4, 1]
keçid 1: 5>2→dəyiş [2,5,4,1] → 5>4→dəyiş [2,4,5,1] → 5>1→dəyiş [2,4,1,5]
keçid 2: 2>4? yox → 4>1→dəyiş [2,1,4,5]
keçid 3: 2>1→dəyiş [1,2,4,5]  → sortlandı
```

```java
static void bubbleSort(int[] a) {
    for (int i = 0; i < a.length - 1; i++) {
        for (int j = 0; j < a.length - 1 - i; j++) {
            if (a[j] > a[j + 1]) {
                int tmp = a[j]; a[j] = a[j + 1]; a[j + 1] = tmp;
            }
        }
    }
}
```

**Niyə `i < a.length - 1`, `j < a.length - 1 - i`?** — hər keçiddən sonra sonda
bir element artıq yerindədir, təkrar yoxlamağa ehtiyac yoxdur. Lövhəyə izah et.

Mürəkkəblik: **O(n²)** — ən pis və orta hal. Ən yaxşı hal (artıq sortlanmış):
O(n) **yalnız** early-exit (dəyişiklik olmadısa dayan) əlavə etsən.

## 25-40 dəq · Selection sort

**İdeya:** hər keçiddə qalan hissədən **ən kiçik** elementi tap, əvvələ qoy.

```
[5, 2, 4, 1]
keçid 1: ən kiçik=1 (indeks 3), 5 ilə dəyiş → [1, 2, 4, 5]
keçid 2: qalan [2,4,5]-də ən kiçik=2, yerindədir → [1, 2, 4, 5]
keçid 3: qalan [4,5]-də ən kiçik=4, yerindədir → sortlandı
```

```java
static void selectionSort(int[] a) {
    for (int i = 0; i < a.length - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < a.length; j++) {
            if (a[j] < a[minIndex]) minIndex = j;
        }
        int tmp = a[i]; a[i] = a[minIndex]; a[minIndex] = tmp;
    }
}
```

Bubble sort ilə fərqi vurğula: bubble **hər addımda** dəyişir, selection
**hər keçiddə bir dəfə** dəyişir (daha az swap, amma hələ O(n²) müqayisə).

Mürəkkəblik: **O(n²)** — həmişə, ən yaxşı hal da daxil (hər dəfə bütün qalanı
yoxlamaq lazımdır, bubble-dan fərqli olaraq early-exit mümkün deyil).

## 40-55 dəq · Insertion sort

**İdeya:** vərəqdəki kartları sırala kimi düşün — hər yeni kartı, artıq
sıralanmış hissənin **düzgün yerinə** soxursan.

```
[5, 2, 4, 1]
i=1 (2): sıralanmış hissə [5] → 2<5, sola keç → [2, 5, 4, 1]
i=2 (4): sıralanmış hissə [2,5] → 4<5, 4>2 → [2, 4, 5, 1]
i=3 (1): sıralanmış hissə [2,4,5] → 1 hamısından kiçik, əvvələ → [1, 2, 4, 5]
```

```java
static void insertionSort(int[] a) {
    for (int i = 1; i < a.length; i++) {
        int key = a[i];
        int j = i - 1;
        while (j >= 0 && a[j] > key) {
            a[j + 1] = a[j];
            j--;
        }
        a[j + 1] = key;
    }
}
```

Mürəkkəblik: ən pis hal **O(n²)** (tərsinə sortlanmış), amma ən yaxşı hal
(artıq sortlanmış) **O(n)** — `while` heç işləmir. Praktik olaraq kiçik və ya
"az qarışıq" massivlər üçün ən sürətli üçdən biridir.

## 55-80 dəq · Counting sort + stability

**İdeya:** elementlər məhdud aralıqdadırsa (məs. 0-100), hər qiymətin **neçə
dəfə** rast gəldiyini say, sonra sayğaclardan sırayla çıxış massivini qur.

```
[4, 2, 2, 8, 3, 3, 1]  →  dəyərlər 0-8 aralığında
sayğac:  0:0  1:1  2:2  3:2  4:1  5:0  6:0  7:0  8:1
çıxış:   1, 2, 2, 3, 3, 4, 8
```

```java
static int[] countingSort(int[] a, int maxValue) {
    int[] count = new int[maxValue + 1];
    for (int x : a) count[x]++;

    int[] result = new int[a.length];
    int index = 0;
    for (int value = 0; value <= maxValue; value++) {
        for (int c = 0; c < count[value]; c++) {
            result[index++] = value;
        }
    }
    return result;
}
```

**Vurğula:** bu, müqayisə əsaslı sortlama deyil — heç bir `a[i] > a[j]` yoxlanmır.
Buna görə O(n log n) sərhədini "qırır": mürəkkəblik **O(n + k)**, `k` = dəyər
aralığı. Qazanc şərti: `k` böyük deyilsə (yaşlar, qiymətlər 1-100, hərflər).
`k` çox böyükdürsə (məs. 32-bit tam ədədlər), fayda itir.

**Stability:** bərabər elementlərin **nisbi sırası** qorunur. Niyə vacib —
nümunə: tələbələri əvvəlcə adına görə sıralayıb sonra qiymətə görə sortlasan,
stabil sort eyni qiymətli tələbələrin ad sırasını qorur, qeyri-stabil qarışdıra
bilər. Bubble və insertion sort stabildir, counting sort da (yuxarıdaki yazılış
stabildir — sırayla say). Selection sort **stabil deyil** (uzaqdan gətirib
dəyişmə sırayı poza bilər) — nümunə ilə göstər.

## 80-90 dəq · Müqayisə və yekun

Lövhəyə cədvəl:

| | Ən yaxşı | Orta | Ən pis | Əlavə yaddaş | Stabil? |
|---|---|---|---|---|---|
| Bubble | O(n)* | O(n²) | O(n²) | O(1) | bəli |
| Selection | O(n²) | O(n²) | O(n²) | O(1) | xeyr |
| Insertion | O(n) | O(n²) | O(n²) | O(1) | bəli |
| Counting | O(n+k) | O(n+k) | O(n+k) | O(n+k) | bəli |

*early-exit optimizasiyası ilə

Mesaj: "Bu 4-ü **müqayisə əsaslı** (bubble/selection/insertion) vs **müqayisəsiz**
(counting) olaraq ikiyə bölürük. Gələn həftə daha ağıllı müqayisə əsaslı üsullar
— merge sort, quick sort — görəcəyik, O(n²)-ni O(n log n)-ə düşürəcəyik."

- Ev tapşırığı (`homework.md`)
- Sual-cavab

## Lövhəyə mütləq yazılacaqlar

1. Bubble sort-un bir keçidi (swap-larla)
2. Selection sort-un "qalan hissədən minimum tap" ideyası
3. Insertion sort-un kart metaforası
4. Counting sort-un sayğac massivi
5. 4 alqoritmin müqayisə cədvəli

## Gələn il üçün qeyd

Bu dərsin bütün 4 alqoritmi bir mühazirəyə sığması çox sıxdır — əgər ICAO
kimi bir kəsinti olmasa, bunu 2 həftəyə (Week 3: bubble+selection,
Week 4: insertion+counting) bölmək daha rahatdır.
