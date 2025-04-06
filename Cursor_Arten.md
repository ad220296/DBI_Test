# 🔁 Cursor in PL/SQL – Vergleich: Normaler Cursor vs. REF CURSOR

## 🧠 Was ist ein Cursor?

Ein **Cursor** ist ein Zeiger auf eine Ergebnisliste aus einem `SELECT`.  
Mit einem Cursor kann man **Datensätze zeilenweise** auslesen.

---

## 📘 Cursor-Arten im Vergleich

| Merkmal               | **Statischer Cursor**                   | **REF CURSOR**                        |
|-----------------------|-----------------------------------------|---------------------------------------|
| Definition            | Fix in PL/SQL-Block                     | Dynamisch mit `OPEN FOR`              |
| SQL-Anweisung         | Fix zur Compile-Zeit                    | Wird **zur Laufzeit** bestimmt        |
| Flexibilität          | Nur 1 SELECT                            | Beliebige Abfragen zur Laufzeit       |
| Anwendung             | Wenn SELECT bekannt ist                | Wenn SELECT **variabel** sein soll    |
| Rückgabe über Prozedur| ❌ (nur lokal nutzbar)                   | ✅ möglich                             |
| Typisierung           | Stark typisiert                        | Schwach oder stark typisierbar        |

---

## 🔍 Beispiel im Vergleich

### 🔹 1. Normaler Cursor (statisch)

```sql
DECLARE
  CURSOR c_emp IS
    SELECT ename FROM emp WHERE deptno = 10;
    
  v_ename emp.ename%TYPE;
BEGIN
  OPEN c_emp;
  LOOP
    FETCH c_emp INTO v_ename;
    EXIT WHEN c_emp%NOTFOUND;
    DBMS_OUTPUT.PUT_LINE('Name: ' || v_ename);
  END LOOP;
  CLOSE c_emp;
END;
/
```

✅ **Fix definierter Cursor**, ideal für einfache bekannte Abfragen.

---

### 🔹 2. REF CURSOR (dynamisch)

```sql
DECLARE
  TYPE ref_cursor_type IS REF CURSOR;
  my_cursor ref_cursor_type;
  v_ename emp.ename%TYPE;
BEGIN
  OPEN my_cursor FOR
    'SELECT ename FROM emp WHERE deptno = 10';
    
  LOOP
    FETCH my_cursor INTO v_ename;
    EXIT WHEN my_cursor%NOTFOUND;
    DBMS_OUTPUT.PUT_LINE('Name: ' || v_ename);
  END LOOP;
  CLOSE my_cursor;
END;
/
```

✅ Perfekt für dynamische SQL-Abfragen, z. B. mit WHERE-Bedingungen aus Variablen.

---

## 🧩 Wann nehme ich was?

| Wenn …                                 | Dann nimm:          |
|----------------------------------------|---------------------|
| die Abfrage **immer gleich bleibt**    | ➤ Statischen Cursor |
| du den **SQL-Text dynamisch erzeugst** | ➤ REF CURSOR        |
| du das Ergebnis weitergeben willst     | ➤ REF CURSOR        |

---

## ✨ Bonus: REF CURSOR mit SQL-Variable

```sql
DECLARE
  TYPE ref_cursor_type IS REF CURSOR;
  my_cursor ref_cursor_type;
  v_sql VARCHAR2(100) := 'SELECT ename FROM emp WHERE deptno = 20';
  v_ename emp.ename%TYPE;
BEGIN
  OPEN my_cursor FOR v_sql;
  LOOP
    FETCH my_cursor INTO v_ename;
    EXIT WHEN my_cursor%NOTFOUND;
    DBMS_OUTPUT.PUT_LINE('Name: ' || v_ename);
  END LOOP;
  CLOSE my_cursor;
END;
/
```

✅ So wird der SQL-Text **variabel** – ideal für Reports, Suchabfragen und Benutzerfilter.

