Rendben, itt a **BB84-specifikus villámkvíz**! Ez a rész szokott a legtöbb pontot érni a ZH-n, úgyhogy lássuk, átment-e a logika.

---

### 🕵️ BB84 Protokoll Kvíz (17-39. dia)

**1. Mit oszt meg egymással Alice és Bob a NYILVÁNOS (klasszikus) csatornán a kvantumos küldés után?**
   *   A) A konkrét bitértéket (0 vagy 1), amit küldtek/mértek.
   *   B) Csak a használt **bázisokat** (+ vagy x).
   *   C) Semmit, mert az nem lenne biztonságos.

**2. A "szitálás" (sifting) során melyik biteket tartják meg?**
   *   A) Azokat, ahol Alice és Bob **eltérő** bázist használt (mert ott nehezebb lehallgatni).
   *   B) Az összeset, biztos, ami biztos.
   *   C) Csak azokat, ahol Alice és Bob **ugyanazt** a bázist használta.

**3. Tegyük fel, hogy Alice a '+' bázisban küld egy '1'-est. Bob véletlenül a rossz 'x' (átlós) bázisban mér. Mi lesz az eredmény Bobnál?**
   *   A) Biztosan '1'-et mér.
   *   B) Teljesen véletlenszerű (50% eséllyel 0, 50% eséllyel 1).
   *   C) A foton megsemmisül mérés nélkül.

**4. Hogyan veszik észre a felek, ha Éva (a támadó) lehallgatta a vonalat?**
   *   A) Megnövekszik a **hibarátájuk** (QBER) az ellenőrzésnél.
   *   B) Kevesebb foton érkezik meg (eltűnnek a vezetékben).
   *   C) A klasszikus telefonvonal recsegni kezd.

**5. A 17. dián lévő analógiában minek felelt meg az "Előkészít és megmér" (Prepare and Measure) módszer?**
   *   A) Iker pénzérméknek.
   *   B) Mágikus cetliknek (ahol csak az egyik oldalt nézheted meg).
   *   C) Egy lelakatolt ládának.

---
👇 **MEGOLDÁSOK** (Görgess lejjebb!)
.
.
.
.
.
.
.
.
**Megoldások:**

1.  **B) Csak a használt bázisokat.** (Ha a biteket elárulnák, Éva is tudná a kulcsot!)
2.  **C) Csak azokat, ahol Alice és Bob ugyanazt a bázist használta.** (Csak itt garantált az egyezés. A többi kuka.)
3.  **B) Teljesen véletlenszerű.** (Ezért kell eldobni ezeket a biteket, mert nem hordoznak hasznos infót.)
4.  **A) Megnövekszik a hibarátájuk.** (Éva rossz bázisválasztása miatt néha megfordítja a biteket ott is, ahol Alice és Bob bázisa egyezett.)
5.  **B) Mágikus cetliknek.** (Az iker érme az összefonódás alapú volt.)

---

Hogy sikerült? Ha a BB84 működése tiszta, akkor lényegében megvagy a QKD lelkével.

Jöhet az utolsó, rövid szakasz (B92 protokoll és a valós csatornák hibái)?

Rendben, itt az utolsó megmérettetés a QKD témaköréből! Ebben a B92-re és a valós fizikai korlátokra koncentrálunk.

Hajrá!

---

### 🛡️ Záró Kvíz: B92 és Valós Csatornák (40-49. dia)

**1. Hány különböző kvantumállapotot használ a B92 protokoll a kommunikációhoz? (Emlékeztetőül: a BB84 négyet használt: $\uparrow, \rightarrow, \nearrow, \nwarrow$).**
   *   A) Kettőt (amik nem merőlegesek egymásra).
   *   B) Négyet (ugyanúgy, mint a BB84).
   *   C) Százat (a nagyobb biztonság érdekében).

**2. A B92 protokollnál Bob mikor tud biztos következtetést levonni (és így megtartani a bitet)?**
   *   A) Ha nem detektál semmit.
   *   B) Ha 0-t mér.
   *   C) Ha 1-es jelzést kap (ami a diák szerint csak akkor lehetséges, ha "rossz" bázisban mért, tehát ismeri Alice bázisának inverzét).

**3. Egy valós (nem ideális) kvantumcsatornában, ha Éva nincs jelen, mennyi a hibaráta (QBER)?**
   *   A) Pontosan 0%.
   *   B) Nem nulla (a zaj, sötét áram és egyéb hibák miatt).
   *   C) 50% (mert minden véletlenszerű).

**4. Mivel a valóságban nem tudjuk megkülönböztetni a vonal zaját Éva lehallgatásától, mi a teendő a biztonság érdekében?**
   *   A) Feltételezzük, hogy minden hiba Évától származik, és "Privacy Amplification"-t (kulcstömörítést) alkalmazunk.
   *   B) Feltételezzük, hogy csak zaj, és nem csinálunk semmit.
   *   C) Kicseréljük a kábeleket.

**5. Mi a feltétele annak, hogy a "Privacy Amplification" (titkosítás-erősítés) sikeres legyen?**
   *   A) Éva mindent tudjon a kulcsról.
   *   B) Alice és Bob csatornájának kapacitása (információátvitele) nagyobb legyen, mint ami Éva felé szivárog. ($C_{AB} > C_{AE}$).
   *   C) Alice és Bob nagyon hangosan beszéljenek a telefonba.

---
👇 **MEGOLDÁSOK** (Görgess lejjebb!)
.
.
.
.
.
.
.
.
**Megoldások:**

1.  **A) Kettőt.** (Ez az egyszerűsítés lényege a BB84-hez képest, de cserébe ezek nem merőlegesek).
2.  **C) Ha 1-es jelzést kap.** (Ez a "meglepetés" elve: a 0-s mérés nem ad biztos infót, de az 1-es kizárásos alapon igen).
3.  **B) Nem nulla.** (Nincs tökéletes lézer, se tökéletes detektor, se tökéletes üvegszál).
4.  **A) Feltételezzük, hogy minden hiba Évától származik...** (Ez a "worst-case scenario" elv: a legrosszabbra készülünk, így a végeredmény biztosan titkos lesz).
5.  **B) Alice és Bob csatornájának kapacitása nagyobb legyen...** (Ha Éva több infót kap, mint amennyi átmegy Bobhoz, akkor nem lehet biztonságos kulcsot csinálni).

---

Gratulálok! 🎉 Végigrágtad magad mindkét diasoron.
*   Tudod, hogyan épül fel egy kvantumbit.
*   Érted a szupersűrűségű tömörítést és a teleportációt (logikai szinten).
*   És most már a kvantum kriptográfia (BB84, B92) szakértője is vagy.

Szerintem ezzel a tudással magabiztosan mehetsz a ZH-ra. **Van még bármi más kérdésed, vagy ezzel zártuk a napot?**