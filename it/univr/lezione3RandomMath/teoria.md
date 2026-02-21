# 🎲 La classe `java.util.Random`

Classe: **java.util.Random**

Serve per generare **numeri casuali** (pseudo-casuali).

Per usarla bisogna importarla:

```java
import java.util.Random;
```

## Creazione di un oggetto Random

```java
Random r = new Random();
```

Ogni volta che chiami un metodo di `r`, ottieni un valore casuale.

---

## 📌 Metodi principali di Random

### 🔹 `boolean nextBoolean()`

Restituisce `true` o `false` casualmente.

```java
boolean valore = r.nextBoolean();
```

---

### 🔹 `double nextDouble()`

Numero casuale tra:

```
0.0 (incluso) e 1.0 (escluso)
```

```java
double x = r.nextDouble();
```

---

### 🔹 `float nextFloat()`

Numero casuale tra:

```
0.0f e 1.0f
```

```java
float f = r.nextFloat();
```

---

### 🔹 `int nextInt()`

Restituisce un intero casuale (anche negativo).

```java
int n = r.nextInt();
```

---

### 🔹 `int nextInt(int max)`

Restituisce un numero tra:

```
0 (incluso) e max (escluso)
```

```java
int n = r.nextInt(10);
```

Produce numeri da 0 a 9.

---

### 🎯 Numero tra min e max

Formula molto usata:

```java
int n = r.nextInt(max - min + 1) + min;
```

Esempio 5–10:

```java
int n = r.nextInt(6) + 5;
```

---

### 🔹 `long nextLong()`

Restituisce un long casuale.

```java
long l = r.nextLong();
```

---

# 📐 La classe `java.lang.Math`

Classe: **java.lang.Math**

Non serve importarla perché è in `java.lang`.

Tutti i metodi sono **statici**.
Si usano così:

```java
Math.nomeMetodo()
```

---

# 📌 Costanti matematiche

### 🔹 `Math.PI`

```java
double p = Math.PI;
```

≈ 3.141592653589793

---

### 🔹 `Math.E`

```java
double e = Math.E;
```

≈ 2.718281828459045

---

# 📌 Valore assoluto

### 🔹 `abs()`

```java
int x = Math.abs(-10);  // 10
```

Esiste per:

* int
* long
* float
* double

---

# 📌 Funzioni trigonometriche

⚠️ Usano **radianti**, non gradi!

### 🔹 `sin()`

```java
double s = Math.sin(Math.PI / 2);
```

---

### 🔹 `cos()`

```java
double c = Math.cos(0);
```

---

### 🔹 `tan()`

```java
double t = Math.tan(Math.PI / 4);
```

---

# 📌 Conversione gradi ↔ radianti

### 🔹 `toDegrees()`

```java
double gradi = Math.toDegrees(Math.PI);
```

---

### 🔹 `toRadians()`

```java
double radianti = Math.toRadians(180);
```

---

# 📌 Logaritmi

### 🔹 `log()` → base e

```java
double l = Math.log(Math.E);  // 1
```

---

### 🔹 `log10()` → base 10

```java
double l = Math.log10(100);  // 2
```

---

# 📌 Radice quadrata

### 🔹 `sqrt()`

```java
double r = Math.sqrt(25);  // 5
```

---

# 📌 Massimo e minimo

### 🔹 `max()`

```java
int m = Math.max(5, 10);  // 10
```

---

### 🔹 `min()`

```java
int m = Math.min(5, 10);  // 5
```

Esistono versioni per altri tipi numerici.

---

# 🎯 Esempio completo

```java
import java.util.Random;

public class EsempioMathRandom {

    public static void main(String[] args) {

        Random r = new Random();

        int numero = r.nextInt(100) + 1;
        System.out.println("Numero casuale: " + numero);

        double radice = Math.sqrt(numero);
        System.out.println("Radice quadrata: " + radice);

        double seno = Math.sin(Math.toRadians(30));
        System.out.println("Seno di 30°: " + seno);

        System.out.println("PI greco: " + Math.PI);
    }
}
```

---

# 🧠 Differenza fondamentale

| Random                            | Math                      |
| --------------------------------- | ------------------------- |
| Genera numeri casuali             | Esegue calcoli matematici |
| Richiede oggetto (`new Random()`) | Solo metodi statici       |
| È in `java.util`                  | È in `java.lang`          |

---

# 📚 Concetti chiave da ricordare

✔ `Random` va importato
✔ `Math` no
✔ `Math` usa metodi statici
✔ Le funzioni trigonometriche usano radianti
✔ `nextInt(max)` esclude max