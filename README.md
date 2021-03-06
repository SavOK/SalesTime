<h1 align='center'> <strong>
Sales Time </br>
</string></h1>
<h3 align='center'> 
Insight Data Engineering Project </br>
</h3>
Provide recommendations to door-to-door sales which potential customer to visit next. Given the stringent time-limit, the sales person would want to know the customer fastest to reach. The app suggests next location to visit based on mode of transportation and real-time road conditions

____
<p align="center">
  <a href="#data-flow">Data Flow</a> •
  <a href="#data-source">Data Source</a> •
  <a href="#approach">Approach</a> •
  <a href="#usage">Usage</a> •
  <a href="#installation">Installation</a> •
  <a href="#contacts">Contacts</a>
</p>

____
<h2 align='center', id='data-flow'> 
Data Flow </br>
</h2>

![Data Flow][flow]
___
<h2 align='center', id='data-source'> 
Data Source </br>
</h2>
List of Licensed business comes from Data.gov

___
<h2 align='center', id='approach'> 
Approach </br>
</h2>

### Outline  
* Process data with PySpark (clean and normalize) 
* Store data in Postgres 
* Use PostGIST to index spacial data (location)
* Use Here.com API to get driving/walking time estimate 
* Dash UI to interact with data
### Cleaning Data 
* Data saved at S3 as 51 csv files
* Removed row without location coordinates, address, or industry description (NAICS number)
* If provided with number of employees, broke number in bins (0-10, 10-100, 100-500, ...)
* If provided with sales value, broke number in bins (0-1000, 1000-10000, 100000-500000, ...)
### Storing Data  
* Cleaned and normalized data stored
![Database schema][schema]
### Calculating Route Time
* Here API
### UI Dash App
* options State 
* options Business type
* Transportation mode
* Time radius
* Starting location

___
<h2 align='center', id='usage'> 
Usage </br>
</h2>

[![Demo Video](https://img.youtube.com/vi/wmZdmdz01LA/0.jpg)](https://www.youtube.com/watch?v=wmZdmdz01LA)

___
<h2 align='center', id='installation'> 
Installation </br>
</h2>

**IMPORTANT** Before doing anything need to setup `config.py`
### Requirements
`boto3`, 
`dash`, 
`GeoAlchemy2`, 
`gunicorn`,
`pandas`, 
`psycopg2-binary`,
`requests`,
`SQLAlchemy`
### Project tree
./  
├── `LICENSE`  
├── `README.md`  
├── `config.py`  
├── data  
|&emsp;└── `6-digit_2017_Codes.csv`  
└── src  
 &emsp;├── APIs  
 &emsp;│ &emsp; ├── `HereAPI.py`  
 &emsp;│ &emsp; └── `YelpAPI.py`  
 &emsp;├── AirFlow  
 &emsp;│ &emsp; └── `UpdateDataSchedule.py`  
 &emsp;├── PySpark  
 &emsp;| &emsp; └── `pyspark_clean_data.py`  
 &emsp;├── SQL  
 &emsp;│ &emsp; ├── `BusinessTable.py`  
 &emsp;│ &emsp; ├── `CategoryTable.py`  
 &emsp;│ &emsp; ├── `LocationTable.py`  
 &emsp;│ &emsp; ├── `MainTable.py`  
 &emsp;│ &emsp; ├── `__init__.py`  
 &emsp;│ &emsp; └── `base.py`  
 &emsp;├── SQLScripts    
 &emsp;│ &emsp;└── `create_index.sql`   
 &emsp;├── assets  
 &emsp;│ &emsp; ├── `base.css`   
 &emsp;│ &emsp; └── `style.css`  
 &emsp;├── `config.py`  
 &emsp;├── `help_functions_app.py`  
 &emsp;└── `main_app.py`  
 ____
<h2 align='center', id='contacts'> 
Contacts </br>
</h2>

<p align="center">|
 <a href="https://www.linkedin.com/in/saveliybelkin/">LinkedIn</a> |
 <a href="https://github.com/SavOK">GitHub</a> |
</p>

___
[flow]: images/data_flow.png "Data Flow" 
[schema]:  ./images/schema.png "DB Schema"
