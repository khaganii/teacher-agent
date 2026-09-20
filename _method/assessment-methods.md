# Qiymətləndirmə üsulları

## Şifahi sorğu rotasiyası

**Problem:** 10 nəfərlik yarımqrupda hamını bir məşğələdə sorğulamaq mümkün deyil —
hərəyə 9 dəqiqə düşür və 9 nəfər boş oturur.

**Həll:** 3 ardıcıl həftə, hər məşğələdə 3-4 nəfər, hərəsi 12 dəqiqə.
3 həftə x 3-4 nəfər = 10 nəfər. Hamı bir dəfə, amma real sorğu ilə.

Sorğu zamanı qalanlar məsələ üstündə işləməyə davam edir.

### 5 sual tipi (12 dəqiqəyə tam sığır)

| # | Tip | Vaxt | Sual nümunəsi |
|---|---|---|---|
| 1 | **Öz kodun** | 3 dəq | "Bu sətir nə edir? Bu dövr niyə `i < n-1`-ə qədər gedir?" |
| 2 | **Mürəkkəblik** | 2 dəq | "Bu metodun vaxt mürəkkəbliyi nədir? Yaddaş nə qədər?" |
| 3 | **Kənar hallar** | 2 dəq | "Massiv boş olsa? Bir elementli olsa? Hamısı eyni olsa?" |
| 4 | **Canlı dəyişiklik** | 4 dəq | "İndi azalan sırada sortla" / "Sonuncu təkrarı qaytar" |
| 5 | **Seçim** | 1 dəq | "Niyə bubble yox counting sort seçdin?" |

Birinci sual AI ilə yazılmış kodu bir dəqiqəyə üzə çıxarır — ən vacib sualdır.

### Bal cədvəli (10 bal)

| Meyar | Bal |
|---|---|
| Kod işləyir, məsələni həll edir | 4 |
| Öz kodunu sətir-sətir izah edə bilir | 3 |
| Mürəkkəbliyi düzgün deyir və əsaslandırır | 2 |
| Kənar halları düşünür / canlı dəyişikliyi edir | 1 |

**Qayda:** izah edə bilməyən tələbə kod işləsə belə maksimum 4 bal alır.
Bunu semestrin əvvəlində elan et.

### Praktiki qeydlər

- Kimin hansı həftədə yoxlanacağını **əvvəlcədən elan etmə** — təsadüfi çağır,
  yoxsa yalnız öz həftəsinə hazırlaşırlar
- Sual öz koduna görə olduğu üçün hər tələbəyə fərqli sual düşür
- Jurnalda qeyd saxla: hansı sualda ilişdi. Qrupun ümumi zəif nöqtəsi görünür

## Tələbə təqdimatları (layihə formatı)

Hər tələbə **iki qohum pattern** alır və hansını nə vaxt seçmək lazım olduğunu
izah edir. Yəni iki ayrı mövzu deyil — bir **qərar**.

Struktur (12-15 dəq):
1. 4-5 slayd: hər iki pattern nədir, nə vaxt tanınır, mürəkkəbliyi
2. **Canlı implementasiya** — birini ekranda sıfırdan yazır (hazır kod yapışdırmaq yoxdur)
3. Bir məsələni həll edib izah edir
4. Sinifdən 2 sual

**Ön yoxlama məcburidir:** slaydlar və kod təqdimatdan 3 gün əvvəl GitHub-a
yüklənir, müəllim baxıb təsdiq edir. Bunsuz zəif tələbə sinfə səhv məlumat öyrədir.

**Dinləyicilər boş oturmasın:** hər təqdimatdan sonra həmin pattern-in bir
məsələsi bütün qrupa ev tapşırığı olur.
