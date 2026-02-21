# 📜 Storia di Java

**Java** nasce nel 1995 grazie a **Sun Microsystems**, guidata da **James Gosling**.

L’obiettivo era creare un linguaggio:

* semplice
* orientato agli oggetti
* portabile su qualsiasi piattaforma

Nel 2010 Sun Microsystems è stata acquisita da **Oracle Corporation**, che oggi gestisce lo sviluppo di Java.

Il motto di Java è:

> **"Write Once, Run Anywhere"**
> (Scrivi una volta, esegui ovunque)

Questo è possibile grazie al **bytecode** e alla **Java Virtual Machine (JVM)**.

---

# 💾 Bytecode

Quando scrivi un programma Java:

1. Scrivi codice in un file `.java`
2. Il compilatore `javac` lo traduce in **bytecode**
3. Il bytecode viene salvato in un file `.class`
4. La **JVM** interpreta il bytecode ed esegue il programma

Il bytecode:

* non è codice macchina
* è indipendente dal sistema operativo
* viene eseguito dalla JVM

---

# ☕ JDK e JRE

## JDK (Java Development Kit)

Contiene:

* compilatore (`javac`)
* strumenti di sviluppo
* JRE

Serve per **sviluppare** programmi Java.

## JRE (Java Runtime Environment)

Contiene:

* JVM
* librerie standard

Serve solo per **eseguire** programmi Java.

👉 In breve:

* Vuoi programmare? → **JDK**
* Vuoi solo eseguire? → **JRE**

---

# 🧠 Programmazione ad Oggetti (OOP)

Java è un linguaggio **orientato agli oggetti**.

## 1️⃣ Incapsulazione

Nascondere i dati interni di una classe e permettere l’accesso solo tramite metodi.

Esempio:

```java
private int eta;

public int getEta() {
    return eta;
}
```

---

## 2️⃣ Ereditarietà

Una classe può ereditare caratteristiche da un’altra.

```java
class Animale {
    void verso() {
        System.out.println("Suono generico");
    }
}

class Cane extends Animale {
}
```

---

## 3️⃣ Polimorfismo

Uno stesso metodo può comportarsi in modo diverso.

```java
class Cane extends Animale {
    void verso() {
        System.out.println("Bau");
    }
}
```

---

# 🖥 Compilazione ed esecuzione da linea di comando

Supponiamo di avere il file `Hello.java`.

## Compilazione:

```
javac Hello.java
```

Viene creato:

```
Hello.class
```

## Esecuzione:

```
java Hello
```

⚠️ Senza `.class` e senza `.java`

---

# 👋 Primo esempio di programma Java

```java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Ciao mondo!");
    }
}
```

Spiegazione:

* `public class Hello` → nome della classe
* `main` → punto di ingresso del programma
* `System.out.println()` → stampa a video

---

# 🖨 Istruzioni di stampa

```java
System.out.println("Testo");  // va a capo
System.out.print("Testo");    // non va a capo
System.out.printf("Numero: %d", 10); // formattata
```

---

# 🧩 Compilazione ed esecuzione con Eclipse

**Eclipse IDE** è un ambiente di sviluppo (IDE).

Passaggi:

1. Creare un nuovo progetto Java
2. Creare una nuova classe
3. Scrivere il codice
4. Premere ▶ Run

Eclipse:

* compila automaticamente
* esegue nella JVM integrata

---

# 🔢 Tipi primitivi

| Tipo    | Dimensione | Esempio      |
| ------- | ---------- | ------------ |
| boolean | 1 bit      | true / false |
| char    | 16 bit     | 'A'          |
| byte    | 8 bit      | 100          |
| short   | 16 bit     | 30000        |
| int     | 32 bit     | 10           |
| long    | 64 bit     | 100L         |
| float   | 32 bit     | 3.14f        |
| double  | 64 bit     | 3.14         |

---

# 📝 Dichiarazione di variabili

```java
int numero;
numero = 5;
```

Oppure:

```java
int numero = 5;
```

---

# 🔒 Costanti (final)

```java
final double PI = 3.14159;
```

Non può essere modificata dopo l’assegnazione.

---

# ⚠️ Inizializzazione obbligatoria delle variabili locali

Le variabili locali **devono essere inizializzate prima di essere usate**.

❌ ERRORE:

```java
int x;
System.out.println(x);
```

✅ CORRETTO:

```java
int x = 0;
System.out.println(x);
```

---

# ➕ Operazioni aritmetiche

```java
int a = 10;
int b = 3;

a + b  // 13
a - b  // 7
a * b  // 30
a / b  // 3 (divisione intera!)
a % b  // 1 (resto)
```

---

# 🔀 Operazioni aritmetiche ibride

Se mischi tipi diversi:

```java
int a = 5;
double b = 2.0;

double risultato = a + b;  // 7.0
```

👉 Java promuove automaticamente il tipo più piccolo a quello più grande.

---

# 📌 Assegnamento

```java
int x = 10;
x = 20;
```

---

# 📌 Assegnamento composto

```java
x += 5;  // x = x + 5
x -= 3;
x *= 2;
x /= 4;
x %= 3;
```

---

# ⬆️ Pre e Post incremento/decremento

## Post-incremento

```java
int x = 5;
int y = x++;
```

* y = 5
* x = 6

## Pre-incremento

```java
int x = 5;
int y = ++x;
```

* x = 6
* y = 6

Stessa cosa per `--`.

---

# 📚 Riepilogo

Hai visto:

* ✔ Storia di Java
* ✔ Bytecode e JVM
* ✔ JDK e JRE
* ✔ Programmazione ad oggetti
* ✔ Compilazione da terminale
* ✔ Uso di Eclipse
* ✔ Tipi primitivi
* ✔ Variabili e costanti
* ✔ Operazioni aritmetiche
* ✔ Incrementi e assegnamenti