Ecco la tua consegna formattata in **Markdown** pronta da salvare in un file `.md`. Ho usato titoli, elenchi puntati, blocchi di codice e commenti per mantenere chiara la struttura.

```markdown
# Implementazione di una Carta del Gioco Poker

Si vuole implementare una carta del gioco del poker, il cui **valore** è uno fra questi:

```

2 3 4 5 6 7 8 9 10 J Q K A

````

Tale valore può essere visto come un numero fra **0 e 12**.  

Una carta ha anche un **seme (in inglese: suit)** che può essere:

- `spades (♠)`
- `clubs (♣)`
- `diamonds (♦)`
- `hearts (♥)`

---

## Classe Card da completare

```java
public class Card {

    /**
     * Il valore della carta.
     */
    private final int value;

    /**
     * Il seme della carta.
     */
    private final int suit;

    /**
     * Genera una carta a caso con un valore da min (incluso) in su.
     *
     * @param min il valore minimo (0-12) della carta che può essere generata
     */
    public Card(int min) { ... }

    /**
     * Genera una carta a caso con un valore da 0 (incluso) in su.
     */
    public Card() { ... }

    /**
     * Restituisce il valore della carta (0-12)
     */
    public int getValue() { ... }

    /**
     * Restituisce il seme della carta (0-3)
     */
    public int getSuit() { ... }

    /**
     * Ritorna una descrizione della carta sotto forma di stringa,
     * del tipo "10♠" oppure "J♥".
     */
    public String toString() { ... }

    /**
     * Determina se questa carta è uguale ad other.
     *
     * @param other l'altra carta con cui confrontarsi
     * @return true se e solo se le due carte sono uguali
     */
    public boolean equals(Card other) { ... }
}
````

---

## Classe Main

Si scriva una classe `Main` con metodo `main` che:

1. Crea una carta `card1` a caso.
2. Crea ripetutamente carte `card2` a caso finché `card1.equals(card2)` diventa `true`.
3. Stampa `card1` e tutte le `card2` generate sul video.

```java
public class Main {
    public static void main(String[] args) {
        // creare card1
        // ciclo per generare card2 finché non è uguale a card1
        // stampare le carte
    }
}
```

---

## Enumerazioni

Si definiscano due enumerazioni:

* `Value` → rappresenta le 13 alternative per il **valore delle carte**
* `Suit` → rappresenta le 4 alternative per il **seme delle carte**

Si modifichi la classe `Card` in modo da usare queste enumerazioni al posto degli interi come **valore** e **seme**.

---

## Metodo compareTo

Si aggiunga alla classe `Card` il metodo:

```java
public int compareTo(Card other)
```

* Confronta due carte
* Ordina **per valore**
* A parità di valore, ordina **per seme** secondo l’ordine:

```
♠ (spades), ♣ (clubs), ♦ (diamonds), ♥ (hearts)
```

---

## JavaDoc

* Si generino le pagine **JavaDoc** da Eclipse
* Tutti i commenti JavaDoc devono essere inclusi nel codice sorgente
* La documentazione deve mostrare:

  * classe `Card`
  * metodi `getValue()`, `getSuit()`, `toString()`, `equals()`, `compareTo()`
  * enumerazioni `Value` e `Suit`