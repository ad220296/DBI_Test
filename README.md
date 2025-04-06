# 📚 DBI_Test

Dieses Repository bietet eine **Übersicht aller wichtigen Themen** im Fach **Datenbanken & PL/SQL**.  
Zu jedem Schwerpunkt gibt es ein eigenes Unter-Repository mit Beispielen, Erklärungen und SQL-Code.

---

## 📌 Themenübersicht

### 🔄 Trigger in PL/SQL  
**Trigger-Arten, Zeitpunkte, Beispiele und Vergleiche**

📁 Repository:  
🔗 [Übersicht zu Instead-Trigger & Compound Trigger](https://github.com/ad220296/DBI-Test)

🔍 Enthalten:
- 🟡 BEFORE/AFTER Trigger  
- 🔵 INSTEAD OF Trigger auf Views  
- 🧩 COMPOUND Trigger (Statement + Row-Teil)  
- Vergleichstabelle & Empfehlungen  

---

### 🧩 Datenstrukturen: Records, Nested Tables, Packages

📁 Repository:  
🔗 [Übersicht zu Datenstrukturen, Records, Nested Tables, Packages](https://github.com/ad220296/-bersicht-zu-Datenstrukturen-Records-Nested-Tables-Packages/blob/main/README.md)

📘 Enthalten:
- Deklaration & Instanzierung  
- Übergabe an Funktionen/Prozeduren  
- Verhalten bei Zuweisung (by-value)  
- 📘 Records (selbst definiert & %ROWTYPE)  
- 🧩 Nested Tables (als Array oder Hash)  
- 📦 Packages (Header, Body, Sichtbarkeit)  
- Übersichtstabellen & Empfehlungen  

---

### ⚠️ Fehlerbehandlung / Exceptions in PL/SQL

📁 Repository:  
🔗 [Übersicht zu Fehlerbehandlung & Exceptions](https://github.com/ad220296/Exceptions)

📙 Enthalten:
- ✅ Named System Exceptions (`NO_DATA_FOUND`, `TOO_MANY_ROWS`)  
- ❗ Programmer-defined Exceptions (named & unnamed)  
- 🔧 `RAISE_APPLICATION_ERROR` für benutzerdefinierte Fehler  
- 🔗 `PRAGMA EXCEPTION_INIT` zur Fehlercode-Verknüpfung  
- 📦 Exception-Deklaration im Package & Handling im aufrufenden Block  
- Beispielcode aus dem Unterricht (KING, SAL-Check, etc.)

---

### 🧠 Native Dynamic SQL

📁 Repository:  
🔗 [Übersicht zu Native Dynamic SQL](https://github.com/ad220296/Native-Dynamic-SQL)

🧩 Enthalten:
- `EXECUTE IMMEDIATE` zum dynamischen Ausführen von SQL-Strings  
- Parameterübergabe mit `USING`  
- Dynamische Abfragen mit `REF CURSOR`  
- Grundlagen zum Data Dictionary (kein Auswendiglernen nötig)  
- Klassische Anwendungsfälle aus der Praxis  

---
