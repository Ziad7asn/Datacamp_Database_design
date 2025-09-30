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


