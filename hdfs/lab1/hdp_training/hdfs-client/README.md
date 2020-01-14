mvn clean install -X

scp target/hdfs-client-1.0-SNAPSHOT.jar root@<your-cluster-mgt-node>:/tmp/artifacts/

create a file sample.txt with some content into it.

hadoop jar hdfs-client-1.0-SNAPSHOT.jar com.guavus.training.hdfs.FileSystemOperations hdfs://gvstraining01:8020 add sample.txt hdfs://gvstraining01:8020/tmp/

hadoop jar hdfs-client-1.0-SNAPSHOT.jar com.guavus.training.hdfs.FileSystemOperations hdfs://gvstraining01:8020 read hdfs://gvstraining01:8020/tmp/sample.txt

