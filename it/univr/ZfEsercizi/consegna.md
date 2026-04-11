Ecco due esercizi graduati e un progetto finale completo!

---

## Esercizio 1 — Gerarchia di forme geometriche

Pratica: classi astratte, ereditarietà, polimorfismo.

Crea una classe astratta `Forma` con:
- attributo `colore` (String)
- metodi astratti `area()` e `perimetro()`
- metodo concreto `descrivi()` che stampa colore, area e perimetro

Poi implementa `Cerchio`, `Rettangolo` e `Triangolo` (con i tre lati). Nel `main`, crea una `List<Forma>`, aggiungici oggetti misti, e itera stampando la descrizione di ognuno — senza mai fare cast.

**Sfida bonus:** aggiungi un'interfaccia `Ridimensionabile` con `scala(double fattore)` e implementala solo su `Cerchio` e `Rettangolo`.

---

## Esercizio 2 — Rubrica telefonica

Pratica: `Map`, `Set`, strutture dati, ricerca.

Implementa una rubrica usando `Map<String, Set<String>>` dove la chiave è il nome e il valore è l'insieme dei numeri associati (una persona può averne più di uno).

Metodi da implementare:
- `aggiungiContatto(String nome, String numero)`
- `rimuoviContatto(String nome)`
- `cercaPerNome(String nome)` → restituisce i numeri
- `cercaPerNumero(String numero)` → restituisce il nome (ricerca inversa)
- `stampaOrdinata()` → nomi in ordine alfabetico con i relativi numeri

**Sfida bonus:** usa `Random` per generare 10 contatti fittizi automaticamente e `Math` per calcolare statistiche (media numeri per contatto, contatto con più numeri, ecc.).

---

Ora il progetto:---

## Progetto — Sistema di gestione torneo

L'idea è simulare un torneo a eliminazione diretta (tipo Champions League) tra squadre di calcio/sport generici.

**Concetti coperti:**

- `Partecipante` (classe astratta) → estesa da `Giocatore` e `Squadra`
- `Punteggiabile` e `Simulabile` (interfacce) → implementate con contratti diversi
- `Ruolo` (enum) con moltiplicatori → rende il codice più espressivo di semplici stringhe
- `Set<Giocatore>` nella squadra → impedisce duplicati automaticamente
- `Map<Squadra, Integer>` per la classifica → accesso diretto per squadra
- `List<Partita>` per lo storico → ordinabile, iterabile
- `Random` e `Math` per pesare i gol in base al rendimento medio dei giocatori

**La logica di simulazione** è il cuore del progetto: ogni partita usa il rendimento medio delle rose (calcolato automaticamente) per influenzare l'estrazione casuale dei gol, quindi non è una slot machine pura — le squadre "forti" vincono più spesso, ma non sempre.

Clicca il pulsante nel widget per generare il codice Java completo, oppure dimmi se vuoi che ti scriva subito una classe specifica!