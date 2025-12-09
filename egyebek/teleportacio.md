Rendben, figyelek a LaTeX-re! Egyszerűbb, "tömör" matematikai jelöléseket fogok használni, amik biztosan megjelennek a chatablakban.

A **Kvantumteleportáció** a szupersűrűségű tömörítés "fordítottja". Itt nem biteket akarunk spórolni, hanem egy törékeny kvantumállapotot akarunk épségben átjuttatni A-ból B-be.

Íme a folyamat, ahogy a ZH-n elvárják:

---

### 0. A Hozzávalók (Setup)

Három kvantumbitünk van összesen:
1.  **Az Üzenet ($|\psi\rangle$):** Ez Alice-nál van. Ez az az állapot, amit át akar küldeni.
    $$ |\psi\rangle = \alpha|0\rangle + \beta|1\rangle $$
2.  **A Csatorna (Bell-pár):** Egy előre megosztott összefonódott pár.
    *   Az egyik fele Alice-nál ($A$), a másik Bobnál ($B$) van.
    *   Közös állapot: $|\beta_{00}\rangle = \frac{|00\rangle + |11\rangle}{\sqrt{2}}$

**A teljes rendszer állapota az elején:**
(Alice üzenete) $\otimes$ (Alice Bell-fele) $\otimes$ (Bob Bell-fele)

---

### 1. Lépés: Alice "összekeveri" a lapokat (CNOT és Hadamard)

Alice célja, hogy az üzenet információját "rákenje" a közös összefonódásra. Ehhez két kaput használ a nála lévő két qubiten (az üzeneten és a Bell-pár felén):

1.  **CNOT kapu:**
    *   Vezérlő: Az Üzenet ($|\psi\rangle$).
    *   Cél: A Bell-pár Alice-nál lévő fele.
    *   *Hatás:* Ezzel "összeköti" az üzenetet az összefonódott csatornával.

2.  **Hadamard kapu ($H$):**
    *   Ezt csak az Üzenet qubitre alkalmazza.
    *   *Hatás:* Ez készíti elő a mérést, szuperpozícióba hozva az első bitet.

**Mi történik a matekban?** (Ezt nem kell fejből levezetni, de a végeredmény fontos). A műveletek után a rendszer egy olyan bonyolult szuperpozícióba kerül, amit így csoportosíthatunk át:

$$
\frac{1}{2} [ |00\rangle (\alpha|0\rangle + \beta|1\rangle) + |01\rangle (\alpha|1\rangle + \beta|0\rangle) + |10\rangle (\alpha|0\rangle - \beta|1\rangle) + |11\rangle (\alpha|1\rangle - \beta|0\rangle) ]
$$

*   A félkövér részek (**$|00\rangle$**, stb.) Alice qubitjei.
*   A zárójelben lévő részek Bob qubitjének lehetséges állapotai.

---

### 2. Lépés: Alice Mér

Alice megméri a nála lévő két qubitet.
*   A mérés eredménye **két klasszikus bit** lesz (00, 01, 10 vagy 11).
*   **A "varázslat":** Abban a pillanatban, hogy Alice mér (pl. azt méri, hogy `01`), a rendszer "összeomlik". Nézd meg a fenti képletet! Ha Alice `01`-et mér, akkor Bob qubitje abban a pillanatban a $(\alpha|1\rangle + \beta|0\rangle)$ állapotba ugrik.

Látható, hogy Bobnál már ott van az infó ($\alpha$ és $\beta$), csak kicsit "összekeveredve" (ebben a példában felcserélődtek).

---

### 3. Lépés: A klasszikus telefonhívás

Alice felhívja Bobot (vagy küld egy e-mailt) a **klasszikus csatornán**:
*"Szia Bob, a mérésem eredménye: 01"*

Emiatt nem lehet fénysebességnél gyorsabban teleportálni: Bobnak meg kell várnia ezt a hívást, addig a nála lévő qubit csak használhatatlan zajnak tűnik.

---

### 4. Lépés: Bob korrigál (Helyreállítás)

Bob a kapott 2 bit alapján tudja, hogy az ő qubitje hogyan torzult el. Ezért egy műveletet végez rajta, hogy "helyretegye".

Itt a szabályrendszer (ez a kulcs a ZH-hoz!):

*   **Ha 00 jött:** Bob qubitje: $\alpha|0\rangle + \beta|1\rangle$.
    *   **Teendő:** Semmi ($I$ kapu). Ez maga a tökéletes $|\psi\rangle$.
*   **Ha 01 jött:** Bob qubitje: $\alpha|1\rangle + \beta|0\rangle$ (felcserélődtek).
    *   **Teendő:** **Bitcsere ($X$ kapu)**. Ezzel visszacseréli a 0-t és 1-et.
*   **Ha 10 jött:** Bob qubitje: $\alpha|0\rangle - \beta|1\rangle$ (előjel hiba).
    *   **Teendő:** **Fáziscsere ($Z$ kapu)**. Ezzel helyreteszi a mínuszt.
*   **Ha 11 jött:** Bob qubitje: $\alpha|1\rangle - \beta|0\rangle$ (mindkét hiba).
    *   **Teendő:** **$Z$ és $X$ kapu** is kell.

**Végeredmény:** Bob kezében ott van az eredeti $|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$ állapot.

---

### Összefoglalás (TL;DR):
1.  **Forrás:** $|\psi\rangle$ üzenet + Bell-pár.
2.  **Alice:** CNOT + Hadamard $\to$ Mérés (2 bit).
3.  **Klasszikus átvitel:** A 2 bit átküldése Bobnak.
4.  **Bob:** A 2 bit alapján $I, X, Z$ vagy $ZX$ kapukkal korrigál.
5.  **Eredmény:** Az állapot átkerült Bobhoz, Alice-nál megsemmisült.

Így már érthetőbb a működés?