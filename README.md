# Database Schema Setup

## Overview
This document provides the SQL commands to create the necessary tables for the relational model, and to add new columns to the existing tables.

## Tables Creation

The following SQL commands create the `CUSTOMER`, `PRODUCT`, and `ORDERS` tables:

```sql
CREATE TABLE CUSTOMER (
    CustID INT PRIMARY KEY,
    CustName VARCHAR2(20) NOT NULL,
    CustAddress VARCHAR2(30),
    CustPhone CHAR(10) NOT NULL
);

CREATE TABLE PRODUCT (
    ProdID INT PRIMARY KEY,
    ProdName VARCHAR2(20) NOT NULL,
    ProdPrice NUMBER(7, 2) NOT NULL
);

CREATE TABLE ORDERS (
    OrderID INT PRIMARY KEY,
    CustID INT,
    ProdID INT,
    OrderQuantity INT CHECK (OrderQuantity > 0),
    OrderDate DATE DEFAULT SYSDATE,
    FOREIGN KEY (CustID) REFERENCES CUSTOMER(CustID),
    FOREIGN KEY (ProdID) REFERENCES PRODUCT(ProdID)
);
