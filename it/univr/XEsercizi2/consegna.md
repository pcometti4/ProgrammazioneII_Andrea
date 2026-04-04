# Esercizi

## Esercizio 1 – Lettura e scrittura base
Scrivi un programma Java che:

Legge un file input.txt usando BufferedReader
Conta quante righe contiene
Scrive il risultato in output.txt usando PrintWriter

👉 Vincoli:

Usa try-with-resources
Usa readLine()

💡 Output esempio:
  ```txt
  Numero righe: 5
  ```
## Esercizio 2 – Copia file con buffer
Crea un programma che:

Legge un file di testo (origine.txt)
Lo copia in copia.txt
Trasforma tutto il testo in MAIUSCOLO

👉 Devi usare:

BufferedReader
BufferedWriter

💡 Suggerimento:
  ```java
line.toUpperCase();
  ```

## Esercizio 3 – Classe astratta + file
Crea:

1. Classe astratta
  ```java
abstract class Date {
    public abstract String toString();
    public abstract Date create(int g, int m);
}
  ```
2. Sottoclasse SimpleDate
3. Programma che:
   Legge da file date (es: 12 5)
   Usa un costruttore con Scanner
   Salva tutte le date in un file usando PrintWriter

👉 Obiettivo:
Integrare:

Factory method
Scanner da file
Scrittura su file

# PROGETTI

## Progetto 1 – Gestore Date da File
Obiettivo

Creare un sistema che legge, gestisce e salva date.

Funzionalità:
Legge un file date.txt (formato: giorno mese)
Usa:
classe astratta Date
sottoclasse SimpleDate
Per ogni data:
stampa toString()
determina la stagione (getSeason())
Salva tutto in output.txt

👉 Tecnologie da usare:

Scanner
PrintWriter
Factory method
try-with-resources

💡 Esempio output:
  ```txt
  12/5 -> Primavera
25/12 -> Inverno
  ```

## Progetto 2 – Mini File Manager (Testo + Binario)

Obiettivo

Simulare un piccolo gestore di file.

Funzionalità:

1. File di testo
   - Scrivere testo in un file (BufferedWriter)
   - Leggere e stampare (BufferedReader)
2. File binario 
   - Scrivere byte in un file (FileOutputStream)
   - Leggere byte (FileInputStream)
3. Statistiche 
   - Conta:
     - numeroaratteri 
     - numero righe 
     - numero byte c
4. Gestione risorse 
   - Usa:
     - try-with-resources
     - oppure finally
5. Aggiungi:
   - gestione errori (IOException)
   - menu interattivo con Scanner
   - uso di AutoCloseable