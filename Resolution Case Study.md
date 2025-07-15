python3.11 -m pip install bs4# Preliminaries: Installing libraries and downloading data   

The preliminary requirements of the exam are the following:  

“*Before building the code, you need to install the required libraries.*  

*The libraries needed for the code are:*  

*`requests` - The library used for accessing the information from the URL.*  

*`bs4` - The library containing the BeautifulSoup function used for webscraping.*  

*`pandas` - The library used for processing the extracted data, storing it in required formats, and communicating with the databases.*  

*`sqlite3` - The library required to create a database server connection.*  

*`numpy` - The library required for the mathematical rounding operations.*  

*`datetime` - The library containing the function datetime used for extracting the timestamp for logging purposes.*”  

Based on such instruction, we must start our code with the following lines.  

```python
from bs4 import BeautifulSoup
import requests
import pandas as pd
import numpy as np
import sqlite3
from datetime import datetime
```  

To install these libraries, in case the EDI does not show a launching terminal at the bottom of the page, we must click on “Terminal” in the Title Bar, at the top of the screen, and select “New Terminal”.  

![Screenshot_1](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Screenshot%201.JPG?raw=true)  

Ensure that the terminal shows the following directory path:  

`home/project`  

![Screenshot_2](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Screenshot%202.JPG?raw=true)  

In case your path is set differently, you can navigate through folders by using the `cd` code, which stands for "change directory".  

If you want to add a child folder, you can type "cd" plus the name folder name.

```python
cd "folder name"
```

On the contrary, if you want to go one level up to the parent folder, you should write the following command.

```python
cd ..
```

`cd` stands for "change directory", whereas `..` stands for "parent directory".   

To install the libraries, type the following 3 lines on the terminal. The first will do the Pandas.  

```python
python3.11 -m pip install pandas
```  

Wait until you see these lines appearing on the termina.

`Installing collected packages: numpy, pandas`  
`Successfully installed numpy-2.3.1 pandas-2.3.0`  

![Screenshot_3](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Screenshot%203.JPG?raw=true)  

Note that the command `python3.11` may vary according to your version of Python.  

We will proceed by installing the Numpy, the libary required for the mathematical rounding operation, by launcing the following code.  

```python
python3.11 -m pip install numpy
```

Wait until the terminal confirms its full installation.  

Finally, we will proceed by installing bs4. the library containing the function used for webscraping.  

```python
python3.11 -m pip install bs4
```

Wait until the terminal shows `Successfully installed bs4-0.0.2`.  

In conclusion, we must download the exchange rate file. To do so, the following code must be launched from the terminal.  

```
wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMSkillsNetwork-PY0221EN-Coursera/labs/v2/exchange_rate.csv
```

Once the process is completed, we will be able to see the file `exchange_rate.csv` in the Explorer Menu of the EDI, under the "project" folder.  

![Screenshot_4](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Screenshot%204.JPG?raw=true)  

# Code Structure  

