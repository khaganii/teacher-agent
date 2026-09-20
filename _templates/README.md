# Şablonlar

## Yeni fənn açmaq

```
cp -r _templates/new-course courses/<fennin-adi-kebab-case>
```

Sonra doldurulacaqlar, bu sırayla:
1. `course.md` — pasport: kod, kredit, saat bölgüsü, təlim nəticələri, qiymətləndirmə
2. `syllabus-official.md` — kafedranın təsdiqlədiyi plan (dəyişdirmə, olduğu kimi köçür)
3. `plan.md` — öz iş planın, həftə-həftə, **tarixsiz**
4. `semesters/<il>-<semestr>.md` — konkret semestrin tarixləri və dəyişiklikləri
5. `weeks/week-NN/` — həftə materialları, dərsdən əvvəl

`_method/` qovluğundakı prinsiplər bütün fənnlərə aiddir, təkrar yazılmır.

## Həftə faylları

Hər həftə qovluğunda dörd fayl:

| Fayl | Nə üçün |
|---|---|
| `lecture.md` | Mühazirə planı — dəqiqə-dəqiqə bölgü, lövhəyə yazılacaqlar |
| `practice.md` | Məşğələ planı — kod, alət, tapşırıq |
| `homework.md` | Tələbəyə verilən tapşırıq, təhvil qaydası ilə |
| `notes.md` | **Dərsdən sonra** doldurulur — nə işlədi, nə işləmədi |

`notes.md` ən dəyərli fayldır. Gələn il planı yenidən qurmaq əvəzinə bunu oxuyursan.
