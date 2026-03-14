# Lezione Universitaria: Java – Metodi e Classi Astratte

## Obiettivi della lezione

* Comprendere il concetto di **classi e metodi astratti** in Java.
* Distinguere tra classi astratte e interfacce.
* Applicare classi astratte per creare gerarchie di oggetti geometrici.
* Esempio pratico: classi astratte per figure geometriche e loro implementazioni.

---

## 1. Cos’è una classe astratta

Una **classe astratta** è una classe che **non può essere istanziata** direttamente e può contenere:

* Metodi **astratti** (dichiarati senza implementazione)
* Metodi concreti (con implementazione)
* Variabili di istanza e costanti

### Caratteristiche principali:

* Una classe astratta si dichiara con la parola chiave `abstract`.
* I metodi astratti si dichiarano con `abstract` e **non hanno corpo**.
* Le classi astratte possono avere costruttori e variabili.
* Una sottoclasse concreta deve implementare tutti i metodi astratti.

```java
abstract class Figura {
    String colore;

    public Figura(String colore) {
        this.colore = colore;
    }

    abstract double area();
    abstract double perimetro();

    public void stampaColore() {
        System.out.println("Colore: " + colore);
    }
}
```

---

## 2. Differenze tra classi astratte e interfacce

* **Classi astratte:** possono avere metodi concreti e variabili di istanza; una classe può estendere solo una classe astratta.
* **Interfacce:** tutti i metodi sono implicitamente astratti fino a Java 7; supportano polimorfismo multiplo.

---

## 3. Esempio pratico: Figure geometriche

### 3.1 Classe astratta Figura

```java
abstract class Figura {
    String colore;

    public Figura(String colore) {
        this.colore = colore;
    }

    abstract double area();
    abstract double perimetro();

    public void stampaColore() {
        System.out.println("Colore: " + colore);
    }
}
```

### 3.2 Sottoclassi concrete

```java
class Rettangolo extends Figura {
    private double larghezza, altezza;

    public Rettangolo(double larghezza, double altezza, String colore) {
        super(colore);
        this.larghezza = larghezza;
        this.altezza = altezza;
    }

    @Override
    double area() {
        return larghezza * altezza;
    }

    @Override
    double perimetro() {
        return 2 * (larghezza + altezza);
    }
}

class Cerchio extends Figura {
    private double raggio;

    public Cerchio(double raggio, String colore) {
        super(colore);
        this.raggio = raggio;
    }

    @Override
    double area() {
        return Math.PI * raggio * raggio;
    }

    @Override
    double perimetro() {
        return 2 * Math.PI * raggio;
    }
}
```

### 3.3 Utilizzo delle classi

```java
public class Main {
    public static void main(String[] args) {
        Figura[] figure = {
            new Rettangolo(5, 10, "rosso"),
            new Cerchio(7, "blu")
        };

        for (Figura f : figure) {
            f.stampaColore();
            System.out.println("Area: " + f.area());
            System.out.println("Perimetro: " + f.perimetro());
            System.out.println("--------------------");
        }
    }
}
```

---

## 4. Vantaggi dell’uso di classi astratte

* Permettono di definire un **modello comune** per oggetti correlati.
* Consentono di condividere **metodi concreti** tra le sottoclassi.
* Favoriscono la **riusabilità del codice** e il polimorfismo.
* Utile quando alcune funzionalità sono comuni, altre devono essere implementate specificamente.

---

## 5. Riepilogo

* Le classi astratte non possono essere istanziate, ma possono contenere sia metodi concreti che astratti.
* Le sottoclassi concrete devono implementare tutti i metodi astratti.
* Le classi astratte sono ideali per gerarchie di oggetti come le figure geometriche, dove alcune funzionalità sono comuni e altre variano.
