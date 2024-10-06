# Step-by-Step Guide for Spark Installation and Configuration on Hadoop

### Step 1: Download and Install Apache Spark

1. **Create a Directory for Spark:**

   We'll use `/data/hadoop` for the Spark installation.

   ```bash
   sudo mkdir -p /data/hadoop/spark
   cd /data/hadoop/spark
   ```

2. **Download Spark:**

   Download the latest version of Apache Spark that’s compatible with Hadoop 3.3.5 (or use Spark 3.x):

   ```bash
   wget https://downloads.apache.org/spark/spark-3.5.3/spark-3.5.3-bin-hadoop3.tgz
   or Donwload file https://downloads.apache.org/spark/spark-3.5.3/spark-3.5.3-bin-hadoop3.tgz and upload to directory /data/hadoop/spark
   ```

3. **Extract Spark:**

   Extract the Spark binary files:

   ```bash
   tar -xvzf spark-3.5.3-bin-hadoop3.tgz
   sudo mv spark-3.5.3-bin-hadoop3 /data/hadoop/spark/spark
   ```

### Step 2: Configure Environment Variables for Spark

1. **Update `.bashrc` with Spark Environment Variables:**

   Open your `.bashrc` file:

   ```bash
   vi ~/.bashrc
   ```

   Add the following lines at the end of the file:

   ```bash
   # Spark environment variables
   export SPARK_HOME=/data/hadoop/spark/spark
   export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin
   export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
   ```

2. **Reload `.bashrc`:**

   Apply the environment variable changes:

   ```bash
   source ~/.bashrc
   ```

### Step 3: Configure Spark with Hadoop

1. **Configure `spark-env.sh`:**

   Open the `spark-env.sh` file:

   ```bash
   vi $SPARK_HOME/conf/spark-env.sh
   ```

   Add the following lines:

   ```bash
   # Java and Hadoop settings
   export JAVA_HOME=~/java/jdk-11.0.20
   export HADOOP_HOME=/data/hadoop/hadoop
   export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
   export SPARK_MASTER_WEBUI_PORT=8081
   
   ```
also do the below
cd /data/hadoop/spark/spark/conf/
cp spark-env.sh.template spark-env.sh
cp spark-defaults.conf.template spark-defaults.conf

2. **Configure `spark-defaults.conf`:**

   Open `spark-defaults.conf`:

   ```bash
   vi $SPARK_HOME/conf/spark-defaults.conf
   ```

   Add these settings for Hadoop integration:

   ```ini
   spark.master                     yarn
   spark.eventLog.enabled           true
   spark.eventLog.dir               hdfs://localhost:9000/spark-logs
   spark.executor.memory            2g
   spark.driver.memory              2g
   spark.history.fs.logDirectory    hdfs://localhost:9000/spark-logs
   ```

3. **Set up Hadoop Integration for Spark:**

   Ensure that Spark is integrated with Hadoop by creating a directory in HDFS for Spark logs:

   ```bash
   hdfs dfs -mkdir /spark-logs
   hdfs dfs -chmod 777 /spark-logs
   ```

### Step 4: Start Spark Services

1. **Start Spark Standalone Mode:**

   To run Spark in standalone mode:

   ```bash
   cd /data/hadoop/spark/spark/sbin/
   ./start-all.sh
   ```

2. **Start Spark on YARN (Optional):**

   If you want to run Spark on YARN:

   cd $SPARK_HOME/sbin
   ./start-yarn.sh


### Step 5: Verify Spark Installation

1. **Verify Spark Services:**

   Run the following command to check running Spark services:

   jps


   You should see the following services:
   - Master
   - Worker
   - ResourceManager (if on YARN)
   - NodeManager (if on YARN)
   
 
 script to stop and start SPARK 
 
$SPARK_HOME/sbin/stop-all.sh
$SPARK_HOME/sbin/start-all.sh

2. **Access Spark Web UI:**
   - **Spark Master Web UI:** [http://localhost:8080](http://localhost:8081)
   - **Spark History Server (if enabled):** [http://localhost:18080](http://localhost:18080)

### Step 6: (Optional) Set Up Spark History Server

If you want to enable the Spark History Server to monitor jobs:

1. **Start the Spark History Server:**

   ```bash
   $SPARK_HOME/sbin/start-history-server.sh
   ```

2. **Configure Log Directory:**

   Ensure logs are written to HDFS (`/spark-logs`) as configured in `spark-defaults.conf`.

3. **Access History Server UI:**

   Access it through [http://localhost:18080](http://localhost:18080).

---  Spark Installation Summary:

1. **Download and Extract Spark** in `/data/hadoop/spark`.
2. **Set Up Environment Variables** for Spark in `.bashrc`.
3. **Configure Spark with Hadoop** for seamless integration.
4. **Start Spark Services** and verify the setup.
5. **(Optional) Set Up the Spark History Server** for job monitoring.
