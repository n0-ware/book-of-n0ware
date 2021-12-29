# Relational Database Management System (RDBMS)

###### MS SQL as an example

# Description
A RDBMS , such as Microsoft SQL (Structured Query Language) can be visualized as a group of tables that all have relationships. 

## Example

Consider an online grocery store database with three tables.

1. Produce
2. Customers
3. Invoices

*Each **Produce** table has the columns*
- ID
- Name
- Price
- Quantity

*Each **Cutomer** table has the columns*
- ID
- Name
- Price
- Quantity

The **Invoices** table shares information from both, referring to a single customer per row with one  or more produce items. This table refers to another table using its ID. In this way, we only need to have the customer details and the invoice written once instead of copying them each to a new invoice.

***For example***

&emsp;&emsp;**customers**&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; **produce**  
###### These are two separate tables  
| id | name | `next table` |  id | name |   
| --- | --- | :---: | --- | --- |   
| 101 | Michael | `next table` | 1 | Lettuce |   
| 102 | Katrina | `next table` | 2 | Tomato |   
| 103 | John | `next table` | 3 | Banana |   

**Invoice**
###### Contains the `ID` from **Customer** and the `ID` from **Produce**
| id_customer | id_produce |   
| --- | --- |   
| 101 | 3, 1 |   
| 102 | 1 |   
| 103 | 2, 3 |   