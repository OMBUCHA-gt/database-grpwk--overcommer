Bookstore Database Design & Programming with SQL

Overview
This project simulates a real-world scenario in which you're tasked with designing and implementing a relational MySQL database for a bookstore. The system supports data on books, authors, customers, orders, shipping, and user role management. It demonstrates good practices in schema design, relationship modeling, and access control.


Tools & Technologies
- MySQL 8+ — Database engine

- MySQL Workbench — For writing and testing SQL scripts

- Draw.io (optional) — For visualizing entity relationships


Key Features
- Fully normalized relational schema

- Foreign keys and referential integrity across 15+ tables

- Support for many-to-many relationships (e.g. books & authors)

- Role-based user access management

- Secure user privilege setup (admin, staff, analyst)

- Future-ready structure for order history and shipping workflows


Tables Implemented

Table                            Purpose
Book                             Stores book details
Author                           Stores author details
Book_author                      Many-to-many mapping of books and authors
Publisher                        Book publishers
Book_language                    Language list
Customer                         Bookstore customers
Customer_address                 Mapping of customers to addresses
Address                          All physical addresses
Address_status                   Track if address is current/old
Country                          Supported countries
Cust_order                       Customer orders
Order_line                       Line items per order
Shipping_method                  Shipping methods (e.g. standard, express)
Order_status                     Status list (e.g. pending, delivered)
Order_history                    Logs of order status transitions


User Roles and Permissions

User                          Description                                    Privileges
Bookstore_admin               Full access to all database actions            ALL PRIVILEGES
Bookstore_staff               Can manage books, customers, orders            SELECT, INSERT, UPDATE
Bookstore_analyst             Read-only access                               SELECT only


Learning Outcomes
- Design a normalized schema for real-world business logic

- Understand SQL constraints: FOREIGN KEY, UNIQUE, AUTO_INCREMENT

- Manage access using CREATE USER, GRANT, and REVOKE

- Handle many-to-many and one-to-many relationships cleanly


LINK TO DRAW.IO
https://docs.google.com/document/d/1pLrZtSvYZejZx4FM07vFg1VOpU05fUI51V9FXh1cYb0/edit?usp=sharing