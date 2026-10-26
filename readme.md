Car Retailers Management System

A MySQL database project for managing a car dealership's inventory, customers, employees, sales, and payments.

Project Objectives
- Store car brand and vehicle details.
- Maintain customer and employee information.
- Track available, sold, and maintenance vehicles.
- Record sales and related payments.

Technologies
- MySQL 8.0+ (MySQL 8.0.16+ recommended for enforced CHECK
  constraints)
- MySQL Command Line Client (recommended)

Database Structure
Database name: car_retailers_db

  Table         Purpose
  brands      Car brand names and countries
  cars        Vehicle details, price, VIN, and status
  customers   Customer contact information
  employees   Employee information
  sales       Sales linked to cars, customers, and employees
  payments    Payment details for sales

Relationships
- One brand can have many cars.
- A car can appear in at most one sale record.
- A customer can have multiple sales.
- An employee can handle multiple sales.
- Each sale can have one payment record.

MySQL Topics Demonstrated
- Database and table creation
- Primary keys and AUTO_INCREMENT
- Foreign keys
- NOT NULL, UNIQUE, DEFAULT, ENUM, and CHECK constraints
- INSERT, SELECT, filtering, sorting, and grouping
- BETWEEN, IN, CASE, aggregate functions, and joins
- Views, stored procedures, triggers, indexes
- Transactions and SQL exception handling

Views
- vw_available_cars --- lists cars currently available.
- vw_sales_details --- combines sale, car, brand, customer,
  employee, and payment details.
- vw_sales_summary --- summarizes completed sales, revenue, and
  average sale price.

Stored Procedure
sp_sell_car checks that a car is available, inserts a sale and payment
record, and commits the transaction. If an SQL exception occurs, it
rolls back.

Triggers
- trg_before_sale_insert --- prevents a sale when the car is not
  available.
- trg_after_sale_insert --- marks the car as Sold after a sale is
  inserted.

Indexes
Indexes are created for frequently searched or joined columns, including
car status, brand/model, sale date, customer, employee, and payment
method.

How to Run
1. Start MySQL Server and open MySQL Command Line Client.
2. Open mysql_queries.txt
3. Review the script, then execute it.
4. Check the sample SELECT query results.

The script creates/selects car_retailers_db, recreates the project's
tables and views, inserts sample data, creates indexes, triggers, a
stored procedure and views, then runs test queries.



