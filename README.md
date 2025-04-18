Table Structure:
CREATE DATABASE ecommerce;
USE ecommerce;

CREATE TABLE customers (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    address TEXT
);

-- Products Table
CREATE TABLE products (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    price DECIMAL(10,2),
    description TEXT
);

CREATE TABLE orders (
    id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10,2),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

SELECT * FROM customers;
INSERT INTO customers (name, email, address)
VALUES
('John Doe', 'john.doe@example.com', '123 Elm St, Springfield'),
('Jane Smith', 'jane.smith@example.com', '456 Oak St, Springfield'),
('Alice Johnson', 'alice.johnson@example.com', '789 Pine St, Springfield'),
('Bob Brown', 'bob.brown@example.com', '101 Maple St, Springfield'),
('Charlie Davis', 'charlie.davis@example.com', '202 Birch St, Springfield'),
('Diana Green', 'diana.green@example.com', '303 Cedar St, Springfield'),
('Ethan White', 'ethan.white@example.com', '404 Pine St, Springfield'),
('Fiona Black', 'fiona.black@example.com', '505 Walnut St, Springfield'),
('George King', 'george.king@example.com', '606 Oak St, Springfield'),
('Helen Turner', 'helen.turner@example.com', '707 Ash St, Springfield'),
('Irene Adams', 'irene.adams@example.com', '808 Elm St, Springfield'),
('Jack Scott', 'jack.scott@example.com', '909 Maple St, Springfield'),
('Kathy Morgan', 'kathy.morgan@example.com', '1010 Cedar St, Springfield'),
('Liam Walker', 'liam.walker@example.com', '1111 Birch St, Springfield'),
('Monica Allen', 'monica.allen@example.com', '1212 Pine St, Springfield'),
('Nathan Young', 'nathan.young@example.com', '1313 Oak St, Springfield'),
('Olivia Hill', 'olivia.hill@example.com', '1414 Ash St, Springfield'),
('Paul Harris', 'paul.harris@example.com', '1515 Walnut St, Springfield'),
('Quinn Mitchell', 'quinn.mitchell@example.com', '1616 Elm St, Springfield'),
('Rachel Carter', 'rachel.carter@example.com', '1717 Maple St, Springfield');

select * from orders;
INSERT INTO orders (customer_id, order_date, total_amount)
VALUES
(10, '2025-02-15', 999.99),
(15, '2025-02-16', 599.99),
(3, '2025-02-17', 149.99),
(8, '2025-02-18', 799.99),
(4, '2025-02-19', 399.99),
(6, '2025-02-20', 1200.00),
(14, '2025-02-21', 349.99),
(1, '2025-02-22', 499.99),
(11, '2025-02-23', 899.99),
(17, '2025-02-24', 399.99),
(2, '2025-02-25', 199.99),
(13, '2025-02-26', 599.99),
(18, '2025-02-27', 649.99),
(5, '2025-02-28', 1099.99),
(12, '2025-03-01', 899.99),
(7, '2025-03-02', 129.99),
(19, '2025-03-03', 799.99),
(9, '2025-03-04', 450.00),
(20, '2025-03-05', 199.99),
(16, '2025-03-06', 599.99),
(3, '2025-03-07', 899.99),
(14, '2025-03-08', 599.99),
(6, '2025-03-09', 1299.99),
(10, '2025-03-10', 799.99),
(17, '2025-03-11', 350.00),
(4, '2025-03-12', 499.99),
(18, '2025-03-13', 649.99),
(2, '2025-03-14', 109.99),
(13, '2025-03-15', 399.99),
(15, '2025-03-16', 899.99),
(19, '2025-03-17', 499.99),
(1, '2025-03-18', 799.99),
(12, '2025-03-19', 1199.99),
(20, '2025-03-20', 549.99),
(7, '2025-03-21', 799.99),
(8, '2025-03-22', 499.99),
(5, '2025-03-23', 1199.99),
(3, '2025-03-24', 899.99),
(4, '2025-03-25', 699.99),
(16, '2025-03-26', 849.99),
(9, '2025-03-27', 649.99),
(11, '2025-03-28', 799.99),
(14, '2025-03-29', 399.99),
(1, '2025-03-30', 1299.99),
(17, '2025-03-31', 249.99),
(6, '2025-03-31', 1199.99),
(5, '2025-03-31', 599.99),
(10, '2025-03-31', 499.99),
(8, '2025-03-31', 349.99);

