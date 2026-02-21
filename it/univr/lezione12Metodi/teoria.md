# 🟢 1️⃣ Ridefinizione o aggiunta di metodi

## 🔹 Ridefinizione (Overriding)

* Una **sottoclasse** può ridefinire un metodo della **superclasse**
* Stesso **nome**, **parametri** e **tipo di ritorno**
* Permette di cambiare il comportamento ereditato

Esempio:

```java
class Animale {
    public void verso() {
        System.out.println("L'animale fa un verso");
    }
}

class Cane extends Animale {
    @Override
    public void verso() {
        System.out.println("Il cane abbaia");
    }
}
```

* `Cane.verso()` sostituisce il comportamento della superclasse `Animale`.

---

## 🔹 Aggiunta di metodi (Overloading)

* Una sottoclasse può **aggiungere nuovi metodi** che la superclasse non possiede
* Non si tratta di overriding, ma di **overloading** o semplicemente di metodi aggiuntivi:

```java
class Cane extends Animale {
    public void dormi() {
        System.out.println("Il cane dorme");
    }
}
```

---

# 🟢 2️⃣ Relazione di sottoclasse e superclasse

* **Superclasse**: classe di livello superiore, contiene metodi e campi comuni
* **Sottoclasse**: classe derivata che **eredita** dalla superclasse

```java
Animale a = new Animale();
Cane c = new Cane(); // Cane è sottoclasse di Animale
```

* Una sottoclasse eredita i metodi e campi pubblici e protetti della superclasse
* Può ridefinirli o aggiungerne di nuovi

---

# 🟢 3️⃣ Tipo statico e tipo dinamico

* **Tipo statico**: tipo dichiarato della variabile
* **Tipo dinamico**: tipo reale dell’oggetto in memoria

```java
Animale a = new Cane(); // tipo statico: Animale, tipo dinamico: Cane
```

* Il compilatore usa **tipo statico** per controllare la sintassi
* Il runtime usa **tipo dinamico** per eseguire i metodi ridefiniti

---

# 🟢 4️⃣ Late binding (risoluzione tardiva dei metodi)

* I metodi ridefiniti vengono **risolti a runtime**, non a compilazione
* Si chiama **late binding** o **dynamic dispatch**

Esempio:

```java
Animale a = new Cane();
a.verso(); // Output: "Il cane abbaia" (runtime sceglie il metodo corretto)
```

* Anche se `a` ha tipo statico `Animale`, viene eseguito il metodo di `Cane` perché `verso()` è ridefinito

---

# 🟢 5️⃣ Il class tag

* Ogni oggetto in Java contiene un **class tag** interno
* Serve al runtime per sapere **di quale classe reale è l’oggetto**
* Permette il **late binding**, cioè scegliere il metodo corretto a runtime

---

# 🟢 6️⃣ Ereditarietà singola e multipla

* **Java supporta solo ereditarietà singola tra classi**

```java
class Animale { ... }
class Cane extends Animale { ... } // ok
```

* **Non è possibile ereditare da più classi contemporaneamente**:

```java
class Gatto extends Animale, Cane { ... } // ERRORE
```

* **Soluzione Java**: usare **interfacce** (`interface`) per ottenere ereditarietà multipla di comportamenti

---

# 📊 7️⃣ Riassunto concettuale

| Concetto                   | Spiegazione                                             |
| -------------------------- | ------------------------------------------------------- |
| Ridefinizione (overriding) | Sottoclasse cambia comportamento di un metodo ereditato |
| Aggiunta di metodi         | Sottoclasse introduce nuovi metodi                      |
| Superclasse / Sottoclasse  | Relazione "is-a" tra classi                             |
| Tipo statico               | Tipo dichiarato della variabile                         |
| Tipo dinamico              | Tipo reale dell’oggetto in memoria                      |
| Late binding               | Risoluzione del metodo ridefinito a runtime             |
| Class tag                  | Informazione interna dell’oggetto sul tipo reale        |
| Ereditarietà singola       | Una classe può estendere solo una superclasse           |
| Ereditarietà multipla      | Non consentita tra classi; risolta con interfacce       |

---

# 🧠 Idee chiave da ricordare

✔ Il tipo statico serve per controlli a compile-time
✔ Il tipo dinamico determina quale metodo ridefinito eseguire
✔ Late binding è alla base del polimorfismo runtime
✔ Class tag permette al runtime di identificare l’oggetto
✔ Java consente ereditarietà singola, ma le interfacce permettono polimorfismo multiplo