# Week 6 — Mühazirə: Rekursiya və sortlama II (90 dəq)

**Qeyd (müəllim üçün):** rəsmi planda bu, Week 5-in mövzusudur (bax `plan.md`),
amma ICAO həftəsində (Week 4) qalan bubble/insertion/selection/counting sort
materialı Week 5-ə keçdiyi üçün rekursiya/merge/quick sort bir həftə sürüşüb
bura gəldi (bax `weeks/week-05/lecture.md`-dəki qeyd və
`semesters/2026-2027-payiz.md`).

**Məqsəd:** tələbə rekursiyanı (call stack, base case) başa düşsün, merge sort və
quick sort-un **ideyasını** izah edə bilsin. Quick sort-un partition detalı
burada deyil — məşğələdə canlı kodlanacaq (bax `practice.md`).

**Qeyd:** bu, sıx həftədir — plana görə rekursiya + 2 sort 90 dəqiqəyə çətin
sığır. Vaxt azalsa, quickselect-i qısalt, əsas itki ora getsin.

**Faktiki nəticə:** mühazirə saatında yalnız rekursiya bölməsinə çatıldı.
Merge sort/quick sort/quickselect ayrıca əlavə mühazirə saatına keçdi — bax
`extra-lecture.md` və `notes.md`.

## Açılış

Keçən həftə bubble, insertion, selection, counting sort yazıldı. Bunu körpü
kimi işlət: "bu dördü O(n²) və ya əlavə yaddaş istəyirdi — bu gün daha ağıllı
bir yol görəcəyik."

## Rekursiya

Tərifdən yox, nümunədən başla.

**Nümunə: faktorial**
```
fakt(5) = 5 × fakt(4)
fakt(4) = 4 × fakt(3)
fakt(3) = 3 × fakt(2)
fakt(2) = 2 × fakt(1)
fakt(1) = 1              ← base case
```

Lövhəyə call stack-i **qutu-qutu** çək — hər çağırış yeni qutu, qutu öz
içindəki nəticəni gözləyir, sonra aşağı-yuxarı geri qatlanır. Bu şəkil
semestrin qalanında da (merge sort, ağaclar) işə düşəcək.

```java
static int fakt(int n) {
    if (n == 1) return 1;      // base case — bunsuz sonsuz çağırış
    return n * fakt(n - 1);    // recursive case
}
```

**İki şərt mütləq vurğulanacaq:**
1. Base case olmalıdır, yoxsa `StackOverflowError`.
2. Hər çağırış problemi **kiçildir** (n → n-1), yoxsa heç vaxt base case-ə çatmaz.

Canlı göstər: base case-i sil, kodu çalıştır, `StackOverflowError`-u ekranda göstər.
Bu, sözdən daha yaxşı yadda qalır.

**Sual ver:** "Rekursiya ilə dövr arasında fərq nədir? Hansı zaman rekursiya
daha təbiidir?" → cavab: problem öz-özünün kiçik versiyasına bölünəndə
(ağac, divide & conquer).

## Merge sort

**İdeya əvvəl, kod sonra.** Lövhəyə 8 elementlik massiv çək, əl ilə bölə-bölə
göstər:

```
[8, 3, 5, 1, 9, 2, 7, 4]
    /              \
[8,3,5,1]        [9,2,7,4]
  /    \            /    \
[8,3]  [5,1]    [9,2]   [7,4]
 / \    / \      / \     / \
[8][3] [5][1]  [9][2]  [7][4]
```

Sonra geri **birləşdirərək** sortla (merge) — iki sortlanmış kiçik siyahını
bir sortlanmış böyük siyahıya çevir. Bu addımı lövhədə bir cüt üzərində əl ilə
et: `[3,8]` + `[1,5]` → göstəricilərlə addım-addım `[1,3,5,8]`.

