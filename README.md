# Simple Pyscopg2 Project

Simple project to demonstrate the use of *Psycopg2*, a popular PostgreSQL adapter for the Python programming language.

### Core Functionality
*Database Connectivity*: Use psycopg2 to establish and manage connections to a PostgreSQL database from a Python application. The primary entry point is the psycopg2.connect() function.

*Executing SQL*: Execute arbitrary SQL commands—such as SELECT, INSERT, UPDATE, DELETE, and DDL statements (CREATE TABLE, etc.)—using cursor.execute().

*Transaction Management*: psycopg2 handles database transactions.

Call connection.commit() after data modification (e.g., INSERT, UPDATE, DELETE) to make the changes permanent.

Call connection.rollback() to discard changes in case of an error or undesirable state.

Fetching Results: Retrieve query results (from SELECT statements) using cursor methods like:

'''python
cursor.fetchone(): #Retrieves a single row.
cursor.fetchall(): #Retrieves all remaining rows as a list of tuples.
cursor.fetchmany(size): #Retrieves a specified number of rows.
'''

###Security and Best Practices
Prevent SQL Injection: Always use parameterized queries (also known as placeholders) for passing variable data to SQL commands. Never format SQL strings directly with user input. Use %s as the placeholder in the SQL string, and pass the values as a separate tuple to cursor.execute().

Example: cursor.execute("INSERT INTO users (name, email) VALUES (%s, %s);", (user_name, user_email))

Context Managers: Utilize Python's with statement for managing connections and cursors to ensure they are properly closed and resources are released, even if errors occur. This handles cleanup automatically.

Example: with psycopg2.connect(dsn) as conn: with conn.cursor() as cur: ...

You can read more about [Pscyopg2](https://github.com/psycopg/psycopg2) from its main repository page on github.

