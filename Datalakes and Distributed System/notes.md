# Datalakes and distributed system : the truth and myths
**Definition**: a datalake is a platform that centralize all data into a single, virtual namespace regardless of the data type, format or volume.

Most common needs for a datalake:
- There is multiple databases to store data and we can't scale them or the cost of data storage and software is unviable.
    - Option: Datalake to transmit the data into a new platform. 
- An organisation has highly-sensitive data that needs to be centralized, store and protected based on clearance level, roles or permissions.
    - Option: A datalake to integrate all the data.
- An organisation to implement cross-organization analytics and generate new insights, relationships and trends from their data. 
    - Option: Connect a datalake to existing databases and data warehouses and transmit data to and from the lake to provide data from analytics and take advange of analytics results.

## Myth and truths
- Myth: It's hard to generate a single searchable index that represents all data stored in different indices accross the datalake.
    - Truth: With Elastic's cross-cluster replication this can be done at scale.

- Myth: We need to perform column-level encryption at rest on the entire table.
    - Truth: Data encryption at rest can be configured for an entire table within redshift or accumulo.

- Myth: It's nearly impossible to establish a single source of truth for data after migrating it to a datalake from legacy systems.
    - Truth: You can establish a single source of truth over time by storing existing data sets in the in the lake and analyzing the provenance and usage of the data. (eg. Apache Nifi, complete data provenance)

- Myth: Data lakes eventually evolve into data swamps where data management becomes difficule and data quality is harder to enforce. 
    - Truth: With proper data curation, management, lifecycle tracking and meta data. Data lakes can properly enforce data lifecycle best practices and enforce good data quality. 

- Ideas to prevent and/or clean data swamp:
    - Establish a data governance framework early. 
    - Be careful of scope creep to prevent vendor lock-in.
    - Leverage data provenance and lineage tools.
    - Tag and catalog data on ingest, so it's easy for your analyst to search for data and reduce acccidental loading of duplicative data sets.
    - Automate everything
    - Improve the data culture - educate data stewards.


- Myth: Legacy or existing databases systems needs to be decommisisioned once a datalake is implemented.
    - Truth: Legacy systems don't need to be decommissioned and many data lakes integrates with existing databases and data warehouses. Many tools exist to integrate existing databases with a data lake. Including Sqoop and Flume.

- Myth: Data of any format can be ingested and ML model will be to instantly input the data.
    - Truth: The lake will accept data of any format, but ML capabilities need data to be curated and formatted to match expected input parameters.

## Use cases and closing thoughts:
- Data culture is important
    - Leading client in aviation wanted to implement a data lake to centralize data for analytics purpose and help facilitate better data quality and data governance.
    - There were many cultural challenges around data ingest that resulted in redundant data elements without a single source of truth.
    - Over the years, many data analyst and stewards input data sets that had the same meaning using different nomenclatures. For example, some analysts were referring to passenger as a "seat" others a "chair" and others as "passenger"
    - **Strategy**
        - Work with the leadership to establish a data governance framework that had input and feedback from all data stewards and system owners. Document the data standards that resulted from the framework to allow us to start flagging inaccurate data once it's in the lake.
        - Ingest only the necessary data into the lake and monitor how users are interacting with the data through data provenance. Start to cleanse the data using the governance fraamework and feedback from data owners.
        - Over time continue to ingest new data sets and repeat the proess to cleanse data and prepare it to production use. 
- Sometimes a data lake is not the right solution
    - For example, federal organisation that wanted to put 12 systems together but for operational purpose (prevent MFA, SSO)

[Complete presentation](https://cdn.oreillystatic.com/en/assets/1/event/307/Data%20lakes%20and%20distributed%20systems_%20The%20truths%20and%20myths%20Presentation.pptx)