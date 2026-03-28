# Lezione di Informatica - Programmazione Java (Parte 2)

## 1. Classi Astratte e Metodo toString()

Possiamo rendere il metodo `toString()` astratto in una superclasse `Date`, rendendo così la classe stessa **astratta**:

```java
public abstract class Date {
    public abstract String toString();
}
```

Le sottoclassi devono implementare il metodo.

---

## 2. Factory Method

Un **factory method** è un metodo astratto che crea oggetti dello stesso tipo della classe concreta:

```java
public abstract class Date {
    public abstract Date create(int giorno, int mese);
}
```

Esempio in una sottoclasse:

```java
public class SimpleDate extends Date {
    private int giorno, mese;

    public SimpleDate(int g, int m) {
        giorno = g;
        mese = m;
    }

    @Override
    public Date create(int g, int m) {
        return new SimpleDate(g, m);
    }
}
```

---

## 3. Utilizzo in getSeason()

```java
public String getSeason() {
    Date primavera = create(21, 3);
    Date estate = create(21, 6);

    // logica di confronto (semplificata)
    return "Primavera";
}
```

Il factory method permette di creare oggetti coerenti con il tipo dinamico.

---

## 4. Interfacce AutoCloseable e Closeable

### AutoCloseable
```java
public interface AutoCloseable {
    void close() throws Exception;
}
```

### Closeable
```java
public interface Closeable extends AutoCloseable {
    void close() throws IOException;
}
```

---

## 5. Clausola finally

Il blocco `finally` viene eseguito sempre:

```java
try {
    // codice
} catch (Exception e) {
    // gestione errore
} finally {
    System.out.println("Sempre eseguito");
}
```

---

## 6. Try-with-Resources

Permette di chiudere automaticamente le risorse:

```java
try (Scanner scanner = new Scanner(new File("file.txt"))) {
    while (scanner.hasNextLine()) {
        System.out.println(scanner.nextLine());
    }
}
```

Funziona con oggetti che implementano `AutoCloseable`.

---

## 7. Classe Scanner

La classe `Scanner` semplifica la lettura di input:

```java
Scanner scanner = new Scanner(System.in);
int numero = scanner.nextInt();
```

Per file:

```java
Scanner scanner = new Scanner(new File("file.txt"));
```

Metodi utili:
- hasNextLine()
- nextLine()
- nextInt()

---

## 8. Metodi principali

### AutoCloseable
- `void close() throws Exception`

### Closeable
- `void close() throws IOException`

---

## Conclusione

Questi strumenti permettono di:
- migliorare il design orientato agli oggetti (classi astratte, factory method)
- gestire correttamente le risorse
- scrivere codice più sicuro e leggibile
