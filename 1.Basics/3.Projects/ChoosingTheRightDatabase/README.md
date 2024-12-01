# [Choosing the Right Database](StorageOptions.pdf)
- [Factors](#factors)
- [Database Types](#database-types)
- [Options](#options)
## Factors

| **S.No** | **Category**                  | **Details**                                  |
|----------|-------------------------------|----------------------------------------------|
| 1        | Nature of Data                | Structured/Unstructured                      |
| 2        | Processing of Data            | Real time/Batch                              |
| 3        | Types of Transactions         | Write Intensive/Read Intensive               |
| 4        | Modification of Data          | Frequency of updates to data                 |
| 5        | Workload Type                 | Read-heavy, write-heavy, or balanced         |
| 6        | Throughput Needs              |                                              |
| 7        | Scalability Requirements      | Will it change, does it need to scale or fluctuate during the day? |
| 8        | Data Storage                  | How much data to store and for how long?     |
| 9        | Data Growth                   | Will it grow?                                |
| 10       | Average Object Size           |                                              |
| 11       | Access Patterns               | How are they accessed?                       |
| 12       | Data Durability               |                                              |
| 13       | Source of Truth               |                                              |
| 14       | Latency Requirements          |                                              |
| 15       | Concurrent Users              |                                              |
| 16       | Data Model                    |                                              |
| 17       | Query Method                  | How will you query the data?                 |
| 18       | Joins                         |                                              |
| 19       | Data Structure                | Structured? Semi-Structured?                 |
| 20       | Schema Flexibility            | Strong schema? More flexibility?             |
| 21       | Reporting                     |                                              |
| 22       | Search                        |                                              |
| 23       | Database Type                 | RDBMS / NoSQL?                               |
| 24       | License Costs                 |                                              |
| 25       | Cloud Native DB               | Switch to Cloud Native DB such as Aurora?    |

Let me know if there's anything else you need! 😊

- Nature of Data: Structured/Unstructured
- Processing of Data: Real time/Batch
- Types of Transactions: Write Intensive/Read Intensive
- Modification of data: Frequency of updates to data
- Read-heavy, write-heavy, or balanced workload? 
  - Throughput needs? 
  - Will it change, does it need to scale or fluctuate during the day?
- How much data to store and for how long? 
  - Will it grow? 
  - Average object size? 
  - How are they accessed?
- Data durability? 
  - Source of truth for the data?
- Latency requirements? 
  - Concurrent users?
- Data model? 
  - How will you query the data? 
  - Joins? 
  - Structured? Semi-Structured?
- Strong schema? 
  - More flexibility? 
  - Reporting? 
  - Search? 
  - RDBMS / NoSQL?
- License costs? 
  - Switch to Cloud Native DB such as Aurora?

## Database Types
- RDBMS (= SQL / OLTP)
  - RDS, Aurora – great for joins
- NoSQL database
  - DynamoDB (~JSON), 
  - ElastiCache (key / value pairs), 
  - Neptune (graphs) – no joins, no SQL
- Object Store
  - S3 (for big objects)
  - Glacier (for backups / archives)
- Data Warehouse (= SQL Analytics / BI)
  - Redshift (OLAP), Athena
- Search
  - ElasticSearch (JSON) – free text, unstructured searches
- Graphs
  - Neptune – displays relationships between data
- Timeseries
  - InfluxDB
## Options
<img src="images/options.jpg">

<img src="images/options-2.jpg">
