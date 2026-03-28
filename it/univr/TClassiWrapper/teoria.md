# Lezione di Informatica - Programmazione Java

## 1. Classi Wrapper della Libreria Standard

Le **classi wrapper** permettono di trattare i tipi primitivi come oggetti.  
Ogni tipo primitivo ha una classe corrispondente:

- int → Integer  
- double → Double  
- char → Character  
- boolean → Boolean  
- ecc.

Queste classi sono **immutabili**, cioè i loro oggetti non possono essere modificati dopo la creazione.

---

## 2. Boxing e Unboxing Automatico

- **Boxing**: conversione automatica da tipo primitivo a wrapper  
  ```java
  Integer x = 10; // boxing automatico
  ```

- **Unboxing**: conversione da wrapper a tipo primitivo  
  ```java
  int y = x; // unboxing automatico
  ```

---

## 3. Eccezioni

Le **eccezioni** rappresentano errori che si verificano durante l'esecuzione del programma.

### Lancio delle eccezioni
- **Implicito** (dal linguaggio)
- **Esplicito** con `throw`

```java
throw new IllegalArgumentException("Errore!");
```

---

## 4. Esempio: Test di Legalità di una Data

```java
public class Data {
    public static void verificaData(int giorno, int mese) {
        if (mese < 1 || mese > 12) {
            throw new IllegalArgumentException("Mese non valido");
        }
        if (giorno < 1 || giorno > 31) {
            throw new IllegalArgumentException("Giorno non valido");
        }
    }
}
```

---

## 5. Gestione delle Eccezioni

```java
try {
    int x = Integer.parseInt("abc");
} catch (NumberFormatException e) {
    System.out.println("Errore di conversione");
} finally {
    System.out.println("Blocco sempre eseguito");
}
```

---

## 6. Gerarchia delle Eccezioni

- Throwable
  - Error
  - Exception
    - RuntimeException

---

## 7. Eccezioni Controllate e Non Controllate

- **Controllate**: devono essere gestite (IOException)
- **Non controllate**: RuntimeException

---

## 8. Clausola throws

```java
public void metodo() throws IOException {
    // codice
}
```

---

## 9. Eccezioni Personalizzate

```java
public class MiaEccezione extends Exception {
    public MiaEccezione(String msg) {
        super(msg);
    }
}
```

---

## 10. Classe Integer

Metodi principali:

- MAX_VALUE
- MIN_VALUE
- intValue()
- compareTo(Integer other)
- parseInt(String s)
- toBinaryString(int i)
- toHexString(int i)
- valueOf(int i)

Esempio:

```java
int x = Integer.parseInt("123");
System.out.println(Integer.toBinaryString(x));
```

---

## 11. Altre Classi Wrapper

- Short
- Long
- Float
- Double
- Byte
- Boolean

---

## 12. Classe Character

Metodi principali:

- isDigit(char c)
- isLetter(char c)
- isLetterOrDigit(char c)
- isLowerCase(char c)
- isUpperCase(char c)
- isWhitespace(char c)
- toLowerCase(char c)
- toUpperCase(char c)
- valueOf(char c)

Esempio:

```java
char c = 'A';
System.out.println(Character.isLetter(c));
System.out.println(Character.toLowerCase(c));
```

---

## Conclusione

Le classi wrapper e la gestione delle eccezioni sono fondamentali per scrivere codice Java robusto, sicuro e orientato agli oggetti.
