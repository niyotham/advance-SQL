# advance-SQL
Contained course material about advance MySQL function.

## Exercises


### USING ROW_NUMBER() FUNCTION
#### Exercise #1 :
Write a query that upon execution, assigns a row number to all managers we have information for in the "employees" database (regardless of their department).

Let the numbering disregard the department the managers have worked in. Also, let it start from the value of 1. Assign that value to the manager with the lowest employee number.

 
``` sql
# The ROW_NUMBER() Ranking Window Functions - Solution

# Solution #1:

SELECT

    emp_no,

    dept_no,

    ROW_NUMBER() OVER (ORDER BY emp_no) AS row_num

FROM

dept_manager;


```

#### Exercise #2:

Write a query that upon execution, assigns a sequential number for each employee number registered in the "employees" table. Partition the data by the employee's first name and order it by their last name in ascending order (for each partition).


``` sql
# Solution #2:

SELECT

emp_no,

first_name,

last_name,

ROW_NUMBER() OVER (PARTITION BY first_name ORDER BY last_name) AS row_num

FROM

employees;


```

### USING  SEVERALL WINDOWE FUNCTIONS

#### Exercise #1:

Obtain a result set containing the salary values each manager has signed a contract for. To obtain the data, refer to the "employees" database.

Use window functions to add the following two columns to the final output:

- a column containing the row number of each row from the obtained dataset, starting from 1.

- a column containing the sequential row numbers associated to the rows for each manager, where their highest salary has been given a number equal to the number of rows in the given partition, and their lowest - the number 1.

Finally, while presenting the output, make sure that the data has been ordered by the values in the first of the row number columns, and then by the salary values for each partition in ascending order.

 

#### Exercise #2:

Obtain a result set containing the salary values each manager has signed a contract for. To obtain the data, refer to the "employees" database.

Use window functions to add the following two columns to the final output:

- a column containing the row numbers associated to each manager, where their highest salary has been given a number equal to the number of rows in the given partition, and their lowest - the number 1.

- a column containing the row numbers associated to each manager, where their highest salary has been given the number of 1, and the lowest - a value equal to the number of rows in the given partition.

Let your output be ordered by the salary values associated to each manager in descending order.

Hint: Please note that you don't need to use an ORDER BY clause in your SELECT statement to retrieve the desired output.



