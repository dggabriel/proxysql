# Setup MySQL Replica

--Do the following after executing the ansible scripts

[Primary Database]
1. Execute this to mysql "show master status"
2. Take note of the following:
  - master log filename
  - master log position
  
[Secondary Database]
1. Execute this to mysql "select uuid();'
2. Take note of the output of the query above.
3. Copy the output and change it on this file /var/lib/mysql/auto.cnf.
4. Execute this to mysql:
change master to 
master_host='<primary-host-ip>',
master_user='<monitor-username>',
master_password='<monitor-password',
master_log_file='<primary binlog file>',
master_log_pos=<primary binlog position>;
5. Then execute this "START REPLICA;'
6. Execute this to check replica status "SHOW REPLICA STATUS \G;"


  

