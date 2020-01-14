mvn clean install -X

scp target/hdfs-client-1.0-SNAPSHOT.jar root@<your-cluster-mst-node>:/tmp/artifacts/

ssh to <your-cluster-mst-node>

# From MST NODE
kinit -kt /etc/security/keytabs/cdap.headless.keytab cdap-gvstraining01@GVS.GGN
klist to verify


pw=`exec pwd`; hadoop jar target/hdfs-client-1.0-SNAPSHOT.jar ProcessLogs -D mapreduce.framework.name=local file://${pw}/access_log file://${pw}/output

OPTIONAL
pw=`exec pwd`; hadoop jar target/hdfs-client-1.0-SNAPSHOT.jar ProcessLogs -D mapreduce.framework.name=yarn file://${pw}/access_log file://${pw}/output 



hdfs dfs -put access_log /tmp/ ; hadoop jar target/hdfs-client-1.0-SNAPSHOT.jar ProcessLogs -D mapreduce.framework.name=local /tmp/access_log /tmp/output
