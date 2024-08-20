Changing Heap Dump Location
If your Spark job encounters memory issues and generates heap dumps, you can specify the location for these dumps via JVM options.

Set JVM Options for Driver and Executors:

bash
Copy code
spark-submit \
  --conf "spark.driver.extraJavaOptions=-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/custom/path/driver-heapdump.hprof" \
  --conf "spark.executor.extraJavaOptions=-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/custom/path/executor-heapdump.hprof" \
  your_spark_job.py
-XX:+HeapDumpOnOutOfMemoryError: This option triggers a heap dump when an OutOfMemoryError occurs.
-XX:HeapDumpPath: Specifies the directory or file path where the heap dump will be stored.



