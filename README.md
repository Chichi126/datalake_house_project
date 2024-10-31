# datalake_housing_project

Overview

The Datalake Housing Project is designed to empower data engineers to create a cost-effective and efficient lakehouse architecture using open-source technologies. The primary objective of this project is to minimize vendor lock-in and reduce the complexity associated with various tools and technologies while ensuring that data remains secure, easily accessible, and free from excessive costs. By leveraging a lakehouse architecture, we can achieve scalable, secure, and cost-efficient data storage and processing.

This project showcases a step-by-step approach to extracting data from a typical transactional database, specifically a local PostgreSQL instance managed through pgAdmin, loading it into a data lake, enhancing the data lake with a catalog, and ultimately converting it into a fully functional lakehouse.


# Project Components

## 1. MinIO: 

Acts as the primary storage layer for the lakehouse architecture.

### Functionality:

Stores raw, unprocessed data as well as processed data.

Provides an S3-compatible interface for easy integration with other tools.

Ensures data durability and availability through redundancy and replication.

## 2. Apache Iceberg

Manages large sets of tabular data stored in MinIO.

### Functionality:


Supports ACID transactions, ensuring data integrity during concurrent writes and reads.

Facilitates schema evolution, allowing for changes to the data structure without disrupting existing queries.

Implements partitioning strategies to optimize query performance and data retrieval.

## 3. Project Nessie

Serves as a catalog for managing Iceberg tables.

### Functionality:

Provides a Git-like experience for data management, enabling version control and branching capabilities.

Manages Iceberg metadata and schema versions, allowing users to track changes and revert to previous states if necessary.

Enhances collaboration among data teams by allowing multiple users to work on the same datasets simultaneously.

## 4. Trino (formerly PrestoSQL)

A powerful SQL query engine that interacts with Iceberg tables.

### Functionality:

Enables users to perform complex analytics and queries on data stored in MinIO.

Supports querying across multiple data sources, providing flexibility in data analysis.

Optimizes query execution for improved performance on large datasets.

## Data Flow

#### Data Ingestion:

Data is extracted from a local PostgreSQL database, which is managed through pgAdmin. This dataset includes various tables like the customers, orders, products, and order_items tables.

The extracted data is then ingested into MinIO, where it is stored as raw data.

#### Iceberg Management:

Apache Iceberg manages the metadata and schema of the data stored in MinIO.

It ensures efficient data handling and enables users to perform complex queries without compromising performance.

Catalog and Version Control:

Project Nessie: It acts as the catalog for Iceberg tables, providing a structured view of available datasets.

It offers version control features, allowing users to track changes and manage different versions of their data easily.
Data Querying:

Trino serves as the SQL query engine, enabling users to run analytical queries on the data stored in Iceberg tables.

I leveraged Trino's capabilities to join datasets, perform aggregations, and generate insights from the data for the gold schema.

Prerequisites

To successfully set up and run this project, ensure that the following prerequisites are met:

Docker: Install Docker on your machine (preferably Docker Desktop) to facilitate containerized deployment of the various components.

PostgreSQL: A local PostgreSQL instance should be set up, with the necessary datasets available for extraction. You can manage this instance using pgAdmin or any other SQL client.

Basic Knowledge: Familiarity with SQL, data engineering concepts, and cloud storage principles will be beneficial for understanding and working with the project.

## Getting Started
##### Clone the Repository:

Use the following command to clone the project repository:

bash
git clone https://github.com/yourusername/datalake_housing_project.git

##### Build and Run Containers:

Navigate to the project directory and use Docker Compose to build and run the necessary containers:

bash

cd datalake_housing_project

docker-compose up --build


##### Access the Services:

Once the containers are running, you can access the various services via their respective ports as defined in the docker-compose.yml file.

##### Load Data:

Follow the provided scripts or instructions to extract data from your local PostgreSQL database, load it into MinIO and manage it using Apache Iceberg, Trinio and Project Nessie.

This involved using ELT (Extract, load, transform) processes to prepare the data


##### Query Data:

Use Trino to connect to the Iceberg tables and start querying the data. Sample SQL queries can be found in the queries directory.

### Conclusion
The Datalake Housing Project provides a comprehensive framework for building a scalable, secure, and cost-effective lakehouse architecture using open-source technologies. By following the outlined steps and utilizing the provided components, data engineers can effectively manage and analyze their data.

