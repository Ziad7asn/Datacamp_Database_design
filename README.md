# Datacamp_Database_design
**Approaches to Processing data**
<br/>
OLTP VS OLAP
- OLTP : Online Transaction Processing
- OLAP : Online Analytical Processing

| - | OLTP | OLAP |
|----------|----------|----------|
| Task    | - Find the price of a book <br/> - Update latest customer transaction <br/> - Keep track of employee hours  |- Calculate Books with best profit margin <br/> - find most loyal customers <br/> - Decide employee of the month     |
|Purpose    | support daily transactions    | report and analyze data     |
|Design   | aplication-oriented    | subject-oriented     |
|Date    | up-to-date, operational    | consolidated, historical     |
|Size    | snapshot, gigabytes    |archive, terabytes     |
|Queries    | Simple transactions & frequent updates    |complex, aggtegated queries & limited update     |
|Users    | thousands  |hundreds    |

## OLTP AND OLAP working together
![GKs8xq-WwAAauCD](https://github.com/user-attachments/assets/83918811-2fab-4a39-bda2-b44c6f2861c6)

## Strucure Data 
Easer To analyze But less flexibilty and scalablilty 

## Data warehouses Vs Data lake 
### Data warehouse
- Optimized for analytics - OLAP
   - Organized for reading/ aggtrgating data
   - Usually read-only
- Contains data from multiple sources
- Massively Parallel Processing
- Typically uses a denormalized schema and dimensional modeling
#### Data marts
- subset of data warehouses
- Deficated to specific topic
### Data lakes
 - Store all types of data at a lower cost:
    - row, operational database, IoT devices logs, real-time, relational and non-relational
- Retains all data and can take up petabytes
- Schema-on-read as opposed to schema-on-write
- need to catalog data otherwise becomes a data swamp
- Run big data analytics using services such as apache spark and hadoop
  - Useful for deep learning and data discovery because activites require so much data
## ETL vs ELT

### ETL (Extract → Transform → Load)

```text
+-------------+       +------------------+       +-------------------+
|             |       |                  |       |                   |
| Data Source | ====> | Transformation   | ====> |  Data Warehouse   |
|             |       |   (ETL Tool)     |       |   (Storage)       |
+-------------+       +------------------+       +-------------------+

 Step 1: Extract    - Pull raw data from source  
 Step 2: Transform  - Clean and reshape data before storage  
 Step 3: Load       - Load transformed data into the warehouse  
```

### ELT (Extract → Load → Transform )
```text
+-------------+       +-------------------+       +-------------------+
|             |       |                   |       |                   |
| Data Source | ====> |  Data Warehouse   | ====> |  Transformation   |
|             |       |   (Storage)       |       |   (in-warehouse)  |
+-------------+       +-------------------+       +-------------------+

 Step 1: Extract    - Pull raw data from source  
 Step 2: Load       - Load raw data directly into the warehouse  
 Step 3: Transform  - Transform data inside the warehouse using SQL or tools  
```


### Star Schema Vs Snowflake schema
#### Dimensional modeling: Star schema 
<p>Fact tables</p> 

* Holds records of a metric
* Changes regularly
* Connects to dimensions via foreign keys
  
<p>Dimension tables</p> 

* Holds descriptions of attributes
* Does not changes as often

<p>Example: </p> 

* Supply books to store is USA and Canada
* Keep track of book sales


<img width="364" height="139" alt="download" src="https://github.com/user-attachments/assets/dbf99647-c222-49f5-8a2b-28ced859d78c" />

#### Dimensional modeling: Snowflake schema

  
<p>Dimension tables</p> 

* More than one dimension because dimension tab0les are normalized

<img width="305" height="165" alt="download" src="https://github.com/user-attachments/assets/4e0acb58-0962-458b-91d4-b27e26dd4ba9" />


### What is normalization ?

* Database design technique
* Divides tables into smaller tables and connects them via relationships
* Goal : reduce redundancy and increase data integrity


### Denormalized Query 
* GOAL: Get quantity of all octavia E. Butler Books solid in Vancouver in Q4 of 2018
  ```text
  SELECT 
    SUM(f.quantity) AS total_quantity
   FROM 
       fact_sales f
   JOIN dim_book b 
       ON f.book_id = b.book_id
   JOIN dim_author a 
       ON b.author_id = a.author_id
   JOIN dim_store s 
       ON f.store_id = s.store_id
   JOIN dim_date d 
       ON f.date_id = d.date_id
   WHERE 
       a.author_name = 'Octavia E. Butler'
       AND s.city = 'Vancouver'
       AND d.quarter = 'Q4'
       AND d.year = 2018
        ```
* Normalization Saves Space
* Denormalized database enable **data redundancy**
* Normalization eliminates **data redundancy**



