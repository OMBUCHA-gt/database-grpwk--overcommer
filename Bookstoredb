<-- CREATE DATABASE bookstore -->
<-- Creating a list of all books 
USE bookstore;

CREATE TABLE book (
    book_id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL,
    isbn VARCHAR(20) UNIQUE,
    publication_date DATE,
    price DECIMAL(10, 2),
    publisher_id INT,
    language_id INT
);


<--- Inserting data Sample
INSERT INTO book (title, isbn, publication_date, price, publisher_id, language_id) VALUES
('Pride and Prejudice', '978-0141439518', '1813-01-28', 12.99, 1, 1),
('One Hundred Years of Solitude', '978-0061120092', '1967-05-30', 15.50, 2, 2),
('Les Miserables', '978-0140444306', '1862-01-01', 18.75, 1, 3),
('The Shining', '978-0385121675', '1977-01-28', 14.25, 3, 1),
('Kafka on the Shore', '978-1400079278', '2002-09-12', 16.00, 5, 5),
('Learning SQL', '978-1492057613', '2020-08-15', 39.99, 4, 1);

-- CREATING AUTHOR TABLE
CREATE TABLE author (
    author_id INT PRIMARY KEY AUTO_INCREMENT,
    author_name VARCHAR(255) NOT NULL
);

-- INSERTING DATA
INSERT INTO author (author_name) VALUES
('Jane Austen'),
('Gabriel Garcia Marquez'),
('Victor Hugo'),
('Stephen King'),
('Haruki Murakami'),
('John Patrick');

-- AUTHOR-BOOK MANY-TO-MANY
CREATE TABLE book_author (
    book_id INT,
    author_id INT,
    PRIMARY KEY (book_id, author_id),
    FOREIGN KEY (book_id) REFERENCES book(book_id),
    FOREIGN KEY (author_id) REFERENCES author(author_id)
);

-- CREATING BOOK LANGUAGE TABLE
CREATE TABLE book_language (
    language_id INT PRIMARY KEY AUTO_INCREMENT,
    language_name VARCHAR(50) NOT NULL
);

-- INSERTING DATA
INSERT INTO book_language (language_name) VALUES
('English'),
('Spanish'),
('French'),
('German'),
('Japanese'),
('English');

-- CREATING TABLE PUBLISHER
CREATE TABLE publisher (
    publisher_id INT PRIMARY KEY AUTO_INCREMENT,
    publisher_name VARCHAR(255) NOT NULL
);


-- INSERTING DATA
INSERT INTO publisher (publisher_name) VALUES
('Penguin Books'),
('HarperCollins'),
('Simon & Schuster'),
('O\'Reilly Media'),
('Kodansha'),
('MacMillan'
);


-- CREATING CUSTOMER TABLE

CREATE TABLE customer (
    customer_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(255) NOT NULL,
    last_name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE,
    phone_number VARCHAR(20)
);

-- INSERTING DATA 
INSERT INTO customer (first_name, last_name, email, phone_number) VALUES
('Alice', 'Smith', 'alice@example.com', '555-1234'),
('Bob', 'Johnson', 'bob@example.com', '555-5678'),
('Carol', 'Williams', 'carol@example.com', '555-9012'),
('David', 'Brown', 'david@example.com', '555-3456');

-- LIST OF COUNTRY
CREATE TABLE country (
    country_id INT PRIMARY KEY AUTO_INCREMENT,
    country_name VARCHAR(255) NOT NULL
);

-- COUNTRY DATA
INSERT INTO country (country_name) VALUES
('USA'),
('Canada'),
('UK'),
('France'),
('Japan');

-- ADDRESS FROM COUNTRIES
CREATE TABLE address (
    address_id INT PRIMARY KEY AUTO_INCREMENT,
    street VARCHAR(255),
    city VARCHAR(255),
    postal_code VARCHAR(20),
    country_id INT,
    FOREIGN KEY (country_id) REFERENCES country(country_id)
);

-- DATA INSERTED
INSERT INTO address (street, city, postal_code, country_id) VALUES
('123 Main St', 'Anytown', '12345', 1),
('456 Oak Ave', 'Toronto', 'M5V 2L9', 2),
('789 Baker St', 'London', 'NW1 6XE', 3),
('10 Rue de Rivoli', 'Paris', '75001', 4),
('2-chōme, 14-8 Jingūmae', 'Tokyo', '150-0001', 5);

-- CREATING ADDRESS STATUS
CREATE TABLE address_status (
    address_status_id INT PRIMARY KEY AUTO_INCREMENT,
    status_name VARCHAR(50) NOT NULL
);

