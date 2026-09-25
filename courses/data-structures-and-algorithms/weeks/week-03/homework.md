# Week 3 — Ev tapşırığı: özün ArrayList qur

**Xəbərdarlıq (müəllim üçün):** bu tapşırıq class/instance metodları tələb edir
— rəsmi planda bu, Week 7-dir (`MyStack`/`MyQueue`). Ona görə skelet çox
doldurulmuş verilir ki, tələbə sintaksislə yox, massivin böyümə məntiqi ilə
məşğul olsun. Məşğələnin sonunda (84-87 dəq) skeleti lövhədə qısaca izah edin.

## Tapşırıq

Aşağıdakı `MyArrayList` sinifini tamamla — 5 metodu doldur, `main`-də sına.

```java
public class MyArrayList {
    private int[] data;
    private int count; // neçə element həqiqətən doludur

    public MyArrayList() {
        data = new int[10]; // başlanğıc tutum
        count = 0;
    }

    public void add(int value) {
        // TODO: əgər data dolubsa (count == data.length),
        // ikiqat böyük yeni massiv yarat, köçür, sonra əlavə et
    }

    public int get(int index) {
        // TODO: data[index] qaytar
    }

    public void remove(int index) {
        // TODO: index-dən sonrakı elementləri bir sola sürüşdür, count-u azalt
    }

    public int size() {
        // TODO: count qaytar
    }

    public boolean contains(int value) {
        // TODO: linear search
    }

    public static void main(String[] args) {
        MyArrayList list = new MyArrayList();
        list.add(5);
        list.add(10);
        System.out.println(list.get(0)); // 5
        System.out.println(list.size()); // 2
    }
}
```

Ən vacib hissə `add`-dəki böyümə məntiqidir — elə buna görə bu gün array-in
"ölçüsü sabitdir" məhdudiyyətini gördünüz. `main`-də ən azı 12 ədəd `add` edib
(10-dan çox) böyümənin işlədiyini yoxlayın.
