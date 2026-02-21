# 📌 1️⃣ Lettura dell’input da tastiera – `java.util.Scanner`

Per leggere dati da tastiera si usa la classe:

```java
import java.util.Scanner;
```

⚠️ Le classi del pacchetto `java.util` **non** sono importate automaticamente.
Invece **`java.lang` è sempre importato di default** (contiene `String`, `System`, ecc.).

Esempio base:

```java
import java.util.Scanner;

public class EsempioInput {
    public static void main(String[] args) {

        Scanner tastiera = new Scanner(System.in);

        System.out.print("Inserisci un numero: ");
        int numero = tastiera.nextInt();

        System.out.println("Hai inserito: " + numero);

        tastiera.close();
    }
}
```

Qui:

* `System.in` → input standard
* `nextInt()` → legge un intero
* `close()` → chiude lo scanner

---

## Metodi principali di `Scanner`

Classe: **java.util.Scanner**

Costruttore:

```java
Scanner(System.in)
```

Metodi frequenti:

```java
nextInt()
nextDouble()
nextFloat()
nextLong()
nextLine()
close()
```

⚠️ Attenzione: dopo `nextInt()` resta il newline nel buffer.
Spesso serve un `nextLine()` di pulizia.

---

# 📌 2️⃣ Strutture di controllo (come in C)

## 🔹 if

```java
if (x > 0) {
    System.out.println("Positivo");
} else {
    System.out.println("Negativo");
}
```

---

## 🔹 while

```java
while (x < 10) {
    x++;
}
```

---

## 🔹 do-while

```java
do {
    x++;
} while (x < 10);
```

---

## 🔹 for

```java
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}
```

---

## 🔹 switch

```java
switch (scelta) {
    case 1:
        System.out.println("Uno");
        break;
    case 2:
        System.out.println("Due");
        break;
    default:
        System.out.println("Altro");
}
```

---

# 📌 3️⃣ Identità vs uguaglianza delle stringhe

Classe: **java.lang.String**

## ❌ Confronto con `==`

Confronta **riferimenti (indirizzi)** in memoria.

```java
String a = new String("ciao");
String b = new String("ciao");

System.out.println(a == b); // false
```

---

## ✅ Confronto con `equals()`

Confronta il contenuto.

```java
System.out.println(a.equals(b)); // true
```

👉 Regola d’oro:
**Le stringhe si confrontano con equals()**

---

# 📌 4️⃣ Concatenazione con +

```java
String s = "Ciao " + "Mario";
```

Internamente Java usa:

* `concat()`
* `String.valueOf()`

Esempio:

```java
int x = 10;
String s = "Numero: " + x;
```

Qui Java usa implicitamente:

```java
String.valueOf(x)
```

---

# 📌 5️⃣ Classe e Oggetto

## Classe

È un modello (blueprint).

```java
class Persona {
    String nome;
    int eta;
}
```

## Oggetto

È un’istanza della classe.

```java
Persona p = new Persona();
```

`new`:

* alloca memoria
* crea l’oggetto

---

## Caso speciale: String

```java
String s1 = "ciao";
String s2 = "ciao";
```

Qui Java usa lo **String Pool**.

Non serve `new`.

---

# 📌 6️⃣ Concetto di metodo

## Metodo d’istanza

Invocato su un oggetto:

```java
s.length();
```

Sintassi:

```
oggetto.metodo()
```

---

## Metodo statico

Invocato sulla classe:

```java
Math.sqrt(25);
```

Sintassi:

```
Classe.metodo()
```

Esempio:

```java
String.valueOf(10);
```

---

# 📌 7️⃣ Garbage e Garbage Collection

Quando un oggetto non ha più riferimenti:

```java
Persona p = new Persona();
p = null;
```

Diventa **garbage**.

La **Garbage Collection** libera automaticamente la memoria.

Java gestisce la memoria automaticamente.

---

# 📌 8️⃣ Classe String – Metodi principali

Ricorda:
**String è immutabile** → ogni modifica crea un nuovo oggetto.

---

## Costruttore di copia

```java
String s2 = new String(s1);
```

---

## Accesso caratteri

```java
charAt(int index)
```

---

## Confronti

```java
compareTo()
compareToIgnoreCase()
equals()
equalsIgnoreCase()
```

`compareTo()` ritorna:

* negativo
* zero
* positivo

---

## Concatenazione

```java
concat(String other)
```

---

## Ricerca

```java
indexOf(int character)
indexOf(String what)
startsWith()
endsWith()
```

---

## Lunghezza

```java
length()
isEmpty()
```

---

## Sottostringhe

```java
substring(start)
substring(start, end)
```

⚠️ end è escluso

---

## Maiuscole / minuscole

```java
toLowerCase()
toUpperCase()
```

---

## Rimozione spazi

```java
trim()
```

---

## Metodo statico format

```java
String.format("Numero: %d", 10);
```

---

# 📌 9️⃣ Classe System

Classe: **java.lang.System**

Costanti:

```java
System.in
System.out
System.err
```

Metodo utile:

```java
System.currentTimeMillis();
```

Restituisce millisecondi dal 1 gennaio 1970 (UTC).

---

# 🎯 Esempio completo riassuntivo

```java
import java.util.Scanner;

public class Demo {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Nome: ");
        String nome = sc.nextLine().trim();

        if (!nome.isEmpty()) {
            System.out.println("Ciao " + nome.toUpperCase());
        }

        long tempo = System.currentTimeMillis();
        System.out.println("Tempo attuale: " + tempo);

        sc.close();
    }
}
```

---

# 📚 Riepilogo concettuale

Hai visto:

* ✔ Scanner e input
* ✔ Importazione librerie
* ✔ If, while, for, switch
* ✔ String: == vs equals()
* ✔ Concatenazione +
* ✔ Classe e oggetto
* ✔ new
* ✔ Metodi statici e di istanza
* ✔ Garbage collection
* ✔ Metodi fondamentali di String
* ✔ Metodi di System
* ✔ Metodi di Scanner