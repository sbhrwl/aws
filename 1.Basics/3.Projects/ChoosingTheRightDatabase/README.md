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
| 5        | Throughput Needs              | Read-heavy, write-heavy, or balanced         |
| 6        | Scalability Requirements      | Will it change, does it need to scale or fluctuate during the day? |
| 7        | Data Storage                  | How much data to store and for how long? Average object size?     |
| 8        | Access Patterns               | How is data accessed?                        |
| 9        | Data Durability               | Source of truth for the data?                |
| 10       | Latency Requirements          |                                              |
| 11       | Concurrent Users              |                                              |
| 12       | Query Method                  | How will you query the data? Joins?          |
| 13       | Schema Flexibility            | Strong or Flexible schema?                   |
| 14       | Database Type                 | RDBMS / NoSQL?                               |
| 15       | License Costs                 |                                              |

## Database Types

| **S.No** | **Category**                  | **Details**                                                         |
|----------|-------------------------------|---------------------------------------------------------------------|
| 1        | RDBMS (= SQL / OLTP)          | RDS, Aurora – great for joins                                       |
| 2        | NoSQL database                | DynamoDB (~JSON), ElastiCache (key/value pairs), Neptune (graphs) – no joins, no SQL |
| 3        | Object Store                  | S3 (for big objects), Glacier (for backups/archives)                |
| 4        | Data Warehouse (= SQL Analytics / BI) | Redshift (OLAP), Athena                                             |
| 5        | Search                        | ElasticSearch (JSON) – free text, unstructured searches             |
| 6        | Graphs                        | Neptune – displays relationships between data                       |
| 7        | Timeseries                    | InfluxDB                                                            |

## Options
<img src="images/options.jpg">

<img src="images/options-2.jpg">