To create the file `banks_project.py` in the path `\home\project\`, we must click on the "Explore" icon on the left pane, select the folder "project", right click below it and select "New File"

![Screenshot_5](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Screenshot%205.JPG?raw=true)  

Once the window is open, we must type `banks_project.py`and click on OK.  

![Screenshot_6](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Screenshot%206.JPG?raw=true)  

The file `banks_project.py`will appear in the project folder, and it will automatically open in the text editor pane. In case it does not appear, double-click the `banks_project.py`icon in the project folder.  

![Screenshot_7](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Screenshot%207.JPG?raw=true)  

There, on line number 1, we must paste the code structure provided, which is the following.

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

Once done, the text editor pane will appear as follows.  

![Screenshot_8](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Screenshot%208.JPG?raw=true)  

Save the file by digiting the combination `Ctrl+S`.  

# Task 1: Logging function  

Task 1 of this exam requires us to write a `log_progress() function` that accepts the message to be logged and enters it to a text file called `code_log.txt`.   
The format requested for the logging must have the following syntax:  

```python
<time_stamp> : <message>
```  

The following entries must all be logged in the text file, and they have to be correctly associated with all the executed function calls; the messages provided in the right column must be written in the file.   
 
| Task	| Log message on completion |
| ----- | ------------------------- |
| Declaring known values |	Preliminaries complete. Initiating ETL process |
| Call extract() function |	Data extraction complete. Initiating Transformation process |
| Call transform() function |	Data transformation complete. Initiating Loading process |
| Call load_to_csv() |	Data saved to CSV file |
| Initiate SQLite3 connection |	SQL Connection initiated |
| Call load_to_db()	| Data loaded to Database as a table, Executing queries |
| Call run_query()	| Process Complete |
| Close SQLite3 connection |	Server Connection closed |  

In the end, we are requested to take a screenshot of the `log_progress()` function and save it as `Task_1_log_function.png`.  

To this end, I wrote the following function, which will be the first in our code structure.

```python
def log_progress(message):
    ''' This function logs the mentioned message of a given stage of the
    code execution to a log file. Function returns nothing'''
    timestamp_format = '%Y-%h-%d-%H:%M:%S' # Year-Monthname-Day-Hour-Minute-Second
    now = datetime.now() # get current timestamp
    timestamp = now.strftime(timestamp_format)
    with open("code_log.txt","a") as f:
        f.write(timestamp + ' : ' + message + '\n')
```  

The `log_progress` function takes one parameter, called `message`, and creates a docstring, which is a set of comments describing the current stage of the ETL.  

The `timestamp_format` string, appearing as `'%Y-%h-%d-%H:%M:%S'`, describes the format in which the time will be written in the log file. `Y` stands for year, `h` for month name, `d`  for day, `H`  for hour, `M` for minute, and finally, `S` for second. 

The line  

```python
now = datetime.now()  # get current timestamp
```  
gets the current date and time as a `datetime` object using the Python built-in `datetime` module.  

The line 

```python
timestamp = now.strftime(timestamp_format)
```

Converts the `datetime` object `now` into a formatted string according to the earlier `timestamp_format`.

The line  

```python
with open("code_log.txt","a") as f:
        f.write(timestamp + ' : ' + message + '\n')
```

Performs the following actions:

1. It opens the file named `code_log.txt` in append mode (appearing as `"a"` between parentheses).
2. If the file does not exist, Python will create it.
3. If the file exists, new log entries are added to the end of the file — previous content is not overwritten.
4. `with` is a context manager, which ensures the file is automatically closed after the block is executed, even if an error occurs.
5. `f` is a file handle used to interact with the file.
6. `f.write(timestamp + ' : ' + message + '\n')` writes one line in the `code_log.txt` file, which includes:
    - The formatted timestamp
    - A column (`:`) and space
    - The custom message passed to the function
    - A newline character `\n` so each log entry appears on its own line.

Following is an example of line in the log file:  

```
2025-Jul-04-14:35:08 : Data extraction complete. Initiating Transformation process
```

The requested `Task_1_log_function.png` screenshot will appear as follows. 

![Task_1](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Task_1_log_function.png?raw=true)  

Note that the function calls must be written at the end of the code and will appear as follows. We will see their meaning in-depth once all functions are defined and explained. 

```python
''' Here, you define the required entities and call the relevant
functions in the correct order to complete the project. Note that this
portion is not inside any function.'''


# Declaring known values


url = "https://web.archive.org/web/20230908091635/https://en.wikipedia.org/wiki/List_of_largest_banks"
csv_path = "./exchange_rate.csv"
table_attribs = ["Name", "MC_USD_Billion"]
output_path = "./Largest_banks_data.csv"
db_name = "Banks.db"
table_name = "Largest_banks"
log_file = "./code_log.txt"


log_progress("Preliminaries complete. Initiating ETL process")


# Call extract() function
df = extract(url, table_attribs)
print(df)


log_progress("Data extraction complete. Initiating Transformation process")


