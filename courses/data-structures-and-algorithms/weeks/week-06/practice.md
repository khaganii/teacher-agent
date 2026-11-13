# Week 6 — Məşğələ: Merge sort, quick sort, divide & conquer + Sliding window (90+ dəq)

**Qeyd (müəllim üçün):** rəsmi planda bu, Week 5-in məşğələsidir — bax
`lecture.md`-dəki sürüşmə qeydi. Əlavə olaraq: sliding window pattern Week
5-ə aid idi (hazır blok var idi, `weeks/week-05/practice.md`), amma dərsdə
ona çatılmadı. Aşağıda **əlavə blok** kimi bura keçdi — heç nə qısaldılmayıb,
dərs 90 dəqiqədən artıq uzanacaq, ona görə sürətlə apar.

**Məqsəd:** hər tələbə merge sort-u tam koda çevirə bilsin, quick sort-un
partition addımını izləyə/dəyişə bilsin, pattern olaraq divide & conquer-i tanısın.

Yarımqruplar ayrı — eyni plan iki dəfə. **Şifahi sorğu davam edir**
(`assessment/oral.md`-dəki qrafikə görə, indi Week 2-5 əhatəsində — keçən
həftənin bubble/insertion/selection/counting sort-u da daxildir).

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
3-4 nəfəri çağırıb şifahi sorğu aparırsan (`assessment/oral.md` — indi
Week 2-5, 10 bal). Təsadüfi çağır, əvvəlcədən demə.

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

## +20 dəq · Pattern: Sliding window (sabit ölçü) — əlavə blok

**Qeyd:** Week 5-dən qalıb, buraya əlavə olundu — 90 dəqiqəlik əsas plandan
sonra gəlir.

**İdeya:** `k` ölçülü pəncərəni massiv üzərində sürüşdür, hər addımda yalnız
**çıxan və daxil olan** elementi hesaba al — hər dəfə bütün pəncərəni yenidən
cəmləməyə ehtiyac yoxdur.

```
a = [2, 1, 5, 1, 3, 2], k = 3

pəncərə [2,1,5] cəm=8
sürüşdür: cəm = cəm - a[0] + a[3] = 8 - 2 + 1 = 7   → [1,5,1]
sürüşdür: cəm = cəm - a[1] + a[4] = 7 - 1 + 3 = 9   → [5,1,3]
sürüşdür: cəm = cəm - a[2] + a[5] = 9 - 5 + 2 = 6   → [1,3,2]
```

```java
static int maxSumSubarray(int[] a, int k) {
    int windowSum = 0;
    for (int i = 0; i < k; i++) windowSum += a[i];   // ilk pəncərə

    int maxSum = windowSum;
    for (int i = k; i < a.length; i++) {
        windowSum += a[i] - a[i - k];                // çıxan/daxil olan
        maxSum = Math.max(maxSum, windowSum);
    }
    return maxSum;
}
```

**Vurğula:** brute force (hər pəncərəni sıfırdan cəmləmək) O(n×k) olardı,
sliding window ilə **O(n)** — hər element yalnız bir dəfə əlavə, bir dəfə
çıxarılır.

Məsələlər (LeetCode, sabit ölçü pəncərə):
1. **Maximum Average Subarray I (643)** — yuxarıdaki kodun üstündə, cəmi `k`-ya böl

**Bonus (vaxt qalsa, dəyişən ölçü pəncərə — qabaqcadan göstər):**
2. **Minimum Size Subarray Sum (209)** — pəncərə böyüyür/kiçilir, cəm şərtə görə

Gəzirsən, ilişənə sual verirsən, kodu demirsən.

## Push

Hamı `week-06/` qovluğuna push etsin. Push etməyəni və şifahi sorğuda kim
çağırıldığını qeyd et.

## Müəllim qeydi

Partition-un tam kodu mühazirədə yox, burada verilir — plan belə qərarlaşdırılıb
(bax `plan.md`, "Sıx həftələr" — rəsmən Week 5 üçün, bu il Week 6-ya tətbiq
olunur). Vaxt azalsa, Sort Colors-u at, yalnız Merge Sorted Array + Sort an
Array kifayətdir.

Sliding window bloku əlavədir (Week 5-dən qalıb) — dərsi 90 dəqiqədən artıq
uzadır. Vaxt tam yoxdursa, bonus (Minimum Size Subarray Sum) at, yalnız
Maximum Average Subarray I kifayətdir; hələ də sıxışırsa, sliding window-u
ev tapşırığına burax.
