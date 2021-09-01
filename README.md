# log-analysis
## Project introduction
In this project, SparkSQL log analysis can be combined with Flume and Kafka to import data. Perform data analysis on the log, clean the log information to convert it into a suitable format, perform multi-dimensional statistical analysis on the cleaned data, and print the results of the statistical analysis to MySQL to facilitate data visualization.

## poject architecture
![image](https://github.com/chengkangck/log-analysis/blob/main/images/offline%20and%20online.png)

### data processing steps

User behavior log: all behavior data (visit, browse, search, click...) every time the user visits the website
    User behavior trajectory, traffic log
 
Log data content:
1) Accessed system properties: operating system, browser, etc.
2) Access features: the url clicked, which url was the referer from, the stay time on the page, etc.
3) Access information: session_id, access ip (visit city), etc.
 
2013-05-19 13:00:00 http://www.taobao.com/17/?tracker_u=1624169&type=1 B58W48U4WKZCJ5D1T3Z9ZY88RU7QA7B1 http://hao.360.cn/ 1.196.34.243
 
Data processing flow
1) Data collection
    Flume: write web logs to HDFS
 
2) Data cleaning
    Dirty data
    Spark, Hive, MapReduce or some other distributed computing framework
    After cleaning, the data can be stored in HDFS (Hive/Spark SQL)
 
3) Data processing
    Perform statistics and analysis of the corresponding business according to our needs
    Spark, Hive, MapReduce or some other distributed computing framework
 
4) Warehousing of processing results
    Results can be stored in RDBMS, NoSQL
 
5) Visualization of data
    Displayed through graphical display: pie chart, bar chart, map, line chart
    ECharts, HUE, Zeppelin
 
The general log processing method, we need to partition,
Perform corresponding partitions according to the access time in the log, such as: d, h, m5 (a partition every 5 minutes)
 
Input: access time, access URL, traffic consumed, access IP address information
Output: URL, cmsType (video/article), cmsId (number), traffic, ip, city information, access time, day
