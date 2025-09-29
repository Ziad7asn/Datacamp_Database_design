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

## OlTP AND OLAP working together
![GKs8xq-WwAAauCD](https://github.com/user-attachments/assets/83918811-2fab-4a39-bda2-b44c6f2861c6)