# Call transform() function
df = transform(df, csv_path)
print(df)


log_progress("Data transformation complete. Initiating Loading process")


# Call load_to_csv()
load_to_csv(df, output_path)


log_progress("Data saved to CSV file")


# Initiate SQLite3 connection
sql_connection = sqlite3.connect(db_name)


log_progress("SQL Connection initiated")


# Call load_to_db()
load_to_db(df, sql_connection, table_name)


log_progress("Data loaded to Database as a table, Executing queries")


# Call run_query()
# 1. Print the contents of the entire table
query_statement = f"SELECT * from {table_name}"
run_query(query_statement, sql_connection)


# 2. Print the average market capitalization of all the banks in Billion GBP
query_statement = f"SELECT AVG(MC_GBP_Billion) FROM {table_name}"
run_query(query_statement, sql_connection)


# 3. Print only the names of the top 5 banks
query_statement = f"SELECT Name from {table_name} LIMIT 5"
run_query(query_statement, sql_connection)


log_progress("Process Complete")


# Close SQLite3 connection
sql_connection.close()


log_progress("Server Connection closed")


# Task 7: Verify log entries
with open(log_file, "r") as log:
    LogContent = log.read()
    print(LogContent)
```

# Task 2: Extraction of data  

Analyse the webpage on the given URL:  

<https://web.archive.org/web/20230908091635/https://en.wikipedia.org/wiki/List_of_largest_banks>  

As we are required to identify the position of the table under the heading `By market capitalization`, which is immediately visible on the central part of the screen, right-click on any point of the table, and select “inspect”, as shown in the following screenshot.  

![Screenshot_9](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Screenshot%209.JPG?raw=true)  

On the right side of the screen, the list of HTML codes composing the page will appear. By moving the mouse pointer on them, the different corresponding parts of the table will be automatically highlighted.  

In the whole code, we must first identify the following element string:  

```HTML
<table class="wikitable sortable mw-collapsible jquery-tablesorter mw-made-collapsible">
```   

That represents the start of a table in an HTML document; being the first, it refers to the one under the heading `By market capitalization`, which is what we are required to analyse.  

If we collapse it, we will observe two further objects, respectively named `<thead>`, representing the start tag of the table heading, and `<tbody>`, which is the start tag of the table’s body.  

By collapsing the latter, we will notice that all the rows are mentioned as `tr` objects in the code.  

As we are required to take a screenshot of the HTML code, as obtained by inspecting the page, ensuring that the contents of at least the first row of the table are visible, we can save the following image as `Task_2a_extract.png`.  

![Screenshot_10](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Screenshot%2010.JPG?raw=true)  

The second part of Task 2 requires us to take a screenshot of the code as created for the `extract()` function, and save it on the local machine as `Task_2b_extract.png`. In the instructions, we are reminded to remove the last character from the `Market Cap` column contents, like `'\n'`, and to typecast the value to float format. 
The screenshot and code are shown below; they will be further commented in depth in the following lines of this case study. 

![Task_2b](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Task_2b_extract.PNG?raw=true)  

```Python
def extract(url, table_attribs):
    ''' This function aims to extract the required
    information from the website and save it to a data frame. The
    function returns the data frame for further processing. '''

    page = requests.get(url).text
    data = BeautifulSoup(page,'html.parser')
    df = pd.DataFrame(columns=table_attribs)
    tables = data.find_all('tbody')
    rows = tables[0].find_all('tr')
    for row in rows:
        col = row.find_all('td')
        if len(col)!=0:
            data_dict = {"Name": col[1].find_all("a")[1]["title"],
                         "MC_USD_Billion": float(col[2].contents[0][:-1])}
            df1 = pd.DataFrame(data_dict, index=[0])
            df = pd.concat([df, df1], ignore_index=True)
    return df
```

## Function Definition and Docstring  

```Python
def extract(url, table_attribs):
    ''' This function aims to extract the required
    information from the website and save it to a data frame. The
    function returns the data frame for further processing. '''
