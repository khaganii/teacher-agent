# Week 5 — Məşğələ: Merge sort, quick sort, divide & conquer (90 dəq)

**Məqsəd:** hər tələbə merge sort-u tam koda çevirə bilsin, quick sort-un
partition addımını izləyə/dəyişə bilsin, pattern olaraq divide & conquer-i tanısın.

Yarımqruplar ayrı — eyni plan iki dəfə. **Bu məşğələdə şifahi sorğu da başlayır**
(bax aşağıda, 55-85 dəq bloku) — `assessment/oral.md`-dəki qrafikə görə hər
yarımqrupdan 3-4 nəfər, Week 2-4 əhatəsində (massiv, bubble/counting sort,
linear search).

## 0-10 dəq · Rekursiya isinmə

Kodsuz, lövhədə, sürətli-atəş:

- "fakt(4) çağırılanda neçə qutu (stack frame) açılır?" — birlikdə say
- "Base case olmasa nə olar?" — `StackOverflowError`
- 1 nəfər lövhədə Fibonacci-ni rekursiv yazsın: `fib(n) = fib(n-1) + fib(n-2)`,
  base case `fib(0)=0, fib(1)=1`

Bağla: "Fibonacci-nin rekursiv versiyası çox təkrar iş görür — bunu Week 12-də
(memoization) düzəldəcəyik. Bu gün problemi **doğru bölən** rekursiyaya baxırıq."

## 10-40 dəq · Merge sort — tam kod

Canlı yaz, onlar yazsın. Əvvəlcə `merge` (birləşdirmə), sonra `mergeSort`.

```java
static void merge(int[] a, int left, int mid, int right) {
    int[] temp = new int[right - left + 1];
    int i = left, j = mid + 1, k = 0;

    while (i <= mid && j <= right) {
        if (a[i] <= a[j]) temp[k++] = a[i++];
        else temp[k++] = a[j++];
    }
    while (i <= mid)   temp[k++] = a[i++];
    while (j <= right) temp[k++] = a[j++];

    for (int x = 0; x < temp.length; x++) {
        a[left + x] = temp[x];
    }
}

static void mergeSort(int[] a, int left, int right) {
    if (left >= right) return;
    int mid = (left + right) / 2;
    mergeSort(a, left, mid);
    mergeSort(a, mid + 1, right);
    merge(a, left, mid, right);
}
```

**Lövhəyə mütləq:** `merge`-i kiçik nümunə üzərində (`[3,8]` + `[1,5]`) üç
göstəricini (`i`, `j`, `k`) əl ilə izləyərək göstər — mühazirədə ideya
görmüşdülər, burada göstəricilərin necə irəlilədiyini görsünlər.

Sına: `main`-də 8 elementlik qarışıq massiv ver, çap et, çağır, yenə çap et.

**Tez-tez düşülən xəta:** `mergeSort(a, 0, a.length)` yazırlar — `a.length - 1`
olmalıdır, çünki `right` indeksdir, uzunluq deyil. Lövhəyə qırmızı ilə işarələ.

## 40-55 dəq · Quick sort — partition canlı

```java
static int partition(int[] a, int left, int right) {
    int pivot = a[right];       // sonuncu element pivot
    int i = left - 1;           // pivotdan kiçiklərin son indeksi

    for (int j = left; j < right; j++) {
        if (a[j] < pivot) {
            i++;
            int tmp = a[i]; a[i] = a[j]; a[j] = tmp;
        }
    }
    int tmp = a[i + 1]; a[i + 1] = a[right]; a[right] = tmp; // pivotu yerinə qoy
    return i + 1;                // pivotun son indeksi
}

static void quickSort(int[] a, int left, int right) {
    if (left >= right) return;
    int pivotIndex = partition(a, left, right);
    quickSort(a, left, pivotIndex - 1);
    quickSort(a, pivotIndex + 1, right);
}
```

Partition-u **kiçik nümunədə əl ilə izlə** (lövhədə, kod yazmadan əvvəl):
`[8,3,5,1,4]`, pivot = `4`. `i` və `j`-nin hər addımda harada olduğunu göstər,
sonra kodu yaz.

Sına: eyni 8 elementlik massivi quick sort-la sortla, nəticəni merge sort-la
müqayisə et (ikisi də düzgün sortlayırsa, yaxşı).

## 55-85 dəq · Sərbəst iş + pattern + şifahi sorğu

**Bu blok paralel gedir:** əksəriyyət məsələ həll edir, sən rotasiya ilə
3-4 nəfəri çağırıb şifahi sorğu aparırsan (`assessment/oral.md` — Week 2-4,
massiv/bubble/counting sort/linear search, 10 bal). Təsadüfi çağır,
əvvəlcədən demə.

**Pattern: Divide & conquer** (son 20 dəqiqənin əsas məzmunu, sorğu ilə yanaşı
ver) — *böl, kiçik hissəni həll et, birləşdir*. Bu gün görülən merge sort elə
bu pattern-in nümunəsidir.

Məsələlər (LeetCode):
1. **Merge Sorted Array (88)** — iki sortlanmış massivi birləşdir, merge
   addımına çox bənzəyir
2. **Sort an Array (912)** — bu gün yazdığın `mergeSort`-u və ya `quickSort`-u
   birbaşa istifadə et
3. **Sort Colors (75)** — bonus, tez bitirənlər üçün (Dutch flag, partition-a
   bənzər fikir)

Gəzirsən, ilişənə sual verirsən, həllini demirsən.

## 85-90 dəq · Push

Hamı `week-05/` qovluğuna push etsin. Push etməyəni və şifahi sorğuda kim
çağırıldığını qeyd et (bal cədvəli üçün).

## Müəllim qeydi

Partition-un tam kodu mühazirədə yox, burada verilir — plan belə qərarlaşdırılıb
(bax `plan.md`, "Sıx həftələr"). Vaxt azalsa, Sort Colors-u at, yalnız Merge
Sorted Array + Sort an Array kifayətdir.
