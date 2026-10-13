# Week 5 — Mühazirə: Sortlama I + Binary search (90 dəq)

**Qeyd (müəllim üçün):** bu, planda olan Week 5 mövzusu deyil — ICAO həftəsində
(Week 4) qalan sortlama materialı tam keçilməmişdi, bu mühazirə o boşluğu
bağlayır. Rekursiya + merge/quick sort + divide & conquer bu səbəbdən
**Week 6**-ya keçdi (bax `weeks/week-06/`). Binary search əlavədir — planda
rəsmən Week 6-nın mövzusudur, buraya "sortlamadan sonra axtarış" körpüsü kimi
tezləşdirilib, Week 6-da tam formal şəkildə (Big O ilə) təkrarlanacaq.

---

## Bubble Sort

Yan-yana olan iki elementi müqayisə edib səhv sıradadırlarsa yerini dəyişir —
hər keçiddə ən böyük element sona "köpüklənir".

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

**Məqsəd:** ən sadə sortlama ideyasını və swap məntiqini göstərmək.
**Harda daha yavaşdır:** demək olar hər yerdə — real layihədə istifadə olunmur,
yalnız təhsil məqsədilə göstərilir.

**Worst case:** O(n²) — tərsinə sıralı massiv.
**Best case:** O(n²), early-exit (dəyişiklik olmayan keçiddə dayan) əlavə
etsən **O(n)**-ə düşür.

---

## Selection Sort

Hər keçiddə **qalan hissədən ən kiçik** elementi tapıb əvvələ qoyur.

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

**Məqsəd:** "hər dəfə minimum tap" ideyasını göstərmək, az swap sayını
bubble sort-la müqayisə etmək.
**Harda daha yavaşdır:** həmişə bütün qalan hissəni yoxlayır — massiv artıq
sortlanmış olsa belə sürətlənmir (bubble/insertion-dan fərqli, early-exit yoxdur).

**Worst case:** O(n²).
**Best case:** O(n²) — heç bir giriş vəziyyəti yaxşılaşdırmır.

---

## Insertion Sort

Hər yeni elementi artıq sıralanmış hissənin düzgün yerinə "soxur" — kartları
əllə sıralamaq kimi.

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

**Məqsəd:** demək olar sıralı massivlərdə təbii sürətlənən sadə alqoritmi
göstərmək.
**Harda daha yavaşdır:** tərsinə sıralı/çox qarışıq massivlərdə hər element
demək olar əvvələ qədər sürüşməli olur.

**Worst case:** O(n²) — tərsinə sıralı massiv.
**Best case:** O(n) — artıq sortlanmış massiv, `while` heç işləmir.

---

## Counting Sort

Müqayisə etmədən, hər dəyərin **neçə dəfə** rast gəldiyini sayır, sonra
sayğaclardan nəticəni qurur.

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

**Məqsəd:** məhdud dəyər aralığında **müqayisəsiz**, xətti (O(n)-ə yaxın)
sortlamanın mümkün olduğunu göstərmək.
**Harda daha yavaşdır/zəifdir:** dəyər aralığı (`k`) böyük olanda (məs. 32-bit
tam ədədlər) yaddaş və vaxt həddindən artıq böyüyür; mənfi və ya kəsr
dəyərlərlə birbaşa işləmir.

**Worst case:** O(n + k).
**Best case:** O(n + k) — girişin sırasından asılı deyil, həmişə eynidir.

---

## Binary Search (əlavə)

Sıralanmış massivdə ortadan başlayıb, axtarılan dəyərə görə sol və ya sağ
yarını bir kənara atır.

```java
static int binarySearch(int[] a, int target) {
    int left = 0, right = a.length - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (a[mid] == target) return mid;
        else if (a[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}
```

**Məqsəd:** sıralanmış massivdə linear search-dən (O(n)) qat-qat sürətli
axtarışı göstərmək — bu günün sortlama mövzusunu axtarışla bağlamaq körpüsü.
**Harda daha yavaşdır/zəifdir:** massiv **sıralı olmalıdır** (sıralama xərci
var), sıralanmamış massivdə işləmir; linked list kimi ardıcıl girişli
strukturlarda ortaya "sıçramaq" mümkün olmadığı üçün səmərəsizdir.

**Worst case:** O(log n).
**Best case:** O(1) — axtarılan dəyər elə ilk ortada çıxır.