```

`def extract(url, table_attribs)` defines a function named extract that takes two arguments:  

`url`: the webpage URL where the data is located.  

`table_attribs`: a list of column names for the resulting DataFrame (e.g., ["Name", "MC_USD_Billion"]).  

Finally, the docstring below provides a literal explanation of the function’s purpose.  

## Requesting the Web Page  

```Python
    page = requests.get(url).text
```

`requests.get(url)`: Sends an HTTP GET request to the given URL.  

`.text`: Retrieves the raw HTML content of the page as a string.  

`page`: now contains the full HTML content of the Wikipedia page.  

## Parsing the HTML with BeautifulSoup  

```Python
    data = BeautifulSoup(page, 'html.parser')
```

`BeautifulSoup(page, 'html.parser')`: Parses the HTML using Python’s built-in html.parser.

`data`: is now a BeautifulSoup object — a structured tree-like representation of the HTML, making it easier to navigate and search.

## Create Empty DataFrame with Desired Columns  

```Python
    df = pd.DataFrame(columns=table_attribs)
```

Initializes an empty DataFrame with columns defined by table_attribs (like ["Name", "MC_USD_Billion"]).  

This is where we’ll store the extracted data.  

## Locate All Table Bodies (`<tbody>` Tags)  

```Python
    tables = data.find_all('tbody')
```

`data.find_all('tbody')`: Finds all <tbody> tags in the HTML.

`tables`: is a list of all <tbody> elements (which contain rows of tables).  

## Extract All the Table Rows from the First Table  

```Python
    rows = tables[0].find_all('tr')
```

`tables[0]`: selects the first `<tbody>`.

`.find_all('tr')`: finds all <tr> elements (table rows) inside it.

`rows`: is now a list of all rows in the first table.  

## Loop Through the Table Rows  

```Python
    for row in rows:
        col = row.find_all('td')
```

Iterates over each `row` in the table.  

`row.find_all('td')`: Gets all <td> elements (table data cells).  

`col`: is a list of columns in the row.  

## Filter Out Non-Data Rows  

```Python
        if len(col)!=0:
```

Skips rows that don’t contain any `<td>` (like header rows that use `<th>`).  

Only processes rows with actual data.  

## Extract and Format the Data from Columns  

```Python
            data_dict = {"Name": col[1].find_all("a")[1]["title"],
                         "MC_USD_Billion": float(col[2].contents[0][:-1])}
```

This string is specifically devised to parse nested tags.  

`col[1].find_all("a")[1]["title"]`

* `col[1]`: This is the second column in the row, typically containing the bank name.  

* `.find_all("a")`: Finds all <a> tags (links) inside it.  

* `[1]`: Selects the second <a> tag — this is based on inspection of the HTML structure of that specific Wikipedia table.  

* `["title"]`: Extracts the title attribute of that <a> tag (e.g., "JPMorgan Chase").  

`float(col[2].contents[0][:-1])`

* `col[2]`: This is the third column — the Market Cap in USD.  

* `.contents[0]`: Grabs the text inside the cell (e.g., '387.0\n' or '387.0%').  

* `[:-1]`: Removes the last character (likely a newline \n or %).  

* `float(...)`: Converts the string into a floating-point number.

## Add to the Main DataFrame  

```Python
            df1 = pd.DataFrame(data_dict, index=[0])
            df = pd.concat([df, df1], ignore_index=True)
```

`df1`: creates a one-row DataFrame from data_dict.

`pd.concat(...)`: appends df1 to df.

`ignore_index=True`: resets row indexes so they remain continuous.  

## Continue Until All Rows are Parsed  

The loop continues for all rows in `rows`.  

## Return the Final DataFrame  

```Python
    return df
```

Returns the full DataFrame containing extracted bank names and their market capitalisations.  

## Function call for `extract()`  

Finally, we are requested to write the function call for `extract()`. It will be located at the end of the code, and it will allow the machine to show the dataframe with the table and log the first entries.  
Following is the code that will be further explained in depth.   

```Python
''' Here, you define the required entities and call the relevant
functions in the correct order to complete the project. Note that this
portion is not inside any function.'''

