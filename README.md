# 🏦 MyBank SQL Project

A comprehensive SQL-based project for a banking system that demonstrates real-world use of SQL for data modeling, querying, and reporting.

---

## 📚 Overview

This project simulates a banking database called `mybank`, including tables like `Customer`, `Accounts`, `Transactions`, `Loans`, `CreditCards`, `Branches`, and `ATMs`. It contains a wide variety of SQL operations including:

* Database creation
* Data retrieval
* Aggregate analysis
* JOIN operations
* Subqueries
* Data transformation
* Temporal analysis

---

## 🧱 Database Schema

* **Customer**: Holds customer personal data (e.g., name, age).
* **Accounts**: Details about customer bank accounts (e.g., balance, status).
* **Transactions**: Log of all transactions on accounts.
* **Loans**: Information on loans taken by customers.
* **CreditCards**: Customer credit card limits and balances.
* **Branches**: Information on different bank branches.
* **ATMs**: ATM locations and statuses.

---

## 📥 Setup Instructions

1. Create the database:

```sql
CREATE DATABASE mybank;
USE mybank;
```

2. Import or define table structures (you can create your own schema or use existing ones).
3. Run the SQL queries provided in `queries.sql` or below.

---

## 📊 Key SQL Queries

### 🔍 Basic Retrieval

```sql
SELECT * FROM Customer;
SELECT * FROM Accounts;
SELECT * FROM Transactions;
```

### 📈 Aggregation

* Total customers:

  ```sql
  SELECT COUNT(*) AS totalcustomer FROM Customer;
  ```
* Total loan amount:

  ```sql
  SELECT SUM(amount) AS totalloanamount FROM Loans;
  ```

### 🔗 Join Queries

* Customer details with accounts:

  ```sql
  SELECT c.customerID, c.name, a.accountNumber
  FROM Customer c
  JOIN Accounts a ON c.customerID = a.customerID;
  ```

* Transactions with account and customer info:

  ```sql
  SELECT t.transactionID, c.name, a.accountNumber
  FROM Transactions t
  JOIN Accounts a ON t.accountNumber = a.accountNumber
  JOIN Customer c ON a.customerID = c.customerID;
  ```

### 🧠 Advanced Queries

* Find customers with multiple accounts:

  ```sql
  SELECT c.customerID, COUNT(*) AS numAccounts
  FROM Customer c
  JOIN Accounts a ON c.customerID = a.customerID
  GROUP BY c.customerID
  HAVING COUNT(*) > 1;
  ```

* Fifth highest loan amount (without `LIMIT`):

  ```sql
  SELECT DISTINCT amount
  FROM Loans l1
  WHERE 5 = (
    SELECT COUNT(DISTINCT amount)
    FROM Loans l2
    WHERE l2.amount >= l1.amount
  );
  ```

* Calculate days remaining on loans:

  ```sql
  SELECT customerID, DATEDIFF(endDate, CURDATE()) AS daysRemaining
  FROM Loans
  WHERE endDate > CURDATE();
  ```

---

## 🛠 Technologies Used

* SQL (MySQL or compatible dialects)
* Relational Database concepts
* Aggregate functions, joins, subqueries

---

## 📸 Screenshots

> *(You can add ER diagrams or query results here)*

---



---

## 👤 Author

**Your Name**
GitHub: [yourusername](https://github.com/Rahul456s)
Email: [youremail@example.com](mailto:youremail@rahul456shende@gmail.com)

---
