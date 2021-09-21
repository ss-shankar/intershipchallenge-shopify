# Winter 2020 Data Science Internship Challenge Answer

<div align="center"> Prepared by Sivasankar S </div>

## Question 1: 

After analysing the dataset, I can find outliers. So I removed outliers using IQR Method. Then grouped the dataset by shop_id and user_id to find the average revenue per shop and average revenue per user.

a. Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 

Answer: 
There are **outliers** in the Dataset which is affecting the calculation. Removing outliers from the dataset will be a better way to evaluate.
	

b. What metric would you report for this dataset?

Answer:



1. Average Order Value
2. Average Value Per Item
3. Average Revenue Per Shop
4. Average Revenue Per User

c. What is its value?

Answer:



1. Average Order Value: $ 300.16
2. Average Value Per Item: $ 150.40
3. Average Revenue Per Shop: $ 15016.98
4. Average Revenue Per User: $ 4905.55

**Github Link:** [Challenge Solution Colab Link](https://github.com/ss-shankar/intershipchallenge-shopify/blob/main/Data_Science_Intern_Challenge.ipynb)

## Question:2 

_a. How many orders were shipped by Speedy Express in total?_

Answer:
**54**
	

SQL Query:

SELECT COUNT(ShipperName)<br/>
FROM Orders<br/>
JOIN Shippers ON Shippers.ShipperID = Orders.ShipperID<br/>
WHERE ShipperName = 'Speedy Express'<br/>


b. What is the last name of the employee with the most orders?

Answer:
**Peacock**
	

SQL Query:

SELECT Employees.LastName, COUNT(*)AS Most<br/>
FROM Orders<br/>
JOIN Employees ON Employees.EmployeeID = Orders.EmployeeID<br/>
GROUP BY LastName ORDER BY Most DESC <br/>


c. What product was ordered the most by customers in Germany?

Answer: 
**Gorgonzola Telino**

SQL Query:

SELECT Products.ProductName, COUNT(*)AS Total<br/>
FROM Customers<br/>
JOIN Orders ON Orders.CustomerID = Customers.CustomerID <br/>
JOIN OrderDetails ON OrderDetails.OrderID = Orders.OrderID<br/>
JOIN Products ON Products.ProductID = OrderDetails.ProductID<br/>
WHERE Country = 'Germany'<br/>
GROUP BY Products.ProductName ORDER BY Total DESC<br/>
