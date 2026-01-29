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
- 