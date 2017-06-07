# assignment16.3

[acadgild@localhost ~]$ create table student (id int, name string,dept string,grade int) clustered by (id) into 3 buckets stored as orc TBLPROPERTIES('transactional' = 'true');
bash: syntax error near unexpected token `('
[acadgild@localhost ~]$ hive
/usr/local/hive/bin/hive-config.sh: line 1: syntax error near unexpected token `('
/usr/local/hive/bin/hive-config.sh: line 1: `﻿# Licensed to the Apache Software Foundation (ASF) under one or more'

Logging initialized using configuration in jar:file:/usr/local/hive/lib/hive-common-0.14.0.jar!/hive-log4j.properties
SLF4J: Class path contains multiple SLF4J bindings.
SLF4J: Found binding in [jar:file:/usr/local/hive/lib/hive-jdbc-0.14.0-standalone.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: Found binding in [jar:file:/usr/local/hadoop-2.6.0/share/hadoop/common/lib/slf4j-log4j12-1.7.5.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: See http://www.slf4j.org/codes.html#multiple_bindings for an explanation.
SLF4J: Actual binding is of type [org.slf4j.impl.Log4jLoggerFactory]
hive> create table student (id int, name string,dept string,grade int) clustered by (id) into 3 buckets stored as orc TBLPROPERTIES('transactional' = 'true');
OK
Time taken: 205.09 seconds
hive> 
    > 
    > show tables;
OK
student
Time taken: 1.059 seconds, Fetched: 1 row(s)
hive> INSERT into table student  values (1,'suresh','EEE',2),(2,'akash','ECE',1),(3,'aswini','IT',2),(4,'pavani','EEE',2);
Query ID = acadgild_20170607083434_21bb0378-d3dc-443e-a9d7-016d2177bdda
Total jobs = 1
Launching Job 1 out of 1
Number of reduce tasks is set to 0 since there's no reduce operator
Starting Job = job_1496801093662_0001, Tracking URL = http://localhost:8088/proxy/application_1496801093662_0001/
Kill Command = /home/acadgild/hadoop-2.6.0/bin/hadoop job  -kill job_1496801093662_0001
Interrupting... Be patient, this might take some time.
Press Ctrl+C again to kill JVM
killing job with: job_1496801093662_0001
Hadoop job information for Stage-1: number of mappers: 0; number of reducers: 0
2017-06-07 08:35:48,452 Stage-1 map = 0%,  reduce = 0%
Ended Job = job_1496801093662_0001 with errors
Error during job, obtaining debugging information...
FAILED: Execution Error, return code 2 from org.apache.hadoop.hive.ql.exec.mr.MapRedTask
MapReduce Jobs Launched: 
Stage-Stage-1:  HDFS Read: 0 HDFS Write: 0 FAIL
Total MapReduce CPU Time Spent: 0 msec
hive> select * from student;
OK
Time taken: 3.273 seconds
hive> desc student;
OK
id                  	int                 	                    
name                	string              	                    
dept                	string              	                    
grade               	int                 	                    
Time taken: 1.194 seconds, Fetched: 4 row(s)
hive> INSERT INTO table student values (1,'suresh','EEE',2),(2,'akash','ECE',1),(3,'aswini','IT',2),(4,'pavani','EEE',2);
Query ID = acadgild_20170607083939_9731f820-1ea7-4395-ad7d-a5c334d26c51
Total jobs = 1
Launching Job 1 out of 1
Number of reduce tasks is set to 0 since there's no reduce operator
Starting Job = job_1496801093662_0002, Tracking URL = http://localhost:8088/proxy/application_1496801093662_0002/
Kill Command = /home/acadgild/hadoop-2.6.0/bin/hadoop job  -kill job_1496801093662_0002
Hadoop job information for Stage-1: number of mappers: 1; number of reducers: 0
2017-06-07 08:42:39,553 Stage-1 map = 0%,  reduce = 0%
2017-06-07 08:43:40,179 Stage-1 map = 0%,  reduce = 0%
2017-06-07 08:44:41,093 Stage-1 map = 0%,  reduce = 0%, Cumulative CPU 10.31 sec
2017-06-07 08:44:50,030 Stage-1 map = 100%,  reduce = 0%, Cumulative CPU 12.72 sec
MapReduce Total cumulative CPU time: 12 seconds 720 msec
Ended Job = job_1496801093662_0002
Stage-4 is selected by condition resolver.
Stage-3 is filtered out by condition resolver.
Stage-5 is filtered out by condition resolver.
Moving data to: hdfs://localhost:9000/tmp/hive/acadgild/cb69abeb-1d6b-4904-b8eb-ab3637464b12/hive_2017-06-07_08-39-19_350_6072334645953101728-1/-ext-10000
Loading data to table default.student
Table default.student stats: [numFiles=1, numRows=4, totalSize=468, rawDataSize=732]
MapReduce Jobs Launched: 
Stage-Stage-1: Map: 1   Cumulative CPU: 13.5 sec   HDFS Read: 334 HDFS Write: 540 SUCCESS
Total MapReduce CPU Time Spent: 13 seconds 500 msec
OK
Time taken: 361.26 seconds
hive> 
    > select * from student;
OK
1	suresh	EEE	2
2	akash	ECE	1
3	aswini	IT	2
4	pavani	EEE	2
Time taken: 0.399 seconds, Fetched: 4 row(s)
