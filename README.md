### Note: Project deployment still in progress will add more updates soon

# Data Lakes Batch Processing On Premises


## Project Description:
This project focuses on setting up an end-to-end Real-Time Data Streaming (RTDS) pipeline using a wide range of big data technologies, including Hadoop, Spark, Apache Flink, and Grafana. The setup begins by preparing a virtual machine with Oracle Linux, configuring a Hadoop single-node cluster, integrating Apache Spark for real-time processing, and extending the setup to include a MySQL and MongoDB database. Grafana is then used for dashboarding and visualization of the processed data.

The goal of this project is to build a scalable and efficient platform that allows real-time data processing and visualization, leveraging the power of distributed systems and big data frameworks.

## Features:
Set up a Hadoop cluster and configure HDFS for distributed data storage.
Install and configure Apache Spark to work with Hadoop.
Enable PySpark integration with Jupyter for interactive data processing.
Set up MySQL and MongoDB as source systems.
Real-time data ingestion and processing with Apache Flink and Spark Streaming.
Create dashboards with Grafana for monitoring data processing and visualization.

## Technologies Used:
Hadoop 3.x: Distributed data storage.
Apache Spark 3.x: Real-time and batch data processing.
Apache Flink: Stream processing for real-time data analytics.
MySQL: Relational database for storing structured data.
MongoDB: NoSQL database for handling semi-structured JSON data.
Grafana: Data visualization and dashboarding tool.
Jupyter Notebooks: Interactive development environment for data processing.

## Setup Guide:
The setup involves the following steps:

### OS Prerequisites Setup:

Install Oracle VM VirtualBox and import Oracle Database 23c Free VirtualBox Appliance.
Configure network adapters (NAT and Host-only).
Enable necessary network services like Telnet.
Hadoop Setup:

Install and configure Hadoop in a single-node cluster.
Set up HDFS directories for Namenode and Datanode.
Configure core-site.xml, hdfs-site.xml, and other Hadoop settings.
Spark Installation:

Download and configure Apache Spark for integration with Hadoop.
Set up Spark with YARN for resource management.
Configure Spark environment variables and start Spark services.
Jupyter Notebook Installation:

Install Jupyter and integrate it with PySpark.
Access Jupyter Notebooks for interactive development.
Configure and test PySpark in the Jupyter environment.
MySQL and MongoDB Installation:

Install MySQL and MongoDB on the VM.
Create sample databases and tables for testing.
Establish Python scripts for connecting to MySQL and MongoDB.

### Apache Flink Setup:

Set up Apache Flink for stream processing.
Configure Flink to integrate with Kafka for real-time data ingestion.

### Grafana Setup:
Install Grafana for data visualization.
Configure Grafana dashboards to monitor real-time data and metrics.

### Project Structure:
/data/ETL/code: Python code for exporting data from source systems to Parquet files.
/data/hadoop: Hadoop and Spark installation directories.
/etc/yum.repos.d: Custom repository configurations for MongoDB and additional packages.
Set up Hadoop and Spark: Follow the setup instructions in the provided documentation to install Hadoop, Spark, and related dependencies on Oracle Linux.

Install MySQL and MongoDB: Install the databases by running the respective installation scripts provided.

Run the Python ETL pipeline: Set up the environment and run Python scripts to export data from MySQL and MongoDB, convert to Parquet format, and ingest into HDFS.

Configure Grafana for Monitoring: Install and configure Grafana to visualize real-time data.

Contributing:
Contributions are welcome! Feel free to open issues or submit pull requests to improve the setup or add new features to the project.

