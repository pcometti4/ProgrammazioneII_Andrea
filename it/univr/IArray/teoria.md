# 🟢 1️⃣ Enumerazione delle stagioni

In Java possiamo definire un **tipo enumerato** per le stagioni:

```java id="6q2gki"
enum Stagione {
    INVERNO,
    PRIMAVERA,
    ESTATE,
    AUTUNNO
}
```

Ora `Stagione` è un **tipo sicuro**, con 4 possibili valori.

---

## 🔹 Metodo per determinare la stagione di una data

Possiamo definire una classe `Data` con metodo `getStagione()`:

```java id="qf2sdg"
class Data {
    private int giorno;
    private int mese;

    public Data(int giorno, int mese) {
        this.giorno = giorno;
        this.mese = mese;
    }

    public Stagione getStagione() {
        switch (mese) {
            case 12: case 1: case 2: return Stagione.INVERNO;
            case 3: case 4: case 5: return Stagione.PRIMAVERA;
            case 6: case 7: case 8: return Stagione.ESTATE;
            case 9: case 10: case 11: return Stagione.AUTUNNO;
            default: return null; // caso non valido
        }
    }
}
```

Esempio di utilizzo:

```java id="78gk4p"
Data d = new Data(15, 4);
System.out.println(d.getStagione()); // PRIMAVERA
```

---

# 🟢 2️⃣ Dichiarazione e inizializzazione degli array

## 🔹 Array di valori espliciti

```java id="9qx8ga"
Stagione[] stagioni = {Stagione.INVERNO, Stagione.PRIMAVERA, Stagione.ESTATE, Stagione.AUTUNNO};
```

## 🔹 Array creato con `new`

```java id="i5xcl0"
Stagione[] stagioni2 = new Stagione[4];
stagioni2[0] = Stagione.INVERNO;
stagioni2[1] = Stagione.PRIMAVERA;
stagioni2[2] = Stagione.ESTATE;
stagioni2[3] = Stagione.AUTUNNO;
```

---

## 🔹 Pseudo-campo `length`

Per ottenere la lunghezza di un array:

```java id="i0p2zk"
int n = stagioni.length;
```

---

# 🟢 3️⃣ Ciclo for-each sugli array

```java id="0soibh"
for (Stagione s : stagioni) {
    System.out.println(s);
}
```

---

# 🟢 4️⃣ Creazione dell’array delle stagioni da un array di date

```java id="1hj5pz"
Data[] date = {new Data(15, 1), new Data(20, 6), new Data(5, 9)};
Stagione[] stagioniDate = new Stagione[date.length];

for (int i = 0; i < date.length; i++) {
    stagioniDate[i] = date[i].getStagione();
}
```

---

# 🟢 5️⃣ Metodi frequenti delle classi `Enum`

Ogni enum eredita da `java.lang.Enum`:

| Metodo                          | Descrizione                                       |
| ------------------------------- | ------------------------------------------------- |
| `static E[] values()`           | Ritorna un array di tutti gli elementi dell’enum  |
| `static E valueOf(String name)` | Ritorna l’elemento che ha il nome indicato        |
| `int compareTo(E other)`        | Determina chi viene prima nell’ordine dell’enum   |
| `int ordinal()`                 | Numero d’ordine dell’elemento nell’enum (0-based) |

### 🔹 Esempio:

```java id="eok0fj"
for (Stagione s : Stagione.values()) {
    System.out.println(s + " ha ordinal " + s.ordinal());
}

Stagione s1 = Stagione.valueOf("ESTATE");
Stagione s2 = Stagione.PRIMAVERA;
System.out.println(s1.compareTo(s2)); // > 0 perché ESTATE viene dopo PRIMAVERA
```

---

# 🟢 6️⃣ Metodi frequenti di `java.util.Arrays`

Classe: **java.util.Arrays**

---

### 🔹 `binarySearch(int[] arr, int key)`

* Restituisce la posizione di `key` in `arr` ordinato
* Se non presente → numero negativo
* Funziona anche per tipi riferimento (usa `compareTo`)

```java id="7v59x3"
int[] numeri = {1, 3, 5, 7, 9};
int pos = Arrays.binarySearch(numeri, 5); // 2
```

---

### 🔹 `equals(int[] arr1, int[] arr2)`

Controlla:

* stessa lunghezza
* stessi elementi nello stesso ordine

```java id="2wnq5v"
int[] a = {1,2,3};
int[] b = {1,2,3};
System.out.println(Arrays.equals(a,b)); // true
```

---

### 🔹 `fill(int[] arr, int val)`

Assegna `val` a tutti gli elementi:

```java id="a5y03b"
int[] arr = new int[5];
Arrays.fill(arr, 7); // {7,7,7,7,7}
```

---

### 🔹 `sort(int[] arr)`

Ordina in senso crescente:

```java id="c9n0ph"
int[] arr = {5,1,3};
Arrays.sort(arr); // arr = {1,3,5}
```

---

### 🔹 `toString(int[] arr)`

Restituisce una stringa leggibile:

```java id="n7ovsz"
int[] arr = {1,2,3};
System.out.println(Arrays.toString(arr)); // [1, 2, 3]
```

Funziona anche per array di oggetti (chiama `toString()` su ciascun elemento).

---

# 🟢 7️⃣ Esempio completo

```java id="q8w4lf"
import java.util.Arrays;

public class StagioniExample {

    public static void main(String[] args) {

        Data[] date = { new Data(15,1), new Data(20,6), new Data(5,9) };
        Stagione[] stagioniDate = new Stagione[date.length];

        for (int i = 0; i < date.length; i++) {
            stagioniDate[i] = date[i].getStagione();
        }

        System.out.println(Arrays.toString(stagioniDate));

        Arrays.sort(stagioniDate); // ordina secondo ordinal
        System.out.println(Arrays.toString(stagioniDate));
    }
}
```

---

# 📊 8️⃣ Riassunto concettuale

| Concetto                | Uso                            |
| ----------------------- | ------------------------------ |
| `enum`                  | Tipo con valori finiti, sicuro |
| `values()`              | Tutti gli elementi dell’enum   |
| `valueOf(String)`       | Ottiene enum dal nome          |
| `compareTo(E)`          | Ordina enum                    |
| `ordinal()`             | Numero d’ordine                |
| `Arrays.binarySearch()` | Cerca in array ordinato        |
| `Arrays.equals()`       | Confronta array                |
| `Arrays.fill()`         | Riempie array                  |
| `Arrays.sort()`         | Ordina array                   |
| `Arrays.toString()`     | Stampa array in stringa        |
| `length`                | Lunghezza array                |
| for-each                | Scorri facilmente array        |

---

# 🧠 Idee chiave da ricordare

✔ Possiamo trasformare un array di date in array di stagioni
✔ Gli enum hanno valori ordinati e confrontabili
✔ `Arrays` fornisce metodi statici per ricerca, confronto, ordinamento e stampa
✔ for-each semplifica la lettura degli array