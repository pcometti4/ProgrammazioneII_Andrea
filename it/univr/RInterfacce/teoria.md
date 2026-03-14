# Lezione Universitaria: Java – Interfacce

## Obiettivi della lezione

* Comprendere il concetto di **interfacce** in Java.
* Conoscere la **visibilità implicita** di interfacce e metodi.
* Applicare interfacce per creare classi flessibili e riutilizzabili.
* Esempio pratico: interfaccia per date con tempo, e semplificazione dei metodi `equals()` e `compareTo()`.

---

## 1. Cos’è un’interfaccia

Un’interfaccia in Java è un **contratto** che definisce un insieme di metodi che una classe deve implementare, senza fornire l’implementazione dei metodi stessi (fino a Java 7).

### Caratteristiche principali:

* Tutti i metodi di un’interfaccia sono **implicitamente `public abstract`**.
* Tutte le variabili sono **implicitamente `public static final`** (costanti).
* Una classe può implementare **più interfacce** (polimorfismo multiplo).
* Non può avere costruttori (non può essere istanziata).

```java
public interface EsempioInterfaccia {
    void metodo1();
    int metodo2(String parametro);
}
```

---

## 2. Visibilità delle interfacce e dei metodi

* L’interfaccia stessa è `public` se deve essere visibile da altri package.
* Tutti i metodi dichiarati in un’interfaccia sono implicitamente `public`, quindi **non serve scrivere `public` davanti a ciascun metodo**.

```java
interface Visibilita {
    void metodo(); // è già public abstract
}
```

---

## 3. Esempio pratico: Interfaccia per Date con tempo

Supponiamo di voler creare un'interfaccia `DataConTempo` per rappresentare date e orari, indipendentemente dalla nazione o dal fuso orario.

### 3.1 Definizione dell’interfaccia

```java
public interface DataConTempo {
    int getAnno();
    int getMese();
    int getGiorno();
    int getOra();
    int getMinuti();
    int getSecondi();
    
    // Metodo di confronto
    int compareTo(DataConTempo altraData);
    
    // Metodo per verificare uguaglianza
    boolean equals(Object obj);
}
```

> Nota: `compareTo` restituisce:
>
> * `< 0` se questa data è precedente a `altraData`
> * `0` se sono uguali
> * `> 0` se questa data è successiva a `altraData`

### 3.2 Implementazione della classe

```java
import java.util.Objects;

public class DataConcreta implements DataConTempo {
    private int anno, mese, giorno, ora, minuti, secondi;

    public DataConcreta(int anno, int mese, int giorno, int ora, int minuti, int secondi) {
        this.anno = anno;
        this.mese = mese;
        this.giorno = giorno;
        this.ora = ora;
        this.minuti = minuti;
        this.secondi = secondi;
    }

    @Override
    public int getAnno() { return anno; }

    @Override
    public int getMese() { return mese; }

    @Override
    public int getGiorno() { return giorno; }

    @Override
    public int getOra() { return ora; }

    @Override
    public int getMinuti() { return minuti; }

    @Override
    public int getSecondi() { return secondi; }

    @Override
    public int compareTo(DataConTempo altraData) {
        if (anno != altraData.getAnno()) return anno - altraData.getAnno();
        if (mese != altraData.getMese()) return mese - altraData.getMese();
        if (giorno != altraData.getGiorno()) return giorno - altraData.getGiorno();
        if (ora != altraData.getOra()) return ora - altraData.getOra();
        if (minuti != altraData.getMinuti()) return minuti - altraData.getMinuti();
        return secondi - altraData.getSecondi();
    }

    @Override
    public boolean equals(Object obj) {
        if (!(obj instanceof DataConTempo)) return false;
        return compareTo((DataConTempo) obj) == 0;
    }

    @Override
    public int hashCode() {
        return Objects.hash(anno, mese, giorno, ora, minuti, secondi);
    }
}
```

### 3.3 Utilizzo della classe

```java
public class Main {
    public static void main(String[] args) {
        DataConTempo data1 = new DataConcreta(2026, 3, 14, 12, 30, 0);
        DataConTempo data2 = new DataConcreta(2026, 3, 14, 12, 30, 0);
        DataConTempo data3 = new DataConcreta(2025, 12, 25, 9, 0, 0);

        System.out.println(data1.equals(data2)); // true
        System.out.println(data1.compareTo(data3)); // > 0
    }
}
```

---

## 4. Vantaggi dell’uso delle interfacce

* **Polimorfismo**: permette di trattare oggetti diversi allo stesso modo.
* **Separazione tra contratto e implementazione**: la logica di confronto e uguaglianza è standardizzata.
* **Riutilizzabilità**: qualsiasi altra classe che rappresenti date può implementare `DataConTempo` senza modificare il codice esistente.

---

### 5. Riepilogo

* Le interfacce definiscono **cosa** un oggetto deve fare, non **come** farlo.
* I metodi sono **implicitamente `public`**, le variabili `public static final`.
* L’interfaccia `DataConTempo` semplifica `equals()` e `compareTo()` per tutte le implementazioni di date.
