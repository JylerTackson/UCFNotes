To learn SQL, Kaggle teaches you using BigQuery, a web service that lets you apply SQL to huge datasets.
```python
#import BigQuery client library
from google.cloud import bigquery

# Create a BigQuery client object
client = bigquery.Client()
```
- Begin by importing BigQuery from the `Google.Cloud` Package. To actually Access BigQuery you will need to authenticate your script with a google Application Default Credentials (ADC) but I am not getting into that today.
- After importing the BigQuery library you will then create an instance of the `bigquery.Client()` object.
#### Datasets
In **BigQuery**, each dataset is contained in a corresponding "**project**". To access the dataset
1) We begin by constructing a reference.
2) Next we use the `get_dataset()` method, along with the reference.
```python
#Construct the reference
    #hacker_news is the dataset name
    #bigquery-public-data is the project name
dataset_ref = client.dataset("hacker_news", project="bigquery-public-data")

#API request to fetch the dataset using the reference
dataset = client.get_dataset(dataset_ref)
```
#### Tables
Datasets are a **collection of tables** where a table can be thought of as an excel sheet.
- When accessing the tables within the dataset you can use the `list_tables()` to return a list of the tables within the dataset
```python
#List all the tables in the referenced dataset
tables = list(client.list_tables(dataset))

#Print names of all tables
for table in tables:
	print(table.table_id)
```

The above for loop will print the names, a.k.a the table ID's, for all the tables held within the dataset. We can then use the `table` method within out dataset reference to create create a table reference and use the `get_table` method to create an instance of our table.
```python
# Construct a reference to the table
table_ref = dataset_ref.table("specific_table_id")

#API request to fetch the table using the table reference
table = client.get_table(table_ref)
```
![[Pasted image 20251208191811.png]]

#### Schemas
Every table is structured into **schemas**. In order to effectively use the information within the table you must understand how the schema of the table is setup.

To access the schema of the table you created an instance of you use the `schema` property which contains a list of all the **SchemaField objects** within the table. 
```python
#Print infromation on all the columns in the table of your dataset
table.schema
```
The SchemaField objects are a 4-tuple that tells us information about the specific columns such as:
- Name
- Data type
- Mode (allowing `NULL` values or not)
- Description

Furthermore, when trying to **look at the data** held within the table we can use the `list_rows()` method. This method returns a BigQuery `RowIterator` object that can be converted to a pandas Data Frame with the `to_dataframe()` method as follows:
```python
client.list_rows(table, selected_fields=table.schema[:1], max_results=(num of rows)).to_dataframe()
```

### Summary:
**BigQuery Basics (Kaggle SQL Intro)**
- Use **BigQuery** to run SQL on large datasets. Start by importing `google.cloud.bigquery` and creating a `bigquery.Client()` object.
- Datasets live inside **projects**. Access one by creating a dataset reference and calling `get_dataset()`.
- A dataset contains **tables**. Use `list_tables()` to view them, and create a table reference with `dataset_ref.table()` followed by `get_table()`.
- Each table has a **schema**, accessible through `table.schema`, which lists `SchemaField` objects describing column name, type, mode, and description.
- View table data using `list_rows()`, which returns a `RowIterator`; convert it to a DataFrame with `.to_dataframe()`.
---

Now that we are able to access and examine a dataset, we will begin using SQL queries to further sort through these datasets. In this section we will use the keywords **SELECT**, **FROM**, and **WHERE**. 

#### SELECT ... FROM
The most basic SQL query selects a single column from a single table:
- specify the column you want after the word **SELECT**
- specify the table after the word **FROM**
```sql
SELECT ColumnName
FROM bigquery-public-data.pet_records.pets
```

#### WHERE
Usually you want to return only the rows meeting specific conditions within your table:
- specify a condition to return only specific rows using **WHERE**
```sql
SELECT Name
FROM bigquery-public-data.pet_records.pets
WHERE Animal='Cat'
```

#### Queries
After building your client object you are now ready to start submitting queries to your BigQuery client object using the **query method**.
```python
#Create a "Client" object
client = bigquery.Client()

#Define your query
query = """
        SELECT city
        FROM `bigquery-public-data.openaq.global_air_quality`
        WHERE country = 'US'
        """

#Set up the query
query_job = client.query(query)

#Convert query results to pandas dataframe
us_cities = query_job.to_dataframe()
```

To return multiple columns, insert a comma between the names within the SELECT parameters:
```sql
SELECT ColumnName1, ColumnName2, ..., ColumnName(n)
```
 To return all columns, use the `*` argument:
 ```sql
 SELECT *
 ```

#### Query size estimation
Everyone has a 30 day limit of scanning 5TB of data so running several queries can run through this quickly. To avoid running large quires repeatedly you can estimate the size of the query before running.

To estimate the size of any query before running it we create a `QueryJobConfig` object and set the `dry_run` parameter:
```python
#Create a QueryJobConfig object to estiamte size of query without running it
dry_run_config = bigquery.QueryJobConfig(dry_run=True)

#dry run query to estiamte costs
dry_run_query_job = client.query(query, job_config=dry_run_config)

print("This query will process {} bytes.".format(dry_run_query_job.total_bytes_processed))
```
This will output the total number of bytes that will be processed by the query.

