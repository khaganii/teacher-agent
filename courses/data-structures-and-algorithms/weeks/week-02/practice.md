# Week 2 — Məşğələ: Java minimum + warm-up (90 dəq)

**Məqsəd:** dərsin sonunda hər tələbə boş fayldan başlayıb işləyən Java proqramı
yaza, işə sala və debug edə bilsin.

Yarımqruplar ayrı — eyni plan iki dəfə.

## 0-15 dəq · Java skeleti

Canlı yaz, onlar da yazsın. Slayd yoxdur.

```java
public class Main {
    public static void main(String[] args) {
        int a = 5;
        double b = 2.5;
        boolean c = true;
        String s = "salam";
        System.out.println(a + " " + b + " " + c + " " + s);
    }
}
```

- `int`, `double`, `boolean`, `String` — bu dörd tip hələlik bəsdir
- `System.out.println` vs `System.out.print`
- Scanner ilə giriş:
  ```java
  Scanner sc = new Scanner(System.in);
  int n = sc.nextInt();
  ```

## 15-30 dəq · Şərt və dövr

```java
if (n % 2 == 0) System.out.println("cüt");
else            System.out.println("tək");

for (int i = 1; i <= n; i++) System.out.println(i);

int i = 0;
while (i < n) { System.out.println(i); i++; }
```

Birini lövhədə yaz, ikincisini onlar yazsın. Gəz, ekranlara bax.

## 30-40 dəq · Metod

```java
static int sum(int a, int b) {
    return a + b;
}
```

- `static` niyə lazımdır (hələlik: "main-dən çağıra bilmək üçün")
- parametr, qaytarılan dəyər, `void`

## 40-55 dəq · IntelliJ debug — semestrin ən dəyərli 15 dəqiqəsi

Bir dövrün içinə qəsdən səhv qoy (məsələn `i <= n` əvəzinə `i < n`), sonra:

1. Sətrin solunda **breakpoint** qoy (qırmızı nöqtə)
2. **Debug** düyməsi (böcək ikonu)
3. **Step Over** (F8) — sətir-sətir irəli
4. **Variables** pəncərəsində dəyişənlərin dəyərini izlə
5. Səhvi birlikdə tap

Mesaj: *"kodum işləmir" demək yoxdur — breakpoint qoy və özün gör.*

## 55-85 dəq · 5 warm-up

Özləri yazır. Sən gəzirsən, ilişənə kömək edirsən — həllini demirsən, sual verirsən.

1. **1-dən n-ə cəm** — həm dövrlə, həm düsturla. İkisinin nəticəsi eynidirmi?
2. **Ədədin rəqəmləri cəmi** (məsələn 1234 → 10)
3. **Sadə ədəd yoxlaması** — n sadədirmi?
4. **Palindrom ədəd** — 121 → bəli, 123 → xeyr
5. **Massivdə max və min** — bir keçiddə, iki ayrı dövrlə yox

Kim tez bitirir: 3-cü məsələdə dövrü `n`-ə qədər yox, `√n`-ə qədər apar — niyə
işləyir?

## 85-90 dəq · Push

Hamı `week-02/` qovluğuna push etsin. Push etməyəni qeyd et.

## Müəllim qeydi
Bu məşğələdə pattern verilmir — hələ tanıdıcı mərhələdir. İlk pattern (two
pointers) Week 3-də gəlir.
