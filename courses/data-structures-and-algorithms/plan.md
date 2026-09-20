# İş planı — 15 həftə

Tarix yoxdur. Həftə nömrələri semestrin həftələridir və rəsmi sillabusla eyni
nömrələnir (aralıq imtahan 8-ci həftədə). Konkret semestrin tarixləri:
`semesters/` qovluğunda.

## Əsas qərarlar

- **Java ayrıca mövzu deyil.** Hər həftənin məşğələsində, o həftənin mövzusu üçün
  lazım olan qədər verilir. `class`/`Node` OOP həftəsində yox, əlaqəli siyahı
  həftəsində gəlir.
- **Həftədə bir pattern.** Yeni başlayanlar üçün bir dənə kifayətdir. Həmin
  həftənin bütün ev tapşırığı eyni pattern-dəndir.
- **DFS və BFS ağac həftəsində öz adları ilə öyrədilir** — buna görə qraflar
  sonda bir həftəyə sığır.
- **Rekursiya ayrıca həftə tutmur** — merge/quick sort-un içində, real məsələ
  üstündə gəlir.
- **15-ci həftə rezervdir.** Geri qalma, final hazırlığı, planda yeri olmayan
  mövzular (string alqoritmləri, segment tree, mürəkkəblik sinifləri) üçün.

## Həftələr

| # | Mövzu | Mühazirə | Məşğələ | Pattern |
|---|---|---|---|---|
| 1 | Kursa giriş | Fənn, qaydalar, qiymətləndirmə, yol xəritəsi | Alət quraşdırma: IntelliJ, JDK, Git, GitHub, LeetCode | — |
| 2 | Alqoritmə giriş | Alqoritm nədir, eyni məsələnin iki həlli, "sürət" hissi, massiv yaddaşda | Java minimum + IntelliJ debug + 5 warm-up | — (brute force) |
| 3 | Massivlər | Massiv əməliyyatları, traversal, prefix sum, linear search, bubble sort | Java: massiv 1D/2D, String/StringBuilder + massiv məsələləri | **Two pointers** |
| 4 | Sortlama I | Counting sort, stability, sortlama alqoritmlərinin müqayisəsi | Bubble və counting sort-u sıfırdan yazmaq | **Frequency array** |
| 5 | Rekursiya və sortlama II | Rekursiya (call stack, base case), divide & conquer, merge sort, quick sort, quickselect | Rekursiv metodlar, merge sort-u kodlamaq | **Divide & conquer** |
| 6 | Axtarış və asimptotik analiz | Binary search, sərhəd xətaları, Big O, run time vs memory, sortların müqayisə cədvəli | Binary search şablonu, off-by-one ovu, mürəkkəblik təyini | **Binary search şablonu** |
| 7 | Xətti strukturlar | Node anlayışı, əlaqəli siyahı, stek, növbə, tətbiqləri, ADT | Java: `class`, `Node`, generics → `MyStack`, `MyQueue` + midterm təkrarı | **Fast & slow**, stack balansı |
| 8 | **ARALIQ İMTAHAN** | Sortlama II təkrarı / imtahana hazırlıq | **İmtahan** (məşğələ saatında) | — |
| 9 | Ağaclar | Terminologiya, DFS (pre/in/post), BFS, BST invariantı, search/insert/delete | BST qurmaq, 4 traversal yazmaq | **Tree DFS** |
| 10 | Çoxluqlar, cədvəllər, heap | Hashing: hash funksiyası, collision, load factor ‖ Heap: sift up/down, PriorityQueue, heap sort | Frequency map + top-K (sort vs heap müqayisəsi) | **Frequency map / Top-K** |
| 11 | Acgöz alqoritmlər | Greedy choice, exchange argument, greedy nə vaxt sınır, activity selection, job scheduling | Interval məsələləri | **Sortla, bir keçiddə seç** |
| 12 | Dinamik proqramlaşdırma I | Overlapping subproblems, optimal substructure, rekursiya → memoization | Naive rekursiya → ölç → memo → ölç | **1D DP** |
| 13 | Dinamik proqramlaşdırma II | Tabulation, knapsack, LCS, edit distance (Kadane və LIS məşğələdə) | DP cədvəlini əllə doldur, sonra kodla | **Grid DP** |
| 14 | Qraflar | Təsvir (matrix/list), DFS, BFS, cycle detection, topological sort, Dijkstra, Floyd-Warshall | Grid DFS məsələləri — islands, maze | **Grid DFS / flood fill** |
| 15 | **REZERV** | Geri qalan mövzu / string alqoritmləri / mürəkkəblik sinifləri / final təkrarı | Mock exam, pattern təkrarı | Təkrar |

## Sıx həftələr — bilərəkdən belədir

- **Week 5** — rekursiya + 2 sort 90 dəqiqəyə çətin sığır. Quick sort-un partition
  detalını məşğələyə at.
- **Week 13** — tabulation + knapsack + LCS + edit distance + Kadane + LIS bir
  mühazirəyə sığmır. Mühazirədə tabulation + knapsack + LCS; Kadane və LIS
  məşğələdə nümunə kimi; edit distance self-study.
- **Week 14** — Dijkstra-ya təxminən 30 dəqiqə qalır. Floyd-Warshall icmal
  səviyyəsində.

Week 15 rezervi məhz bunların əvəzini ödəmək üçündür.

## Qiymətləndirmə axını

| Həftə | Nə baş verir |
|---|---|
| 5-7 | Şifahi sorğu rotasiyası — hər məşğələdə 3-4 nəfər (bax: `assessment/oral.md`) |
| 8 | Aralıq imtahan (30%) |
| 9 | Layihə mövzularının paylanması |
| 10-14 | Tələbə təqdimatları — hər məşğələdə 2 nəfər (layihə, 20%) |
| 16-20 | Yekun imtahan (50%) |
