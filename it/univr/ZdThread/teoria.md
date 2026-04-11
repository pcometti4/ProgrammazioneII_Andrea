# Concorrenza, Thread e Immutabilità

---a

## 1. Introduzione

La concorrenza in Java consente l'esecuzione parallela di più flussi di controllo (thread), migliorando prestazioni e reattività delle applicazioni.

---

## 2. Iterable: Sequenze Lessicografiche

Un esempio avanzato di `Iterable` è la generazione di sequenze in ordine lessicografico.

### Esempio

```java
import java.util.*;

public class Lessico implements Iterable<String> {

    private List<String> parole;

    public Lessico(List<String> parole) {
        this.parole = new ArrayList<>(parole);
        Collections.sort(this.parole);
    }

    @Override
    public Iterator<String> iterator() {
        return parole.iterator();
    }
}
```

---

## 3. Concorrenza e Thread

In Java, un **thread** è un flusso di esecuzione indipendente.

### Classe Thread

Permette di creare ed eseguire thread.

---

## 4. Costruzione dei Thread

### Costruttori principali

```java
Thread()
Thread(Runnable runnable)
```

### Esempio con Runnable

```java
Runnable task = () -> {
    System.out.println("Esecuzione parallela");
};

Thread t = new Thread(task);
t.start();
```

---

## 5. Metodi fondamentali di Thread

```java
void start()
void run()
void join() throws InterruptedException
static void sleep(long ms) throws InterruptedException
static Thread currentThread()
```

### Descrizione

* `start()` → avvia il thread
* `run()` → codice eseguito dal thread
* `join()` → attende la terminazione
* `sleep()` → sospende il thread
* `currentThread()` → thread corrente

---

## 6. Race Condition

Una **race condition** si verifica quando più thread accedono e modificano dati condivisi senza sincronizzazione.

### Esempio

```java
class Contatore {
    int valore = 0;

    void incrementa() {
        valore++; // NON sicuro
    }
}
```

---

## 7. synchronized

Il costrutto `synchronized` evita accessi concorrenti non sicuri.

### Esempio

```java
synchronized void incrementa() {
    valore++;
}
```

---

## 8. Deadlock

Un **deadlock** si verifica quando due o più thread restano bloccati in attesa reciproca.

### Esempio

```java
synchronized (risorsa1) {
    synchronized (risorsa2) {
        // rischio deadlock
    }
}
```

---

## 9. Oggetti Immutabili

Un oggetto immutabile non può essere modificato dopo la creazione.

### Vantaggi

* Thread-safe
* Più semplice da gestire

### Esempio

```java
final class Punto {
    private final int x;
    private final int y;

    public Punto(int x, int y) {
        this.x = x;
        this.y = y;
    }

    public int getX() { return x; }
    public int getY() { return y; }
}
```

---

## 10. Auto-frasi: Sequenziale vs Parallelo

### Versione Sequenziale

```java
for (String s : lista) {
    processa(s);
}
```

### Versione Parallela

```java
List<Thread> threads = new ArrayList<>();

for (String s : lista) {
    Thread t = new Thread(() -> processa(s));
    threads.add(t);
    t.start();
}

for (Thread t : threads) {
    t.join();
}
```

---

## 11. Confronto

| Approccio   | Vantaggi | Svantaggi |
| ----------- | -------- | --------- |
| Sequenziale | Semplice | Lento     |
| Parallelo   | Veloce   | Complesso |

---

## 12. Best Practices

* Minimizzare lo stato condiviso
* Preferire oggetti immutabili
* Usare `synchronized` solo quando necessario
* Evitare deadlock con ordine di lock consistente

---

## 13. Esercizi suggeriti

1. Implementare un contatore thread-safe
2. Simulare una race condition
3. Scrivere un algoritmo parallelo con Thread

---

**Fine della lezione (Concorrenza)**
