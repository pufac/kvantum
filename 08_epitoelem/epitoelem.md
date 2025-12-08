Köszönöm a harmadik diasort! Ez a prezentáció (43 dia) átvezet minket a **kvantumkommunikációtól** a **kvantumszámítógépek építőkövei** felé.

Mivel ez is egy hosszabb anyag, és logikailag jól elkülönülő részekre bomlik, ezt is **két részben** fogjuk feldolgozni:

1.  **I. Rész (1-24. dia):** Ismétlés, QKD a gyakorlatban (hálózatok, műholdak) és a hitelesítés problémája.
2.  **II. Rész (25-43. dia):** A kvantumszámítógép építőelemei (hardver, DiVincenzo-kritériumok) és az algoritmusok általános receptje.

Kezdjük az első felével!

---

### I. Rész: Ismétlés és Kvantumhálózatok (1-24. dia)

**1-4. dia: Bevezetés**
*   Címoldal és adminisztráció (ZH utáni hangulatfelmérés). Ezekkel nem kell foglalkoznunk, csak töltelék diák.

**5-6. dia: Interferométer (Kísérlet vs. Áramkör)**
*   **5. dia (Kísérlet):** Egy Mach-Zehnder interferométert látsz.
    *   A fény jön balról ($|0\rangle$).
    *   Az első tükör (nyalábosztó - Beam splitter) szétbontja két útra.
    *   A két út találkozik, és interferál (erősítik vagy kioltják egymást).
*   **6. dia (Áramkör):** Ugyanez a folyamat kvantumkapukkal:
    *   Első **Hadamard (H)**: Ez a nyalábosztó (szuperpozíciót csinál).
    *   **Fázistoló (P)**: Ez a fény útjának eltolása (fáziskésleltetés).
    *   Második **Hadamard (H)**: Ez a második nyalábosztó, ahol újraegyesül a jel.
*   **Tanulság:** A fizikai kísérletek tökéletesen leírhatók ezekkel az absztrakt kapukkal.

**7. dia: No-Cloning Tétel (Nagyon fontos!)**
*   **Definíció:** Nem létezik olyan gép ("fénymásoló"), amibe beteszel egy *ismeretlen* kvantumállapotot, és kijön belőle két tökéletes másolat.
*   **Kivételek:**
    *   Ha **ismered** az állapotot (pl. tudod, hogy $|0\rangle$), azt elő tudod állítani újra.
    *   Ha az állapotok **ortogonálisak** (merőlegesek, pl. 0 és 1), akkor lemásolhatók (ez a klasszikus másolás).
*   **Miért fontos?** Ez a kvantumkriptográfia alapja. Ha Éva nem tudja lemásolni a fotont, nem tudja észrevétlenül lehallgatni a kulcsot.

**8. dia: Tetszőleges állapot előállítása**
*   Ezt már láttuk az első diasorban. H és P kapukkal a $|0\rangle$-ból bármi kikeverhető. (Ismétlés).

**9. dia: A jövőkép**
*   **Jelen:** QKD (kulcscsere) – pont-pont összeköttetés (Alice és Bob).
*   **Jövő:** Kvantuminternet. Itt már nemcsak két ember beszélget, hanem kvantumszámítógépeket kötünk össze hálózatba, hogy megosszák a számítási kapacitást.

**10-12. dia: Protokollok ismétlése**
*   Ezek a diák (Szupersűrűségű tömörítés, Teleportáció) egy-az-egyben megegyeznek az első diasor anyagával.
*   **Lényeg:**
    *   Szupersűrűségű: 1 qubit $\to$ 2 klasszikus bit infó.
    *   Teleportáció: 2 klasszikus bit + összefonódás $\to$ 1 qubit állapot átvitele.

**13. dia: QKD a gyakorlatban**
*   A QKD ma már nem sci-fi, hanem **kereskedelmi termék**.
*   Lehet venni ilyen "dobozokat" (pl. Toshiba, ID Quantique cégek), amiket optikai szálra kötsz, és gyártják a titkos kulcsokat.
*   Kompatibilis a mostani rendszerekkel (AES titkosítás), csak a kulcsot cseréli le kvantumosra.

**14-16. dia: Mérés és Támadás (Ismétlés)**
*   A BB84 protokoll és a támadás (Éva) elméletét már átvettük a második diasorban.
*   **16. dia:** Ez az ábra mutatja, hogy Éva "közbeékelődik", mér, és továbbküld. Ezzel hibát (zajt) visz a rendszerbe.

