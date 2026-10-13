# Week 5 — Məşğələ: Bubble, insertion, selection, counting sort + Sliding window (90 dəq)

**Qeyd (müəllim üçün):** planda olan Week 5 məşğələsi deyil — bax `lecture.md`-dəki
qeyd. Rekursiya/merge/quick sort/divide & conquer `weeks/week-06/`-ya keçdi.
Bunun yerinə bu həftənin pattern-i **sliding window** oldu (planda ikinci
mərtəbədə, Week 6 üçün nəzərdə tutulmuşdu — bura tezləşdi).

**Məqsəd:** hər tələbə 4 sortlama alqoritmini sıfırdan yaza bilsin, nəticələri
müqayisə etsin, sliding window pattern-ini (sabit ölçü) tanısın.

Yarımqruplar ayrı — eyni plan iki dəfə. **Şifahi sorğu davam edir**
(`assessment/oral.md`, Week 2-4 əhatəsində) — bu məşğələdə də 3-4 nəfər çağır,
sortlama koda yazma blokunda (10-50 dəq) paralel apar.

## 0-8 dəq · Təkrar

Kodsuz, lövhədə: "Linear search niyə O(n)? Prefix sum niyə qurulduqdan sonra
sorğu O(1)?" — keçən həftənin köprüsü.

## 8-50 dəq · 4 alqoritmi sıfırdan yaz

Şablon vermə — mühazirədə gördükləri ideyadan özləri kodlasın. Sən lövhədə
pseudocode-u xatırlat, kodu demə. **Bu blokda paralel şifahi sorğu apar**
(3-4 nəfər, Week 2-4 əhatəsində).

1. **Bubble sort** — iç-içə dövr, yan-yana müqayisə
2. **Selection sort** — qalan hissədən minimum tapıb əvvələ qoy
3. **Insertion sort** — sıralanmış hissəyə düzgün yerə soxmaq
4. **Counting sort** — sayğac massivi (yalnız 0-100 aralığında ədədlər üçün sına)

Hər alqoritmi eyni test massivində işlət, nəticələri çap et, hamısının eyni
sortlanmış nəticəni verdiyini göstər:

```java
int[] test = {5, 2, 9, 1, 5, 6, 3};
```

Tez bitirən olsa, `System.nanoTime()` ilə 4-ünü böyük massivdə (məs. 10.000
element) ölçdürt, fərqi gör.

## 50-55 dəq · Körpü: frequency array-dan sliding window-a

Qısa xatırlatma (bloka çevirmə): "Week 4-də frequency array pattern-ini
gördünüz — bütün massivi gəzib sayğac qurmaq. Bəzən isə bütün massivə yox,
massivin **ardıcıl bir parçasına** (pəncərə) baxmaq lazımdır. Bu, sliding
window-dur."

## 55-85 dəq · Pattern: Sliding window (sabit ölçü)

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
çıxarılır. Bu, həmin "iki yol, bir sürət fərqi" hissinin (Week 2) davamıdır.

Məsələlər (LeetCode, sabit ölçü pəncərə):
1. **Maximum Average Subarray I (643)** — yuxarıdaki kodun üstündə, cəmi `k`-ya böl
2. **Maximum Sum Subarray of Size K** (GeeksforGeeks klassiki, LeetCode-da yoxdur
   amma çox tapşırılır) — yuxarıdaki kodu birbaşa yaz

**Bonus (tez bitirənlər üçün, dəyişən ölçü pəncərə — qabaqcadan göstər):**
3. **Minimum Size Subarray Sum (209)** — pəncərə böyüyür/kiçilir, cəm şərtə görə

Gəzirsən, ilişənə sual verirsən, kodu demirsən.

## 85-90 dəq · Push

Hamı `week-05/` qovluğuna push etsin. Push etməyəni və şifahi sorğuda kim
çağırıldığını qeyd et.

## Müəllim qeydi

Bu məşğələ əslində Week 3/4-ün tamamlanmasıdır (bubble sort rəsmən Week 3-ün,
counting sort Week 4-ün mövzusu idi, ICAO-due düzgün keçilməmişdi). Insertion
və selection sort rəsmi planda yoxdur, bu il əlavə edilib. Sliding window
planda Week 6 üçün (ikinci mərtəbə) nəzərdə tutulmuşdu, bura tezləşdi —
`patterns/README.md`-i buna uyğun yenilə.
