# Week 3 — Məşğələ: Massivlər + ArrayList (90 dəq)

**Məqsəd:** dərsin sonunda hər tələbə array və ArrayList arasındakı fərqi bilsin,
hər ikisi üzərində traversal/cəm/max/axtarış yaza bilsin.

Yarımqruplar ayrı — eyni plan iki dəfə.

**Qeyd:** bu, rəsmi planda Week 3-ün mövzusudur, adi vaxtından tez keçilir —
bax `semesters/2026-2027-payiz.md`.

## 0-8 dəq · Təkrar

Kodsuz, sürətli-atəş, lövhədə. `week-02/warmup.md`-dən 3 sual:

- **#5** — cüt/tək (`if/else`)
- **#13** — 1-dən n-ə cəm (`for`)
- **#17** — 0 yazana qədər davam (`while`)

Hər sual: məntiqi şifahi sor, 1 nəfər lövhədə kodlasın. ~2-3 dəq/sual.

## 8-26 dəq · Array giriş və traversal

Canlı yaz, onlar yazsın.

```java
int[] nömrələr = new int[5];        // boş, 5 xana, default 0
int[] yaşlar = {23, 19, 31, 27, 22}; // birbaşa doldur
System.out.println(yaşlar[0]);       // indeks 0-dan başlayır
System.out.println(yaşlar.length);   // uzunluq, mötərizəsiz
yaşlar[2] = 30;                      // xananı dəyiş
```

Sonra traversal + cəm:

```java
for (int i = 0; i < yaşlar.length; i++) {
    System.out.println(yaşlar[i]);
}

int cəm = 0;
for (int i = 0; i < yaşlar.length; i++) {
    cəm += yaşlar[i];
}
```

Bağla: çərşənbə günkü mühazirədən "massiv yaddaşda" (ardıcıl xanalar,
`a[5]` = O(1), ölçü sabitdir) — bunu indi kodda göstərirsən.

## 26-42 dəq · ArrayList giriş

Motivasiya: array-in ölçüsü sabitdir, dolubsa yeni massiv yaradıb köçürmək
lazımdır. ArrayList bunu həll edir.

```java
import java.util.ArrayList;

ArrayList<Integer> siyahı = new ArrayList<>();
siyahı.add(5);
siyahı.add(10);
siyahı.add(15);

System.out.println(siyahı.get(0));       // 5
System.out.println(siyahı.size());       // uzunluq — .length YOX
siyahı.remove(0);                        // silmə — array-də yoxdur
System.out.println(siyahı.contains(10)); // true
```

Lövhəyə mütləq yazılacaq **iki tələ**:

1. `ArrayList<int>` YAZILMIR, mütləq `ArrayList<Integer>` — primitiv tip
   generic-ə girmir.
2. Uzunluq üçlüyü — yan-yana yaz: array → `.length`, String → `.length()`,
   ArrayList → `.size()`.

For-each göstər, adi `for`-la müqayisə et:

```java
for (int x : siyahı) {
    System.out.println(x);
}
```

## 42-80 dəq · Sərbəst iş — 10 sual + bonus

Özləri yazır. Gəzirsən, ilişənə kömək edirsən — həllini demirsən, sual verirsən.
Hamı 10-a çatmayacaq, normaldır.

**Array**
1. Massivin elementlərinin cəmini tap.
2. Massivdə ən böyük elementi tap.
3. Massivdə cüt ədədlərin sayını tap.
4. Massivi tərsinə çap et.
5. Verilən ədəd massivdə neçə dəfə rast gəlinir, say.

**ArrayList**
6. Boş `ArrayList<Integer>` yarat, istifadəçidən 5 ədəd `add` et, for-each ilə
   çap et.
7. ArrayList-dəki elementlərin cəmini tap.
8. ArrayList-dəki ən böyük elementi tap.
9. Verilən ədədi siyahıdan `remove` et.
10. Siyahıda verilən ədəd `contains` olub-olmadığını yoxla.

**Bonus (tez bitirənlər üçün)**

11. Massivdə hər fərqli ədədin neçə dəfə təkrarlandığını tap və çap et.
    Məsələn `{1, 2, 2, 3, 1, 1}` → `1: 3 dəfə`, `2: 2 dəfə`, `3: 1 dəfə`.
    İki iç-içə dövrdən istifadə et — artıq sayılmış ədədi bir daha sayma.
    (Bu, Week 4-ün "Frequency array" pattern-inin erkən görüntüsüdür — indi
    sadəcə işləyən nested-loop həll kifayətdir, optimallaşdırma sualı verməyin.)

## 80-84 dəq · Yekun müqayisə

Lövhəyə cədvəl: array (sabit ölçü, sürətli) vs ArrayList (dəyişən ölçü,
`add`/`remove` var). "Nə vaxt hansını seçərsən?" sualı ver, cavab al.

## 84-87 dəq · Ev tapşırığı preview

`homework.md`-dəki `MyArrayList` skeletini lövhədə göstər — bir `class`
daxilində field və metodun necə yazıldığını 2-3 dəqiqə izah et. Sintaksisi
indi görməsələr, evdə tək başına çətin olar.

## 87-90 dəq · Push

Hamı `week-03/` qovluğuna push etsin. Push etməyəni qeyd et.

## Müəllim qeydi

Bu məşğələdə pattern rəsmən verilmir (Two pointers Week 3 mühazirəsindədir,
bura sadəcə praktika sıxışdırılıb). Bonus sual frequency pattern-inin ilk
görüntüsüdür, formal deyil.
