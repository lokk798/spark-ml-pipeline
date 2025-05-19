# Spark ML Pipeline - Iris Dataset Classification

## Problem Statement

The goal of this project is to build a machine learning pipeline using Apache Spark to classify iris flower species based on their morphological measurements. The Iris dataset contains features such as sepal length, sepal width, petal length, and petal width, and the target is to correctly predict the species of iris flowers.

## Why Spark?

- **Scalability:** Spark can efficiently process large datasets distributed across a cluster, making it suitable for big data applications.
- **Speed:** Spark’s in-memory computation allows faster data processing compared to traditional MapReduce frameworks.
- **Ease of Use:** The Spark MLlib library provides high-level APIs to build machine learning pipelines that integrate feature extraction, transformation, and model training.
- **Integration with HDFS:** Spark works seamlessly with HDFS for data storage and retrieval in distributed environments.

## Project Structure and Steps

1. **Initialize Spark Session:** Connect to a Spark cluster.
2. **Load Dataset:** Read the Iris CSV file from HDFS into a Spark DataFrame.
3. **Data Preparation:** Inspect data, drop unnecessary columns (like `Id`), and understand feature columns.
4. **Feature Engineering:** Use `VectorAssembler` to combine feature columns into a single vector column.
5. **Label Indexing:** Convert categorical labels (species) into numeric indices for model compatibility.
6. **Split Dataset:** Divide data into training (70%) and testing (30%) sets.
7. **Model Training:** Train a Decision Tree classifier using a Spark ML Pipeline.
8. **Prediction:** Generate predictions on the test data.
9. **Evaluation:** Evaluate model accuracy using Spark’s `MulticlassClassificationEvaluator`.

## How to Run

### Prerequisites

- Docker with Spark and HDFS configured (e.g., using a Docker Compose setup).
- Jupyter Notebook installed or accessible.
- The Iris dataset file placed in HDFS at `/data/Iris.csv`.

### Why We Used Docker

    Consistent Environment: Docker ensures the Spark cluster, HDFS, and all dependencies run in a consistent, isolated environment across different machines, eliminating the "it works on my machine" problem.

    Simplified Setup: Using Docker containers makes it easy to set up a multi-node Spark cluster and HDFS quickly without manual installation and complex configurations.

    Portability: The entire environment can be easily shared, deployed, or reproduced by simply sharing the Docker configuration files.

    Resource Isolation: Containers provide resource isolation, allowing safe parallel execution of different services like Spark master, workers, and HDFS nodes on the same host.

    Integration Testing: Docker enables testing of the full distributed stack (Spark + HDFS) locally, closely simulating a production cluster setup.

### Getting started

```bash
# Clone the project
git clone https://github.com/lokk798/spark-ml-pipeline.git

cd spark-ml-pipeline
```

```bash
# Run the docker-compose file
docker-compose up -d

# Create directory in HDFS for data
docker exec namenode hdfs dfs -mkdir -p /data

# Upload Iris.csv file to HDFS
docker exec namenode hdfs dfs -put /tmp/Iris.csv /data/

# Verify file upload
docker exec namenode hdfs dfs -ls /data

# Go to jupyter notebook
http://localhost:8888/
```