# Declaring known values

url = "https://web.archive.org/web/20230908091635/https://en.wikipedia.org/wiki/List_of_largest_banks"
csv_path = "./exchange_rate.csv"
table_attribs = ["Name", "MC_USD_Billion"]
output_path = "./Largest_banks_data.csv"
db_name = "Banks.db"
table_name = "Largest_banks"
log_file = "./code_log.txt"

log_progress("Preliminaries complete. Initiating ETL process")

# Call extract() function
df = extract(url, table_attribs)
print(df)

log_progress("Data extraction complete. Initiating Transformation process")
```

## Purpose of This Section  

This section sets up the environment and runs the ETL pipeline by:  

1. Declaring key variables (file paths, URLs, etc.)  

2. Calling the ETL functions (extract, transform, etc.)  

3. Logging progress for traceability and debugging  

It's not inside any function, but it runs immediately when the script is executed.  

## 1. Declaring Known Values  

```Python
url = "https://web.archive.org/web/20230908091635/https://en.wikipedia.org/wiki/List_of_largest_banks"
```

`url` is the source of the data: a snapshot of a Wikipedia page listing the largest banks.  

Used by the `extract()` function to get the HTML content.  

```Python
csv_path = "./exchange_rate.csv"
```
It declares the local path to a CSV file with the exchange rates (EUR, GBP, and INR).  

Used by the `transform()` function to convert USD market cap to other currencies.  

```Python
table_attribs = ["Name", "MC_USD_Billion"]
```

This string shows the column names for the output DataFrame.  

It is used during the extraction process to initialise and organise the data structure.  

```Python
output_path = "./Largest_banks_data.csv"
```

This declares the `output_path`, or the name of the file where the final transformed data will be saved as a CSV.

Used by `load_to_csv()`.  

```Python
db_name = "Banks.db"
```

`db_name` is the SQLite database file name where the data will be stored.

Used by `load_to_db()` and `run_query()`.  

```Python
table_name = "Largest_banks"
```

It is the name of the database table inside `Banks.db`, where the DataFrame will be loaded.  

```Python
log_file = "./code_log.txt"
```

It declares the name of the log file that records each stage of the process with a timestamp.  

Used inside the `log_progress()` function.  

## 2. Logging Preliminaries  

```Python
log_progress("Preliminaries complete. Initiating ETL process")
```

This records a log entry indicating that the variable declarations are done and the ETL pipeline is starting.  

It helps with tracking and debugging in production workflows.  

## 3. Extracting the Data  

```Python
df = extract(url, table_attribs)
```

Calls the `extract()` function:  

* Fetches the HTML from the Wikipedia URL  

* Parses the table rows using BeautifulSoup  

* Extracts the bank name and market cap  

* Returns a pandas DataFrame

```Python
print(df)
```

It displays the extracted DataFrame in the terminal, which is useful for quick verification during development.  

## 4. Logging Extraction Completion  

```Python
log_progress("Data extraction complete. Initiating Transformation process")
```

It adds another timestamped entry to the log file.

It indicates that extraction was successful, and transformation is next.  

Ultimately, as the function call is now complete, by running the following command in the terminal, we can complete `Task_2c`, which consists of taking a screenshot of the output as obtained in the terminal and saving it as `Task_2c_extract.png`. 

```
python3.11 banks_project.py
```

![Task_2c](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Task_2c_extract.PNG?raw=true)  

# Task 3: Transformation of data  

We are now requested to write a Transform function that performs the following tasks:

1.	Read the exchange CSV file and convert the contents to a dictionary so that the contents of the first columns are the keys to the dictionary and the contents of the second column are the corresponding values.  
<details>
<summary>Hint</summary>
<br>
The following syntax, fine-tuned for our code, can be employed to achieve this end.  
    
```Python 
dict = dataframe.set_index('Col_1_header').to_dict()['Col_2_header']
```
</details>  

2. Add 3 different columns to the dataframe, viz. `MC_GBP_Billion`, `MC_EUR_Billion` and `MC_INR_Billion`, each containing the content of `MC_USD_Billion` scaled by the corresponding exchange rate factor. Remember to round the resulting data to 2 decimal places.  

A sample statement is being provided for adding the `MC_GBP_Billion` column. You can use this to add the other two statements.

   ```Python
   df['MC_GBP_Billion'] = [np.round(x*exchange_rate['GBP'],2) for x in df['MC_USD_Billion']]
   ```  

Finally, to complete this section of the test, we are required to write the function call for `transform()`, take a screenshot of the code, as created for the `transform()` functon, and save it as `Task_3a_transform.png`.  

Furthermore, a snapshot of the output after being run is requested as well, to be saved as `Task_3b_tranform.png`.  

To achieve this end, I wrote the following function, which I will break it down line by line.  

Point 1 and point and point 2 are shown in the documentation comments, and the image below can be used to satisfy the screenshot request named `Task_3a_transform.png`  

![Task_3a](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Task_3a_transform.PNG?raw=true)  

```Python
def transform(df, csv_path):
    ''' This function accesses the CSV file for exchange rate
    information, and adds three columns to the data frame, each
    containing the transformed version of Market Cap column to
    respective currencies'''

        # Read exchange rate CSV file
    exchange_rate = pd.read_csv(csv_path)

    # Convert to a dictionary with "Currency" as keys and "Rate" as values
    exchange_rate = exchange_rate.set_index("Currency").to_dict()["Rate"]

    # columns to dataframe. Round off to two decimals
    df["MC_GBP_Billion"] = [np.round(x * exchange_rate["GBP"], 2) for x in df["MC_USD_Billion"]]
    df["MC_EUR_Billion"] = [np.round(x * exchange_rate["EUR"], 2) for x in df["MC_USD_Billion"]]
    df["MC_INR_Billion"] = [np.round(x * exchange_rate["INR"], 2) for x in df["MC_USD_Billion"]]

    return df
