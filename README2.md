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

Configure Grafana for Monitoring: Install and configure Grafana to visualize dashboard for data visualization.


#### Frequently Asked Questions (FAQs)

##### 1. Why Use Spark Alongside Hadoop?
Hadoop: Primarily designed for batch processing using its HDFS (Hadoop Distributed File System) and the MapReduce programming model. While it works well for large-scale data storage and batch processing, Hadoop is not optimized for real-time data processing.

Spark: Spark enhances Hadoop by offering both batch and real-time data processing capabilities. Its in-memory computation model makes it significantly faster than Hadoop's MapReduce, especially for iterative algorithms and real-time analytics.

Spark Streaming: Essential for real-time data processing. Spark Streaming (and Structured Streaming) allows you to ingest and process data streams from sources like Kafka in near real-time, making it ideal for use cases that require low-latency data pipelines.

##### 2. Do You Really Need Spark?
For Real-Time Data Streaming (RTDS), yes, Spark or an equivalent real-time processing framework (like Apache Flink or Kafka Streams) is necessary. Spark Streaming or Structured Streaming is especially well-suited for processing real-time data streams, whereas Hadoop alone focuses more on batch processing, making it less effective for time-sensitive applications.

##### 3. Is Spark Separate from Hadoop?
Yes, Spark is a standalone data processing engine. While it can be integrated with Hadoop for distributed storage (HDFS) and resource management (via YARN), Spark operates independently and provides additional capabilities that Hadoop alone lacks, such as real-time data processing and more complex pipeline designs.

##### 4. Why Use Spark for Real-Time Data Streaming (RTDS)?
Real-Time Processing: Spark's Structured Streaming API allows real-time data ingestion and low-latency processing, making it a perfect choice for time-sensitive applications.

Unified Framework: With Spark, you can handle both batch and real-time processing within a unified platform, simplifying the integration and management of your data pipelines.

Integration with Hadoop: Spark integrates seamlessly with Hadoop for storage and resource management, allowing you to leverage the best of both worlds—batch processing with Hadoop and real-time streaming with Spark.

##### Conclusion:
Spark is a crucial part of any Real-Time Data Streaming (RTDS) pipeline. It provides the real-time processing capabilities that Hadoop lacks, making it an essential tool for building robust and efficient data pipelines. For complex, scalable real-time systems, Spark (or similar frameworks like Flink) is indispensable.

##### Common Network Access Issues
If you encounter issues accessing URLs from outside the virtual machine (VM), these steps will help resolve common network access issues:

Disable the OS Firewall:

bash
sudo firewall-cmd --state
sudo systemctl disable firewalld
sudo systemctl stop firewalld
Disable Linux iptables:

bash
sudo iptables -L
sudo iptables -F
sudo iptables -X
sudo iptables -t nat -F
sudo iptables -t nat -X
sudo systemctl stop iptables
sudo systemctl disable iptables


##### Scripts for Managing Spark and Hadoop
##### Spark Management Scripts
To start or stop Spark services, use the following commands:

Stop Spark:
$SPARK_HOME/sbin/stop-all.sh


Start Spark:
$SPARK_HOME/sbin/start-all.sh

Access Spark Web UI:
Spark Master Web UI: http://localhost:8081

Spark History Server (if enabled): http://localhost:18080
Setting Up the Spark History Server (Optional)
If you want to enable the Spark History Server to monitor past jobs:

Start the History Server:
$SPARK_HOME/sbin/start-history-server.sh

Access the History Server UI:
http://localhost:18080

##### Hadoop Management
Starting Hadoop Daemons:
To start all Hadoop services (NameNode, DataNode, ResourceManager, etc.):
cd /data/hadoop/hadoop/sbin/
./start-all.sh

Verify Hadoop Installation:

Check running Hadoop services with:
jps

Access Hadoop Web Interfaces:
NameNode Web UI: http://localhost:9870
ResourceManager Web UI: http://localhost:8088

# Contributing:
Contributions are welcome! Feel free to open issues or submit pull requests to improve the setup or add new features to the project.

