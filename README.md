# Legacy-Data-Conversion
Data Conversion Project

# 🐘 Legacy Data Conversion Project (Postgres + Python)

This project simulates a **real-world data conversion**: migrating data from a messy **legacy database** into a clean **destination schema** using both **SQL (dblink)** and **Python ETL**.

It mirrors the work of a Conversion Engineer — extracting data from legacy systems, transforming it with business rules, and loading it into a modern schema. 

---

## 📂 Project Structure

## 🛠 Tech Stack
- **PostgreSQL 17** (via Postgres.app)  
- **Python 3.12** (`psycopg2`)  
- **Azure Data Studio** (query execution & validation)  
- **dblink extension** (SQL cross-database migration)  

---

## 🚀 Workflow

### 1. Setup
- Run `sql/source_setup.sql` → seeds `source_db` with **legacy-style tables** (`contr`, `addr`).
- Run `sql/destination_setup.sql` → creates `destination_db` with **clean schema** (`Contact`, `Address`).

### 2. Migration
- **Option 1 (SQL only):** Run `sql/migration_scripts.sql`  
  Uses `dblink` to pull directly from `source_db` → `destination_db`.  
- **Option 2 (Python ETL):** Run `src/etl_pipeline.py`  
  Extracts from `source_db`, applies transformations, and loads into `destination_db`.

### 3. Validation
- Run `sql/validation_report.sql` → compares row counts between source & destination, ensuring successful migration.

---

## 📊 Architecture

![Architecture Diagram](img/architecture.png)

---

## ✅ Business Rules Applied
- `Active → A`, `Inactive → I` in `Contact.STATUS`  
- `IS_PERSON = TRUE` if `FirstName` exists and `CompanyName` is NULL  

---

## 📈 Deliverables
- `source_setup.sql` → Build & seed legacy DB  
- `destination_setup.sql` → Clean schema  
- `migration_scripts.sql` → SQL-based ETL with dblink  
- `etl_pipeline.py` → Python-based ETL  
- `validation_report.sql` → QA report  

---

## 🎯 Key Learnings
- Designed and tested a **repeatable migration pipeline**.  
- Learned how to use **Postgres dblink** (similar to Linked Servers in SQL Server).  
- Reinforced importance of **validation reporting** in conversion projects.  

---

## 📌 Future Enhancements
- Add more legacy tables (Phones, Licenses, Payments).  
- Build cumulative validation reports (row counts, transformation mismatches).  
- Containerize with Docker for easier environment setup.
