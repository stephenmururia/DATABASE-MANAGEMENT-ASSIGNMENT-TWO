# DATABASE-MANAGEMENT-ASSIGNMENT-TWO

```sql
-- Create Customers table
CREATE TABLE Customers (
    CustomerNo INT PRIMARY KEY,
    CustomerName VARCHAR(255) NOT NULL,
    CustomerAdd VARCHAR(255) NOT NULL
);

-- Create Clerks table
CREATE TABLE Clerks (
    ClerkNo INT PRIMARY KEY,
    ClerkName VARCHAR(255) NOT NULL
);

-- Create Inventory Items table
CREATE TABLE InventoryItems (
    ItemNo INT PRIMARY KEY,
    Description VARCHAR(255) NOT NULL
);

-- Create Sales Orders table
CREATE TABLE SalesOrders (
    SalesOrderNo INT PRIMARY KEY,
    Date DATE NOT NULL,
    CustomerNo INT,
    ClerkNo INT,
    FOREIGN KEY (CustomerNo) REFERENCES Customers(CustomerNo),
    FOREIGN KEY (ClerkNo) REFERENCES Clerks(ClerkNo)
);

-- Create Sales Order Detail table
CREATE TABLE SalesOrderDetail (
    SalesOrderNo INT,
    ItemNo INT,
    Qty INT NOT NULL,
    UnitPrice DECIMAL(10, 2) NOT NULL,
    PRIMARY KEY (SalesOrderNo, ItemNo),
    FOREIGN KEY (SalesOrderNo) REFERENCES SalesOrders(SalesOrderNo),
    FOREIGN KEY (ItemNo) REFERENCES InventoryItems(ItemNo)
);
