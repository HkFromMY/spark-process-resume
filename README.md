### Reflection on using Spark for processing data
1. When there's deadlock, please set to more partitions, one of the CPU cores may not be handling big chunks of data and cause that.
2. Ensure that each partition has similar number of records to yield the syokness (high performance) of Spark, because if the partition is skewed (where 1 partition has significantly much more records), then it's no difference than sequential processing.
3. `df.withColumn` to transform existing column, you can chain them like `df.withColumn().withColumn()` to form a pipeline-like process.
4. Use the built-in function such as `regexp_replace` provided by Spark for better readability and performance, rather than using User-Defined Function (UDF) unless you have no choice.
