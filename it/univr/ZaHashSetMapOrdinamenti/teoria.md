# HashSet, Map e Ordinamenti in Java

## 1. Classe `HashSet<E>`

`HashSet` è un insieme che:

* non permette duplicati
* non mantiene ordine
* usa hash per memorizzare gli elementi

Costruttori:

```java
new HashSet<>()
new HashSet<>(collection)
```

---

## 2. Metodo `equals()`

Il metodo `equals()` deve essere una **relazione di equivalenza**:

* Riflessiva → x.equals(x)
* Simmetrica → x.equals(y) == y.equals(x)
* Transitiva → se x=y e y=z allora x=z

---

## 3. Metodo `hashCode()`

Serve per determinare dove memorizzare un oggetto nelle strutture hash.

### Regola fondamentale:

Se due oggetti sono uguali (`equals()`), devono avere lo stesso `hashCode()`.

### Esempio:

```java
@Override
public int hashCode() {
    return Objects.hash(campo1, campo2);
}
```

⚠️ Evitare implementazioni banali (es: sempre 1).

---

## 4. Interfaccia `SortedSet<E>`

Insieme ordinato automaticamente.

Metodi principali:

* `E first()` → elemento più piccolo
* `E last()` → elemento più grande

---

## 5. Classe `TreeSet<E>`

Implementa `SortedSet`.

Caratteristiche:

* mantiene ordine naturale o personalizzato
* non permette duplicati

Costruttori:

```java
new TreeSet<>()
new TreeSet<>(collection)
```

---

## 6. `compareTo()` ed `equals()`

Se `compareTo()` restituisce 0, allora gli oggetti dovrebbero essere considerati uguali.

⚠️ Devono essere **consistenti**:

* compareTo(x, y) == 0 ⇒ x.equals(y)

---

## 7. Iteratori e ConcurrentModificationException

Quando si modifica una collezione durante l'iterazione:

```java
for (E e : collezione) {
    collezione.remove(e); // ERRORE
}
```

Si ottiene:
➡️ `ConcurrentModificationException`

### Soluzione:

Usare un iteratore esplicito:

```java
Iterator<E> it = collezione.iterator();
while (it.hasNext()) {
    E e = it.next();
    if (condizione) {
        it.remove();
    }
}
```

---

## 8. Esempio con `Date`

```java
class Date implements Comparable<Date> {
    int giorno, mese, anno;

    @Override
    public int compareTo(Date other) {
        if (anno != other.anno) return anno - other.anno;
        if (mese != other.mese) return mese - other.mese;
        return giorno - other.giorno;
    }

    @Override
    public boolean equals(Object o) {
        if (!(o instanceof Date)) return false;
        Date d = (Date) o;
        return giorno == d.giorno && mese == d.mese && anno == d.anno;
    }

    @Override
    public int hashCode() {
        return Objects.hash(giorno, mese, anno);
    }
}
```

### Rimozione date autunnali:

```java
Iterator<Date> it = set.iterator();
while (it.hasNext()) {
    Date d = it.next();
    if (d.mese >= 9 && d.mese <= 11) {
        it.remove();
    }
}
```

---

## 9. Interfaccia `Map<K,V>`

Struttura chiave-valore.

Metodi principali:

* `containsKey(key)`
* `containsValue(value)`
* `get(key)`
* `getOrDefault(key, default)`
* `put(key, value)`
* `putIfAbsent(key, value)`
* `remove(key)`
* `keySet()`
* `values()`
* `size()`

---

## 10. Classe `HashMap<K,V>`

Mappa basata su hash.

Costruttori:

```java
new HashMap<>()
new HashMap<>(map)
```

---

## 11. Esempio: dizionario

```java
Map<String, String> dizionario = new HashMap<>();

dizionario.put("cane", "dog");
dizionario.put("gatto", "cat");

System.out.println(dizionario.get("cane"));
```

---

## 12. Interfaccia `SortedMap<K,V>`

Versione ordinata di `Map`.

Metodi principali:

* `firstKey()`
* `lastKey()`

---

## 13. Classe `TreeMap<K,V>`

* mantiene le chiavi ordinate
* usa un albero (Red-Black Tree)

Costruttori:

```java
new TreeMap<>()
new TreeMap<>(map)
```

---

## 14. Ordinamento personalizzato

È possibile specificare un comparatore:

```java
TreeSet<Integer> set = new TreeSet<>(Comparator.reverseOrder());
```

Oppure:

```java
TreeMap<String, Integer> map = new TreeMap<>(Comparator.naturalOrder());
```

---

## 15. Riassunto

* `HashSet` → insieme non ordinato
* `TreeSet` → insieme ordinato
* `equals()` e `hashCode()` devono essere consistenti
* `Map` → coppie chiave-valore
* `HashMap` → veloce, non ordinata
* `TreeMap` → ordinata
* attenzione a modifiche durante iterazione
