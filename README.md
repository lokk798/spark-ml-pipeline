# spark-ml-pipeline

# Create HDFS directory
docker exec namenode hdfs dfs -mkdir -p /data

# Upload the file
docker exec namenode hdfs dfs -put /tmp/Iris.csv /data/

# Verify it's there
docker exec namenode hdfs dfs -ls /data