This can allow us to limit the size of a single query to ensure we are using a safe amount for each query. By configuring the `query.Job.Config` method within the BigQuery library we are able to set the amount of billable bytes we are allowed to process.
```python
#Setting the query to only run if its < 1MB
ONE_MEGABYTE = 1000*1000
safe_config = bigquery.QueryJobConfig(maximum_bytes_billed=ONE_MB)

#Set up the query
safe_query_job = client.query(query, job_config = safe_config)

#try to run the query and return a pandas df
safe_query_job.todataframe()
```

### Summary:
This section introduces basic SQL querying in BigQuery.

- Use **SELECT** to choose columns and **FROM** to specify the table.
- Use **WHERE** to filter rows based on conditions.
- Queries are submitted through a BigQuery **Client** object using the `query()` method, and results can be converted to a pandas Data Frame.
- Multiple columns can be selected with commas, or all columns with `*`.
- Because BigQuery has a data-scanning limit, you can estimate query size beforehand using a `QueryJobConfig` with `dry_run=True`.
- You can also control costs by setting a maximum number of billable bytes in `QueryJobConfig` so the query only runs if it stays within a safe data limit.

---

Now that we are able to select raw data based on criteria its important to be able to group the data and count the items within the group.

#### COUNT()
`COUNT` is an example of an aggregate function, which takes many values and returns one, more example include **SUM(), AVG(), MIN()**, and **MAX()**.
```sql
SELECT COUNT(ID)
FROM 'bigquery-public-dat.pet_records.pets'
```
This specific query returns the count of rows within the table ID parsed into the COUNT function.

#### GROUP BY
The `GROUP BY` function takes the name of one or more columns and treats all rows with the same value in that column as a single **group** when applying an aggregate function on to them.
![[Pasted image 20251209161432.png]]
The above query shows that we are able to `GROUP BY 'Animaul'` for and then aggregate to count the amount of Distinct animals within the dataset.
#### GROUP BY ... HAVING
The `HAVING` function is used in combination with the `GROUP BY` function to ignore groups that don't meet certain criteria. For example:
```sql
SELECT Animaul, COUNT(ID)
FROM 'bigquery-public-data.pet_records.pets'
GROUP BY Animal
HAVING COUNT(ID)>1
```
In the above query, we are using the `HAVING` function to only return **animal groups** that have a **count of** $>1$. **You cannot GROUP BY an aggregate result** (like `COUNT(1)`), because **GROUP BY is evaluated _before_ aggregates are computed**.

##### Aliasing (AS)
If we are trying to Aggregate the data, or just alias the responses, we can use the **AS** function within our SELECT line:
```sql
SELECT Column, COUNT(1) AS ColumnAlias
```
This will return a column with our results however the column name will be set as `ColumnAlias`

### Summary
This section explains how to aggregate and group data in SQL.
- **COUNT()** is an aggregate function that returns how many rows match a condition.
- **GROUP BY** groups rows with the same column value so aggregates apply to each group.
- **HAVING** filters groups _after_ aggregation, such as keeping only groups where `COUNT(ID) > 1`.
- You cannot group by an aggregate value because grouping happens before aggregates are computed.
- Use **AS** to rename output columns when applying aggregates (e.g., `COUNT(1) AS CountAlias`).

---

Now we will learn how to order our results, like applying a filter within excel, by using the `ORDER BY` function. 

#### ORDER BY
This clause is generally the **last clause within the query**, sorting the results returned by the query.
```sql
SELECT ID, Name, Animal
FROM `database.project.table`
ORDER BY ID
```
This clause works on all forms of datatypes as well as being able to order in descending by using the `DESC` keyword.

#### DATES
Within BigQuery, there are two ways dates are stored:
1) **DATE**
```
YYYY-[M]M-[D]D
```
2) **DATETIME**
```
YYYY-[M]M-[D]D-00:00
```
It is important to know this format for the following clause

#### EXTRACT
The `EXTRACT` clause will allow you to look at part of a date without pulling the other unneeded data. For example:
```sql
SELECT Name, EXTRACT(DAY from Date) AS DAY
FROM `database.project.table`
```
The above query returns a column where the `EXTRACT` clause pulls only the day from each date column for each row.

---

#### WITH ... AS
A **"Common Table Expression"** **(CTE)** is a temporary table that you return within your query that are helpful for splitting your queries into readable chunks. For example we can write a CTE for a pets data table as follows:
```sql
WITH alias AS
(
	SELECT ID, Name
	FROM `dataset.project.table`
	WHERE Condition
)
SELECT ID
FROM alias
```
This query creates a CTE for the specific condition provided, then you are able to reference that table using the alias provided to it.

---

#### JOINING DATA
If the data you want is spread across multiple tables you can use the `JOIN` command. This is where the idea of **Primary and Foreign Keys** come in to play. **Primary Keys**, such as the ID column in the pets table below, are the primary identifier for each row in the table and are unique for each row. Meanwhile, **Foreign Keys** are non-unique identifiers for these items that are housed on a foreign table, for example the `Pet_ID` within the owners table. This is how we are able to link items between tables.
![[Pasted image 20251209201858.png]]

