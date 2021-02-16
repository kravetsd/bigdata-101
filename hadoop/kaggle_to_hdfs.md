## 1. Downloading dataset using kaggle api, unzip:
```
[root@sandbox-hdp ~]# kaggle competitions download -c expedia-hotel-recommendations                                                                                    
Downloading expedia-hotel-recommendations.zip to /root                                                                                                                 
100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████▉| 686M/686M [01:11<00:00, 10.5MB/s]
100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 686M/686M [01:11<00:00, 10.1MB/s]
                                                                                                                          
[root@sandbox-hdp ~]# ll                                                                                                                                               
total 702708                                                                                                                                                           
-rw------- 1 root root      3302 May 31  2018 anaconda-ks.cfg                                                                                                          
-rw-r--r-- 1 root root 719563791 Feb 14 11:36 expedia-hotel-recommendations.zip
[root@sandbox-hdp ~]# unzip expedia-hotel-recommendations.zip                                                                                                          
Archive:  expedia-hotel-recommendations.zip                                                                                                                            
  inflating: destinations.csv                                                                                                                                          
  inflating: sample_submission.csv                                                                                                                                     
  inflating: test.csv                                                                                                                                                  
  inflating: train.csv                                                                                                                                                 
[root@sandbox-hdp ~]#                                                                                                                                  
```
## 2. Moved to tmp:
```
root@sandbox-hdp ~]# ll /tmp/*.csv                                                                                                                                    
-rw-r--r-- 1 root root  138159416 Dec 15  2019 /tmp/destinations.csv                                                                                                   
-rw-r--r-- 1 root root   31756066 Dec 15  2019 /tmp/sample_submission.csv                                                                                              
-rw-r--r-- 1 root root  276554476 Dec 15  2019 /tmp/test.csv                                                                                                           
-rw-r--r-- 1 root root 4070445781 Dec 15  2019 /tmp/train.csv  
```
## 3. moving files to HDFS:
```                                                                                                        
[root@sandbox-hdp ~]# su - hdfs -c "hadoop fs -put /tmp/*.csv /user/admin "                                                                                            
[root@sandbox-hdp ~]# hdfs dfs -ls /user/admin                                                                                                                         
Found 5 items                                                                                                                                                          
drwxr-xr-x   - admin hdfs          0 2021-02-14 11:58 /user/admin/.Trash                                                                                                
-rw-r--r--   1 hdfs  hdfs  138159416 2021-02-14 11:56 /user/admin/destinations.csv                                                                                      
-rw-r--r--   1 hdfs  hdfs   31756066 2021-02-14 11:56 /user/admin/sample_submission.csv                                                                                 
-rw-r--r--   1 hdfs  hdfs  276554476 2021-02-14 11:56 /user/admin/test.csv                                                                                              
-rw-r--r--   1 hdfs  hdfs 4070445781 2021-02-14 11:58 /user/admin/train.csv                                                                                             
[root@sandbox-hdp ~]#                                                                     
```