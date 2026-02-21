# 🧱 Definizione di una nostra classe

Una **classe** è un modello (blueprint) per creare oggetti.

Una classe può contenere:

* ✅ **Campi** (variabili d’istanza → rappresentano lo stato)
* ✅ **Costruttori** (inizializzano l’oggetto)
* ✅ **Metodi** (comportamenti)

---

# 📌 Struttura generale di una classe

```java
public class Persona {

    // CAMPI
    private String nome;
    private int eta;

    // COSTRUTTORE
    public Persona(String nome, int eta) {
        this.nome = nome;
        this.eta = eta;
    }

    // METODI
    public void saluta() {
        System.out.println("Ciao, mi chiamo " + nome);
    }

    public int getEta() {
        return eta;
    }
}
```

---

# 🟦 1️⃣ Campi (variabili d’istanza)

I **campi** rappresentano lo stato dell’oggetto.

```java
private String nome;
private int eta;
```

Ogni oggetto della classe `Persona` avrà il suo `nome` e la sua `eta`.

Esempio:

```java
Persona p1 = new Persona("Luca", 20);
Persona p2 = new Persona("Anna", 25);
```

Ogni oggetto ha i propri valori.

---

# ⚙️ Valore di default dei campi

Se non inizializzi un campo, Java assegna un valore di default.

| Tipo             | Valore di default |
| ---------------- | ----------------- |
| int              | 0                 |
| double           | 0.0               |
| boolean          | false             |
| char             | '\u0000'          |
| Tipo riferimento | null              |

Esempio:

```java
class Esempio {
    int x;
    String s;
}
```

Qui:

* `x` vale 0
* `s` vale null

⚠️ Questo vale solo per **campi**, non per variabili locali!

---

# 🏗 2️⃣ Costruttore

Il **costruttore** serve per inizializzare l’oggetto.

Caratteristiche:

* Ha lo stesso nome della classe
* Non ha tipo di ritorno
* Viene chiamato con `new`

Esempio:

```java
public Persona(String nome, int eta) {
    this.nome = nome;
    this.eta = eta;
}
```

Creazione oggetto:

```java
Persona p = new Persona("Mario", 30);
```

---

# 🔒 3️⃣ Modificatori public e private

Servono per controllare l’accesso.

## 🔹 public

Accessibile ovunque.

## 🔹 private

Accessibile solo dentro la stessa classe.

---

# 🛡 Incapsulazione dello stato

Principio fondamentale della OOP:

> Lo stato dell’oggetto deve essere protetto.

Per questo i campi si dichiarano **private**.

Esempio corretto:

```java
private int eta;
```

E si forniscono metodi pubblici per accedere:

```java
public int getEta() {
    return eta;
}
```

Questo permette di:

* controllare i dati
* evitare modifiche non valide
* rendere il codice più sicuro

---

# ❌ Esempio NON incapsulato

```java
public int eta;
```

Chiunque può fare:

```java
p.eta = -100;
```

Pericoloso.

---

# ✅ Esempio incapsulato con controllo

```java
public void setEta(int eta) {
    if (eta >= 0) {
        this.eta = eta;
    }
}
```

Ora l’oggetto è protetto.

---

# 🧠 Il parametro implicito `this`

`this` è un riferimento all’oggetto corrente.

Si usa quando:

* Il nome del parametro è uguale al nome del campo
* Vogliamo riferirci esplicitamente all’oggetto

Esempio:

```java
public Persona(String nome) {
    this.nome = nome;
}
```

Qui:

* `this.nome` → campo dell’oggetto
* `nome` → parametro del costruttore

Senza `this`:

```java
nome = nome; // ERRORE LOGICO
```

Non funzionerebbe come previsto.

---

# 🧭 Cosa rappresenta this?

Se scriviamo:

```java
Persona p = new Persona("Luca", 20);
```

Dentro il costruttore, `this` è come se fosse:

```
this → p
```

---

# 🧪 Esempio completo

```java
public class Contatore {

    private int valore;

    public Contatore(int valore) {
        this.valore = valore;
    }

    public void incrementa() {
        valore++;
    }

    public int getValore() {
        return valore;
    }
}
```

Uso:

```java
Contatore c = new Contatore(5);
c.incrementa();
System.out.println(c.getValore()); // 6
```

---

# 📊 Riassunto concettuale

| Concetto       | Significato                      |
| -------------- | -------------------------------- |
| Classe         | Modello                          |
| Oggetto        | Istanza della classe             |
| Campi          | Stato dell’oggetto               |
| Costruttore    | Inizializza l’oggetto            |
| public         | Accessibile ovunque              |
| private        | Accessibile solo nella classe    |
| Incapsulazione | Protezione dello stato           |
| this           | Riferimento all’oggetto corrente |

---

# 🎯 Idee fondamentali da ricordare

✔ I campi devono essere private
✔ Il costruttore inizializza l’oggetto
✔ this distingue campo da parametro
✔ L’incapsulazione protegge lo stato