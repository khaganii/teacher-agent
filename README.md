# Teaching

Xaqani Abdullayevin tədris arxivi — fənn materialları, dərs planları, imtahan
blueprintləri və tədris metodikası.

## Prinsip

Bu repo **tarixə bağlı deyil**. Hər şey həftə nömrəsi ilə işarələnir (Week 1 … Week 15).
Konkret semestrin tarixləri, qrupu və dəyişiklikləri yalnız bir yerdə saxlanır:
`courses/<fənn>/semesters/<il>-<semestr>.md`.

Gələn il eyni fənni keçəndə: yeni `semesters/` faylı yaradılır, qalan hər şey
olduğu kimi təkrar işlədilir. Keçən ilin təcrübəsi hər həftənin `notes.md`
faylında qalır — nə işlədi, nə işləmədi, nəyi dəyişmək lazımdır.

## Quruluş

```
_method/          Fənndən asılı olmayan tədris metodikası
_templates/       Boş şablonlar (dərs planı, imtahan, layihə)
courses/          Hər fənn üçün bir qovluq
  data-structures-and-algorithms/
    course.md           Fənnin pasportu (kod, kredit, saat, təlim nəticələri)
    syllabus-official.md Kafedra tərəfindən təsdiqlənmiş rəsmi plan
    plan.md             İş planı — həftə-həftə, tarixsiz
    patterns/           Pattern kitabxanası
    weeks/week-NN/      Hər həftə: mühazirə, məşğələ, ev tapşırığı, qeydlər
    assessment/         Layihə, midterm, final, şifahi sorğu
    semesters/          Konkret semestrin tarixləri və dəyişiklikləri
```

## Claude ilə işləmək

`/teacher` yazıb davam et. Skill bu repo-nu tanıyır və materialları buradan
oxuyur, yenilərini bura yazır.
