---

---
---
## Chapter 2 - What is the Data Engineering Lifecycle
- Reverse ETL - Takes the processed data from the output of the Data Engineering Lifecycle and feeds that back into the source systems.
- Undercurrents of the data engineering lifecycle include 1)Security 2) Data Management 3) Data ops 4) Data Architecture 5) Orchestration 6) Software Engineering
- Principle of Least Privilege - Granting a system or user access to only the essential data that is required to perform a task.
- Data Management - Development, execution, and supervision of plans, policies, practices, and programs that deliver, control, or protect the value of data and information assets throughout their cycle.
- Data Governance - A data management function that ensures the quality, integrity, security, and usability of data collected by an organization. It engages people, processes, and technologies to maximize data quality in an organization while protecting data with appropriate security controls.
- Metadata - data about data and it underpins every section of the data engineering lifecycle. There are 2 sections of metadata: Human Generated and Auto Generated. Additionally, there are 4 major types of metadata that a DE needs to be familiar with: 1) Business Metadata 2) Technical Metadata 3) operational metadata 4) reference metadata.
- Data Quality - the optimization of data towards a desired state. It revolves around the question: "What do you get VS what do you expect"? There are 3 main characteristics of data quality: 1)Accuracy 2) Completeness 3) Timeliness 
- Data Modeling and Design - the process of converting data into a usable form. 
- Data Lineage - the recording of an audit trail of data through its lifecycle, tracking both the systems that process the data and the upstream data it depends on.
- Data Ops - Collection of technical technical processes, workflows, cultural norms, and architectural patterns that enable rapid innovation and experimentation, high data quality, low error rates, collaboration, etc. 

## Chapter 3 - Good Data Architecture
- 9 Principles of good data architecture - 1) Choose common components wisely 2) Plan for failure 3) architect for scalability 4) architecture is leadership 5) always be architecting 6) build loosely coupled systems 7) make reversible decisions 8) prioritize security 9) embrace financial operations
- Examples of data architecture include: 1) Data Warehouse 2) Data Lake 3) Data Lakehouse 
- Data Warehouse - Defined by Inmon, is a subject oriented, integrated, non-volatile, time-variant collection of data used in support of management decisions. 
- There are 2 types of a data warehouse architecture: 1) Organizational - refers to organizing data associated with certain business team structures and processes. Organizational data warehousing has 2 main characteristics - separating online analytical processing from production databases and Centralizing and organizing the data, think ETL. 2) Technical - which refers to the technical nature of the data warehouse.
- Separating online analytics processing systems (OLAP systems) from production databases is critial as businesses grow because it directs the load away from production systems and greatly increases analytics performance.
- ELT - Is a variation of ETL in which you extract data from the production databases and load the data directly into the data warehouse. Then, all of the transformations happen directly within the database itself.
- Cloud Data Warehouse - stores data in object storage, which allows for virtually limitless storage. Amazon Redshift were the ones to kick this off and the line between data warehouses and data lakes is starting to blur.
- Data Mart - is a refined subset of a data warehouse, designed to serve analysts and reporting, focused on a single sub organization, department or line of business. This is in contrast to the full data warehouse that serves the entire business. Data marts exist for 2 main reasons: 1) to make data more easily accessible to analysts and report developers and 2) to Improve query and report performance.
- Data Lake - Stores structured and unstructured data in a central location.
- Data Lakehouse - Incorporated the controls, data management, and data structures that exist in a data warehouse while still housing the data in object storage. It supports ACID transactions which the data lake does not.
- Lambda Architecture - where you have systems operating independently from each other -- Batch, streaming, serving. It has many challenges and not very popular or recommended.
- Kappa Architecture - Where a stream processing platform acts as the backbone of all data handling -- Ingestion, storage, and serving.

## Chapter 4 
- Core purpose of data engineering is to design robust and reliable systems to carry data through the full data engineering lifecycle and save it according to the needs of users.
- In Data Engineering, Architecture does NOT equal tools. Architecture is the what, why, and when. Tools are the how. Architecture comes first and tools come second. 
- On Premises VS Cloud VS Serverless - On premises is the default for established companies, this is where companies own their own hardware which live in data centers or leased colocation space. Cloud is where you rent hardware instead of purchasing it, typically you rent from providers like AWS, Azure, Google Cloud, etc. Serverless is basically many invisible servers where you have less control and are managed by the providers.
- When to build vs buy in terms of on premises/cloud: Choose to invest and customize when doing so will give your company a competitive advantage, otherwise, don't.