**17. dia: Nem ideális csatorna (Fontos fogalmak!)**
*   **QBER (Quantum Bit Error Rate):** Kvantumos hibaráta.
*   **A probléma:** A valós optikai szálban van zaj. Éva is zajt kelt. Nem tudjuk megkülönböztetni a kettőt.
*   **Megoldás:** Minden zajt Évának tekintünk (biztonsági ráhagyás).
*   **Privacy Amplification (Titkosítás-erősítés / Kulcstömörítés):**
    *   Van egy hosszú kulcsunk, amiről Éva talán tud pár bitet (a zaj miatt).
    *   Ezt egy matematikai eljárással (hash-függvényekkel) "összenyomjuk" egy rövidebb kulccsá.
    *   Az új, rövid kulcsról Éva már **semmit** sem tud (az információja eltűnik az átalakításban).
    *   **Feltétel:** $C_{AB} - C_{AE} > 0$. (Bobnak több infója legyen a kulcsról, mint Évának).

**18-19. dia: QKD típusok (Csak érdekesség)**
*   **DV (Discrete Variable):** Egyedi fotonokat számolunk (BB84).
*   **CV (Continuous Variable):** A fény hullámtermészetét mérjük (homodin detektálás). Ez közelebb áll a mai távközlési technológiához, de bonyolultabb a matekja.
*   Ez "csak zárójelben" van, nem hiszem, hogy mélyen kérdeznék.

**20-22. dia: Kvantumhálózatok Európában**
*   **EAGLE-1:** Európai kvantumos műhold. Miért kell műhold? Mert az optikai szálon a fotonok kb. 100-150 km után elnyelődnek. Műholddal viszont a világ bármely pontjára eljuthatnak (vákuumban nincs elnyelődés).
*   **EuroQCI:** Európai kezdeményezés egy kontinens méretű kvantumhálózat kiépítésére (földi szálak + műholdak kombinációja). Magyarország is részt vesz benne (22. dia - Budapest, Győr, Szeged, stb. csomópontok).

**23-24. dia: A HITELESÍTÉS (Authentication) problémája (Kritikus!)**
*   **Szituáció:** Van egy szuperbiztonságos kvantumcsatornád. De honnan tudod, hogy a drót másik végén tényleg Bob van, és nem Éva, aki Bobnak adja ki magát?
*   A QKD **csak a titkosítást** (Confidentiality) oldja meg, a **személyazonosság igazolását** (Authentication) NEM.
*   **Man-in-the-Middle támadás:** Éva elvághatja a vezetéket, és játszhatja azt Alice-nak, hogy ő Bob, Bobnak meg azt, hogy ő Alice. Külön-külön csinál velük kvantumkulcsot.
*   **Megoldás:** A QKD elkezdéséhez **már rendelkezniük kell egy előre megosztott kis titokkal** (pl. egy jelszóval), amivel hitelesítik az első lépéseket. Ezért hívják "kulcsnövesztésnek" (egy kis titokból csinálnak nagyot).

---

**I. Rész összefoglalása:**
Átismételtük az alapokat (interferométer, no-cloning). Láttuk, hogy a QKD a valóságban zajos, ezért kell a *Privacy Amplification*. Beszéltünk a skálázódásról (műholdak kellenek nagy távolságra) és a legfontosabb korlátról: a QKD nem mondja meg, kivel beszélsz, ezért előtte hitelesíteni kell a feleket klasszikus módszerrel.

Mehetünk a rövid kvízre ebből a részből?

Rendben, igazad van, a java (az új anyag) most jön. Itt lépünk be a **hardver** és az **algoritmusok** világába. Ez a rész (főleg a DiVincenzo-kritériumok és az algoritmus recept) szintén nagyon gyakori vizsgatéma.

---

### II. Rész: Építőelemek és az Algoritmus "Receptje" (25-43. dia)

**25-27. dia: Az építőelemek hierarchiája**
Ahogy a klasszikus gépnél tranzisztor $\to$ kapu $\to$ processzor a sorrend, itt is van egy hierarchia:
1.  **Kvantumbit (Qubit):** A legkisebb egység.
2.  **Kvantumregiszter:** Több qubit együtt (pl. 3 qubit = 8 állapot egyszerre).
3.  **Kvantumkapu:** A művelet, ami megváltoztatja a qubitek állapotát (mint a klasszikus AND/OR, csak itt unitér mátrixok).
4.  **Kvantumáramkör:** Kapuk sorozata, ami egy algoritmust valósít meg.

**28. dia: A Szent Grál (Fizikai megvalósítás)**
*   Elméletben bármi lehet qubit, ami két állapotot fel tud venni (elektron spinje, atom energiaszintje).
*   **A nehézség:** Olyan rendszert találni, ami:
    *   **Skálázható:** Nem elég 2 qubit, milliók kellenek.
    *   **Összekapcsolható:** A qubiteknek "beszélgetniük" kell egymással (összefonódás).
    *   **Zajtűrő:** Ne essen szét az állapot (dekoherencia) a számítás vége előtt.

---

### ⚠️ KULCSFONTOSSÁGÚ: DiVincenzo-kritériumok (29-30. dia)
David DiVincenzo (IBM) 2000-ben lefektette azt az **5 feltételt**, aminek egy fizikai rendszernek meg kell felelnie, hogy kvantumszámítógép lehessen. **Ezt szinte biztosan kérdezhetik!**