**Divide & conquer** adını indi ver: *böl (divide) → kiçik hissələri həll et
(conquer, rekursiya ilə) → birləşdir (combine)*. Bu, bu həftənin pattern-idir —
gələn həftələrdə tez-tez görəcəklər.

```java
static void mergeSort(int[] a, int left, int right) {
    if (left >= right) return;              // base case — 1 və ya 0 element
    int mid = (left + right) / 2;
    mergeSort(a, left, mid);                // sol yarını sortla
    mergeSort(a, mid + 1, right);           // sağ yarını sortla
    merge(a, left, mid, right);             // ikisini birləşdir
}
```

`merge` metodunun daxilini kod olaraq yazma — ideyası kifayətdir, tam kod
məşğələdə. Mürəkkəbliyi ver: **O(n log n)**, həmişə — ən yaxşı, orta, ən pis
hal fərq etmir. Niyə: log n səviyyə, hər səviyyədə n iş.

Yaddaş: merge sort əlavə massiv istəyir — **O(n) əlavə yaddaş**. Keçən həftənin
sortları ilə müqayisə et (lövhəyə əlavə sətir): stabil, əlavə yaddaş istəyir.

## Quick sort (konseptual)

**İdeya:** bir element seç (**pivot**), massivi pivotdan kiçiklər və böyüklər
olaraq iki yerə böl (**partition**), hər iki yarını rekursiv sortla. Merge
sort-dan fərqi: birləşdirmə addımı yoxdur — partition özü işi görür.

```
pivot = axırıncı element seçilsin: [8, 3, 5, 1, 9, 2, 7, 4]
                                                          ^pivot=4
partition-dan sonra: [3, 1, 2] [4] [8, 5, 9, 7]
                      kiçiklər  piv   böyüklər
```

Partition-un addım-addım necə işlədiyini (iki göstərici, dəyişmə) **kodlamadan**,
yalnız oxla göstər — tam kod məşğələdə canlı yazılacaq.

Mürəkkəblik: orta halda **O(n log n)**, ən pis halda (artıq sortlanmış massiv,
həmişə ən kiçik/böyük pivot seçilsə) **O(n²)**. Niyə pivot seçimi vacibdir —
bunu şifahi sorğuda soruşacaqsan (bax `assessment/oral.md`).

Merge sort vs quick sort cədvəli lövhəyə:

| | Merge sort | Quick sort |
|---|---|---|
| Əlavə yaddaş | O(n) | O(1) (in-place) |
| Ən pis hal | O(n log n) | O(n²) |
| Stabil? | bəli | xeyr |
| Praktikada | — | adətən daha sürətli (cache-friendly) |

## Quickselect (qısa)

Bir cümlə ilə bağla: "K-ci ən kiçik elementi tapmaq üçün massivi **tam**
sortlamağa ehtiyac yoxdur — partition-u bir tərəfə davam etdir, digər tərəfi at."
Kod yox, yalnız ideya. Tam material Week 10-da top-K məsələsində qayıdacaq.

## Yekun və tapşırıq

- Bu həftə məşğələdə nə olacaq: rekursiv metodlar + merge sort-u tam kodlamaq +
  quick sort partition-u canlı yazmaq
- Ev tapşırığı (`homework.md`)
- Şifahi sorğu davam edir (indi Week 2-5 əhatəsində — keçən həftənin sortları
  da daxil oldu)

## Lövhəyə mütləq yazılacaqlar

1. Faktorial call stack-i (qutu-qutu)
2. Merge sort-un bölünmə ağacı (8 elementlik nümunə)
3. Quick sort-un bir partition addımı
4. Merge sort vs quick sort cədvəli

## Gələn il üçün qeyd

Quickselect-ə ayrılan 10 dəqiqə bu il bir az yarışdı keçdi — gələn il bunu
tamam Week 10-a köçürmək, burada heç adını çəkməmək də olar. Həmçinin: əgər
ICAO kimi kəsinti olmasa, bu mövzu öz həftəsinə (rəsmən Week 5) qayıtmalıdır.
