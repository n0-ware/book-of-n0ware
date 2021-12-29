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


###### These are two separate tables  
&emsp;&emsp;`customers`&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; `produce`  

<table>
	<thead>
		<tr>
			<th colspan=2><b>customers</b></th>
			<th colspan=2><b>produce</b></th>
		</tr>
	</thead>
<table>

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



<table>
    <thead>
        <tr>
            <th>Layer 1</th>
            <th>Layer 2</th>
            <th>Layer 3</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=4>L1 Name</td>
            <td rowspan=2>L2 Name A</td>
            <td>L3 Name A</td>
        </tr>
        <tr>
            <td>L3 Name B</td>
        </tr>
        <tr>
            <td rowspan=2>L2 Name B</td>
            <td>L3 Name C</td>
        </tr>
        <tr>
            <td>L3 Name D</td>
        </tr>
    </tbody>
</table>
