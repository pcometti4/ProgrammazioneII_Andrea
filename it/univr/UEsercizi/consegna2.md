🧩 Esercizio: Sistema di Punteggi di Giochi
1. Interfaccia

Si definisca una interfaccia che rappresenta un punteggio:

public interface Score extends Comparable<Score> {
int getPoints(); // restituisce il punteggio normalizzato
}
2. Classe astratta

Si completi la seguente classe astratta:

public abstract class AbstractScore implements Score {
private final int points;

    protected AbstractScore(int points) {
        // se points < 0 → IllegalArgumentException
        // altrimenti inizializza
        ...
    }

    public final int getPoints() {
        ...
    }

    // nome del gioco (es: "Calcio", "Basket", ...)
    protected abstract String getGameName();

    // fattore di normalizzazione (serve per confrontare giochi diversi)
    protected abstract double getWeight();

    // punteggio normalizzato
    public double getNormalizedScore() {
        ...
    }

    public String toString() {
        // es: "Calcio: 3 punti"
        ...
    }

    public final boolean equals(Object other) {
        // due score sono uguali se hanno lo stesso punteggio normalizzato
        ...
    }

    public final int compareTo(Score other) {
        // confronto su punteggio normalizzato
        ...
    }
}
3. Sottoclassi concrete

Si implementino:

SoccerScore
→ vittoria = 3 punti
BasketScore
→ punti diretti (es: 85 punti)
TennisScore
→ punteggio convertito (es: set vinti → moltiplicati per 10)

Ogni classe:

definisce nome gioco
definisce peso (getWeight())

⚠️ NON ridefinire toString()

4. Comportamento speciale (override)

Si implementi:

public class BonusScore extends SoccerScore
ridefinisce solo toString()
aggiunge un bonus testuale:

Esempio:

Calcio: 3 punti (bonus fair play)
5. Nuova tipologia

Si implementi:

public class ArcadeScore extends AbstractScore
rappresenta giochi arcade
il punteggio viene ridotto dividendo per 100
NON ridefinire toString()
6. Classe di test

Scrivere:

public class MainScores

Che:

legge un intero ≥ 0
crea:
soccer
basket
tennis
bonus
arcade
stampa tutto
7. Ordinamento

Scrivere:

public class MainScoresSort

Array con:

SoccerScore(3)
BasketScore(80)
TennisScore(2)
ArcadeScore(5000)

Ordinare e stampare.