## Chapter 5 - Data Generation in Source Systems
- Data can be defined as an unorganized, context-less creation of facts and figures. There are 2 main and broad types of data: Analog data, which occurs in the real world like vocal speech, asl, writing, etc. There is also digital data, which is created by either converting analog data to digital form or is the native product of a digital system.
- Files: Are important to understand when learning about computers and data engineering. They can be defined as a sequence of bytes, typically stored on a disk. They may store parameters, events, logs, images, etc. There are 3 main broad types of files: 1) structured files like excels or csvs 2) semi-structured files like json, xml, and also csvs. 3) unstructured files like txt.
- API: Stands for application programming interface and is a standard way of exchanging data between systems, especially in the cloud. 
- There are 3 main types of APIs that Data Engineers should be familiar with: 1) REST APIs which stand for representational state transfer. Here, interactions are state-less and each rest call is independent. Rest calls can change the systems state, but these changes are global. 2) GraphQl which was created at facebook as a query language for application data and an alternative to REST APIs. It allows you to retrieve multiple data models with a single request. It is built around JSON and returns data in a shape resembling the JSON query. 3) Webhooks, which are basically reverse apis.
- An application database, or an OLAP system, stores the state of an application. It reads and writes individual data records at a high rate. They work well as application backends but are not well suited for analytics
- ACID stands for atomicity, consistency, Isolation, and durability. Consistency means that any database read will return consistent results. Isolation means that if two updates are in flight concurrently for the same thing, the end database state will be consistent with the sequential execution of these updates in the order that they were submitted. Durability means that committed data will never be lost.
- Online analytical processing systems, or OLAP systems, refer to any database system that supports high-scale interactive queries. "Online" means that the system is always listening for incoming queries. OLAP systems are typically storage and query systems for analysts.
- Change data capture, or CDC, is a method for extracting each change event that occurs in a database.
- CRUD stands for create, read, update, and delete.
- An "Insert Only" pattern allows you to retain history directly within a table. Usually this is supplemented with a process date or a time stamp, and you add new records rather than updating or deleting existing records.
- There are, in general, 3 types of times that should be captured in a data pipeline, generation time, ingested time, and processed time.
- The first major type of source system is a relational database. Major considerations of relational database are: 1) The RDMS, which consists of a storage engine, a query optimizer, disaster recovery, etc 2) Lookups, it is important to understand how your database uses indexes 3) Query optimizer, which comes with the RDMS 4) Scaling and distribution -- do you want your db to scale horizontally or vertically 5) modeling patterns -- do you want normalized or wide tables 6) CRUD 7) Consistency
- Relational Database are the most common type of application backend. Here, data is stored in a table of relations and each relation contains multiple fields. Each relation in the table has the same schema. 
- In relational databases, normalization is the process of ensuring that data in records is not duplicated in multiple locations at once and prevents inconsistencies. 
- Another major type of source system includes non-relational databases. Non-relational database abandon the whole "relational paradigm" and examples include: 1) key-value stores, which are basically just a hash map or a dictionary, that you might find in python 2) Document Stores, which are basically like a collection of key-value stores 3) Wide column, which is optimized to store massive amounts of data 4) Graph databases, which store data in a mathematical graph structure with nodes and edges 5) search databases 6) time series databases.

## Chapter 6 - Storage
- Storage Abstractions in Data Engineering include: 1) Data Lakes 2) Data Lakehouses 3) data warehouse 4) data platform.
- Storage Systems in Data Engineering include: 1) HDFS 2) Cache/Memory based systems 3) RDMS 4) Object Storage 5) Streaming Storage
- Raw Ingredients in terms of storage in data engineering include: 1) Disk Drives 2) Memory 3) Networking/CPU 4) Serialization 5) Compression 6) Caching 
- Magnetic Disk Drives (HDDs): Worse than SSds at random access lookups, higher latency, lower IOPS and lower transfer speeds. Note: Object storage on magnetic disks have emerged as the leading option for large scale data storage in data lakes and cloud data warehouses.
- Solid State Drives (SSDs): Store data as charges in flash memory cells. These are the standard for commericial deployment of OLTP systems. 
- Random access memory (RAM): Attached to the CPU and mapped to the CPU address space. This stores the code and data that CPUs execute. It's more expensive than SSDs and slower than CPU cache. 
- Networking and CP: CPUs handle the details of servicing requests, aggregating reads, and delivering writes. 
- Serialization: Process of flattening data into a standard format that a reader would be able to decode.
- Compression: Makes data smaller.
- Caching: Stores frequently or recently accessed data in a fast access layer.
- Distributed Storage: Coordinates the activities of multiple servers to store, retrieve, and process data faster and at a larger scale. Apache Spark, object storage, and cloud data warehouses rely on distributed storage architecture.
- Eventual Consistency: Allows you to retrieve data quickly without verifying you have the latest version across all nodes. 
- BASE: Stands for basically available, Soft State, and eventual consistency. 
- Strong consistency: Means that any database read will return consistent values. 
- Block Storage: A type of raw storage provided by SSDs and magnetic Disks. A block is the smallest addressable unit of data supported by a disk. 
- Object Storage: Contains data of all shapes and sizes. This includes Txt, csvs, excel, images, audio, video, etc. In object storage, after the initial write the data becomes immutable. Object storage provides excellent performance for large scale batch reads and writes. Object storage is the gold standard of storage for data lakes. Lastly, object storage is basically a key/value store.
- Memcached is basically a key-value store designed for caching query results, api call responses, and more. 
- Redis: Like memcached, it is a key-value store, but designed to support more complex data types. 
- Hadoop: Similar to object storage but combines compute and data together on the same node.
- Indexes: provide a map of the table for particular fields and allows for extremely quick lookups of individual records. Without Indexes, databases need to scan the entire database to find the records that satisfy the where clause. Indexes are primarily used on primary keys and foreign keys and commonly used fields.
- Columnar Serialization: allows a database to scan only the columns that are required by a query. Columnar databases perform well when large quantities of data must be scanned.
- Partitioning: Is breaking a table into multi sub-tables by splitting it on a field. Date and time partitioning is extremely common. 
- Clustering: Sorts your data by fields, where you colocate similar values.
- Data Catalog is a centralized meta store for all data that exists in an organization. 
- Separation of compute and storage has become increasingly common recently. For example, data lakehouses store data in object storage and spin up temporary compute in order to read and process it.
- Colocation of compute and storage offers high performance and there has been a shift to this for a couple main reasons: Scalability, durability, and availability, to name a few.
- 