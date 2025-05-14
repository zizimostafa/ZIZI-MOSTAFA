
-- CREATE TABLES
CREATE TABLE Users (
    UserID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100),
    Email VARCHAR(100) UNIQUE,
    Phone VARCHAR(20)
);

CREATE TABLE Products (
    ProductID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100),
    Description TEXT,
    Price DECIMAL(10,2),
    Stock INT
);

CREATE TABLE Orders (
    OrderID INT PRIMARY KEY AUTO_INCREMENT,
    UserID INT,
    OrderDate DATE,
    Status VARCHAR(50),
    FOREIGN KEY (UserID) REFERENCES Users(UserID)
);

CREATE TABLE Payments (
    PaymentID INT PRIMARY KEY AUTO_INCREMENT,
    OrderID INT,
    PaymentDate DATE,
    Amount DECIMAL(10,2),
    PaymentMethod VARCHAR(50),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);

CREATE TABLE OrderItems (
    OrderItemID INT PRIMARY KEY AUTO_INCREMENT,
    OrderID INT,
    ProductID INT,
    Quantity INT,
    Price DECIMAL(10,2),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
    FOREIGN KEY (ProductID) REFERENCES Products(ProductID)
);

-- INSERT SAMPLE DATA

-- Users
INSERT INTO Users (Name, Email, Phone) VALUES
('Zizi', 'zizi@example.com', '0100000001'),
('Ahmed', 'ahmed@example.com', '0100000002'),
('Sara', 'sara@example.com', '0100000003'),
('Omar', 'omar@example.com', '0100000004'),
('Laila', 'laila@example.com', '0100000005'),
('Mona', 'mona@example.com', '0100000006'),
('Khaled', 'khaled@example.com', '0100000007'),
('Youssef', 'youssef@example.com', '0100000008'),
('Nada', 'nada@example.com', '0100000009'),
('Tamer', 'tamer@example.com', '0100000010');

-- Products
INSERT INTO Products (Name, Description, Price, Stock) VALUES
('Laptop', 'Gaming laptop', 15000.00, 10),
('Mouse', 'Wireless mouse', 150.00, 50),
('Keyboard', 'Mechanical keyboard', 300.00, 30),
('Monitor', '24 inch LED', 1200.00, 20),
('Phone', 'Smartphone', 8000.00, 15),
('Tablet', '10 inch Android tablet', 3500.00, 12),
('Headphones', 'Bluetooth headphones', 500.00, 40),
('Charger', 'Fast charger', 250.00, 60),
('USB Cable', 'Type-C cable', 100.00, 80),
('Camera', 'DSLR camera', 20000.00, 5);

-- Orders
INSERT INTO Orders (UserID, OrderDate, Status) VALUES
(1, '2025-05-01', 'Pending'),
(2, '2025-05-02', 'Shipped'),
(3, '2025-05-03', 'Delivered'),
(4, '2025-05-04', 'Cancelled'),
(5, '2025-05-05', 'Pending'),
(6, '2025-05-06', 'Delivered'),
(7, '2025-05-07', 'Shipped'),
(8, '2025-05-08', 'Pending'),
(9, '2025-05-09', 'Delivered'),
(10, '2025-05-10', 'Shipped');

-- Payments
INSERT INTO Payments (OrderID, PaymentDate, Amount, PaymentMethod) VALUES
(1, '2025-05-01', 15000.00, 'Credit Card'),
(2, '2025-05-02', 150.00, 'PayPal'),
(3, '2025-05-03', 800.00, 'Cash'),
(4, '2025-05-04', 1200.00, 'Credit Card'),
(5, '2025-05-05', 500.00, 'Cash'),
(6, '2025-05-06', 9000.00, 'PayPal'),
(7, '2025-05-07', 250.00, 'Cash'),
(8, '2025-05-08', 20000.00, 'Credit Card'),
(9, '2025-05-09', 750.00, 'PayPal'),
(10, '2025-05-10', 100.00, 'Credit Card');

-- OrderItems
INSERT INTO OrderItems (OrderID, ProductID, Quantity, Price) VALUES
(1, 1, 1, 15000.00),
(2, 2, 1, 150.00),
(3, 3, 2, 400.00),
(4, 4, 1, 1200.00),
(5, 5, 1, 8000.00),
(6, 6, 1, 3500.00),
(7, 7, 1, 500.00),
(8, 8, 1, 250.00),
(9, 9, 2, 200.00),
(10, 10, 1, 20000.00);