1.  **Skálázhatóság (Scalable):** Legyenek jól definiált qubitek, és tudjunk sokat összerakni belőlük.
2.  **Inicializálás (Initialization):** Tudjuk az egész rendszert egy ismert alapállapotba (pl. tiszta $|00...0\rangle$-ba) állítani a számítás kezdetén. (Ha szeméttel indítunk, szemetet kapunk).
3.  **Hosszú koherencia-idő (Long decoherence times):** A qubitek tartsák meg az állapotukat (emlékezetüket) sokkal tovább, mint ameddig egy kapuművelet tart. (Legyen idő számolni, mielőtt összeomlik a rendszer).
4.  **Univerzális kapukészlet (Universal set of gates):** Legyen pár alap kapu (pl. H, CNOT, T), amikből *bármilyen* bonyolult algoritmus összerakható.
5.  **Mérés (Measurement):** A végén képesnek kell lennünk kiolvasni az eredményt (specifikus qubitek mérése).

**30. dia:** Ez egy táblázat a különböző technológiákról (ioncsapdák, szupravezetők, fotonika). Látható, hogy mindegyiknek van előnye és hátránya, nincs még meg a "tökéletes" technológia.

**31-35. dia: Hardware körkép (Képek)**
*   Csak illusztrációk a mai gépekről.
*   **IBM / Google:** Szupravezető qubitek (azok a lógó arany csillárok, amiket képeken látsz - ezeket hűteni kell abszolút nulla fok közelébe).
*   **Xanadu:** Fotonikus (fény alapú) chipek.
*   **Ioncsapdák:** Lebegő atomok lézerrel piszkálva.

---

### ⚠️ A Kvantumalgoritmusok "Receptje" (36-41. dia)
Hogyan működik *minden* kvantumalgoritmus? Van egy 5 lépéses általános sémájuk (36. dia ábrája).

**1. Inicializálás (37. dia):**
*   A problémát lefordítjuk a kvantumgép nyelvére.
*   Előállítjuk a **szuperpozíciót** (általában Hadamard kapukkal).
*   *Miért?* Hogy az összes lehetséges bemenet (válaszjelölt) egyszerre legyen jelen a gépben.

**2. Kvantumpárhuzamosság (Quantum Parallelism) (38. dia):**
*   Elvégzünk egy műveletet ($U_f$) a szuperpozíción.
*   Mivel a bemenet az összes lehetőség egyszerre volt, a kimenet is tartalmazza az **összes lehetséges eredményt** egyszerre.
*   *Csapda:* Ha most mérnénk, kapnánk egy véletlenszerű eredményt, ami nem biztos, hogy a jó megoldás.

**3. Amplitúdó-erősítés (Amplitude Amplification) (39. dia):**
*   **Ez a legfontosabb trükk!**
*   A párhuzamosság után van egy massza állapotunk, ahol a "jó" válasz és a "rossz" válaszok is ott vannak, kb. egyforma eséllyel.
*   Olyan műveleteket (interferenciát) végzünk, ami:
    *   A **jó válasz** valószínűségét (amplitúdóját) **felnagyítja** (konstruktív interferencia).
    *   A **rossz válaszokét** **lecsökkenti/kioltja** (destruktív interferencia).
*   Példa erre a *Grover-algoritmus* vagy a *QFT*.

**4. Mérés (40. dia):**
*   Most, hogy felerősítettük a jó választ, megmérjük a regisztert.
*   Nagy valószínűséggel a helyes eredményt kapjuk (de nem 100%!).

**5. Utófeldolgozás (Post-processing) (41. dia):**
*   A kapott biteket értelmezzük, esetleg klasszikus számítógéppel ellenőrizzük. Ha nem jó, futtatjuk újra az egészet.

**42. dia: Mi jön ezután?**
*   A következő anyagokban konkrét példákat fogunk látni erre a receptre:
    *   **Deutsch-Jozsa:** A "helló világ" algoritmus (haszontalan, de demonstrálja a párhuzamosságot).
    *   **Shor:** Prímfelbontás (feltöri az RSA-t).
    *   **Grover:** Keresés adatbázisban.

---

### Összefoglalás a 3. diasorról:
Két dolgot kell nagyon megjegyezned innen:
1.  **DiVincenzo-kritériumok:** Skálázhatóság, Inicializálás, Koherencia, Univerzális kapuk, Mérés.
2.  **Algoritmus recept:** Inicializálás $\to$ Párhuzamosítás $\to$ **Amplitúdó-erősítés** (ez a kulcs!) $\to$ Mérés.

Készen állsz egy gyors ellenőrző kvízre ezekből? (Főleg a kritériumokra és a receptre fogok fókuszálni).