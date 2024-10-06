## 1. Java Version Check:
The installed Java version is 11.0.20 LTS, which is compatible with Hadoop 3.x. No need to install a new version. 

## 2. Download and Set Up Hadoop Directory:
   sudo yum update -y
   sudo yum groupinstall "Development Tools" -y
   sudo yum install cmake zlib-devel pkgconfig openssl-devel -y

   # Create /data/hadoop directory:
   sudo mkdir -p /data/hadoop
   cd /data/hadoop

   # Download and extract Hadoop:
   w4get wget --no-check-certificate https://downloads.apache.org/hadoop/common/hadoop-3.3.5/hadoop-3.3.5.tar.gz
   or Download file https://downloads.apache.org/hadoop/common/hadoop-3.3.5/hadoop-3.3.5.tar.gz  and upload in directory 
   tar -xzvf hadoop-3.3.5.tar.gz
   sudo mv hadoop-3.3.5 /data/hadoop/hadoop

## 3. Configure Environment Variables:
   vi ~/.bashrc

   # Add the following lines:
   export HADOOP_HOME=/data/hadoop/hadoop
   export HADOOP_INSTALL=$HADOOP_HOME
   export HADOOP_MAPRED_HOME=$HADOOP_HOME
   export HADOOP_COMMON_HOME=$HADOOP_HOME
   export HADOOP_HDFS_HOME=$HADOOP_HOME
   export YARN_HOME=$HADOOP_HOME
   export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
   export PATH=$PATH:$HADOOP_HOME/sbin:$HADOOP_HOME/bin
   export JAVA_HOME=~/java/jdk-11.0.20
   export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib/native"

   source ~/.bashrc

## 4. Hadoop Configuration:
   vi $HADOOP_HOME/etc/hadoop/core-site.xml

   # Add the following:
   <configuration>
       <property>
           <name>fs.defaultFS</name>
           <value>hdfs://localhost:9000</value>
       </property>
   </configuration>

## 5. Configure HDFS:
   vi $HADOOP_HOME/etc/hadoop/hdfs-site.xml

   # Add the following:
   <configuration>
       <property>
           <name>dfs.replication</name>
           <value>1</value>
       </property>
       <property>
           <name>dfs.namenode.name.dir</name>
           <value>file:///data/hadoop/hadoop_data/namenode</value>
       </property>
       <property>
           <name>dfs.datanode.data.dir</name>
           <value>file:///data/hadoop/hadoop_data/datanode</value>
       </property>
   </configuration>

   # Create directories for namenode and datanode:
   sudo mkdir -p /data/hadoop/hadoop_data/namenode
   sudo mkdir -p /data/hadoop/hadoop_data/datanode
   sudo chown -R $USER:$USER /data/hadoop/hadoop_data

## 6. Configure MapReduce:
   cp $HADOOP_HOME/etc/hadoop/mapred-site.xml.template $HADOOP_HOME/etc/hadoop/mapred-site.xml
   vi $HADOOP_HOME/etc/hadoop/mapred-site.xml

   # Add the following:
   <configuration>
       <property>
           <name>mapreduce.framework.name</name>
           <value>yarn</value>
       </property>
   </configuration>

7. Configure YARN:
   vi $HADOOP_HOME/etc/hadoop/yarn-site.xml

   # Add the following:
   <configuration>
       <property>
           <name>yarn.nodemanager.aux-services</name>
           <value>mapreduce_shuffle</value>
       </property>
   </configuration>

## 8. Format the HDFS Filesystem:
   hdfs namenode -format

## 9. Set Up SSH for Passwordless Access:
   ssh-keygen -t rsa -P ""
   cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys

## 10. Start Hadoop Daemons:
   cd /data/hadoop/hadoop/sbin/
    ./start-all.sh

## 11. Verify Installation:
   jps

## 12. Access Hadoop Web Interfaces:
   - NameNode: http://localhost:9870
   - ResourceManager: http://localhost:8088
