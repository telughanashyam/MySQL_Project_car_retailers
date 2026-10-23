# Car Retailers Management System

A MySQL database project for managing the core records of a car dealership, including vehicle inventory, brands, customers, employees, sales, and payments.

## Project Overview

This project organizes dealership information in a relational database and demonstrates commonly used MySQL database concepts. It is intended for learning, practice, and academic project submissions.

## Objectives

- Maintain car brand and vehicle information.
- Track vehicle model details, price, fuel type, transmission, and availability.
- Store customer and employee records.
- Record vehicle sales and related payments.
- Summarize inventory and sales information.
- Demonstrate relational constraints, views, stored procedures, triggers, and indexes.

## Technologies

- **Database:** MySQL
- **Recommended client:** MySQL Workbench
- **Recommended version:** MySQL 8.0.16 or later

## Database Structure

The database is named `car_retailers_db` and includes six main tables.

| Table | Purpose |
|---|---|
| `brands` | Stores brand names and countries of origin. |
| `cars` | Stores vehicle details, prices, status, and VIN field. |
| `customers` | Stores customer names, contact details, and cities. |
| `employees` | Stores employee details, job titles, and hire dates. |
| `sales` | Records sales and links cars with customers and employees. |
| `payments` | Stores payment amounts, dates, methods, and statuses. |

## Relationships

- One brand can be associated with multiple cars.
- Each car can be associated with at most one sale record in the current design.
- One customer can be associated with multiple sales.
- One employee can handle multiple sales.
- Each sale can have one associated payment record.

## Key Features

- Vehicle inventory and availability tracking.
- Customer and employee record management.
- Sales and payment tracking.
- Brand-wise inventory summaries.
- Sales and revenue summaries.
- Reusable views for reporting.
- A stored procedure for processing a sale and its payment.
- Triggers to check car availability and update the car status after a sale.
- Indexes on selected columns used for common searches and joins.

## MySQL Concepts Demonstrated

- Database and table creation.
- Primary keys and auto-increment identifiers.
- Foreign key relationships.
- `NOT NULL`, `UNIQUE`, `DEFAULT`, `ENUM`, and `CHECK` constraints.
- Data insertion and retrieval.
- Filtering, sorting, grouping, and aggregate functions.
- Joins, subqueries, and conditional expressions.
- Views, stored procedures, triggers, and indexes.
- Transactions and error handling.

**Project requirement:** Common Table Expressions (CTEs) and window functions are not used.

## Views

- **`vw_available_cars`** — displays cars currently marked as available.
- **`vw_sales_details`** — combines sale information with related car, brand, customer, employee, and payment details.
- **`vw_sales_summary`** — summarizes completed sales, total revenue, and average sale price.

## Stored Procedure

The project includes **`sp_sell_car`**, which checks vehicle availability, creates a sale record and corresponding payment record, and commits the transaction. If an SQL exception occurs, the procedure rolls back the transaction.

## Triggers

- **`trg_before_sale_insert`** — checks that a car is available before allowing a sale record to be inserted.
- **`trg_after_sale_insert`** — changes the car status to `Sold` after a sale record is inserted.

## Indexes

Indexes are created on selected columns used in common filtering and joins, including car status, brand/model, sale date, customer, employee, and payment method.

## How to Run

1. Install and start MySQL Server.
2. Open MySQL Workbench or another compatible MySQL client.
3. Open the project's SQL script.
4. Review the script before executing it.
5. Execute the script in order.
6. Inspect the created tables, views, and sample query results.

> **Important:** The setup script drops and recreates the project's tables and views. Back up existing project data before running it, because records in those tables may be deleted. MySQL 8.0.16 or later is recommended for enforced `CHECK` constraints.

## Reports Supported

- Available cars.
- Detailed sales with customer and employee information.
- Completed sales revenue and average sale price.
- Available car counts by brand.
- Paid amounts grouped by payment method.
- Cars within a price range.
- Customers from selected cities.
- Vehicle price categories.

Sales and payment reports may be empty until a sale is recorded. This is expected in a newly initialized database.

## Suggested Repository Structure

- `car_retailers_management.sql` — database setup, sample data, and database objects.
- `README.md` — project documentation.
- `diagrams/ER_Diagram.png` — ER diagram, if included.
- `presentation/Car_Retailers_Management_System.pptx` — presentation, if included.
- `docs/Step_by_Step_Tenglish.md` — Tenglish explanation, if included.

## Limitations

- This is an educational database project, not a complete production dealership application.
- Sample VIN values are placeholders, not real manufacturer-issued Vehicle Identification Numbers.
- The current design allows at most one sale record per car because the car identifier in the sales table is unique.
- Additional validation, security, and business rules would be required for real-world deployment.

## Learning Outcomes

This project provides practice with relational database design, constraints, table relationships, reporting queries, and MySQL programmable objects.

## License

No license is specified. Add a license file if you want to define how others may use, modify, or distribute the project.
