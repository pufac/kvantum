A **Szupersűrűségű tömörítés (Superdense Coding)** a kvantuminformatika egyik leglátványosabb trükkje.

**A lényeg egy mondatban:** Alice képes **2 klasszikus bitet** (pl. "10") átküldeni Bobnak úgy, hogy fizikailag csak **1 darab kvantumbitet** küld át a csatornán.

Hogy ez működjön, szükség van egy "előjátékra": a kommunikáció előtt rendelkezniük kell egy közös erőforrással (összefonódással).

Nézzük lépésről lépésre, pontosan mi történik a motorháztető alatt!

---

### 0. Lépés: Előkészületek (A közös erőforrás)
Mielőtt bármi történne, Alice és Bob kapnak egy-egy kvantumbitet, amelyek **össze vannak fonódva**. Ez egy Bell-pár.
A rendszer állapota ekkor (a leggyakoribb Bell-állapot):
$$ |\psi_{start}\rangle = \frac{|00\rangle + |11\rangle}{\sqrt{2}} $$
*   Az első qubit Alice-nál van.
*   A második qubit Bobnál van.

---

### 1. Lépés: Kódolás (Alice oldala)
Alice-nak eszébe jut egy 2 bites üzenet (pl. "10"), amit el akar küldeni. Ehhez egyetlen logikai kaput alkalmaz a **saját** kvantumbitjén. A közös állapot ettől megváltozik, méghozzá a 4 lehetséges Bell-állapot egyikére.

Itt a "szótár", amit Alice használ (ez volt a 11. dián):

| Üzenet | Alice művelete (Kapu) | Mi történik az állapottal? | Új állapot neve |
| :--- | :--- | :--- | :--- |
| **00** | **I (Identitás)** | Semmi. Marad a régi. | $|\beta_{00}\rangle = \frac{|00\rangle + |11\rangle}{\sqrt{2}}$ |
| **01** | **Z (Fáziscsere)** | A $|1\rangle$ előjelet vált. | $|\beta_{01}\rangle = \frac{|00\rangle - |11\rangle}{\sqrt{2}}$ |
| **10** | **X (Bitcsere/NOT)** | A 0-ból 1, 1-ből 0 lesz. | $|\beta_{10}\rangle = \frac{|10\rangle + |01\rangle}{\sqrt{2}}$ |
| **11** | **iY (Fázis+Bitcsere)** | Mindkettő egyszerre. | $|\beta_{11}\rangle = \frac{|01\rangle - |10\rangle}{\sqrt{2}}$ |

*Figyeld meg:* Alice csak a saját bitjéhez nyúlt, de mivel össze voltak fonódva, az *egész rendszer* állapota átfordult egy másik, jól megkülönböztethető (ortogonális) állapotba.

---

### 2. Lépés: Küldés (A fizikai átvitel)
Alice fogja a saját qubitjét (amin elvégezte a műveletet), és **elküldi Bobnak**.
*   **Fontos:** A csatornán fizikailag csak 1 db részecske (pl. foton) utazik át.
*   Most már Bobnál van mindkét qubit (a sajátja, ami eddig is ott volt, és amit Alice küldött).

---

### 3. Lépés: Dekódolás (Bob oldala)
Bobnak most az a feladata, hogy kitalálja, a rendszer a 4 lehetséges Bell-állapot közül melyikben van. Ehhez egy **Bell-bázis mérést** végez.

Ez a mérés valójában a Bell-állapot előállításának a "visszajátszása" (inverze):
1.  **CNOT kapu:** Bob alkalmaz egy CNOT-ot a két qubiten (Alice-é a vezérlő, Bobé a cél).
    *   Ez "szétbontja" az összefonódást.
2.  **Hadamard kapu:** Bob alkalmaz egy H kaput az első (Alice-tól kapott) qubiten.
    *   Ez a szuperpozíciót alakítja vissza bázisállapottá.

**Mi történik a matekban? (Példa a "10" üzenetre)**
*   Bejövő állapot (amit Alice X kapuval csinált): $\frac{|10\rangle + |01\rangle}{\sqrt{2}}$
*   **CNOT után:** (Ha az első bit 1, fordítjuk a másodikat. Ha 0, nem.)
    *   $|10\rangle \to |11\rangle$
    *   $|01\rangle \to |01\rangle$
    *   Új állapot: $\frac{|11\rangle + |01\rangle}{\sqrt{2}} = \frac{(|1\rangle + |0\rangle)}{\sqrt{2}} \otimes |1\rangle = |+\rangle \otimes |1\rangle$
*   **Hadamard az elsőn:** Tudjuk, hogy $H|+\rangle = |0\rangle$. (Várjunk, itt a konvenciók miatt lehet eltérés a jelekben, de a lényeg:)
    *   A transzformáció végére az állapot tisztán **$|10\rangle$** lesz.

---

### 4. Lépés: Mérés
Bob megméri a két qubitet a standard bázisban.
*   Mivel a rendszer állapota $|10\rangle$ lett, Bob mérőműszere azt mutatja: **1** és **0**.
*   Ez pontosan az az üzenet, amit Alice küldött!

---

### Összefoglalva a vizsgára:
1.  **Kezdés:** Van egy közös Bell-pár.
2.  **Alice:** A 2 bitje alapján a 4 Pauli-kapu ($I, X, Z, iY$) egyikét alkalmazza a saját felén.
3.  **Küldés:** 1 qubit utazik.
4.  **Bob:** "Kicsomagolja" az állapotot (Bell-bázis mérés: CNOT + H + Mérés) és visszakapja a 2 bitet.

**Miért "szupersűrű"?** Mert a kapacitás duplája a klasszikusnak (2 bit / 1 qubit).
**Mi az ára?** Előre megosztott összefonódás kell hozzá (ami fogyóeszköz, minden üzenethez új pár kell).

Tiszta így a folyamat?