# Lezione Universitaria: Java – Parametri Varargs, Tipi Generici e Comparable<T>

## Obiettivi della lezione

* Comprendere l’uso di **parametri varargs** in Java.
* Applicare tipi generici in classi e metodi.
* Utilizzare l’interfaccia di libreria `Comparable<T>`.
* Gestire vincoli sulle variabili di tipo generico.
* Implementare un metodo per restituire il **minimo di un array di oggetti comparabili**.

---

## 1. Parametri Varargs

I parametri varargs (`...`) permettono di passare un **numero variabile di argomenti** a un metodo o costruttore. Sono utili per rendere il codice più flessibile.

```java
public class FormationVarArgs {
    private SoccerPlayer[] players;

    public FormationVarArgs(SoccerPlayer... players) {
        this.players = players.clone();
    }

    public void stampa() {
        for (SoccerPlayer p : players) {
            System.out.print(p + ", ");
        }
        System.out.println();
    }
}
```

> Esempio d’uso:

```java
FormationVarArgs f = new FormationVarArgs(
    new GoalKeeper("Szczesny"),
    new Defence("Chiellini"),
    new Forward("Dybala")
);
f.stampa();
```

---

## 2. Tipi generici

I tipi generici permettono di **dichiarare classi, interfacce e metodi con variabili di tipo**, garantendo la sicurezza del tipo a compile-time.

### 2.1 Classe generica

```java
public class Box<T> {
    private T content;

    public Box(T content) {
        this.content = content;
    }

    public T getContent() {
        return content;
    }
}
```

> Esempio:

```java
Box<String> boxString = new Box<>("Hello");
Box<Integer> boxInt = new Box<>(123);
```

---

## 3. Interfaccia Comparable<T>

`Comparable<T>` è un’interfaccia della libreria Java che permette di **ordinare oggetti** di un certo tipo.

### 3.1 Metodo principale

```java
int compareTo(T other);
```

* Ritorna **< 0** se `this` viene prima di `other`
* Ritorna **> 0** se `other` viene prima di `this`
* Ritorna **0** se `this` e `other` sono equivalenti

### 3.2 Esempio di implementazione

```java
class Player implements Comparable<Player> {
    private String name;

    public Player(String name) {
        this.name = name;
    }

    @Override
    public int compareTo(Player other) {
        return this.name.compareTo(other.name);
    }

    @Override
    public String toString() {
        return name;
    }
}
```

---

## 4. Vincoli sulle variabili di tipo

È possibile imporre vincoli sui tipi generici per limitare T a classi o interfacce specifiche.

```java
public <T extends Comparable<T>> T minimo(T[] array) {
    if (array == null || array.length == 0) {
        throw new IllegalArgumentException("Array non può essere vuoto");
    }
    T min = array[0];
    for (T elem : array) {
        if (elem.compareTo(min) < 0) {
            min = elem;
        }
    }
    return min;
}
```

> Questo metodo ritorna l’elemento **minimo** di un array di oggetti comparabili.

---

## 5. Applicazione ai costruttori di Formation e Formation433

I costruttori possono usare **varargs** per accettare un numero variabile di giocatori.

```java
public class FormationVarArgs {
    private SoccerPlayer[] players;

    public FormationVarArgs(SoccerPlayer... players) {
        this.players = players.clone();
        // validazione formazione
    }
}

public class Formation433VarArgs extends FormationVarArgs {
    public Formation433VarArgs(SoccerPlayer... players) {
        super(players);
        // validazione 4-3-3
    }
}
```

> Grazie ai varargs, si può creare una formazione senza dover passare un array esplicito.

---

## 6. Riepilogo

* **Varargs:** semplificano il passaggio di un numero variabile di argomenti.
* **Tipi generici:** permettono di scrivere codice riutilizzabile e sicuro.
* **Comparable<T>:** facilita il confronto e l’ordinamento di oggetti.
* **Vincoli di tipo:** garantiscono che le variabili generiche rispettino certe interfacce o classi.
* Metodo `minimo` con `Comparable<T>` permette di trovare facilmente il più piccolo elemento di un array.

---

**Nota:** I concetti di varargs, generics e Comparable possono essere combinati per creare classi flessibili e generalizzate, come nei costruttori e metodi di Formation e Formation433.
