# E-Shopping

A Java console application for an online store with separate admin and customer roles. Data is stored in PostgreSQL through JDBC.

## Features

**Sign in / sign up.** Users log in by role: admin or customer.

**Admin**
- Add products
- Accept orders
- Handle cancellation and return requests

**Customer**
- Browse products and view product details
- Place orders and make payments
- Manage orders: cancel, return, view order history

## Requirements

- JDK 8 or later (tested with JDK 17)
- PostgreSQL running on `localhost:5432`
- PostgreSQL JDBC driver (`postgresql-<version>.jar`) from https://jdbc.postgresql.org/download/

## Database setup

1. Create an empty database:
   ```sql
   CREATE DATABASE eshopping;
   ```
2. The connection details are in `Database.java` (`jdbc:postgresql://localhost:5432/eshopping`, user `postgres`). Change the username and password there to match your PostgreSQL install.
3. You don't need to create any tables. On startup the app creates them (`Tables.java`) and inserts sample data, including demo admin and customer accounts (`TableInsertion.java`).

## Build and run

Put the JDBC driver jar in a `lib/` folder, then run from the `eshopping` folder:

```bash
javac -d out *.java
java -cp "out;lib/postgresql-42.7.4.jar" com.zoho.E_Shopping.E_Shopping
```

> On Linux/macOS, use `:` instead of `;` in the classpath.

## Project structure

| File(s) | Purpose |
|---|---|
| `E_Shopping.java` | Entry point and main menu |
| `SignIn.java`, `SignUp.java` | Authentication |
| `AdminView.java`, `AddProduct.java`, `AcceptOrder.java`, `AcceptCancel.java`, `AcceptReturn.java` | Admin features |
| `CustomerView.java`, `BrowseProduct.java`, `Order.java`, `Payment.java`, `CancelOrder.java`, `OrderHistory.java` | Customer features |
| `*Model.java` | Data models |
| `Database.java`, `SingletonStatement.java` | Database connection |
| `Tables.java`, `TableInsertion.java` | Table creation and sample data |
| `*Exception.java` | Custom exceptions |
