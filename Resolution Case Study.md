# Preliminaries: Installing libraries and downloading data   

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

If you want to add one folder, you can type "cd" plus the name of the folder you want to add.  

```python
cd "folder name"
```

On the contrary, if you want to go backward, or more technically "one level up", you should write the following command.

```python
cd ..
```

`cd` stands for "change directory", whereas `..` stands for "parent directory". 
