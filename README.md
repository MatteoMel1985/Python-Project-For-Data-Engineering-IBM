# Hands-on Lab: Acquiring and Processing Information on the World's Largest Banks 

![Skills_Network](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-PY0221EN-Coursera/images/image.png)

## Estimated Time: 60 mins  

In this project, you will put all the skills acquired throughout the course and your knowledge of basic Python to test. You will work on real-world data and perform the operations of Extraction, Transformation, and Loading (ETL) as required.  

### Disclaimer:  

> ***Cloud IDE is not a persistent platform, and you will lose your progress every time you restart this lab. We recommend saving a copy of your file on your local machine as a protective measure against data loss.***

# Project Scenario:  

You have been hired as a data engineer by research organization. Your boss has asked you to create a code that can be used to compile the list of the top 10 largest banks in the world ranked by market capitalization in billion USD. Further, the data needs to be transformed and stored in GBP, EUR and INR as well, in accordance with the exchange rate information that has been made available to you as a CSV file. The processed information table is to be saved locally in a CSV format and as a database table.  

Your job is to create an automated system to generate this information so that the same can be executed in every financial quarter to prepare the report.  

Particulars of the code to be made have been shared below.  

|	Parameter |	Value |
|	--------- |	----- |	
|	Code name |	`banks_project.py` |
|	Data URL  |	<https://web.archive.org/web/20230908091635/https://en.wikipedia.org/wiki/List_of_largest_banks> |
|	Exchange rate CSV path  | 	<https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-PY0221EN-Coursera/labs/v2/exchange_rate.csv>  |
|	Table Attributes (upon Extraction only) |	`Name`, `MC_USD_Billion`  |
|	Table Attributes (final) |	`Name`, `MC_USD_Billion`, `MC_GBP_Billion`, `MC_EUR_Billion`, `MC_INR_Billion` |
|	Output CSV Path  |	`./Largest_banks_data.csv` |
|	Database name |	`Banks.db` |
|	Table name  |	`Largest_banks` |
|	Log file  |	`code_log.txt` |  

# Project tasks  

## **Task 1:**  

Write a function `log_progress()` to log the progress of the code at different stages in a file `code_log.txt.` Use the list of log points provided to create log entries as every stage of the code.  

## **Task 2:**  

Extract the tabular information from the given URL under the heading 'By market capitalization' and save it to a dataframe.  
a. Inspect the webpage and identify the position and pattern of the tabular information in the HTML code  
b. Write the code for a function `extract()` to perform the required data extraction.  
c. Execute a function call to `extract()` to verify the output.  


## **Task 3:** 

Transform the dataframe by adding columns for Market Capitalization in GBP, EUR and INR, rounded to 2 decimal places, based on the exchange rate information shared as a CSV file.  
a. Write the code for a function `transform()` to perform the said task.
b. Execute a function call to `transform()` and verify the output.  

## **Task 4:** 

Load the transformed dataframe to an output CSV file. Write a function `load_to_csv()`, execute a function call and verify the output.  

## **Task 5:** 

Load the transformed dataframe to an SQL database server as a table. Write a function `load_to_db()`, execute a function call and verify the output.  

## **Task 6:** 

Run queries on the database table. Write a function `run_queries()`, execute a given set of queries and verify the output.  

## **Task 7:** 

Verify that the log entries have been completed at all stages by checking the contents of the file `code_log.txt`. 

# Preliminaries: Installing libraries and downloading data  

Before building the code, you need to install the required libraries.

The libraries needed for the code are:  

`requests` - The library used for accessing the information from the URL.  

`bs4` - The library containing the BeautifulSoup function used for webscraping.  

`pandas` - The library used for processing the extracted data, storing it in required formats, and communicating with the databases.  

`sqlite3` - The library required to create a database server connection.  

`numpy` - The library required for the mathematical rounding operations.  

`datetime` - The library containing the function datetime used for extracting the timestamp for logging purposes.  

Install the required libraries from the terminal window. The command syntax is:  

```python
python3.11 -m pip install <library_name>
```

Also, download the required exchange rate file using the terminal command:  

```python
wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-PY0221EN-Coursera/labs/v2/exchange_rate.csv
```

# Code Structure  

Create the file `banks_project.py` in the path `\home\project\`. Copy and paste the following code structure to the file:

```python
# Code for ETL operations on Country-GDP data

# Importing the required libraries

def log_progress(message):
    ''' This function logs the mentioned message of a given stage of the
    code execution to a log file. Function returns nothing'''

def extract(url, table_attribs):
    ''' This function aims to extract the required
    information from the website and save it to a data frame. The
    function returns the data frame for further processing. '''

    return df

def transform(df, csv_path):
    ''' This function accesses the CSV file for exchange rate
    information, and adds three columns to the data frame, each
    containing the transformed version of Market Cap column to
    respective currencies'''

    return df

def load_to_csv(df, output_path):
    ''' This function saves the final data frame as a CSV file in
    the provided path. Function returns nothing.'''

def load_to_db(df, sql_connection, table_name):
    ''' This function saves the final data frame to a database
    table with the provided name. Function returns nothing.'''

def run_query(query_statement, sql_connection):
    ''' This function runs the query on the database table and
    prints the output on the terminal. Function returns nothing. '''

''' Here, you define the required entities and call the relevant
functions in the correct order to complete the project. Note that this
portion is not inside any function.'''
```

At this stage, import the required libraries at the space mentioned in the code structure. Save the file using `Ctrl+S`.  

Also, initialize all the known variables as shared in the project scenario.  

# Task 1: Logging function

Write the function to log the progress of the code, `log_progress()`. The function accepts the message to be logged and enters it to a text file `code_log.txt`.  

The format to be used for logging must have the syntax:  

```python
<time_stamp> : <message>
```

Each log entry must happen in the next line in the text file.  

You must associate the correct log entries with each of the executed function calls. Use the following table to note the logging message at the end of each function call that follows.  

Task |	Log message on completion |
---- | -------------- |
Declaring known values | Preliminaries complete. Initiating ETL process |
Call extract() function | Data extraction complete. Initiating Transformation process |
Call transform() function |	Data transformation complete. Initiating Loading process |
Call load_to_csv() | Data saved to CSV file |
Initiate SQLite3 connection | SQL Connection initiated |
Call load_to_db() | Data loaded to Database as a table, Executing queries |
Call run_query() | Process Complete |
Close SQLite3 connection | Server Connection closed |

At this stage, you should now make the first log entry from the table above.  

### Peer graded assignment prompt:

Take a screenshot of the code, as created for the `log_progress()` function and save it to your local machine as `Task_1_log_function.png`
