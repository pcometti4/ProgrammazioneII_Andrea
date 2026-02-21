# 🟢 1️⃣ Tipo enumerato (`enum`)

## 📌 Cos’è un enum?

Un **tipo enumerato** è un tipo che può assumere **un numero finito di valori predefiniti**.

Si definisce con la parola chiave:

```java
enum
```

---

## 🔹 Esempio base

```java
enum Giorno {
    LUNEDI,
    MARTEDI,
    MERCOLEDI,
    GIOVEDI,
    VENERDI,
    SABATO,
    DOMENICA
}
```

Ora `Giorno` è un nuovo tipo.

---

## 🔹 Uso dell’enum

```java
Giorno oggi = Giorno.LUNEDI;
```

Confronto:

```java
if (oggi == Giorno.LUNEDI) {
    System.out.println("Inizio settimana");
}
```

⚠️ Gli enum si confrontano con `==`
(perché ogni valore è unico e costante)

---

# 🧠 Perché usare enum?

Meglio di usare stringhe:

❌ Sbagliato:

```java
String giorno = "lunedi";
```

Rischio errori di scrittura.

✅ Con enum:

* Più sicuro
* Più leggibile
* Controllato dal compilatore

---

# 🔹 Enum con metodi e costruttori

Un enum è in realtà una **classe speciale**.

Possiamo definire:

* Campi
* Costruttori
* Metodi

Esempio:

```java
enum Livello {

    BASSO(1),
    MEDIO(2),
    ALTO(3);

    private int codice;

    Livello(int codice) {
        this.codice = codice;
    }

    public int getCodice() {
        return codice;
    }
}
```

Uso:

```java
Livello l = Livello.ALTO;
System.out.println(l.getCodice());
```

---

# 🔎 Metodi utili degli enum

Ogni enum ha automaticamente:

```java
values()       // restituisce tutti i valori
valueOf()      // converte da stringa a enum
name()         // nome della costante
ordinal()      // posizione (0,1,2,...)
```

Esempio:

```java
for (Giorno g : Giorno.values()) {
    System.out.println(g);
}
```

---

# 🔵 2️⃣ Metodi di confronto tra oggetti

Quando lavoriamo con oggetti dobbiamo distinguere:

* 🔹 Identità
* 🔹 Uguaglianza logica

---

## 🔹 Identità (==)

Confronta i riferimenti in memoria.

```java
Persona p1 = new Persona("Luca");
Persona p2 = new Persona("Luca");

System.out.println(p1 == p2);  // false
```

Sono due oggetti diversi.

---

## 🔹 Uguaglianza logica (equals)

Metodo definito nella classe:

**java.lang.Object**

Firma:

```java
public boolean equals(Object obj)
```

Di default confronta i riferimenti
→ quindi si comporta come `==`

---

# ✏️ Ridefinire equals()

Per confrontare il contenuto, dobbiamo sovrascriverlo.

Esempio:

```java
class Persona {

    private String nome;

    public Persona(String nome) {
        this.nome = nome;
    }

    @Override
    public boolean equals(Object obj) {

        if (this == obj) return true;

        if (obj == null) return false;

        if (getClass() != obj.getClass()) return false;

        Persona other = (Persona) obj;

        return nome.equals(other.nome);
    }
}
```

Ora:

```java
Persona p1 = new Persona("Luca");
Persona p2 = new Persona("Luca");

System.out.println(p1.equals(p2));  // true
```

---

# 📊 equals vs ==

| Operatore  | Cosa confronta            |
| ---------- | ------------------------- |
| `==`       | Riferimenti               |
| `equals()` | Contenuto (se ridefinito) |

---

# 🔁 Metodo compareTo()

Per confronti di ordinamento si usa:

```java
compareTo()
```

Fa parte dell’interfaccia:

```java
Comparable<T>
```

Esempio:

```java
class Persona implements Comparable<Persona> {

    private String nome;

    public Persona(String nome) {
        this.nome = nome;
    }

    @Override
    public int compareTo(Persona other) {
        return this.nome.compareTo(other.nome);
    }
}
```

Restituisce:

* negativo → minore
* zero → uguale
* positivo → maggiore

---

# 📌 Buone pratiche

Quando ridefiniamo `equals()`:

* È buona norma ridefinire anche `hashCode()`
* equals deve essere:

  * riflessivo
  * simmetrico
  * transitivo
  * consistente

---

# 🎯 Esempio completo con enum e confronto

```java
enum Stato {
    NUOVO,
    IN_LAVORAZIONE,
    COMPLETATO
}

class Ordine {

    private int codice;
    private Stato stato;

    public Ordine(int codice, Stato stato) {
        this.codice = codice;
        this.stato = stato;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;

        Ordine other = (Ordine) obj;
        return this.codice == other.codice;
    }
}
```

---

# 📚 Riassunto finale

| Concetto    | Significato               |
| ----------- | ------------------------- |
| enum        | Tipo con valori finiti    |
| == (enum)   | Confronto diretto         |
| equals()    | Confronto logico oggetti  |
| compareTo() | Confronto per ordinamento |
| values()    | Tutti i valori enum       |
| ordinal()   | Posizione enum            |

---

# 🧠 Idee chiave

✔ enum è una classe speciale
✔ Gli enum si confrontano con `==`
✔ equals() va ridefinito per confronto logico
✔ compareTo() serve per ordinamento
✔ equals di default confronta riferimenti