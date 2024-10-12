-- Таблица хаба для клиентов
CREATE TABLE Hub_Customer (
    Customer_ID UInt64,
    Segment String,
    Load_Datetime DateTime DEFAULT now()
) ENGINE = MergeTree() 
ORDER BY Customer_ID;

-- Таблица хаба для географии
CREATE TABLE Hub_Geography (
    Geography_ID UInt64,
    Country String,
    City String,
    State String,
    Postal_Code String,
    Region String,
    Load_Datetime DateTime DEFAULT now()
) ENGINE = MergeTree() 
ORDER BY Geography_ID;

-- Таблица хаба для продуктов
CREATE TABLE Hub_Product (
    Product_ID UInt64,
    Category String,
    Sub_Category String,
    Load_Datetime DateTime DEFAULT now()
) ENGINE = MergeTree() 
ORDER BY Product_ID;

-- Таблица хаба для доставки
CREATE TABLE Hub_Shipment (
    Shipment_ID UInt64,
    Ship_Mode String,
    Load_Datetime DateTime DEFAULT now()
) ENGINE = MergeTree() 
ORDER BY Shipment_ID;

-- Таблица хаба для транзакций
CREATE TABLE Hub_Transaction (
    Transaction_ID UInt64,
    Transaction_Date Date,
    Load_Datetime DateTime DEFAULT now()
) ENGINE = MergeTree() 
ORDER BY Transaction_ID;

-- Таблицы связей (Links)
CREATE TABLE Link_Transaction_Product (
    Transaction_ID UInt64,
    Product_ID UInt64,
    Load_Datetime DateTime DEFAULT now()
) ENGINE = MergeTree()
ORDER BY Transaction_ID;

CREATE TABLE Link_Transaction_Customer (
    Transaction_ID UInt64,
    Customer_ID UInt64,
    Load_Datetime DateTime DEFAULT now()
) ENGINE = MergeTree()
ORDER BY Transaction_ID;

CREATE TABLE Link_Transaction_Geography (
    Transaction_ID UInt64,
    Geography_ID UInt64,
    Load_Datetime DateTime DEFAULT now()
) ENGINE = MergeTree()
ORDER BY Transaction_ID;

CREATE TABLE Link_Transaction_Shipment (
    Transaction_ID UInt64,
    Shipment_ID UInt64,
    Load_Datetime DateTime DEFAULT now()
) ENGINE = MergeTree()
ORDER BY Transaction_ID;

-- Таблицы сателлитов (Satellites)
CREATE TABLE Satellite_Customer (
    Customer_ID UInt64,
    Segment String,
    Timestamp DateTime DEFAULT now()
) ENGINE = MergeTree()
ORDER BY Customer_ID;

CREATE TABLE Satellite_Geography (
    Geography_ID UInt64,
    Country String,
    City String,
    State String,
    Postal_Code String,
    Region String,
    Timestamp DateTime DEFAULT now()
) ENGINE = MergeTree()
ORDER BY Geography_ID;

CREATE TABLE Satellite_Product (
    Product_ID UInt64,
    Category String,
    Sub_Category String,
    Timestamp DateTime DEFAULT now()
) ENGINE = MergeTree()
ORDER BY Product_ID;

CREATE TABLE Satellite_Transaction (
    Transaction_ID UInt64,
    Sales Float32,
    Quantity UInt32,
    Discount Float32,
    Profit Float32,
    Timestamp DateTime DEFAULT now()
) ENGINE = MergeTree()
ORDER BY Transaction_ID;
