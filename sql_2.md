# Clauses
### 1. Distinct  
- Avoid duplicate records from a table  
- retrieves only unique values
- Example :
  SELECT DISTINCT name FROM books;
  
  > The above statment will retrieve only unique entries/records from the table and avoid the duplicate name of books.   

### 2. GROUP BY  
- Groups rows with the same values in specified column(s).  
- Used with aggregate functions (COUNT(), SUM(), AVG(), MAX(), MIN()).  
- Returns one result for each group.
- Example 1:-
  SELECT name, COUNT(*)  
  FROM books  
  GROUP BY name  

- Example 2:-
  SELECT category, SUM(amount)
  FROM hacking_tools,  
  GROUP by category

> This statment will group the list of tools by category {some tools are of same category} and aggregate the amount of tools which belongs to same category.

