![image](https://github.com/user-attachments/assets/e1e31f32-25e3-4317-8867-c74d8bd1ea12)# Preliminaries: Installing libraries and downloading data   

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

```python
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

