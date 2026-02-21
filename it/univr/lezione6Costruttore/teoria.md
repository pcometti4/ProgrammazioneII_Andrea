# 🏗 1️⃣ Costruttore di default

Se **non scriviamo nessun costruttore**, Java ne genera automaticamente uno:

```java
public Classe() {
}
```

Esempio:

```java
class Persona {
    String nome;
}
```

Java crea automaticamente:

```java
public Persona() { }
```

⚠️ Ma attenzione:

Se definiamo **almeno un costruttore**, quello di default **non viene più generato automaticamente**.

Esempio:

```java
class Persona {
    String nome;

    public Persona(String nome) {
        this.nome = nome;
    }
}
```

Ora `new Persona()` genera errore.

---

# ▶️ 2️⃣ Attivazione di un metodo o costruttore

Quando chiamiamo un metodo o creiamo un oggetto:

```java
Persona p = new Persona("Luca");
p.saluta();
```

Avviene una **attivazione**:

1. Vengono creati i parametri
2. Viene riservato spazio in memoria
3. Il metodo/costruttore viene eseguito

---

# 🧾 3️⃣ Parametri formali e attuali

## 🔹 Parametri formali

Sono quelli dichiarati nel metodo:

```java
public void saluta(String messaggio)
```

`messaggio` è parametro formale.

---

## 🔹 Parametri attuali

Sono quelli passati alla chiamata:

```java
p.saluta("Ciao!");
```

`"Ciao!"` è parametro attuale.

---

# 📚 4️⃣ Record di attivazione e Stack

Quando un metodo viene chiamato:

* viene creato un **record di attivazione**
* viene messo nello **stack (pila)**

Lo stack contiene:

* parametri
* variabili locali
* indirizzo di ritorno

Esempio:

```java
main()
   ↓
metodoA()
   ↓
metodoB()
```

Lo stack cresce e poi si svuota al ritorno dei metodi.

È chiamato **stack di attivazione**.

---

# 🔒 5️⃣ Modificatore final

## 🔹 final per variabili locali

```java
final int x = 10;
```

Non può essere modificata.

---

## 🔹 final per campi

```java
private final int anno;
```

Deve essere inizializzato:

* nel costruttore
* oppure direttamente alla dichiarazione

Esempio:

```java
public Persona(int anno) {
    this.anno = anno;
}
```

Dopo non può più cambiare.

---

# 📦 6️⃣ Creazione di array (enumerazione degli elementi)

Un array è una struttura che contiene più elementi dello stesso tipo.

## Creazione:

```java
int[] numeri = new int[5];
```

Oppure:

```java
int[] numeri = {1, 2, 3, 4, 5};
```

---

## Enumerazione con for:

```java
for (int i = 0; i < numeri.length; i++) {
    System.out.println(numeri[i]);
}
```

Oppure for-each:

```java
for (int n : numeri) {
    System.out.println(n);
}
```

---

# 🏢 7️⃣ Campi static

Un campo static appartiene alla **classe**, non agli oggetti.

Esempio:

```java
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

Qui:

* `numeroOggetti` è condiviso da tutti gli oggetti
* Si accede con:

```java
Contatore.getNumeroOggetti();
```

---

# 📅 8️⃣ Controllo di legalità delle date

Esempio classe Data:

```java
class Data {

    private int giorno;
    private int mese;
    private int anno;

    public Data(int giorno, int mese, int anno) {

        if (mese < 1 || mese > 12) {
            throw new IllegalArgumentException("Mese non valido");
        }

        if (giorno < 1 || giorno > 31) {
            throw new IllegalArgumentException("Giorno non valido");
        }

        this.giorno = giorno;
        this.mese = mese;
        this.anno = anno;
    }
}
```

Il controllo deve essere fatto nel costruttore
→ garantisce che l’oggetto sia sempre valido.

---

# 🔁 9️⃣ Overloading dei costruttori

Possiamo avere più costruttori con parametri diversi.

```java
class Persona {

    private String nome;
    private int eta;

    public Persona(String nome) {
        this.nome = nome;
        this.eta = 0;
    }

    public Persona(String nome, int eta) {
        this.nome = nome;
        this.eta = eta;
    }
}
```

Si chiama **overloading**.

Regola:

* stesso nome
* parametri diversi

---

# 🔗 🔟 Concatenazione dei costruttori – this()

Possiamo far chiamare un costruttore da un altro usando:

```java
this(...)
```

Esempio migliorato:

```java
class Persona {

    private String nome;
    private int eta;

    public Persona(String nome) {
        this(nome, 0);
    }

    public Persona(String nome, int eta) {
        this.nome = nome;
        this.eta = eta;
    }
}
```

Quando chiami:

```java
new Persona("Luca");
```

Viene eseguito:

```
this("Luca", 0);
```

⚠️ Regola importante:

`this()` deve essere **la prima istruzione del costruttore**.

---

# 📊 Riassunto finale

| Concetto               | Significato                                |
| ---------------------- | ------------------------------------------ |
| Costruttore di default | Creato automaticamente se non ne scriviamo |
| Parametri formali      | Nella definizione                          |
| Parametri attuali      | Nella chiamata                             |
| Stack                  | Memoria per chiamate metodo                |
| final                  | Non modificabile                           |
| static                 | Appartiene alla classe                     |
| Array                  | Collezione di elementi                     |
| Overloading            | Stesso nome, parametri diversi             |
| this()                 | Chiama altro costruttore                   |

---

# 🎯 Concetti chiave da memorizzare

✔ Se definisci un costruttore, perdi quello di default
✔ Lo stack gestisce le chiamate ai metodi
✔ final rende immutabile
✔ static appartiene alla classe
✔ this() collega costruttori
✔ Il controllo di validità va fatto nel costruttore