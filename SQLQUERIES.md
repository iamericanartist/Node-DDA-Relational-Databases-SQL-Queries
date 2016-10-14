# SQL Queries  

###### For each of the following exercises, provide the appropriate query.
***
**1 Provide a query showing Customers (just their full names, customer ID and country) who are not in the US.**  
```
SELECT Customer.FirstName || " " || Customer.LastName AS Name, Customer.CustomerId, Customer.Country FROM Customer
WHERE Customer.Country IS NOT "USA"
ORDER BY Customer.Country, Customer.CustomerId ASC;
```
46 rows returned / 3 cols

**2 Provide a query only showing the Customers from Brazil.**            <!-- Tested with Customer.Country first  -->
```
SELECT Customer.FirstName || " " || Customer.LastName AS Name FROM Customer
WHERE Customer.Country IS "Brazil"
ORDER BY Name ASC;
```
5 rows returned / 1 col

**3 Provide a query showing the Invoices of customers who are from Brazil. The resultant table should show the customer's full name, Invoice ID, Date of the invoice and billing country.**  
``` 
SELECT Customer.FirstName || " " || Customer.LastName AS Name, Invoice.InvoiceId, Invoice.InvoiceDate, Invoice.BillingCountry FROM Customer
JOIN Invoice ON Customer.CustomerId = Invoice.CustomerId
WHERE Customer.Country IS "Brazil"
ORDER BY Invoice.InvoiceDate ASC;
```
35 rows returned / 4 cols

**4 Provide a query showing only the Employees who are Sales Agents.**  
```
SELECT Employee.FirstName || " " || Employee.LastName AS Name, Employee.Title FROM Employee
WHERE Employee.Title IS "Sales Support Agent"
ORDER BY Name DESC;
```
3 rows returned

**5 Provide a query showing a unique list of billing countries from the Invoice table.**  
```
SELECT Invoice.BillingCountry FROM Invoice
GROUP BY Invoice.BillingCountry;
```
24 rows returned

**6 Provide a query showing the invoices of customers who are from Brazil.**      <!-- Wasn't sure if supposed to include ALL data (which his returns)  => "SELECT Invoice.* FROM Invoice" to only get back the Invoice data-->
```
SELECT * FROM Invoice           
JOIN Customer ON Invoice.CustomerId = Customer.CustomerId
WHERE Customer.Country IS "Brazil"
ORDER BY Invoice.CustomerId ASC;
```
35 rows returned

**7 Provide a query that shows the invoices associated with each sales agent. The resultant table should include the Sales Agent's full name.**  
```
SELECT Employee.FirstName || " " || Employee.LastName AS EmpFullName, Customer.FirstName || " " || Customer.LastName AS CustFullName, Invoice.* FROM Invoice
JOIN Customer ON Invoice.CustomerId = Customer.CustomerId
JOIN Employee ON Customer.SupportRepId = Employee.EmployeeId
ORDER BY EmpFullName, Customer.CustomerId;
```
412 rows returned

**8 Provide a query that shows the Invoice Total, Customer name, Country and Sale Agent name for all invoices and customers.**  
<!-- CUSTOMER FULL NAME + SALES AGENT FULL NAME + COUNTRY + SUM(INVOICE TOTAL) -->
```
SELECT Customer.FirstName || " " || Customer.LastName AS CustFullName, Employee.FirstName || " " || Employee.LastName AS EmpFullName, Invoice.*, Customer.Country, Customer.CustomerId, SUM(Invoice.Total) AS Total FROM Invoice
JOIN Customer ON Invoice.CustomerId = Customer.CustomerId
JOIN Employee ON Customer.SupportRepId = Employee.EmployeeId
GROUP BY Customer.CustomerId
```
59 rows returned / 14 cols

**9 How many Invoices were there in 2009 and 2011? What are the respective total sales for each of those years?**  
<!-- INVOICES > 2009 / SALES TOTAL 2009 / 2011 / SALES TOTAL 2011  --> 3 separate answers needed in SQLite
```
SELECT * FROM Invoice
WHERE Invoice.InvoiceDate LIKE '2009%' OR Invoice.InvoiceDate LIKE '2011%';
```
```
SELECT SUM(Total) AS '2009 Total' FROM Invoice 
WHERE Invoice.InvoiceDate LIKE '2009%';
```
```
SELECT SUM(Total) AS '2011 Total' FROM Invoice 
WHERE Invoice.InvoiceDate LIKE '2011%';
```

**10 Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for Invoice ID 37.**
```
SELECT COUNT(InvoiceLine.InvoiceId) AS InvoiceCount FROM InvoiceLine Where InvoiceLine.InvoiceId = 37
```

**11 Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for each Invoice.** HINT: [GROUP BY](http://www.sqlite.org/lang_select.html#resultset)  
``` 

```

**12 Provide a query that includes the track name with each invoice line item.**  
```

```

**13 Provide a query that includes the purchased track name AND artist name with each invoice line item.**  
```

```

**14 Provide a query that shows the # of invoices per country.** HINT: [GROUP BY](http://www.sqlite.org/lang_select.html#resultset)  
```

```

**15 Provide a query that shows the total number of tracks in each playlist. The Playlist name should be include on the resultant table.**  
```

```

**16 Provide a query that shows all the Tracks, but displays no IDs. The resultant table should include the Album name, Media type and Genre.**  
```

```

**17 Provide a query that shows all Invoices but includes the # of invoice line items.**  
```

```

**18 Provide a query that shows total sales made by each sales agent.**  
```

```

**19 Which sales agent made the most in sales in 2009?**  
```

```

**20 Which sales agent made the most in sales in 2010?**  
```

```

**21 Which sales agent made the most in sales over all?**  
```

```

**22 Provide a query that shows the # of customers assigned to each sales agent.**  
```

```

**23 Provide a query that shows the total sales per country. Which country's customers spent the most?**  
```

```

**24 Provide a query that shows the most purchased track of 2023.**  
```

```

**25 Provide a query that shows the top 5 most purchased tracks over all.**  
```

```

**26 Provide a query that shows the top 3 best selling artists.**  
```

```

**27 Provide a query that shows the most purchased Media Type.**  
```

```
