# 🧩 I due mondi di Java: tipi primitivi e tipi riferimento

In Java esistono **due categorie completamente diverse di tipi**:

## 1️⃣ Tipi primitivi

## 2️⃣ Tipi riferimento (oggetti)

Sono due “mondi” separati.

---

# 🔹 1️⃣ Tipi primitivi

Esempi:

```java
int
double
boolean
char
byte
short
long
float
```

Caratteristiche:

* Contengono **direttamente il valore**
* Non sono oggetti
* Non hanno metodi
* Non possono essere `null`

Esempio:

```java
int x = 10;
```

Qui `x` contiene direttamente il numero 10.

---

# 🔹 2️⃣ Tipi riferimento (Oggetti)

Esempi:

```java
String
Scanner
Random
Persona (classe definita da noi)
```

Caratteristiche:

* Contengono **un riferimento (indirizzo) a un oggetto**
* Possono essere `null`
* Hanno metodi
* Si creano con `new` (tranne casi speciali come String letterali)

Esempio:

```java
String s = "ciao";
```

Qui `s` contiene un riferimento a un oggetto `String`.

---

# ⚠️ Nessuna conversione tra i due mondi

Non esistono conversioni automatiche tra:

* tipi primitivi
* tipi riferimento

Esempio **non valido**:

```java
int x = 5;
String s = x;   // ERRORE
```

Sono due mondi separati.

---

# 🚫 I tipi primitivi NON hanno metodi

Questo è fondamentale.

❌ Errore:

```java
int x = 10;
x.toString();  // ERRORE
```

Perché?
Perché `int` **non è un oggetto**.

Invece:

```java
String s = "ciao";
s.length();   // OK
```

Funziona perché `String` è un oggetto.

---

# 🕳 Il valore speciale `null`

Solo le variabili di tipo riferimento possono valere:

```java
null
```

Esempio:

```java
String s = null;
```

Significa:

> la variabile non punta a nessun oggetto

---

# 💥 Mai usare metodi su null!

Esempio pericoloso:

```java
String s = null;
System.out.println(s.length());  // ERRORE a runtime
```

Questo genera:

```
NullPointerException
```

Regola d’oro:

> ⚠️ Mai chiamare metodi su una variabile che può essere null!

Meglio fare:

```java
if (s != null) {
    System.out.println(s.length());
}
```

---

# 🔗 Concatenazione con +

Quando concateni un oggetto con una stringa:

```java
String nome = "Mario";
System.out.println("Ciao " + nome);
```

Oppure:

```java
Persona p = new Persona();
System.out.println(p);
```

Java **chiama automaticamente il metodo `toString()`**.

---

# 🔍 toString() implicito

Classe: **java.lang.Object**

Tutte le classi in Java ereditano da `Object`.

`Object` contiene il metodo:

```java
toString()
```

Quando fai:

```java
System.out.println(oggetto);
```

Java fa implicitamente:

```java
System.out.println(oggetto.toString());
```

---

# 🧪 Esempio pratico

```java
class Persona {
    String nome;

    public String toString() {
        return "Persona: " + nome;
    }
}
```

Uso:

```java
Persona p = new Persona();
p.nome = "Luca";

System.out.println(p);
```

Output:

```
Persona: Luca
```

Perché viene chiamato automaticamente `toString()`.

---

# 🔄 Concatenazione e toString()

Quando scrivi:

```java
System.out.println("Oggetto: " + p);
```

Java fa:

1. Converte `p` in stringa tramite `toString()`
2. Concatena le stringhe
3. Stampa il risultato

---

# 📌 Caso particolare: tipi primitivi

Se scrivi:

```java
int x = 10;
System.out.println("Valore: " + x);
```

Java usa automaticamente:

```java
String.valueOf(x);
```

per convertire il primitivo in stringa.

---

# 🧠 Differenza fondamentale in memoria

## Tipo primitivo

```
x = 10
```

La variabile contiene direttamente 10.

---

## Tipo riferimento

```
s ----> "ciao"
```

La variabile contiene un indirizzo.

---

# 📊 Confronto riassuntivo

| Primitivi               | Riferimento           |
| ----------------------- | --------------------- |
| Contengono valore       | Contengono indirizzo  |
| Non hanno metodi        | Hanno metodi          |
| Non possono essere null | Possono essere null   |
| Non usano new           | Usano new (di solito) |

---

# 🎯 Errori tipici da evitare

❌ Chiamare metodi su primitivi
❌ Usare metodi su variabili null
❌ Pensare che un oggetto contenga direttamente il valore

---

# 📚 Concetti chiave da ricordare

✔ Due mondi separati
✔ I primitivi non sono oggetti
✔ null vale solo per riferimenti
✔ Mai usare metodi su null
✔ println() chiama implicitamente toString()
✔ + con oggetti usa toString()