-- ADDRESS STATUS DATA
INSERT INTO address_status (status_name) VALUES
('Current'),
('Old'),
('Current'),
('Old'),
('Old');

-- CREATING CUSTOMER ADDRESS
CREATE TABLE customer_address (
    customer_id INT,
    address_id INT,
    address_status_id INT,
    PRIMARY KEY (customer_id, address_id),
    FOREIGN KEY (customer_id) REFERENCES customer(customer_id),
    FOREIGN KEY (address_id) REFERENCES address(address_id),
    FOREIGN KEY (address_status_id) REFERENCES address_status(address_status_id)
);

-- CUSTOMER ADDRESS DATA
INSERT INTO customer_address (customer_id, address_id, address_status_id) VALUES
(1, 1, 1),
(2, 2, 1),
(3, 3, 1),
(4, 4, 1),
(1, 2, 2);

-- CREATING SHIPPING METHOD
CREATE TABLE shipping_method (
    shipping_method_id INT PRIMARY KEY AUTO_INCREMENT,
    method_name VARCHAR(50) NOT NULL
);

-- DATA IN SHIPPING METHOD
INSERT INTO shipping_method (method_name) VALUES
('Standard'),
('Express'),
('Overnight');

-- ORDER STATUS
CREATE TABLE order_status (
    order_status_id INT PRIMARY KEY AUTO_INCREMENT,
    status_name VARCHAR(50) NOT NULL
);

-- ORDER STATUS DATA
INSERT INTO order_status (status_name) VALUES
('Pending'),
('Shipped'),
('Delivered'),
('Cancelled');

-- CUSTOMER ORDER
CREATE TABLE cust_order (
    order_id INT PRIMARY KEY AUTO_INCREMENT,
    customer_id INT,
    order_date DATE,
    shipping_method_id INT,
    order_status_id INT,
    FOREIGN KEY (customer_id) REFERENCES customer(customer_id),
    FOREIGN KEY (shipping_method_id) REFERENCES shipping_method(shipping_method_id),
    FOREIGN KEY (order_status_id) REFERENCES order_status(order_status_id)
);

-- CUSTOMER ORDER DATA
INSERT INTO cust_order (customer_id, order_date, shipping_method_id, order_status_id) VALUES
(1, '2024-10-26', 1, 2),
(2, '2024-10-27', 2, 3),
(3, '2024-10-28', 1, 1),
(4, '2024-10-29', 3, 2);

--ORDER LINE
CREATE TABLE order_line (
    order_line_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    book_id INT,
    quantity INT,
    FOREIGN KEY (order_id) REFERENCES cust_order(order_id),
    FOREIGN KEY (book_id) REFERENCES book(book_id)
);

--ORDER LINE DATA
INSERT INTO order_line (order_id, book_id, quantity) VALUES
(1, 1, 2),
(1, 4, 1),
(2, 2, 1),
(3, 5, 1),
(4, 6, 1);

CREATING HISTORY TABLE
CREATE TABLE order_history (
    history_id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    order_status_id INT,
    change_date DATETIME,
    FOREIGN KEY (order_id) REFERENCES cust_order(order_id),
    FOREIGN KEY (order_status_id) REFERENCES order_status(order_status_id)
);

-- INSERTING SAMPLE DATA
INSERT INTO order_history (order_id, order_status_id, change_date) VALUES
(1, 1, '2024-10-26 10:00:00'),
(1, 2, '2024-10-26 14:00:00'),
(2, 1, '2024-10-27 09:00:00'),
(2, 3, '2024-10-28 12:00:00'),
(3, 1, '2024-10-28 10:00:00'),
(4, 1, '2024-10-29 10:00:00'),
(4, 2, '2024-10-29 14:00:00');

-- Create roles
CREATE ROLE bookstore_admin;
CREATE ROLE bookstore_staff;
CREATE ROLE bookstore_reader;

-- Grant privileges to roles
GRANT ALL PRIVILEGES ON bookstore_db.* TO bookstore_admin;
GRANT SELECT, INSERT, UPDATE ON bookstore_db.* TO bookstore_staff;
GRANT SELECT ON bookstore_db.* TO bookstore_reader;

-- Create users
CREATE USER 'admin_user'@'localhost' IDENTIFIED BY 'AdminPass123';
CREATE USER 'staff_user'@'localhost' IDENTIFIED BY 'StaffPass123';
CREATE USER 'reader_user'@'localhost' IDENTIFIED BY 'ReadPass123';
