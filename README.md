**Winter 2020 Data Science Internship Challenge Answer **

_Prepared by Sivasankar S_

**Question 1: **

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

**Question:2**

_a. How many orders were shipped by Speedy Express in total?_

Answer:

	**54**

SQL Query:

	

	SELECT COUNT(ShipperName)

FROM Orders

JOIN Shippers ON Shippers.ShipperID = Orders.ShipperID

WHERE ShipperName = 'Speedy Express'

_b. What is the last name of the employee with the most orders?_

Answer:

	**Peacock**

SQL Query:

	SELECT Employees.LastName, COUNT(*)AS Most

FROM Orders

JOIN Employees ON Employees.EmployeeID = Orders.EmployeeID

GROUP BY LastName ORDER BY Most DESC 

_c.. What product was ordered the most by customers in Germany?_

Answer: 

**Gorgonzola Telino**

SQL Query:

	SELECT Products.ProductName, COUNT(*)AS Total

FROM Customers

JOIN Orders ON Orders.CustomerID = Customers.CustomerID 

JOIN OrderDetails ON OrderDetails.OrderID = Orders.OrderID

JOIN Products ON Products.ProductID = OrderDetails.ProductID

WHERE Country = 'Germany'

GROUP BY Products.ProductName ORDER BY Total DESC
