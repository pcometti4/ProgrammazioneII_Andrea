# 🧩 Esercizio: Misure Fisiche
## Contesto
Si vuole modellare un sistema di misure fisiche (lunghezze, pesi, temperature), ognuna espressa in un'unità di misura specifica, con la possibilità di confrontarle, ordinarle e stamparle in modo appropriato.
1. i crei un'interfaccia Measure che rappresenta una misura fisica generica:
  ```java
public interface Measure extends Comparable<Measure> {
    double getRawValue();   // restituisce il valore grezzo nella sua unità
    double toBaseUnit();    // converte il valore nell'unità base della categoria
}
  ```
2. Si completi la seguente classe astratta AbstractMeasure:
  ```java
public abstract class AbstractMeasure implements Measure {
    private final double rawValue;

    protected AbstractMeasure(double rawValue) {
        // se rawValue è strettamente negativo lancia IllegalArgumentException
        // (le misure fisiche assolute non possono essere negative in questo sistema)
        ...
    }

    public final double getRawValue() { ... }

    // restituisce il simbolo dell'unità di misura (es. "km", "kg", "°C")
    protected abstract String getUnitSymbol();

    // restituisce una stringa nel formato "valore simbolo", es. "3.50 km"
    public String toString() { ... }

    public final boolean equals(Object other) {
        // due misure sono uguali se e solo se hanno lo stesso valore in unità base
        ...
    }

    public final int compareTo(Measure other) {
        // ordinamento crescente per valore in unità base
        ...
    }
}
```

> **Nota:** l'unità base per le lunghezze è il **metro**, per i pesi il **grammo**, per le temperature il **kelvin**.

---

**3.** Si scrivano le seguenti sottoclassi concrete di `AbstractMeasure`:

| Classe | Unità | Simbolo | Conversione in unità base |
|---|---|---|---|
| `Meters` | metro | `m` | × 1 |
| `Kilometers` | chilometro | `km` | × 1000 |
| `Centimeters` | centimetro | `cm` | × 0.01 |
| `Grams` | grammo | `g` | × 1 |
| `Kilograms` | chilogrammo | `kg` | × 1000 |
| `Celsius` | grado Celsius | `°C` | + 273.15 |
| `Kelvin` | kelvin | `K` | × 1 |

Non si ridefinisca `toString()` in queste sottoclassi: quello di `AbstractMeasure` deve funzionare per tutte.

---

**4.** Si implementi una sottoclasse concreta `ScientificNotationMeasure` di `Meters`, che ridefinisce **solo** `toString()` per stampare il valore in notazione scientifica (es. `3500.0 m` → `3.50E3 m`). Si usi `String.format("%.2E %s", ...)`.

---

**5.** Si implementi una sottoclasse concreta `FeetAndInches` di `AbstractMeasure`, che rappresenta una lunghezza espressa in piedi e pollici. Il costruttore accetta **piedi** e **pollici** separatamente. L'unità base rimane il metro (1 piede = 0.3048 m, 1 pollice = 0.0254 m). Si ridefinisca `toString()` per stampare nel formato `"2ft 5in"`. Si presti attenzione a come gestire `getRawValue()` (si può scegliere di restituire i piedi interi, documentando la scelta).

---

**6.** Si scriva una classe `MainMeasures` con un metodo `main()` che:
- chiede all'utente di inserire una lunghezza in metri
- crea la misura in metri, in chilometri, in centimetri e in notazione scientifica, e le stampa tutte
- chiede poi di inserire una massa in grammi e stampa il valore in grammi e in chilogrammi
- chiede infine una temperatura in Celsius e la stampa sia in Celsius che in Kelvin

Esempio con lunghezza `3500`, massa `75000`, temperatura `100`:
```
3500.00 m
3.50 km
350000.00 cm
3.50E3 m
75000.00 g
75.00 kg
100.00 °C
373.15 K
  ```

7. Si scriva una classe MainMeasuresSort con un metodo main() che crea un array di Measure con:
  ```
1.5 km
800 cm
3 m
0 ft 70 in
0.002 km in notazione scientifica
  ```
Lo ordina con Arrays.sort(...) e lo stampa con Arrays.toString(...). L'ordinamento dovrà avvenire per valore convertito in unità base (cioè in metri), così misure eterogenee risultano confrontabili.