```

## Function Definition and Docstring  

* `def transform(df, csv_path):` *creates a function named transform that expects*
    * `df` – a Pandas DataFrame already containing a column called MC_USD_Billion.
    * `csv_path` – a string or pathlib object pointing to a CSV file of exchange rates (one row per currency).
* **Docstring** (written between " ''' ") – briefly summarises the purpose: read rates, add three new currency columns.

## Read the exchange‑rate CSV  

```Python
    # Read exchange rate CSV file
    exchange_rate = pd.read_csv(csv_path)
```

* `pd.read_csv(csv_path)` – loads the CSV into a DataFrame named `exchange_rate`.

## Convert that DataFrame to a handy dictionary  

```Python
    # Convert to a dictionary with "Currency" as keys and "Rate" as values
    exchange_rate = exchange_rate.set_index("Currency").to_dict()["Rate"]
```

* `set_index("Currency")` – makes the Currency column the row index.
* `to_dict()` – transforms the DataFrame into a nested dict of the form
{'Rate': {'GBP': 0.8, 'EUR': 0.93, 'INR': 82.95}}
* `["Rate"]` – picks out the inner dictionary keyed by Currency.  
Result:  
`exchange_rate = {'GBP': 0.8, 'EUR': 0.93, 'INR': 82.95}`

### *This part of the code satisfies the criteria point 1 of task 3. Let's proceed with point 2.* 

## Add currency‑converted columns  

```Python
    # columns to dataframe. Round off to two decimals
    df["MC_GBP_Billion"] = [np.round(x * exchange_rate["GBP"], 2) for x in df["MC_USD_Billion"]]
    df["MC_EUR_Billion"] = [np.round(x * exchange_rate["EUR"], 2) for x in df["MC_USD_Billion"]]
    df["MC_INR_Billion"] = [np.round(x * exchange_rate["INR"], 2) for x in df["MC_USD_Billion"]]
