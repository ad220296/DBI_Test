# 📦 Funktionen, Prozeduren und Packages in PL/SQL

In PL/SQL kannst du wiederverwendbare **Programmbausteine** definieren, um Struktur, Klarheit und Modularität zu verbessern. Die drei wichtigsten sind:

---

## 🔹 1. Prozedur (Procedure)

Eine **Prozedur** führt eine **Aktion** aus und gibt **nichts zurück**.

### 🧪 Beispiel:

```sql
CREATE OR REPLACE PROCEDURE greet_user(p_name IN VARCHAR2) IS
BEGIN
  DBMS_OUTPUT.PUT_LINE('Hallo, ' || p_name || '!');
END;
/
```

### 🔄 Aufruf:

```sql
BEGIN
  greet_user('Christoph');
END;
/
```

---

## 🔸 2. Funktion (Function)

Eine **Funktion** berechnet einen **Wert** und gibt ihn zurück – wie in Mathe.

### 🧪 Beispiel:

```sql
CREATE OR REPLACE FUNCTION get_bonus(p_salary NUMBER)
  RETURN NUMBER IS
BEGIN
  RETURN p_salary * 0.1;
END;
/
```

### 🔄 Aufruf:

```sql
DECLARE
  v_bonus NUMBER;
BEGIN
  v_bonus := get_bonus(3000);
  DBMS_OUTPUT.PUT_LINE('Bonus: ' || v_bonus);
END;
/
```

---

## 📦 3. Package (Paket mit Funktionen & Prozeduren)

Ein **Package** ist ein Container, in dem du **mehrere Prozeduren, Funktionen und Variablen** zusammenfassen kannst.

### 🧩 a) Header (Schnittstelle):

```sql
CREATE OR REPLACE PACKAGE my_tools IS
  PROCEDURE say_hello(p_name VARCHAR2);
  FUNCTION double_it(p_val NUMBER) RETURN NUMBER;
END;
/
```

### 🔧 b) Body (Implementierung):

```sql
CREATE OR REPLACE PACKAGE BODY my_tools IS

  PROCEDURE say_hello(p_name VARCHAR2) IS
  BEGIN
    DBMS_OUTPUT.PUT_LINE('Hi, ' || p_name || '!');
  END;

  FUNCTION double_it(p_val NUMBER) RETURN NUMBER IS
  BEGIN
    RETURN p_val * 2;
  END;

END;
/
```

### 🔄 Aufruf:

```sql
BEGIN
  my_tools.say_hello('Nici');
  DBMS_OUTPUT.PUT_LINE('Doppelt: ' || my_tools.double_it(5));
END;
/
```

---

## 📘 Vergleichstabelle

| Element     | Rückgabewert | Parameter | Aufrufbar aus SQL | Teil von Package möglich |
|-------------|---------------|-----------|--------------------|---------------------------|
| Funktion    | ✅ Ja         | ✅ Ja     | ✅ (wenn ohne OUT) | ✅ Ja                     |
| Prozedur    | ❌ Nein       | ✅ Ja     | ❌ (nicht direkt)  | ✅ Ja                     |
| Package     | ✅/❌ (enthält beides) | ✅ | ✅                 | —                         |

---

✅ Diese drei Bausteine machen dein PL/SQL-Projekt **modular, wiederverwendbar und testbar**.

