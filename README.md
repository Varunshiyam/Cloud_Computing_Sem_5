# 🧠 Experiment No: 8  
**Date:** 01/06/2025  

## 🚀 INSTALL AND CONFIGURE A HADOOP SINGLE-NODE CLUSTER AND EXECUTE A SAMPLE APPLICATION (WORDCOUNT)

---

## 🎯 AIM
To install and configure a Hadoop single-node cluster and execute a sample application (WordCount) to validate the setup.

---

## 🧩 SOFTWARE / TOOLS USED
- **Operating System:** Ubuntu 20.04 LTS (or compatible Linux distribution)  
- **Java Development Kit (JDK):** Java 8 (OpenJDK 1.8.0)  
- **Hadoop Version:** Apache Hadoop 3.x (stable release)  
- **Terminal / Command Line Interface**  
- **Text Editor:** gedit, nano, or vim  
- **SSH (Secure Shell):** Enabled for localhost communication  

---

## 💡 APPLICATIONS
- **Big Data Processing:** Enables distributed processing of large datasets using the MapReduce programming model.  
- **Data Analysis and Mining:** Supports tasks such as word frequency analysis, log parsing, and ETL operations.  
- **Educational and Research Purpose:** Provides a simulated Hadoop environment for academic learning, testing, and prototyping.  

---

## ⚙️ PROCEDURE

### **Step 1: Download Java 8 Package**
Download the Java 8 Development Kit (JDK) and save it in the home directory.  
Ensure compatibility with Hadoop by using **Java 1.8.x only.**


```bash
tar -xvf jdk-8u101-linux-i586.tar.gz
```

### **Step 2: Download Hadoop Package**

Download Hadoop 2.7.3 from the Apache archives.

```
wget https://archive.apache.org/dist/hadoop/core/hadoop-2.7.3/hadoop-2.7.3.tar.gz
```

### **Step 3: Configure Environment Variables**

Open the .bashrc file:

```
vi ~/.bashrc
```

```
# Java Environment
export JAVA_HOME=~/jdk1.8.0_101
export PATH=$JAVA_HOME/bin:$PATH

# Hadoop Environment
export HADOOP_HOME=~/hadoop-2.7.3
export HADOOP_INSTALL=$HADOOP_HOME
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_COMMON_HOME=$HADOOP_HOME
export HADOOP_HDFS_HOME=$HADOOP_HOME
export YARN_HOME=$HADOOP_HOME
export PATH=$PATH:$HADOOP_HOME/bin:$HADOOP_HOME/sbin
```

### **Step 4: Verify Installations**

Check Java version:

```
java -version
```


Check Hadoop version:

```
hadoop version
```

### **Step 5: Edit Hadoop Configuration Files**

Navigate to configuration directory:

```
cd ~/hadoop-2.7.3/etc/hadoop/
ls
```
### **Step 6: Configure core-site.xml**

```
<configuration>
   <property>
       <name>fs.defaultFS</name>
       <value>hdfs://localhost:9000</value>
   </property>
</configuration>

```

### **Step 7: Configure hdfs-site.xml**

```
<configuration>
   <property>
       <name>dfs.replication</name>
       <value>1</value>
   </property>

   <property>
       <name>dfs.namenode.name.dir</name>
       <value>file:///home/hduser/hadoopdata/hdfs/namenode</value>
   </property>

   <property>
       <name>dfs.datanode.data.dir</name>
       <value>file:///home/hduser/hadoopdata/hdfs/datanode</value>
   </property>
</configuration>
```

### **Step 8: Configure mapred-site.xml**

- If not available, copy from template:

```
cp mapred-site.xml.template mapred-site.xml
vi mapred-site.xml
```

- Insert:
```
<configuration>
   <property>
       <name>mapreduce.framework.name</name>
       <value>yarn</value>
   </property>
</configuration>
```

### **Step 9: Configure yarn-site.xml**

```
<configuration>
   <property>
       <name>yarn.nodemanager.aux-services</name>
       <value>mapreduce_shuffle</value>
   </property>
   <property>
       <name>yarn.nodemanager.auxservices.mapreduce.shuffle.class</name>
       <value>org.apache.hadoop.mapred.ShuffleHandler</value>
   </property>
</configuration>
```

### **Step 10: Configure hadoop-env.sh**

- Edit file:
```
vi hadoop-env.sh
```

- Add:
```
export JAVA_HOME=/home/username/jdk1.8.0_101

```

(Replace /home/username/ with your actual path.)

----
