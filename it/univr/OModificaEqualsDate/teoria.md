# Lezione Universitaria di Java: Modifica di `equals()` e `compareTo()` per le Date

## 1. Introduzione

In Java, quando si lavora con oggetti **data**, spesso è necessario ridefinire i metodi `equals()` e `compareTo()` per confrontare correttamente le date, considerando sia la parte della data (giorno, mese, anno) sia la parte dell'orario (ore, minuti, secondi). Questa lezione illustra una logica completa per gestire questi casi, incluso il problema di eventuali sottoclassi con formati diversi.

---

## 2. Ridefinizione del metodo `equals()`

### Regole per confrontare due date

1. Se **giorno, mese o anno** sono diversi, le date **non sono uguali**.
2. Se una data ha l'orario e l'altra **no**, le date **non sono uguali**.
3. Se **nessuna** delle due date ha l'orario, le date **sono uguali**.
4. Se **entrambe** hanno l'orario, le date sono uguali **solo se ore, minuti e secondi coincidono**.

### Esempio in Java

```java
class Data {
    int giorno, mese, anno;

    Data(int g, int m, int a) {
        giorno = g; mese = m; anno = a;
    }

    public boolean hasTime() {
        return false;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (!(obj instanceof Data)) return false;
        Data other = (Data) obj;

        if (this.giorno != other.giorno || this.mese != other.mese || this.anno != other.anno)
            return false;

        if (this.hasTime() != other.hasTime())
            return false;

        return true; // entrambe non hanno tempo
    }
}

class DataConOrario extends Data {
    int ore, minuti, secondi;

    DataConOrario(int g, int m, int a, int h, int min, int s) {
        super(g, m, a);
        ore = h; minuti = min; secondi = s;
    }

    @Override
    public boolean hasTime() {
        return true;
    }

    @Override
    public boolean equals(Object obj) {
        if (!super.equals(obj)) return false;
        if (!(obj instanceof DataConOrario)) return false;
        DataConOrario other = (DataConOrario) obj;
        return this.ore == other.ore && this.minuti == other.minuti && this.secondi == other.secondi;
    }
}
```

---

## 3. Ridefinizione del metodo `compareTo()`

### Regole per ordinamento

1. Le date si ordinano prima per **anno, mese, giorno**.
2. Se una data ha il tempo e l'altra no, **la data senza tempo viene prima**.
3. Se nessuna ha tempo, sono considerate **uguali**.
4. Se entrambe hanno tempo, ordinamento per **ore, minuti, secondi**.

### Esempio in Java

```java
class Data implements Comparable<Data> {
    int giorno, mese, anno;

    Data(int g, int m, int a) {
        giorno = g; mese = m; anno = a;
    }

    public boolean hasTime() {
        return false;
    }

    @Override
    public int compareTo(Data other) {
        if (this.anno != other.anno) return this.anno - other.anno;
        if (this.mese != other.mese) return this.mese - other.mese;
        if (this.giorno != other.giorno) return this.giorno - other.giorno;

        if (this.hasTime() && !other.hasTime()) return 1;
        if (!this.hasTime() && other.hasTime()) return -1;

        return 0; // entrambe non hanno tempo
    }
}

class DataConOrario extends Data {
    int ore, minuti, secondi;

    DataConOrario(int g, int m, int a, int h, int min, int s) {
        super(g, m, a);
        ore = h; minuti = min; secondi = s;
    }

    @Override
    public boolean hasTime() {
        return true;
    }

    @Override
    public int compareTo(Data other) {
        int cmp = super.compareTo(other);
        if (cmp != 0) return cmp;

        if (!(other instanceof DataConOrario)) return 1;
        DataConOrario o = (DataConOrario) other;

        if (this.ore != o.ore) return this.ore - o.ore;
        if (this.minuti != o.minuti) return this.minuti - o.minuti;
        return this.secondi - o.secondi;
    }
}
```

---

## 4. Problema: altre sottoclassi di date con tempo

* Se arrivano altre sottoclassi come `AmericanDateAndTime` o `AustralianDateAndTime`, possono verificarsi problemi:

1. `equals()` potrebbe fallire se le classi non sono esattamente uguali (`instanceof` può restituire false tra sottoclassi diverse).
2. `compareTo()` potrebbe generare eccezioni di **ClassCastException** o comportamenti imprevisti se non si gestiscono le classi diverse.
3. Soluzione consigliata:

    * Creare un **interfaccia comune** `DateInterface` con `hasTime()` e metodi di confronto.
    * Implementare `equals()` e `compareTo()` basandosi su **contenuto effettivo**, non sulla classe concreta.
    * Evitare cast diretti tra sottoclassi diverse.

---

## 5. Conclusioni

* `equals()` deve confrontare prima la data e poi il tempo se presente.
* `compareTo()` ordina prima per data, poi per tempo se disponibile.
* L’uso di sottoclassi diverse può complicare il confronto, quindi è consigliabile progettare un'interfaccia comune o usare pattern **Template Method** per gestire il confronto in modo uniforme.

---

Se vuoi, posso creare anche una **versione Markdown con diagramma UML delle classi Data, DataConOrario e possibili sottoclassi internazionali** per rendere la lezione più visiva.

Vuoi che faccia anche quello?