```

* List comprehensions iterate over every USD market‑cap value (`x`), multiply by the chosen rate, then round to two decimal places with `np.round`.
* Three new columns are created:
    * `MC_GBP_Billion`  
    * `MC_EUR_Billion`  
    * `MC_INR_Billion`  
* `np` assumes you’ve already imported `numpy as np` (and `pandas as pd`), which we have done in the preliminaries.

Finally, before running the program, we are required to write the `transform()` function call, which must be added below the `# Call extract() function`.

```Python
# Call transform() function
df = transform(df, csv_path)
print(df)

log_progress("Data transformation complete. Initiating Loading process")
```

Finally, we can run the program by digiting in the terminal  

```
python3.11 banks_project.py
```

The following is what should appear on the terminal, which can be used as the requested screenshot named `Task_3b_tranform.png`  

![Task_3b](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Task_3b_tranform.PNG?raw=true)  

# Task 4: Loading to CSV  

In Task for of this activity, we are required to write the function to load the transformed data frame to a CSV file, called `load_to_csv()`, in the path mentioned in the project scenario.  

Finally, the peer graded assignment asks us to double-click the created CSV file in the `Explorer` tab on the left ribbon of the programming pane in Cloud IDE, take a snapshot of it on the editor screen screen and save it as `Task_4_CSV.png`.  

This is a fairly easy task, as the `load_to_csv()` function can be described with a single line.

```Python
def load_to_csv(df, output_path):
    ''' This function saves the final data frame as a CSV file in
    the provided path. Function returns nothing.'''

    df.to_csv(output_path, index=False)
```  

## Function Purpose  

This function is the “L” (Load) step in the Extract–Transform–Load (ETL) pipeline. It takes a transformed DataFrame (i.e. your bank market cap data in multiple currencies) and writes it to a CSV file on the local file system.  

## Line-by-line Description  

## 1. Function Definition

```Python
def load_to_csv(df, output_path):
```

* `def` is a keyword that defines a new function.
* `load_to_csv` is the function name.
* It takes two arguments:
    * `df`: the Pandas DataFrame you want to save
    * `output_path`: the file path (string) where the DataFrame should be saved, which is `"./Largest_banks_data.csv"`.  

## 2. Docstring

```Python
    ''' This function saves the final data frame as a CSV file in
    the provided path. Function returns nothing.'''
```
* This is a docstring — a block of text that explains what the function does.  
* It describes that:  
    * The function saves the DataFrame as a CSV file.  
    * The file is saved to the location given by `output_path`.  
    * The function doesn’t return anything (it just performs a saving action).
 
  ## 3. Saving the CSV

  * This line writes the DataFrame to a CSV file on disk.  
  * `df.to_csv(...)` is a Pandas method that exports a DataFrame to a CSV file.  
  * `output_path` is the file path where the CSV will be saved, passed in as an argument.
  * `index=False` tells Pandas not to write the row index (or the rows enumeration, such as 0, 1, 2, ...) as a column in the CSV.

Before running the program, however, we must write the function call for `load_to_csv()`, which must be added at the bottom of our code, below the `# Call transform() function`

```Python
# Call load_to_csv()
load_to_csv(df, output_path)


log_progress("Data saved to CSV file")
```  

Finally, we can run the program by launching the following string in the terminal.  

```
python3.11 banks_project.py
```

Once done, aside from its expected output, a new CSV file will appear on the left Explorer pane, in the selected path `\home\project\`.  

![Screenshot_12](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Screenshot%2012.JPG?raw=true)  

By clicking on it and opening it, we can take a screenshot of the editor screen and save it under the name `Task_4_CSV.png`.  

![Task_4](https://github.com/MatteoMel1985/Relational-Dataset-Images/blob/main/Data%20Engineering%20Images/Task_4_CSV.PNG?raw=true)  

# Task 5: Loading to Database  
