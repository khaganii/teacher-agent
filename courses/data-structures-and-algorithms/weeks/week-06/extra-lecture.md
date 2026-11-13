# Week 6 — Əlavə mühazirə: Quick sort, quickselect

**Qeyd (müəllim üçün):** normal mühazirə saatında yalnız **rekursiya** keçildi
(bax `lecture.md`). 22 oktyabrda merge sort və sliding window pattern də
keçildi (bax `notes.md`) — bu fayldan merge sort bölməsi artıq çıxarılıb.
Qalan yalnız **quick sort + quickselect**-dir.

**Məqsəd:** tələbə quick sort-un **ideyasını** izah edə bilsin. Partition-un
detalı burada deyil — məşğələdə canlı kodlanacaq (bax `practice.md`).

## Açılış

Rekursiya və merge sort artıq keçilib. Körpü: "merge sort-da **birləşdirərək**
sortladıq — bu gün birləşdirmə addımı olmayan başqa bir divide & conquer
üsuluna baxaq: quick sort."

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

## Yekun

- Qısa sessiyadır — əsas məqsəd quick sort-un ideyasını məşğələdən (partition
  canlı kodlanmasından) əvvəl vermək.
- Məşğələdə (`practice.md`) partition-un tam kodu yazılacaq.

## Lövhəyə mütləq yazılacaqlar

1. Quick sort-un bir partition addımı
2. Merge sort vs quick sort cədvəli