SELECT * from products;

INSERT INTO products (name, price, description)
VALUES
('Wireless Mouse', 29.99, 'Ergonomic wireless mouse with USB receiver.'),
('Mechanical Keyboard', 89.99, 'RGB backlit mechanical keyboard with blue switches.'),
('Gaming Headset', 59.99, 'Over-ear gaming headset with noise cancellation.'),
('Laptop Stand', 39.99, 'Adjustable aluminum laptop stand for desk use.'),
('Webcam 1080p', 49.99, 'Full HD webcam with built-in microphone.'),
('USB-C Hub', 24.99, 'Multiport USB-C hub with HDMI and SD card support.'),
('Bluetooth Speaker', 44.99, 'Portable Bluetooth speaker with bass boost.'),
('Fitness Tracker', 69.99, 'Waterproof fitness tracker with heart rate monitor.'),
('Smartphone Tripod', 19.99, 'Flexible tripod for smartphones and action cameras.'),
('Portable SSD 1TB', 129.99, '1TB external SSD with USB 3.1 Gen 2.'),
('Wireless Charger', 22.99, 'Fast charging pad for Qi-enabled devices.'),
('LED Desk Lamp', 34.99, 'Dimmable LED lamp with USB charging port.'),
('Noise Cancelling Earbuds', 99.99, 'True wireless earbuds with ANC.'),
('Smartwatch', 149.99, 'Touchscreen smartwatch with fitness features.'),
('Laptop Backpack', 59.99, 'Water-resistant backpack with 15-inch laptop compartment.');


Queries to Write:

**1. Retrieve all customers who have placed an order in the last 30 days.
USE ecommerce;**
select name from customers c
join orders o on c.id = o.customer_id
where o.order_date >= curdate() - interval 30 day;

**2. Get the total amount of all orders placed by each customer.
USE ecommerce;**
SELECT c.id, c.name, SUM(o.total_amount) AS total_spent
FROM customers c
JOIN orders o ON c.id = o.customer_id
GROUP BY c.id, c.name;

**3. Update the price of Bluetooth Speaker to 45.00.**
USE ecommerce;
UPDATE products
SET price = 45.00
WHERE name = 'Bluetooth Speaker';

**4. Add a new column discount to the products table.**
ALTER TABLE products
ADD COLUMN discount DECIMAL(5, 2) DEFAULT 0.00;

**5. Retrieve the top 3 products with the highest price.**
SELECT * 
FROM products 
ORDER BY price DESC 
LIMIT 3;

**6. Get the names of customers who have ordered  Bluetooth Speaker.**


**7. Join the orders and customers tables to retrieve the customer's name and order date for each order.** 
SELECT o.id AS order_id, c.name AS customer_name, o.order_date
FROM orders o
JOIN customers c ON o.customer_id = c.id;

**8. Retrieve the orders with a total amount greater than 150.00.**
SELECT * FROM orders
WHERE total_amount > 150.00;


**9. Normalize the database by creating a separate table for order items and updating the orders table to reference the order_items table.**
CREATE TABLE order_items (
    id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT DEFAULT 1,
    price DECIMAL(10, 2),
    FOREIGN KEY (order_id) REFERENCES orders(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);

**10. Retrieve the average total of all orders.**
SELECT AVG(total_amount) AS avg_order_total
FROM orders;

