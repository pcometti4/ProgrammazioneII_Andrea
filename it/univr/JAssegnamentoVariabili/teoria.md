# 🟢 1️⃣ Assegnamento fra variabili di tipo array

In Java, quando assegniamo un array a un’altra variabile:

```java id="q6x0bf"
int[] a = {1, 2, 3};
int[] b = a;
```

* `a` e `b` **puntano allo stesso array** in memoria
* Modifiche tramite `b` si riflettono su `a`

```java id="z4nr1k"
b[0] = 99;
System.out.println(a[0]); // 99
```

> Questo si chiama **aliasing**.

---

# 🟢 2️⃣ Array multidimensionali

## 🔹 Dichiarazione

```java id="n1q7so"
int[][] matrice = new int[3][4];
```

* 3 righe
* 4 colonne

---

## 🔹 Struttura in memoria

* Ogni riga è **un array separato**
* Si può avere **array sparsi (jagged array)**

```java id="p8x7kz"
int[][] sparso = new int[3][];
sparso[0] = new int[2];
sparso[1] = new int[5];
sparso[2] = new int[3];
```

* Dimensioni diverse per ogni riga
* Maggiore flessibilità

---

# 🟢 3️⃣ Metodi static

* Appartengono **alla classe**, non all’oggetto
* Si chiamano con `Classe.metodo()`
* Non possono usare direttamente campi non statici

```java id="rt5gnc"
class Contatore {

    private static int numeroOggetti = 0;

    public Contatore() {
        numeroOggetti++;
    }

    public static int getNumeroOggetti() {
        return numeroOggetti;
    }
}
```

Uso:

```java id="rsm9cj"
Contatore c1 = new Contatore();
Contatore c2 = new Contatore();
System.out.println(Contatore.getNumeroOggetti()); // 2
```

---

# 🟢 4️⃣ Metodi static di date

Esempio: primo gennaio e 31 dicembre di un anno

```java id="js8gwt"
class DataUtils {

    public static Data primoGennaio(int anno) {
        return new Data(1, 1, anno);
    }

    public static Data trentunoDicembre(int anno) {
        return new Data(31, 12, anno);
    }
}
```

Uso:

```java id="lka9zc"
Data d1 = DataUtils.primoGennaio(2026);
Data d2 = DataUtils.trentunoDicembre(2026);
```

---

# 🟢 5️⃣ Interfaccia pubblica di una classe

* Definisce **come gli altri vedono la classe**
* Include **metodi pubblici** e **costruttori**
* Non include campi privati

Esempio:

```java id="2kn5qf"
public class Contatore {
    private int valore;

    public Contatore() { valore = 0; }
    public void incrementa() { valore++; }
    public int getValore() { return valore; }
}
```

* Interfaccia pubblica: `incrementa()`, `getValore()`
* Stato interno (`valore`) è nascosto (encapsulation)

---

# 🟢 6️⃣ Oggetti mutabili e immutabili

| Tipo       | Esempi                        | Caratteristiche                                    |
| ---------- | ----------------------------- | -------------------------------------------------- |
| Mutabile   | Array, `StringBuilder`        | Stato interno può cambiare                         |
| Immutabile | `String`, wrapper (`Integer`) | Stato non cambia, ogni modifica crea nuovo oggetto |

---

## ⚠️ Aliasing e rischi

```java id="pz4h1m"
int[] a = {1,2,3};
int[] b = a;
b[0] = 99;  // anche a[0] cambia
```

* **Problema**: con oggetti mutabili, più riferimenti condividono lo stesso stato
* Soluzione: clonare l’oggetto se serve isolamento

---

# 🟢 7️⃣ JavaDoc

* Sistema di documentazione automatica
* Commenti speciali `/** ... */`
* Eclipse genera pagine HTML

Esempio:

```java id="k2h4jz"
/**
 * Rappresenta una data.
 * @author Studente
 * @version 1.0
 */
public class Data {

    /**
     * Giorno della data
     */
    private int giorno;

    /**
     * Restituisce la data come stringa
     * @return Stringa nel formato gg/mm/aaaa
     */
    public String toString() {
        return giorno + "/" + mese + "/" + anno;
    }
}
```

---

# 🟢 8️⃣ Ereditarietà e `super()`

* Una classe può **estendere** un’altra classe
* I campi e i metodi **vengono ereditati**
* **I costruttori non si ereditano**
* Per chiamare il costruttore della superclasse:

```java id="4kps5n"
class DataItaliana extends Data {
    public DataItaliana(int giorno, int mese, int anno) {
        super(giorno, mese, anno); // chiama il costruttore della superclasse
    }
}
```

---

# 🟢 9️⃣ Esempio Date generiche, italiane, americane, australiane

```java id="w6z2kp"
class Data {
    protected int giorno, mese, anno;

    public Data(int giorno, int mese, int anno) {
        this.giorno = giorno;
        this.mese = mese;
        this.anno = anno;
    }
}

class DataItaliana extends Data {
    public DataItaliana(int giorno, int mese, int anno) {
        super(giorno, mese, anno);
    }
}

class DataAmericana extends Data {
    public DataAmericana(int mese, int giorno, int anno) {
        super(giorno, mese, anno); // riordina giorno/mese
    }
}

class DataAustraliana extends Data {
    public DataAustraliana(int giorno, int mese, int anno) {
        super(giorno, mese, anno);
    }
}
```

* Tutte ereditano campi e metodi da `Data`
* Costruttori sono distinti
* `super()` concatena i costruttori

---

# 📊 10️⃣ Riassunto dei concetti principali

| Concetto                    | Spiegazione                                       |
| --------------------------- | ------------------------------------------------- |
| Assegnamento array          | Crea alias, stessa memoria                        |
| Array multidimensionale     | Array di array, può essere sparso                 |
| Metodo static               | Appartiene alla classe, accessibile senza oggetto |
| Contatore oggetti           | Esempio tipico di campo static                    |
| Primo gennaio / 31 dicembre | Esempio di metodo static di utilità               |
| Interfaccia pubblica        | Metodi accessibili agli altri oggetti             |
| Mutabile vs immutabile      | Controllo stato interno, rischi aliasing          |
| JavaDoc                     | Documentazione automatica, genera HTML            |
| Ereditarietà                | Classe figlia eredita campi/metodi                |
| super()                     | Chiamata al costruttore della superclasse         |