---
description: Teaching archive-a bax — vəziyyəti göstər, tapşırığı icra et
argument-hint: [sual/tapşırıq (istəyə bağlı)]
---

# Teacher

Bu, Xaqaninin NAA-dakı tədrisi üçün istifadə etdiyi köməkçi agentin çağırış
komandasıdır. `/teacher` yazıldıqda aşağıdakıları et:

1. `~/Desktop/edu/teaching` qovluğuna keç, `git log --oneline -5` və `git status -sb`
   ilə arxivin real vəziyyətini yoxla (əvvəlki sessiyadan yaddaşa güvənmə).
2. `CLAUDE.md`-ni oxu.
3. Hər kurs üçün `courses/<course>/plan.md` və `courses/<course>/semesters/<current>.md`
   fayllarına bax, cari həftəni (semester faylındakı tarixlərdən) müəyyən et.
4. Qısa status ver: hər kurs hansı həftədədir, ən son `notes.md` hansı həftəyə
   qədər doludur (bundan sonrakı həftələr hazırlanmayıb deməkdir), commit
   olunmamış dəyişiklik və ya push edilməmiş iş varsa bunu bir sətirdə qeyd et.
5. `$ARGUMENTS` boş deyilsə, onu bu kontekstlə icra et (`anthropic-skills:teacher`
   skilindəki "Common requests" bölməsinə uyğun: həftə hazırlığı, dərs qeydləri,
   imtahan sualları, tələbələrə mesaj, qiymətləndirmə, yeni fənn).
6. `$ARGUMENTS` boşdursa, status verdikdən sonra "indi nə lazımdır" sualına qısa
   təklif ver (məs. növbəti hazırlanmamış həftə).

## Davranış qaydaları

- Detallı qaydalar (`_method/`, qiymətləndirmə rubrikaları, git push icazəsi və s.)
  üçün `anthropic-skills:teacher` skilinin qaydalarını əsas tut — bu komanda ona
  əvəz deyil, sürətli giriş nöqtəsidir.
- Push əməliyyatını heç vaxt öz təşəbbüsünlə etmə, yalnız aydın "bəli" cavabından
  sonra.
