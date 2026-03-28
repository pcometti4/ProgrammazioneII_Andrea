# Lezione Universitaria di Programmazione Java

## 1. La parola chiave `final` in Java

### 1.1 Classi `final`

* Una classe dichiarata `final` **non può essere estesa**.

```java
public final class Utility {
    public static void stampa(String messaggio) {
        System.out.println(messaggio);
    }
}

// Tentativo di estendere Utility genera errore
// class Estensione extends Utility {} // ERRORE
```

### 1.2 Metodi `final`

* Un metodo `final` **non può essere ridefinito** nelle sottoclassi.

```java
class Animale {
    public final void mangia() {
        System.out.println("L'animale mangia");
    }
}

class Cane extends Animale {
    // public void mangia() {} // ERRORE
}
```

## 2. Visibilità dei membri: `public`, `protected`, `package` (default) e `private`

| Modificatore                  | Accesso nella stessa classe | Subclass (stesso package) | Classe in altro package      |
| ----------------------------- | --------------------------- | ------------------------- | ---------------------------- |
| `public`                      | sì                          | sì                        | sì                           |
| `protected`                   | sì                          | sì                        | sì (solo tramite estensione) |
| default (nessun modificatore) | sì                          | sì                        | no                           |
| `private`                     | sì                          | no                        | no                           |

```java
class Persona {
    public String nome;
    protected int eta;
    String citta; // package-private
    private String codiceFiscale;
}
```

## 3. La classe `java.lang.Object`

* Tutte le classi in Java **ereditano implicitamente da `Object`**.
* Metodi principali: `toString()` e `equals()`

### 3.1 `toString()`

```java
class Persona {
    String nome;
    Persona(String nome) { this.nome = nome; }
}

Persona p = new Persona("Luca");
System.out.println(p.toString()); // Persona@1a2b3c4
```

### 3.2 `equals()`

```java
class Persona {
    String nome;
    Persona(String nome) { this.nome = nome; }
    
    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (!(obj instanceof Persona)) return false;
        Persona other = (Persona) obj;
        return this.nome.equals(other.nome);
    }
}
```

## 4. Cast fra tipi riferimento vs conversione tipi primitivi

```java
Object o = "ciao";       // Upcast automatico
String s = (String)o;    // Downcast manuale

int x = 10;
double y = x;            // Widening automatico
int z = (int)y;           // Narrowing manuale
```

### 4.1 Operatore `instanceof`

```java
if (o instanceof String) {
    System.out.println("o è una stringa");
}
```

## 5. Ridefinizione del metodo `equals()` e `compareTo()`

```java
class Data {
    int giorno, mese, anno;

    Data(int g, int m, int a) {
        giorno = g; mese = m; anno = a;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (!(obj instanceof Data)) return false;
        Data other = (Data) obj;
        return giorno == other.giorno && mese == other.mese && anno == other.anno;
    }

    @Override
    public String toString() {
        return giorno + "/" + mese + "/" + anno;
    }
}
```

```java
class DataOra extends Data {
    int ore, minuti;

    DataOra(int g, int m, int a, int h, int min) {
        super(g,m,a);
        ore = h; minuti = min;
    }

    @Override
    public boolean equals(Object obj) {
        if (!super.equals(obj)) return false;
        if (!(obj instanceof DataOra)) return false;
        DataOra other = (DataOra)obj;
        return ore == other.ore && minuti == other.minuti;
    }

    @Override
    public String toString() {
        return super.toString() + " " + ore + ":" + minuti;
    }
}
```

## 6. Aggiunta di campi nelle sottoclassi e `super.metodo()`

```java
class Animale {
    void verso() { System.out.println("Suono generico"); }
}

class Cane extends Animale {
    void verso() {
        super.verso();  // richiamo della versione della superclasse
        System.out.println("Bau Bau");
    }
}
```

```java
DataOra d = new DataOra(14, 3, 2026, 15, 30);
System.out.println(d.toString());  // 14/3/2026 15:30
```

## 7. Riepilogo

* `final` impedisce estensione o override.
* `public`, `protected`, `package`, `private` controllano l’accessibilità.
* `Object` è la superclasse di tutte le classi.
* `toString()` e `equals()` vanno spesso ridefiniti.
* Cast tra riferimenti differisce dalla conversione di tipi primitivi.
* `instanceof` verifica il tipo.
* Le sottoclassi possono aggiungere campi e usare `super` per richiamare la logica della superclasse.
