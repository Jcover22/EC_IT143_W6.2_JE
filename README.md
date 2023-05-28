# EC_IT143_W6.2_JE
*****************************************************************************************************************
NAME: W6.2 - Adventure Works: Create Answers
PURPOSE: Solve and craft answers using SQL
MODIFICATION LOG:
 Ver    Date       Author      Description
-----   -----     ---------     ------------------------------------------------------------------------------------------
1.0  05/27/2023    JESCOBAR        1. Built this script for EC IT143


RUNTIME:
Xm Xs
NOTES:
Built for W6.2 - Adventure Works: Create Answers, SQL script will contain the questions and the answers for W6.1.

I am building this script in order to show my fellow online students how to solve the EIGHT (8) Business User questions that have a single specific answer using AdventureWorks Database,
with the help of the following tools...
- Adventure Works Meta data -> https://dataedo.com/samples/html/AdventureWorks/index.html
- SQL
- SSMS

******************************************************************************************************************/
--MARGINAL COMPLEXITY QUESTIONS--

-- Q1: What are the five highest sales taxes?
-- A1: Get a list of the highest sales taxes
*Author: Cristhian Pacheco*

SELECT TOP 5 TaxRate AS Q2_Top5_TaxRate, Name AS TaxName
FROM Sales.SalesTaxRate
ORDER BY TaxRate DESC;


-- Q2: How many product are there in the "Product" table of AdventureWorks?
-- A2: To determine the number of products in the "Product" table of AdventureWorks
*Author: Benjamin Sarpong*

SELECT COUNT(*) AS ProductCount
From AdventureWorks2019.Production.Product;


******************************************************************************************************************/
--MODERATE COMPLEXITY QUESTIONS--
-- Q3: I am interested to know a list of the unique job titles in the employee table from the Adventure Works database. Can you please create a list that provides this information? Also, return the job title column in ascending Order. 
-- A3: Obtain a list of unique job titles from the employee table in the Adventure Works database and return the job title column in ascending Order.
*Author: Judith Escobar*

SELECT DISTINCT JobTitle
FROM AdventureWorks2019.HumanResources.Employee
ORDER BY JobTitle ASC;

-- Q4: Who are the three top sales personnel we have in our organization? What are their email addresses and their contact information?
-- A4: To obtain the top sales personnel and their email addresses with their contact information.
*Author: Benelyn Njoku*

SELECT TOP 3 SP.BusinessEntityID, P.FirstName, P.LastName, E.EmailAddress, PH.PhoneNumber
FROM AdventureWorks2019.Sales.SalesPerson SP
JOIN AdventureWorks2019.Person.Person P ON SP.BusinessEntityID = P.BusinessEntityID
JOIN AdventureWorks2019.Person.EmailAddress E ON P.BusinessEntityID = E.BusinessEntityID
JOIN AdventureWorks2019.Person.PersonPhone PH ON P.BusinessEntityID = PH.BusinessEntityID
ORDER BY SP.SalesYTD DESC;
******************************************************************************************************************/
--INCREASED COMPLEXITY QUESTIONS--

-- Q5:I have noticed that on the website when I am trying to purchase items and am noticing that some items have been placed in several different sections. 
If you can put together a list of each item and where they are located so we can put the products back in their correct spot.
-- A5: To retrieve a list of each item and their respective locations from the AdventureWorks database using the tables Production.Product, Production.ProductInventory, and Production.Location.
*Author: Matt Hale*

SELECT 
P.ProductID,
P.Name AS ProductName,
L.Name AS LocationName
FROM 
AdventureWorks2019.Production.Product AS P
JOIN 
AdventureWorks2019.Production.ProductInventory AS PI ON P.ProductID = PI.ProductID
JOIN 
AdventureWorks2019.Production.Location AS L ON PI.LocationID = L.LocationID
ORDER BY 
P.ProductID; 


-- Q6:Could you please provide a list with the names, organization levels, and salaries of all our Production Technicians?
-- A6: Obtain columns with the lists of names, organizational levels and salaries from Production table.
*Author Dario Gallardo*

SELECT 
P.ProductID,
P.Name AS ProductName,
L.Name AS LocationName
FROM 
AdventureWorks2019.Production.Product AS P
JOIN 
AdventureWorks2019.Production.ProductInventory AS PI ON P.ProductID = PI.ProductID
JOIN 
AdventureWorks2019.Production.Location AS L ON PI.LocationID = L.LocationID
ORDER BY 
P.ProductID; 
******************************************************************************************************************/
--METADATA QUESTIONS--
-- Q7:Can you create a list of tables in AdventureWorks that contain a column with one of these names: Color or 
-- A7:Create a list of tables that contains columns with the names color or weight
*Author Enzama Norbert

SELECT TABLE_NAME
FROM AdventureWorks2019.INFORMATION_SCHEMA.COLUMNS
WHERE COLUMN_NAME IN ('Color', 'Weight');

-- Q8:How many columns are in the Cryptographic providers?
-- A8:Obtain a table that shows how many colums Cryptographic providers
*Author Judith Escobar*

SELECT GETDATE() AS my_date;
